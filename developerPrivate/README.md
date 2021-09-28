# developerPrivate API

Beside normal APIs Chrome uses some special ("private") ones internally. One of these is the `developerPrivate` API, which grants
access to features regarding extensions.

## API reference

```json
{
  "onProfileStateChanged": {},
  "onItemStateChanged": {},
  "CommandScope": {
    "CHROME": "CHROME",
    "GLOBAL": "GLOBAL"
  },
  "ErrorLevel": {
    "ERROR": "ERROR",
    "LOG": "LOG",
    "WARN": "WARN"
  },
  "ErrorType": {
    "MANIFEST": "MANIFEST",
    "RUNTIME": "RUNTIME"
  },
  "EventType": {
    "COMMAND_ADDED": "COMMAND_ADDED",
    "COMMAND_REMOVED": "COMMAND_REMOVED",
    "ERRORS_REMOVED": "ERRORS_REMOVED",
    "ERROR_ADDED": "ERROR_ADDED",
    "INSTALLED": "INSTALLED",
    "LOADED": "LOADED",
    "PERMISSIONS_CHANGED": "PERMISSIONS_CHANGED",
    "PREFS_CHANGED": "PREFS_CHANGED",
    "SERVICE_WORKER_STARTED": "SERVICE_WORKER_STARTED",
    "SERVICE_WORKER_STOPPED": "SERVICE_WORKER_STOPPED",
    "UNINSTALLED": "UNINSTALLED",
    "UNLOADED": "UNLOADED",
    "VIEW_REGISTERED": "VIEW_REGISTERED",
    "VIEW_UNREGISTERED": "VIEW_UNREGISTERED",
    "WARNINGS_CHANGED": "WARNINGS_CHANGED"
  },
  "ExtensionState": {
    "BLACKLISTED": "BLACKLISTED",
    "DISABLED": "DISABLED",
    "ENABLED": "ENABLED",
    "TERMINATED": "TERMINATED"
  },
  "ExtensionType": {
    "EXTENSION": "EXTENSION",
    "HOSTED_APP": "HOSTED_APP",
    "LEGACY_PACKAGED_APP": "LEGACY_PACKAGED_APP",
    "PLATFORM_APP": "PLATFORM_APP",
    "SHARED_MODULE": "SHARED_MODULE",
    "THEME": "THEME"
  },
  "FileType": {
    "LOAD": "LOAD",
    "PEM": "PEM"
  },
  "HostAccess": {
    "ON_ALL_SITES": "ON_ALL_SITES",
    "ON_CLICK": "ON_CLICK",
    "ON_SPECIFIC_SITES": "ON_SPECIFIC_SITES"
  },
  "ItemType": {
    "EXTENSION": "extension",
    "HOSTED_APP": "hosted_app",
    "LEGACY_PACKAGED_APP": "legacy_packaged_app",
    "PACKAGED_APP": "packaged_app",
    "THEME": "theme"
  },
  "Location": {
    "FROM_STORE": "FROM_STORE",
    "THIRD_PARTY": "THIRD_PARTY",
    "UNKNOWN": "UNKNOWN",
    "UNPACKED": "UNPACKED"
  },
  "PackStatus": {
    "ERROR": "ERROR",
    "SUCCESS": "SUCCESS",
    "WARNING": "WARNING"
  },
  "SelectType": {
    "FILE": "FILE",
    "FOLDER": "FOLDER"
  },
  "ViewType": {
    "APP_WINDOW": "APP_WINDOW",
    "BACKGROUND_CONTENTS": "BACKGROUND_CONTENTS",
    "COMPONENT": "COMPONENT",
    "EXTENSION_BACKGROUND_PAGE": "EXTENSION_BACKGROUND_PAGE",
    "EXTENSION_DIALOG": "EXTENSION_DIALOG",
    "EXTENSION_GUEST": "EXTENSION_GUEST",
    "EXTENSION_POPUP": "EXTENSION_POPUP",
    "EXTENSION_SERVICE_WORKER_BACKGROUND": "EXTENSION_SERVICE_WORKER_BACKGROUND",
    "TAB_CONTENTS": "TAB_CONTENTS"
  },
  "addHostPermission": "function",
  "allowFileAccess": "function",
  "allowIncognito": "function",
  "autoUpdate": "function",
  "choosePath": "function",
  "deleteExtensionErrors": "function",
  "enable": "function",
  "getExtensionInfo": "function",
  "getExtensionSize": "function",
  "getExtensionsInfo": "function",
  "getItemsInfo": "function",
  "getProfileConfiguration": "function",
  "inspect": "function",
  "installDroppedFile": "function",
  "isProfileManaged": "function",
  "loadDirectory": "function",
  "loadUnpacked": "function",
  "notifyDragInstallInProgress": "function",
  "openDevTools": "function",
  "packDirectory": "function",
  "reload": "function",
  "removeHostPermission": "function",
  "repairExtension": "function",
  "requestFileSource": "function",
  "setShortcutHandlingSuspended": "function",
  "showOptions": "function",
  "showPath": "function",
  "showPermissionsDialog": "function",
  "updateExtensionCommand": "function",
  "updateExtensionConfiguration": "function",
  "updateProfileConfiguration": "function"
}
```

