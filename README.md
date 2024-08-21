# kakao_talk
The **kakao_talk** platform uses KakaoTalk to deliver notifications from [Home Assistant][hass] to your Android device, your Windows phone, or your iOS device.

<div>
  <img width="600" src="https://user-images.githubusercontent.com/11463289/69047831-69a72300-0a3f-11ea-9382-94141f96a88e.png"/>
</div>

## Installation

HACS
* Custom repositories
```
  Repository:
    https://github.com/clipman/kakao_talk
  Category:
    Integration
```
* Kakao Talk Download
* Restart the Home Assistant service

## Setup

The requirements are:
* You need the REST API Key for KakaoTalk.

To enable KakaoTalk notifications in your installation, add the following to your `configuration.yaml` file:
```
kakao_talk:
  api_key: YOUR_API_KEY
  redirect_uri: YOUR_HASSIO_URL
  send_to_friends: True
  
notify:
  - name: kakaotalk_noti
    platform: kakao_talk

```

Restart the Home Assistant service.

And type YOUR_HASSIO_URL/api/kakao_talk on the web browser such as Chrome, Firefox...<br>
You can see below screen then you can find the Login Redirection URI, 
it should be input Login Redirection URI on the Kakao Development site.<br>
![Kakao_Login_Screen](https://user-images.githubusercontent.com/11463289/69050463-73cc2000-0a45-11ea-8445-734e60556bd1.png)

Login KakaoTalk service by clicking '카카오톡 로그인' button.<br>

## Configuration

To use notifications, please see the [getting started with automation page][hass2].

### Text message

```yaml
...
action:
  service: notify.NOTIFIER_NAME
  data:
    title: Send a message
    message: That''s an example that _sends_ a formatted message with a custom inline keyboard.
```

#### CONFIGURATION VARIABLES
* **title:**
>>  **description**: Will be composed as '%title\n%message'.<br>
>>  **required**: false<br>
>>  **type**: string<br>
* **message:**
>>  **description**: Message text.<br>
>>  **required**: true<br>
>>  **type**: string<br>

### Photo support

```yaml
...
action:
  service: notify.NOTIFIER_NAME
  data:
    title: Send an images
    message: That''s an example that sends an image.
    data:
      photo:
        - url: https://i.ibb.co/jkbTKZz/hassio.png
```

#### CONFIGURATION VARIABLES
* **url:**
>>  **description**: A remote path to an image.<br>
>>  **required**: true to support Photo<br>
>>  **type**: string<br>

![image_sample](https://user-images.githubusercontent.com/11463289/69052464-6e250900-0a4a-11ea-8c5c-844caa8d9983.png)

[hass]: https://home-assistant.io
[hass2]: https://www.home-assistant.io/getting-started/automation/
