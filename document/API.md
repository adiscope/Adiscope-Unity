# Adiscope SDK Documentation for Unity
<br>

- Interface
	- Core
		- GetCoreInstance
		- Initialize
		- SetUserId
		- GetUnitStatus
	- Offerwall
		- GetOfferwallAdInstance
		- Show
	- RewardedVideo
		- GetRewardedVideoAdInstance
		- Load
		- IsLoaded
		- Show
	- Interstitial
		- GetInterstitialAdInstance
		- Load
		- IsLoaded
		- Show
	- OptionSetter
		- SetUseCloudFrontProxy
		- SetChildYN
		- SetUseOfferwallWarningPopup
		- SetUseAppTrackingTransparencyPopup
		- SetEnabledForcedOpenApplicationSetting
	- OptionGetter
		- GetNetworkVersions

<br><br>


### Interface
<br>

#### Core
##### GetCoreInstance

Adiscope의 핵심 기능이 있는 Singleton객체를 가져옵니다.

<br>

##### Initialize

Adiscope SDK 초기화를 진행합니다.

| Parameters     |              |
| ----------- | ------------------------------------------------------------ |
| mediaID     | Amdin page에서 등록한 해당 application에 대한 ID             |
| mediaSecret | mediaId에 대응되는 Secret key                                |
| callBackTag | 보상 콜백을 복수 개로 등록해서 사용할시에 어떤 보상 콜백을 사용할지 지정. 지정하지 않을시에는 기본 보상콜백이 사용. |

##### SetUserId

Application 사용자의 Unique Id를 설정. 이 정보는 reward 지급 등에 있어 사용자를 구분하는데 사용합니다.

- ⚠️ UserID의 최대 길이는 32자 입니다.

| Parameters |                     |
| ---------- | ------------------- |
| userId     | 고유한 유저의 ID 값 |

| Return     |                                     |
| ---------- | ----------------------------------- |
| isSuccesss | UserID의 형식이 잘못 되었을 경우 NO |

<br>

##### GetUnitStatus

유닛의 상태 정보를 구한다. AdiscopeDelegate의 onGetUnitStatus() callback을 통해 결과를 받습니다.

- ⚠️ `initialize` 가 먼저 호출되어야 합니다.

| Parameters |                                                    |
| ---------- | -------------------------------------------------- |
| unitId     | 얻고자 하는 Offerwall 혹은 Rewarded Video의 UnitID |

<br>

#### Offerwall
##### GetOfferwallAdInstance
##### Show

Adiscope 의 Offerwall ViewController 를 Display 합니다.

- ⚠️ `initialize` 가 먼저 호출되어야 합니다.

| Parameters |                           |
| ---------- | ------------------------- |
| unitId     | 보여질 Offerwall의 UnitID |

| Return     |                              |
| ---------- | ---------------------------- |
| isSuccesss | UnitID이 잘못 되었을 경우 NO |

<br>

#### RewardedVideo
##### GetRewardedVideoAdInstance
##### Load

Application 에서 사용할 수 있는 모든 Rewarded Video 관련 Framework 를 load 하며, unitId 에 해당하는 광고를 Pre-load 합니다.

- ⚠️ `initialize` 가 먼저 호출되어야 합니다.

| Parameters |                                |
| ---------- | ------------------------------ |
| unitId     | 로드 할 RewardedVideo의 UnitID |

<br>

##### IsLoaded

unitId 에 해당하는 광고가 load 되어 있는지 여부 확인 합니다.

- ⚠️ `initialize` 가 먼저 호출되어야 합니다.
- ⚠️ `show` method 를 call 하기 전, `isLoaded` 를 통해 show 가능 여부를 확인합니다.

| Parameters |                                           |
| :--------- | ----------------------------------------- |
| unitId     | load 여부를 체크할 RewardedVideo의 UnitID |
| **Return** |                                           |
| isReady       | show할 광고가 존재할 경우 YES             |

<br>

##### Show

