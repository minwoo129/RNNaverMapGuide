# react native 네이버맵 연결 가이드

## 패키지 공식문서

---

[GitHub - QuadFlask/react-native-naver-map: 🗺️naver map for react-native](https://github.com/quadflask/react-native-naver-map)

## **연결 순서**

---

- [ ]  클라이언트 id 설정
- [네이버클라우드](https://www.ncloud.com/) 플랫폼 접속

![스크린샷 2021-10-18 오후 5 58 11](https://user-images.githubusercontent.com/73742422/137847372-50dfbe8a-81d3-4a0d-9dd3-8ae1c3e5a4ce.png)

- 로그인 및 회원가입 후 콘솔 접속

![스크린샷 2021-10-18 오후 5.58.52.png](react%20native%20%E1%84%82%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A5%E1%84%86%E1%85%A2%E1%86%B8%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B3%20f905de882eba474a941c04bf04cdf764/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-10-18_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_5.58.52.png)

- Products & Services → AI-Application Service → AI.NAVER API → Maps 접근

![스크린샷 2021-10-18 오후 5.59.56.png](react%20native%20%E1%84%82%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A5%E1%84%86%E1%85%A2%E1%86%B8%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B3%20f905de882eba474a941c04bf04cdf764/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-10-18_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_5.59.56.png)

- Application 등록 선택

![스크린샷 2021-10-18 오후 6.02.51.png](react%20native%20%E1%84%82%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A5%E1%84%86%E1%85%A2%E1%86%B8%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B3%20f905de882eba474a941c04bf04cdf764/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-10-18_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_6.02.51.png)

- Maps 전체 선택

![스크린샷 2021-10-18 오후 6.04.58.png](react%20native%20%E1%84%82%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A5%E1%84%86%E1%85%A2%E1%86%B8%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B3%20f905de882eba474a941c04bf04cdf764/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-10-18_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_6.04.58.png)

- 프로젝트 안드로이드 패키지명, ios bundle ID 입력 후 저장
- 저장 후 발급받은 인증정보(client ID, client Secret) 복사 후 기록해두기
- [ ]  패키지 설치

yarn add react-native-nmap

cd ios & pod install

- [ ]  프로젝트 설정
- 네이버 공식 sdk 레포지토리 경로: [https://naver.jfrog.io/artifactory/maven/](https://naver.jfrog.io/artifactory/maven/)
- 안드로이드 설정
    - /android/build.gradle 파일에 네이버맵 sdk 레포지토리 경로 추가
    
    ```jsx
    buildscript {
        ext {
            buildToolsVersion = "29.0.3"
            minSdkVersion = 21
            compileSdkVersion = 29
            targetSdkVersion = 29
            ndkVersion = "20.1.5948944"
            googlePlayServicesAuthVersion = "16.0.1" // <--- use this version or newer
            kotlinVersion = '1.3.41'
        }
        repositories {
            google()
            jcenter()
        }
        dependencies {
            classpath("com.android.tools.build:gradle:4.1.0")
            // classpath 'com.google.gms:google-services:4.1.0' // <--- use this version or newer
            classpath 'com.google.gms:google-services:4.3.3' // <--- use this version or newer
            // NOTE: Do not place your application dependencies here; they belong
            // in the individual module build.gradle files
            classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlinVersion"
        }
    }
    
    allprojects {
        repositories {
            mavenLocal()
            maven {
                // All of React Native (JS, Obj-C sources, Android binaries) is installed from npm
                url("$rootDir/../node_modules/react-native/android")
            }
            maven {
                // Android JSC is installed from npm
                url("$rootDir/../node_modules/jsc-android/dist")
            }
            google()
            jcenter()
            // 아래 부분만 적용하면 됨
            maven { url 'https://naver.jfrog.io/artifactory/maven/'}
            maven { url 'https://www.jitpack.io' }
            maven { url 'https://devrepo.kakao.com/nexus/content/groups/public/' }
        }
    }
    
    subprojects {
      repositories {
        mavenCentral()
        maven { url 'http://devrepo.kakao.com:8088/nexus/content/groups/public/' }
      }
    }
    ```
    
    - /android/app/sec/AndroidManifest.xml 파일에 네이버 인증정보 추가
    
    ```xml
    <manifest xmlns:android="http://schemas.android.com/apk/res/android"
      package="com.banmoapp"
      xmlns:tools="http://schemas.android.com/tools">
    
        <uses-permission android:name="android.permission.INTERNET" />
        <uses-permission android:name='android.permission.CAMERA' />
        <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    
        <application
          android:name=".MainApplication"
          android:label="@string/app_name"
          android:icon="@mipmap/ic_launcher"
          android:roundIcon="@mipmap/ic_launcher_round"
          android:allowBackup="false"
          tools:replace="android:allowBackup"
          android:fullBackupContent="false"
          android:theme="@style/AppTheme"
          android:usesCleartextTraffic="true"
          android:requestLegacyExternalStorage="true">
          // 하단의 코드만 추가하면 됨
          <meta-data 
            android:name="com.naver.maps.map.CLIENT_ID"
            android:value="{네이버 client ID}"
          />
          <activity
            android:name=".MainActivity"
            android:label="@string/app_name"
            android:configChanges="keyboard|keyboardHidden|orientation|screenSize|uiMode"
            android:launchMode="singleTask"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="adjustResize">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
          </activity>
          <!--추가-->
          <activity android:name="com.kakao.sdk.auth.AuthCodeHandlerActivity">
            <intent-filter>
                <action android:name="android.intent.action.VIEW" />
                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />
                <data android:host="oauth"
                    android:scheme="kakao5620410cb011932f3bd9aee3ac931150" />
            </intent-filter>
    ```
    
    - /android/app/build.gradle 파일에 sdk 의존성 선언
    
    ```xml
    ...
    
    dependencies {
    
        ...
    
        // 하단의 코드만 추가하면 됨
        implementation 'com.naver.maps:map-sdk:{sdk버전(사이트 확인후 최신버전으로 매칭)}'
    
        ...
    }
    
    ...
    ```
    
- ios 설정
    - git-lfs 설치
        - sudo gem install cocoapods
        - brew install git-lfs
        - git-lfs install
        - pod install —repo-update
            
            (만약 최신버전으로 업데이트가 안될 경우 아래와 같이 sdk 의존성 선언을 하고 위 명령어를 다시 실행할 것)
            
            경로: /ios/Podfile
            
            ```xml
            require_relative '../node_modules/react-native/scripts/react_native_pods'
            require_relative '../node_modules/@react-native-community/cli-platform-ios/native_modules'
            
            platform :ios, '11.0'
            
            target 'banmoApp' do
              config = use_native_modules!
            
              use_react_native!(
                :path => config[:reactNativePath],
                # to enable hermes on iOS, change `false` to `true` and then install pods
                :hermes_enabled => false
              )
              permissions_path = '../node_modules/react-native-permissions/ios'
              
              pod 'Firebase/Core','~> 6.13.0'
              pod 'Firebase/Messaging'
              pod 'Firebase/Analytics'
              pod 'GoogleSignIn', '~> 5.0.2'
             // 하단의 코드만 추가할 것
              pod 'NMapsMap','{네이버맵 sdk버전(안드로이드에서 매칭한 sdk 버전과 맞출 것)}'
              pod 'Permission-PhotoLibrary', :path => "#{permissions_path}/PhotoLibrary"
            
              target 'banmoAppTests' do
                inherit! :complete
                # Pods for testing
              end
            
              # Enables Flipper.
              #
              # Note that if you have use_frameworks! enabled, Flipper will not work and
              # you should disable the next line.
              use_flipper!()
            
              post_install do |installer|
                react_native_post_install(installer)
              end
            end
            ```
            
        
    - info.plist 네이버 인증정보 추가
    
    ```xml
    <코드: 예시>
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
    	<key>CFBundleDevelopmentRegion</key>
    	<string>ko_KR</string>
    	<key>CFBundleDisplayName</key>
    	<string>{앱 이름}</string>
    	<key>CFBundleExecutable</key>
    	<string>$(EXECUTABLE_NAME)</string>
    	<key>CFBundleIdentifier</key>
    	<string>$(PRODUCT_BUNDLE_IDENTIFIER)</string>
    	<key>CFBundleInfoDictionaryVersion</key>
    	<string>6.0</string>
    	<key>CFBundleName</key>
    	<string>$(PRODUCT_NAME)</string>
    	<key>CFBundlePackageType</key>
    	<string>APPL</string>
    	<key>CFBundleShortVersionString</key>
    	<string>$(MARKETING_VERSION)</string>
    	<key>CFBundleSignature</key>
    	<string>????</string>
    	<key>CFBundleURLSchemes</key>
    	<array>
    		<string>kakao5620410cb011932f3bd9aee3ac931150</string>
    	</array>
    	<key>CFBundleURLTypes</key>
    	<array>
    		<dict>
    			<key>CFBundleTypeRole</key>
    			<string>Editor</string>
    			<key>CFBundleURLName</key>
    			<string>naverlogin</string>
    			<key>CFBundleURLSchemes</key>
    			<array>
    				<string>naverlogin</string>
    			</array>
    		</dict>
    		<dict>
    			<key>CFBundleTypeRole</key>
    			<string>Editor</string>
    			<key>CFBundleURLSchemes</key>
    			<array>
    				<string>com.googleusercontent.apps.130610169974-8tmjrb509oq9jl0jhh1ed349j4hjota8</string>
    			</array>
    		</dict>
    		<dict>
    			<key>CFBundleTypeRole</key>
    			<string>Editor</string>
    			<key>CFBundleURLSchemes</key>
    			<array>
    				<string>kakao5620410cb011932f3bd9aee3ac931150</string>
    			</array>
    		</dict>
    	</array>
    	<key>CFBundleVersion</key>
    	<string>1</string>
    	<key>KAKAO_APP_KEY</key>
    	<string>5620410cb011932f3bd9aee3ac931150</string>
    	<key>LSApplicationQueriesSchemes</key>
    	<array>
    		<string>kakaokompassauth</string>
    		<string>instagram://camera</string>
    		<string>instagram</string>
    		<string>kakao5620410cb011932f3bd9aee3ac931150</string>
    		<string>storykompassauth</string>
    		<string>kakaolink</string>
    		<string>kakaotalk-5.9.7</string>
    		<string>naversearchapp</string>
    		<string>naversearchthirdlogin</string>
    	</array>
    	<key>LSRequiresIPhoneOS</key>
    	<true/>
                // 하단의 코드만 추가할 것
    	<key>NMFClientId</key>
    	<string>{네이버 client ID}</string>
    	<key>NSAppTransportSecurity</key>
    	<dict>
    		<key>NSAllowsArbitraryLoads</key>
    		<true/>
    		<key>NSExceptionDomains</key>
    		<dict>
    			<key>localhost</key>
    			<dict>
    				<key>NSExceptionAllowsInsecureHTTPLoads</key>
    				<true/>
    			</dict>
    		</dict>
    	</dict>
    	<key>NSCameraUsageDescription</key>
    	<string>사진 및 동영상 촬영/녹화 및 첨부를 하기 위해 카메라 접근 권한을 허용해주세요.
    (동/식물 사진 등록, 프로필 이미지 첨부, 이미지 첨부)</string>
    	<key>NSLocationWhenInUseUsageDescription</key>
    	<string>'반모'이(가) 사용자의 위치를 사용하도록 허용하겠습니까? 지도 첨부 위치 공유를 위해 위치 정보를 사용하도록 허용해주세요.</string>
    	<key>NSMicrophoneUsageDescription</key>
    	<string>동영상 촬영/녹화 및 첨부를 하기 위해 마이크 접근 권한을 허용해주세요.</string>
    	<key>NSPhotoLibraryUsageDescription</key>
    	<string>이미지 첨부 및 저장을 위해 포토 라이브러리 권한을 허용해주세요.</string>
    	<key>UIAppFonts</key>
    	<array>
    		<string>Fonts/NotoSansKR-Black.otf</string>
    		<string>Fonts/NotoSansKR-Bold.otf</string>
    		<string>Fonts/NotoSansKR-DemiLight.otf</string>
    		<string>Fonts/NotoSansKR-Light.otf</string>
    		<string>Fonts/NotoSansKR-Medium.otf</string>
    		<string>Fonts/NotoSansKR-Regular.otf</string>
    		<string>Fonts/NotoSansKR-Thin.otf</string>
    		<string>Fonts/S-CoreDream-1Thin.ttf</string>
    		<string>Fonts/S-CoreDream-2ExtraLight.ttf</string>
    		<string>Fonts/S-CoreDream-3Light.ttf</string>
    		<string>Fonts/S-CoreDream-4Regular.ttf</string>
    		<string>Fonts/S-CoreDream-5Medium.ttf</string>
    		<string>Fonts/S-CoreDream-6Bold.ttf</string>
    		<string>Fonts/S-CoreDream-7ExtraBold.ttf</string>
    	</array>
    	<key>UIBackgroundModes</key>
    	<array>
    		<string>fetch</string>
    		<string>remote-notification</string>
    	</array>
    	<key>UILaunchStoryboardName</key>
    	<string>LaunchScreen</string>
    	<key>UIRequiredDeviceCapabilities</key>
    	<array>
    		<string>armv7</string>
    	</array>
    	<key>UISupportedInterfaceOrientations</key>
    	<array>
    		<string>UIInterfaceOrientationPortrait</string>
    	</array>
    	<key>UIUserInterfaceStyle</key>
    	<string>Light</string>
    	<key>UIViewControllerBasedStatusBarAppearance</key>
    	<false/>
    </dict>
    </plist>
    ```
    

### 유의사항

- react-native 버전이 0.64.0인 경우 app 강제종료 현상이 확인됨(안드로이드)
    - 확인결과 react-native 버전의 내부 구조적 문제로 확인됨
    - 최소 0.64.2버전 이상으로 업데이트 필요
- 네이버맵 패키지 버전이 0.0.56 인 경우 지도가 표시가 안되는 문제가 발생됨
    - 확인결과: 해당 패키지의 내부 오류로 확인(개발자가 확인 후 업데이트 하였음)
    - 버전 업데이트 권장
    

## 패키지 제공 컴포넌트

---

- NaverMapView
- Marker: 마커
- Polyline: 직선
- Path
- Circle: 원형 범위 설정
- Polygon: 다각형 범위 지정

## 컴포넌트 별 props 핵심 정리

---

- 기본타입

```jsx
export interface Coord {
    latitude: number;
    longitude: number;
}
export interface Region extends Coord {
    latitudeDelta: number;
    longitudeDelta: number;
}
export interface Rect {
    left?: number;
    top?: number;
    right?: number;
    bottom?: number;
}
```

- NaverMapView

[NaverMapView](react%20native%20%E1%84%82%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A5%E1%84%86%E1%85%A2%E1%86%B8%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B3%20f905de882eba474a941c04bf04cdf764/NaverMapView%20f4be4ff301424c8fa6c077aee319c1e3.csv)

- Marker

[Marker](react%20native%20%E1%84%82%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A5%E1%84%86%E1%85%A2%E1%86%B8%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B3%20f905de882eba474a941c04bf04cdf764/Marker%20652642b1b04b48409b1d9466816ab05a.csv)

- Polyline

[Polyline](react%20native%20%E1%84%82%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A5%E1%84%86%E1%85%A2%E1%86%B8%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B3%20f905de882eba474a941c04bf04cdf764/Polyline%206057d3c089564f71aeaf83638f2061d8.csv)

- Path

[Path](react%20native%20%E1%84%82%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A5%E1%84%86%E1%85%A2%E1%86%B8%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B3%20f905de882eba474a941c04bf04cdf764/Path%2089c917053e424448b74c0fe1c6f2cba8.csv)

- Circle

[Circle](react%20native%20%E1%84%82%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A5%E1%84%86%E1%85%A2%E1%86%B8%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B3%20f905de882eba474a941c04bf04cdf764/Circle%20aa7f9c4cec874e42a8cdb07d0d7bcb71.csv)

## 부가기능

---

1. **geocoding**
    1. 개요: 주소의 텍스트를 받아 좌표를 포함한 상세정보로 변환하는 기능
    2. api url
        1. 메서드: GET
        2. 인증: id(client ID), key(client Secret)
        3. 요청 url: https://naveropenapi.apigw.ntruss.com/map-geocode/v2/geocode
        4. 응답형식: JSON
    3. 요청 헤더
        1. X-NCP-APIGW-API-KEY-ID: client ID
        2. X-NCP-APIGW-API-KEY: client Secret
        3. Accept: 응답포멧(JSON(def), XML)
    4. 요청 파라미터
    
    [요청 파라미터](react%20native%20%E1%84%82%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A5%E1%84%86%E1%85%A2%E1%86%B8%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B3%20f905de882eba474a941c04bf04cdf764/%E1%84%8B%E1%85%AD%E1%84%8E%E1%85%A5%E1%86%BC%20%E1%84%91%E1%85%A1%E1%84%85%E1%85%A1%E1%84%86%E1%85%B5%E1%84%90%E1%85%A5%206c4eca26fa4d44f7b441ed221b942be3.csv)
    
    ### 실행 예시 코드
    
    ```jsx
    NaverGeocoding('분당구 불정로 6')
    .then((res) => {
    	console.log(res);
    })
    
    const NaverGeocoding = (addr) => {
        return new Promise((resolve) => {
            fetch(`https://naveropenapi.apigw.ntruss.com/map-geocode/v2/geocode?query=${addr}`, {
                headers: {
                    'X-NCP-APIGW-API-KEY-ID': CLIENT_ID,  // 네이버 client id
                    'X-NCP-APIGW-API-KEY': CLIENT_SECRET // 네이버 client secret
                }
            })
            .then((res) => {
                resolve(res.json());
            })
        });
    }
    ```
    
2. **reverse geocoding**
    1. 개요: 위경도 좌표를 이용해 주소정보로 변환하는 기
    2. api url
        1. method: GET
        2. 인증: id(client ID), key(client Secret)
        3. 요청 url: https://naveropenapi.apigw.ntruss.com/map-reversegeocode/v2/gc
        4. 응답형식: JSON, XML
    3. 요청 헤더
        1. X-NCP-APIGW-API-KEY-ID: client ID
        2. X-NCP-APIGW-API-KEY: client Secret
    4. 요청 파라미터
    
    [요청 파라미터](react%20native%20%E1%84%82%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A5%E1%84%86%E1%85%A2%E1%86%B8%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%83%E1%85%B3%20f905de882eba474a941c04bf04cdf764/%E1%84%8B%E1%85%AD%E1%84%8E%E1%85%A5%E1%86%BC%20%E1%84%91%E1%85%A1%E1%84%85%E1%85%A1%E1%84%86%E1%85%B5%E1%84%90%E1%85%A5%200992ec223ee243df800099084419d6dc.csv)
    
    ### 실행 예시 코드
    
    ```jsx
    NaverReverseGeocoding(`${경도},${위도}`)
    .then(res) => {
    	console.log(res)
    })
    
    const NaverReverseGeocoding = (coords) => {
        return new Promise((resolve) => {
            fetch(`https://naveropenapi.apigw.ntruss.com/map-reversegeocode/v2/gc?coords=${coords}&orders=legalcode&output=json`, {
                headers: {
                    'X-NCP-APIGW-API-KEY-ID': CLIENT_ID,  // 네이버 client id
                    'X-NCP-APIGW-API-KEY': CLIENT_SECRET  // 네이버 client secret
                }
            })
            .then((res) => {
                resolve(res.json());
            })
        });
    }
    ```