## Further explanations

The permission is only available to packaged apps ("Apps"), this means we need to add the `app` entry and specify a script inside it.
We also need to define the `developerPrivate` and `management` permissions. If we don't define the second one, `developerPrivate` will be null.
The `key` has to be set, as the permission is only available to selected extensions. 

There are several whitelisted extensions. You can use one of the following values for the `key` attribute:
- `MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA2OvldPjAqgEboHyyZM7GpCMmGMSQ8aExOlQyOhN3C9fDRXqnAN/Ie20TEwD9Eb2CciV3Ru4Gm7PmDnkHzsljD84qLgBdN39FzPGDyViXTS442xTElWRZMZQfJYQpbMpiePL720kTHgLLAcwTgdP9DnvRPrKukIs/U4Y76NFk7NNbsNOc6FWisLJykw2POTB1RR5ZlZrA4Ax1P7kt7qQdomE6i8wy1TA1jDhG8AhEXKRfpyELvJmzyVIyR9uiSHDHCdihiS5oyjADjmmbklvL7Ns0cSAgEX/lWN8UX8r17zoKZzJ0MkmCQ5Nlfql8qUtn2oZXaHztkkAcXCxkq9/37QIDAQAB`
- `MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAiC2CjQDYZcE1Pn8QHpLh1F32QiJqcO63CObY4ulPEHHmIDfIyflB2WXc7D1bDJtHBahkJEtHY4I8wN8gjowgYVKiiqMpwiuV7Evivyf7Qyvg537Kb0aBdGKVFCpk12H/Z9k835BTWZ3t/uk/ZK2r4fwUF06LYWtZ3XS1W5OrV0NTxGF/keX4qidKMDl3pKLNjKPSPl0G3WFEMui+L68VnC2HzCfrpyrC1/oGGLTa2xg/lkEZhzuUUjWsar8YazZYmVPmZQOjdyls/tGxrVac3IcDaSve40PuKgmmn7H2Gb1h4NKRbDTgBhqmIewQCGpuHMRf/EXNDROhNCx2byStkwIDAQAB`
- `MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAwqXKrcvbi1a1IjFM5COs07Ee9xvPyOSh9dhEF6kwBGjAH6/4F7MHOfPk+W04PURi707E8SsS2iCkvrMiJPh4GnrZ3fWqFUzlsAcUljcYbkyorKxglwdZEXWbFgcKVR/uzuzXD8mOcuXRLu0YyVSdEGzhfZ1HkeMQCKEncUCL5ziE4ZkZJ7I8YVhVG+uiROeMg3zjxxSQrYHOfG5HOqmVslRPCfyiRbIHH3JPD0lax5FudngdKy0+1nkkqVJCpRSf75cRRnxGPjdEvNzTEFmf5oGFxSVs7iXoVQvNXB35Qfyw5rV6N+JyERdu6a7xEnz9lbw41m/noKInlfP+uBQuaQIDAQAB`
- `MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDV/GMX7sjLe3ceUizalvfZK0qhsWnXcjJ3cCbYvXFo43Q2F7SZM8/0roex0wSpNRSO1j9c/m7YXLYBAOiy21ERRJEVEIvOvWp1LLeoBSsbQnnhSPKInqUrkA8fMRCqI0gHRUK3K7dIiOC2A7jkWUMs4DqRiQSkntUUGzVIoY6OYQIDAQAB`
- `MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDIhi5zNAGD4SvQyCSVCj7KIt4w3OX0r9S7VFdxtzhagQVm58Kuz5XoJsbIhISEHjukldlZQZn9s0e9x1aK/s48ZJMe5KHyv6o0pYsslPEMro3aZG8bkPW9HMUMHe9uhyhw2DT90UMzWrOatOdj2QI41J+9Q4eP2TgXBTfJstE5QQIDAQAB`

## References

- [Permission features](https://github.com/chromium/chromium/blob/ef3c0b7e3f9387e57570cdfd6c7e65ee5add4ec9/chrome/common/extensions/api/_permission_features.json#L222)
- [Whitelisted extensions](https://stackoverflow.com/questions/35932942/how-to-load-build-chrome-app-extension-and-run-programmatically/35951201#35951201)
- [developerPrivate implementation](https://github.com/chromium/chromium/blob/ef3c0b7e3f9387e57570cdfd6c7e65ee5add4ec9/third_party/closure_compiler/externs/developer_private.js)