Adiscope 에 설정된 순번으로 load 된 광고를 보여줍니다.

- ⚠️ `initialize` 가 먼저 호출되어야 합니다.
- ⚠️ `show` method 를 call 하기 전, `isLoaded` 를 통해 show 가능 여부를 확인합니다.
- ⚠️ Rewarded Video 의 정확한 보상정보 처리를 위해 `setUserId` 를 미리 설정해야 합니다.

| Return |                                      |
| :----- | ------------------------------------ |
| isReady   | 로드된 광고가 가용할 수 없을 경우 NO |

<br>

#### Interstitial
##### GetInterstitialAdInstance
##### Load

Application 에서 사용할 수 있는 모든 Interstitial 관련 Framework 를 load 하며, unitId 에 해당하는 광고를 Pre-load 합니다.

- ⚠️ `initialize` 가 먼저 호출되어야 합니다.

| Parameters |                               |
| ---------- | ----------------------------- |
| unitId     | 로드 할 Interstitial의 UnitID |

<br>

##### IsLoaded

unitId 에 해당하는 광고가 load 되어 있는지 여부 확인 합니다.

- ⚠️ `initialize` 가 먼저 호출되어야 합니다.
- ⚠️ `show` method 를 call 하기 전, `isLoaded` 를 통해 show 가능 여부를 확인합니다.

| Parameters |                                          |
| :--------- | ---------------------------------------- |
| unitId     | load 여부를 체크할 Interstitial의 UnitID |
| **Return** |                                          |
| isReady       | show할 광고가 존재할 경우 YES            |

<br>

##### Show

Adiscope 에 설정된 순번으로 load 된 광고를 보여줍니다.

- ⚠️ `initialize` 가 먼저 호출되어야 합니다.
- ⚠️ `show` method 를 call 하기 전, `isLoaded` 를 통해 show 가능 여부를 확인합니다.

| Return |                                      |
| :----- | ------------------------------------ |
| isReady   | 로드된 광고가 가용할 수 없을 경우 NO |

<br>

#### OptionSetter
##### SetUseCloudFrontProxy

AWS Cloud Front Proxy를 사용 유무를 설정합니다.

이 옵션을 사용하게되면, 북미, 유럽에서 게임을 서비스할시에 Adiscope API의 응답속도가 향상됩니다.

| Parameters         |                                 |
| :----------------- | ------------------------------- |
| useCloudFrontProxy | AWS Cloud Front Proxy 사용 유무 |

<br>

##### SetChildYN

- ⚠️ Supported Android

##### SetUseOfferwallWarningPopup

Adiscope 의 Offerwall ViewController 를 Display 할 때, iOS 설정중 광고 차단 기능이 활성화 되었을 때, 안내 팝업 표시를 설정합니다.
Default 설정은 YES 입니다.

- ⚠️ Supported only iOS 11+

| Parameters |                           |
| ---------- | ------------------------- |
| useOfferWallWarningPopup     | Offerwall 경고 팝업 표시 유/무 |

<br>

##### SetUseAppTrackingTransparencyPopup

iOS의 ATT Popup을 띄울지 설정합니다. 
Default 설정은 YES 입니다.

- ⚠️ Supported only iOS 11+

| Parameters |                           |
| ---------- | ------------------------- |
| useAppTrackingTransparencyPopup     | ATT 팝업 표시 유/무 |

<br>

##### SetEnabledForcedOpenApplicationSetting

권한이 없는 팝업에서, confirm버튼이 앱의 설정으로 이동하는 Flag입니다. 
Default 설정은 NO 입니다.

- ⚠️ Supported only iOS 11+

| Parameters |                           |
| ---------- | ------------------------- |
| enabledForcedOpenApplicationSetting     | 강제 이동 유/무 |

<br>

#### OptionGetter
##### GetNetworkVersions

Adiscope SDK Version 을 확인합니다.

| Return     |                              |
| :--------- | ---------------------------- |
| String | Adiscope.framework의 Version |

<br>