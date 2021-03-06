# Activity

### 액티비티란?
 >액티비티란 ~~ test test test test 진행 중



### Activity Lifecycle
<img width="534" alt="스크린샷 2021-02-18 오후 11 40 55" src="https://user-images.githubusercontent.com/52733201/108373149-e6c4d780-7242-11eb-8266-cc36ed7ea22e.png">



* onCreate()
 >이 함수는 필수적으로 구현해야한다. 이 메서드는 전체 생명주기 동안 "한 번"만 발생한다.
  이 메서드에는 XML, 멤버 변수 정의, 일부 UI 구성 등 설정을 한다.



* onStart()
 >활성상태에 들어가면 이 메서드가 호출된다(사용자한테 보여지기 직전). 이 함수가 호출되면 포그라운드에 보내 상호작용할 수 있도록 준비한다. 
  이 메서드에서는 주로 앱이 UI를 관리하는 코드를 초기화 한다. 이 메서드는 매우 빠르게 완료되고 바로 onResume을 호출한다.



* onResume()
 >사용자한테 화면에 보여지고 상호작용하는 메서드이다. 어떤 이벤트가 발생하여 앱에서 포커스가 떠날 때까지 이 상태에 머무른다.
  이 상태에서는 생명주기 구성요소가 포그라운드에서 사용자에게 보이는 동안 실행해야 하는 모든 기능을 활성화 한다.(예: 카메라 미리보기)
  방해가 되는 이벤트가 발생하면 일시중지 상태에 들어가고, 시스템이 onPause를 호출한다. (예: 전화가 오거나, 사용자가 다른 화면으로 이동하거나, 기기 화면이 꺼질때)



* onPause()
 >사용자가 화면을 떠날 때 시스템이 첫 번째로 이 메서드를 호출한다. (상태가 포그라운드에 있지 않게 되었다는 것을 나타냄)
  포그라운드에 있지 않을 때 실행할 필요가 없는 기능을 모두 정지할 수 있다.(예: 카메라 미리보기 정지) 또한, 시스템 리소스, 센서 핸들(GPS), 사용자가 필요로 하지 않을 때 배터리 수명에 영향을 미칠 수 있는 모든 리  소스를 해제할 수도 있다. UI 관련 리소스와 작업을 완전히 해제하거나 조정할 때는 onPause 보다 onStop을 사용하는 것이 좋다. (멀티 윈도우 모드 떄문, 화면분할 or pip)
  이 메서드는 아주 잠깐 실행되므로 저장 작업을 하기에는 시간이 부족할 수 있다. 사용자 데이터를 저장하거나, 네트워크를 호출하거나, 데이터베이스 트랜잭션을 실행해서는 안된다. 이 메서드가 끝나기 전에 완료하지 못할 수 있다! 무거운 작업은 onStop에서 하고 데이터 저장은 viewmodel, onSaveInstanceState()를 참조하자.
  (일반적인 다이얼로그는 activity가 아니기 때문에 onPause를 호출하지 않는다. 권한요청은 다이얼로그처럼 보이는 ui일 뿐 실제로 동작은권한을 허용할 것인지 거절할 것인지에 대한 ui를 띄우므로 onPause를 호출한다)



* onStop()
 >포커스가 완전히 빠졌을 때 시스템은 이 콜백 메서드를 호출한다. (화면전체가 가려졌을때 또는 백그라운드로 갔을 때)
  이 메서드에서는 앱이 사용자에게 보이지 않는 동안 앱이 필요하지 않은 리소스를 해제하거나 조정해야 한다. (예: 애니메이션 중지, 세밀한 위치 업데이트에서 대략적인 위치 업데이트로 전환할 수 있다) 
  onStop에서 무거운 작업을 실행해야 한다고 했는데 예를들어 정보를 데이터베이스에 저장해야하는데 적절한 위치를 찾지 못했다면 이 메서드에서 저장할 수 있다.
  사용자가 포그라운드로 다시 돌아오게 된다면 onRestart()를 호출하고 Activity가 종료되면 시스템은 onDestroy()를 호출한다.



* onDestroy()
 >애기비티가 소멸되기 전에 호출된다. 시스템은 다음 중 하나에 해당할 때 이 콜백을 호출한다.
  -활동이 종료되는 경우(스택에서 날리거나 finish()를 호출)
  -구성 변경(예: 기기회전 또는 멀티 윈도우 모드)으로 인해 시스템이 일시적으로 활동을 소멸시키는 경우
   onStop에서 해제하지 않은 모든 리소스를 해제해야 한다.
   이 메서드가 호출되는 경우 시스템이 즉시 인스턴스를 생성한 다음, 새로운 구성에서 인스턴스에 관해 onCreate()를 호출한다.



* onRestart()
 >onStop상태에 있던 화면이 다시 화면에 접근 했을 때 호출되는 콜백함수





---


Click [Here](https://developer.android.com/guide/components/activities/activity-lifecycle#onpause)
