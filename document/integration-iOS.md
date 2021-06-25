# Unity Integration for iOS
## Unity 설정
1. Unity Package 추가
	- AdiscopeUnitySdk.unitypackage 파일을 Import합니다. 
		- Assets > Import Package > Custom Package 메뉴
2. (Optional) PostProcessBuild 설정
	1. 다음의 위치에 폴더를 생성합니다. 
		- Assets/Plugins/iOS
	2. `.framework` 파일을 (1)의 폴더위치에 옮깁니다.
		- Adiscope.framework
		- AdiscopeMediaUnityAds.framework
		- UnityAds.framework
	3. 빌드를 진행합니다.
	4. _(Check up!)_ 두번째 빌드 시, Xcode내의 실행할 Scheme의 `Build Phases` 탭의 `Embed Framework` 에 Adiscope가 중복 표시되었을 경우에 체크되어있지 않는 Adiscope.framework를 삭제합니다.
3. (Optional) Manual 추가
	1. BuildPostProcessor.cs 삭제합니다.
		- Assets/Adiscope/Editor/Scripts에 위치함.
	2. [Manual iOS Integration](https://github.com/adiscope/Adiscope-iOS-Sample/blob/main/Installation_manual.md)을 따라 진행합니다.
