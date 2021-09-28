# developerPrivate API

Beside normal APIs Chrome uses some special APIS internally. One of these is the `developerPrivate` API, which grants
access to special developer features.

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

https://github.com/chromium/chromium/blob/ef3c0b7e3f9387e57570cdfd6c7e65ee5add4ec9/chrome/common/extensions/api/_permission_features.json#L222

https://stackoverflow.com/questions/35932942/how-to-load-build-chrome-app-extension-and-run-programmatically/35951201#35951201