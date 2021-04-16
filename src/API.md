# Hole Frontend API

<!-- ## Loginning and Registration -->

<!-- ### Registration request -->
<!-- On base of password will be generted keypair for signing and keypair for encoding. -->
<!-- ``` json -->
<!--     { -->
<!--     request_type: "registration", -->
<!--     username: "user", -->
<!--     password: "passwd123", -->
<!--     } -->
<!-- ``` -->


<!-- ### Login request -->
<!-- ```json -->
<!--     { -->
<!--     request_type: login, -->
<!--     username: "name", -->
<!--     decode_key: "key", -->
<!--     sign_key: "key", -->
<!--     } -->
<!-- ``` -->

<!-- ## Adding friends -->
<!-- Each user have :w -->

----

# Requests 
``` Rust
pub enum Request {
    StartApp,
        StopApp,
        LoadUsers,
        #[serde(rename_all = "camelCase")]
        SendMessage {
            user_id: Id,
            message: String,
        },
        #[serde(rename_all = "camelCase")]
        LoadMessages {
            user_id: Id,
            count: u32,
            start_index: u32,
        },
        #[serde(rename_all = "camelCase")]
        AddUser {
            name: String,
            sign_key: String,
            insert_key: String,
        }, //    CreateInstance TODO v0.3
}
```
## `StartApp`
Require when when client started.
``` json
{
     type: "startApp"
}
```

## `StopApp`
``` json
{
    type: "stopApp"
}
```
## `LoadUsers`
``` json
{
    type: "loadUsers"
}
```
## `SendMessage`
``` json
{
    type: "sendMessage",
    userId: "UUID_V4...",
    message: "hellow world"
}
```
## `AddUser`
``` json
{
    type: "addUser",
    name: "username",
    signKey: "USK@key...",
    insertKey: "insertkey..."
}
```
## `LoadMessages`
Requesting `count` messages from `userId` started from `startIndex`'s message
``` json
{
    type: "loadMessages",
    userId: "UUID_V4...",
    count: 10,
    startIndex: 30
}
```
