# macOS sandbox-exec profiles
This is a repository of profiles for Apple's ```sandbox-exec``` for usage with different Applications.  
All profiles have been somewhat reverese-engineered by using the following boilerplate for a ```profile.sb``` file. And after creation of the first profile with which the app actually starts the output of Console.app executed as root via sudo.

````
(version 1)
(deny default)
(trace "output.sb")
`````
What these three lines do is to do two things.  
First: ignore ```(deny default)``` and allow everything to enable execution as usual  
Second: Log everything that would otherwise have been denied into ```output.sb```

This might look like this:
`````
(version 1) ; Sun Aug 13 14:26:31 2017
(allow mach-lookup (global-name "com.apple.distributed_notifications@Uv3"))
(allow mach-lookup (global-name "com.apple.coreservices.launchservicesd"))
(allow mach-lookup (global-name "com.apple.lsd.mapdb"))
(allow mach-lookup (global-name "com.apple.CoreServices.coreservicesd"))
(allow mach-lookup (global-name "com.apple.CoreServices.coreservicesd"))
(allow mach-lookup (global-name "com.apple.CoreServices.coreservicesd"))
(allow mach-lookup (global-name "com.apple.windowserver.active"))
(allow mach-lookup (global-name "com.apple.windowserver.active"))
(allow mach-lookup (global-name "com.apple.windowserver.active"))
(allow mach-lookup (global-name "com.apple.dock.server"))
(allow ipc-posix-shm-read-data (ipc-posix-name "/tmp/com.apple.csseed.184"))
(allow iokit-open (iokit-registry-entry-class "RootDomainUserClient"))
(allow mach-lookup (global-name "com.apple.fonts"))
(allow mach-lookup (global-name "com.apple.FSEvents"))
(allow mach-lookup (global-name "com.apple.FSEvents"))
(allow mach-lookup (global-name "com.apple.FSEvents"))
(allow mach-lookup (global-name "com.apple.pbs.fetch_services"))
(allow file-read-data (path "/Library/Application Support/CrashReporter/SubmitDiagInfo.domains"))
...
`````
