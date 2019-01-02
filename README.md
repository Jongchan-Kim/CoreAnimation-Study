# CoreAnimation-Study

## Chapter1: Getting Started with View Animations

#### Your first animation
UIView의 클래스메서드인 animate메서드를 이용해서 애니메이션을 적용 할 수 있다.
withDuration 파라미터는 애니메이션 지속시간, delay 파라미터는 애니메이션의 시작

#### Animatable properties
애니메이션 적용가능한 프로퍼티는 bounds, frame, center, backgroundColor, alpha, transform(로테이션, 스케일, 위치)이 있다.

#### Animation options
Repeat 옵션을 통해 무한반복 할수 있고, autoreverse를 통해 반복시 정방향-역방향-정방향-역방향-... 의 움직임을 설정 할 수 있다.

#### Animation easing
애니메이션 실행속도를 조절하기위한 옵션들로 .curveLinear, .curveEaseIn, .curveEaseOut, .curveEaseInOut 이 있다.

## Chapter2: Springs

#### Spring animations
animate(withDuration:delay:usingSpringWithDamping:initialSpringVelocity:optio ns:animations:completion:)을 이용해서 Spring애니메이션을 적용 할 수 있다.
usingSpringWithDamping은 0~1 값으로 설정가능하며 0에가까울수록 더 튕기는 애니메이션이 강해진다.
initialSpringVelocity는 애니메이션이 실행되는 시간을 설정한다.
1.0으로 설정하면 속도가 애니메이션 총거리/s 와 같이 설정된다.
따라서 velocity라는 파라미터명을 갖고있지만 값이 클수록 느려진다.(사실상 시간개념인듯) => X잘못됨. 초기에 시작속도

#### Animating user interactions
초기뿐만아니라 유저의 버튼 탭 액션시에도 애니메이션을 적용할 수 있다.

## Chapter3: Transitions

#### Example transitions
Transition은 뷰에 적용할 수 있는 미리 정의된 애니메이션이다.
이전장과는 달리 Animation container view에 트랜지션 이펙트를 적용한다.
제거, 숨김, 뷰변경등에 이용가능하다.

#### Mixing in transitions
completion블럭을 이용해서 애니메이션을 조합할 수 있다

## Chapter4: View Animations in Practice

#### Crossfading animations
UIView.transition의 transitionCrossDissolve 옵션을 통해 배경이미지를 교체하고, 눈내리는배경뷰의 alpha를 조정하는 애니메이션 예제
transition으로 imageView, textView 등은 바로내용전환가능

#### Cube transitions
label.transform = .identity는 x, y, rotate 값을 원상태로 복구한다.

두개의 라벨을 이용해서 하나는 scale을 1/10으로 줄이고 원래대로 복구되며 하나는 원상태에서 점점커지는 식으로 같은방향으로 애니메이션 시켜서 주사위가 돌아가듯이 애니메이션 적용할수있다(신기하네요!..)

#### Fade and bounce transitions
기존뷰와 신규애니메이션뷰 2개를 교차시킬때 duration과 delay를 이용해서 라벨을 오버랩시키고, 기존뷰의 애니메이션이 적용되는 도중 신규애니메이션뷰의 컴플리션블럭이 실행되면서 바운스 효과를 줌.

남은 0.15초의 애니메이션 시간동안에는 0,35초 후에 실행되는 completion 블럭에서 변경된 transform 값으로 애니메이션이 실행이 되는것으로 보이는데 스터디시간에 같이논의해보면 좋을 것 같습니다. =>  애니메이션블록의 시간이 남아있으면 중간에 변경된 프로퍼티값 감지해서 그변경된 값에 대한 애니메이션수행

## Chapter 5: Keyframe Animations

#### Keyframe animation
animateKeyframes(withDuration:delay:options:animations:completion:)을 이용해서 키프레임 애니메이션을 설정할 수있다.
옵션파라미터는 animate에사용되는 옵션과 달리 UIViewKeyFrameAnimationOptions 을따른다.

#### Adding keyframes
animateKeyframes메서드안에 addKeyframe(withRelativeStartTime:relativeDuration:animations)을 이용해 각 프레임에 대한 설정을 할 수 있다.
withRelativeStartTime, relativedurations 는 0~1의 값으로 totalduration의 %개념(0.5 = totalduration의 50% )

Animate 함수는 딜레이 되어 처리되는것이아님(논 애니메이션프로퍼티는 즉시반영)

## Chapter 6: Introduction to Auto Layout
#### Auto Layout to the rescue

#### Auto Layout Constraint
스토리보드를 이용한 AutoLayout 설정에대한 설명
First Item = Multiplier * Second Item + Constant

#### Finalizing the UI
Ctrl + drag 를 활용해서 아울렛 연결 및 기타 스토리보드에서의 설정에대한설명

## Chapter 7 : Animating Constraints
#### Animating Interface Builder constraints
NSLayoutConstraints의 constant 값 변경과 버튼 로테이트 애니메이션을 통해 효과적용

#### Inspecting and animating constraints
NSLayoutConstraints의 firstItem, firstAttribute 를 이용해서 로직에 활용 가능

#### Animating by replacing constraints
스토리보드에서 Constraint의 identifer값을 지정해서 로직에 활용가능
NSLayoutConstraints의 isActive를 true로 설정하거나 NSLayoutConstraints.activate(_:)를 이용해서 코드로 생성한 오토 레이이아웃을 설정가능 activate메서드 같은경우에는 여러개 컨스트레인트들을 배열형태로 받아 처리가능

#### Adding menu content
#### Animating dynamically created views
컨스트레인트를 코드로 설정하고, constant를 변경하는 애니메이션을통해 아래에서 위로 올라오면서 길이가 커지는 스프링애니메이션예제
view.layoutIfNeeded()를 호출해주어야만 애니메이션이 정상적으로 작동한다.

#### Challenges
위의 소챕터에서 적용한 애니메이션을 다시 되돌리는(숨기는) 애니메이션 적용


## Chapter 8: Getting Started with Layer Animation
레이어는 뷰보다 더 많은 애니메이션 가능 속성을 갖고 있다. CALayer를 이용하여 애니메이션에 이용할 수 있다.

#### Animatable Properties
Border, Shadow 뿐만 아니라 contents, mask 도 애니메이션가능한 속성이다.

#### Your first layer animation
코어애니메이션의 객체들은 데이터 모델이어서 인스턴스를 생성하고 속성들을 지정해주면된다.
CABasicAnimation(keyPath:)의 keyPath에 애니메이션 시킬 속성값을 넣어 인스턴스를 생성하고 애니메이션 설정값을 할당 한뒤 레이어에 add하면 애니메이션이 적용된다.

#### More elaborate layer animations
CABasicAnimation의 beginTime 속성은 절대시간이며 CACurrentMediaTime() + delay 현재시간 + delay형태로 설정 할 수 있고, 이 속성을 설정해서 애니메이션 시작시간을 설정할 수 있다.
fillMode를 이용해서 애니메이션 시작과 끝에 대한 처리방법(애니메이션 전/후 프레임)을 바꿀수있다. 
fillMode 옵션은 kCAFillModeRemoved, kCAFillModeBackwords, kCAFillModeForwards, kCAFillModeBoth 이 있다.

#### Debugging basic animations View UI Hierarchy를 이용한 디버깅 방법 소개

#### Animations vs real content
isRemovedOnCompletion 속성은 true가 기본값으로 설정되어 있어, 애니메이션 완료 후 사라진다.
레이어를 이용한 애니메이션을 사용 할때 인터페이스빌더에서 설정할 레이아웃은 애니메이션의 최종값으로 설정하고, fromValue를 시작값이나 중간값으로 설정하는게 좋다.

#### Best Practices
가능하면 fillMode를 사용하지 않고 애니메이션을 구현하는게 좋다

#### Challenges
 1. 구름 fadeIn 애니메이션 적용하는 예제
 2. 로그인버튼 백그라운드 컬러 애니메이션 적용하는 예제
 3. 로그인버튼 cornerRadius 애니메이션 적용 예제

## Chapter 9: Animation Keys and Delegates
UIKit 애니메이션에서는 애니메이션을 일시정지하거나 정지 할 수 없는 반면에 코어애니메이션에서는 중간에 애니메이션을 멈출수도있고, 애니메이션 상태에 대한 델리게이트 콜백을 받을 수도 있다.

#### Introducing animation delegates
CAAnimationDelegate 는 animationDidStart, animationDidStop 의 메서드를 제공한다.

#### Key-value coding compliance
CAAnimation 클래스의 setValue를 통해 임의의 키-밸류 값을 설정할 수 있다

#### Switching on key values
value(forKey:)로 꺼내 쓸수있다.

#### Animation Keys
layer.add(_:key:) 의 key 파라미터를 이용해서 애니메이션이 시작된 후에도 접근 할 수 있다.

#### Adding a second layer animation
하나의 레이어에 여러개의 애니메이션을 독립적으로 실행 할 수 있다.

#### identifying running animations
layer.animationKeys()를 이용해 실행중인 애니메이션 키를 확인 할 수 있다.
애니메이션은 layer에 붙은 순간부터 immutable

#### Challenge 
animationDidStop 에서 설정한 구름 애니메이션 name키를 이용해서 구름애니메이션이 종료되면 재시작 시키는 내용

## Chapter 10: Groups and Advanced Timing
CAAnimationGroup은 duration, delegate, timingFunction 을 포함해서 여러개의 애니메이션을 그룹으로 관리할 수 있게 해준다.

#### CAAnimationGroup
CAAnimationGroup은 CAAnimation을 상속 받았기때문에 CAAnimation과 같은 프로퍼티를 사용한다.
CAAnimationGroup의 animations 프로퍼티에 [CAAnimation] 을 할당해서 그룹으로 처리 할 수 있다.

#### Animation easing
CAAnimationGroup의 timingFunction 프로퍼티에 CAMediaTimingFunction을 설정해서 easing 방식을 적용할 수 있다.
Easing방식은 Linear, EaseIn, EaseOut, EaseInEaseOut을 지원하고, 직접만든 easing function을 지정할 수 도 있다.

#### Repeating animations
repeatCount 프로퍼티를 이용해서 반복횟수를 지정할 수 있고, Float타입으로 지정가능하다.
autoreverses 프로퍼티를 통해 애니메이션의 역방향으로 다시 애니메이션 시킬 수 있다. 
Autoreverses가 true일 경우 역방향 애니메이션이 끝나는 시점까지가 repeatCount 1이다.

#### Changing the animation speed
duration과 독립적으로 spped 프로퍼티를 통해 기본 애니메이션속도의 배수로 속도를 설정 할 수 있다. ex) spped 2, duration 5일때 2.5초 만에 끝남
spped 프로퍼티는 Layer계층 구조를 거치며 곱해진다.

#### Challenges
CAAnimationGroup을 이용해서 상단 라벨, 텍스트필드에 위치변경, 투명도 조절 애니메이션 적용하는 예제
CAAnimationGroupd의 프로퍼티도 레이어에 add될 때 CABasicAnimation과 마찬가지로 복사되어 중간에 프로퍼티를 바꿔 적용 할 수 있다. 
## Chapter 11: Layer Springs

#### Damped harmonic oscillators
실제 물리환경에서 이상적인 harmonic oscillator는 발생할 수 없으므로 여러가지 요인에 의해 진폭이 줄어드는데, 이걸 Damped harmonic oscillators라고 함

#### UIKit vs Core Animation springs
UIKit과 달리 CASpringAnimation 클래의 파라미터로는 damping, mass, stiffness, initial velocity 가 있다.

#### Creating your first layer spring animation
CASpringAnimation을 이용해서 스프링 애니메이션을 적용할때 스프링 애니메이션이 안정화 되기위한 시간으로 설정하지 않으면 애니메이션이 도중에 끊겨 이상하게 느껴진다. 따라서 duration을 CASpringAnimation의 프로퍼티인 settlingDuration으로 설정해주어야 한다.
Damping이 클수록 저항이 크므로 settlingDuration이 짧아진다.

#### Spring animation properties
CASpringAnimation 이용해서 입력이 끝난 후 살짝 튕기는 애니메이션을 만들 수 있다

#### Initial velocity
initialVelocity는 duration이전에 설정해야하고, 0이 초기값이며, 설정된 값만큼 애니메이션이 시작할때 힘을 받는다.

#### mass
Mass는 질량개념으로 기본값이 1이며, mass 값을 증가시킬수록 더 크고 느리게(duration증가) 스프링 애니메이션이 나타난다.

#### Stiffness
Stiffness는 스프링의 힘의 개념으로 기본값이 100이며 작은값으로 설정할 수록 부드러운 스프링으로 더많이 움직이게되고 높은값으로 설정하게되면 더 적게 움직이게 된다.

#### Damping
Damping값은 저항계수 값으로 0으로 설정할 경우 계속 동일한 왕복운동을 하게 되고, 값이 높아질 수록 점점 빠르게 진폭이 줄어든다.

#### Specific layer properties
SpringAnimation은 위치뿐만아니라 컬러변경에도 사용 할 수 있으며, 이를 통해 깜빡이는 효과 애니메이션을 구현할 수 있다.

#### Challenges
로그인버튼 눌렀을때 로그인버튼의 cornerRadius, backgroundColor 애니메이션을 스프링애니메이션으로 대체하기


## Chapter 12: Layer Keyframe Animations and Struct Properties

#### Introducing keyframe animations
일반 애니메이션의 경우 구간별로 변하는 정도가 같지만, 키프레임 애니메이션의 경우 0 ~ 1의 keyTimes에 대응하는 value를 설정해 구간별로 다른 움직임을 갖는다.

#### Creating a layer keyframe animation
CAKeyframeAnimation(keyPath:)를 통해 애니메이션을 생성하고
해당클래스의 values와 keyTimes 를 설정해주면 설정된 keyTimes에 인덱스에 맞는 values 값이 실행된다.
values와 keyTimes는 짝이 맞지않아도 오류가 발생하지 않는다. 앞에서 부터 순차적으로 처리되고 짝이 맞지않는건 실행되지 않는듯?

#### Animating struct values
NSValue 클래스를 이용해서 CGPoint, CGSize, CGRect, CATransform3D를 형변환해서 fromValue와 toValue에 설정해서 애니메이션 시킬 수 있다.
질문: 지우고해도 제대로 동작합니다.

#### Intermediate keyframe animations
values가 [CGPoint]타입인 예제(열기구 키프레임 애니메이션)
오토레이아웃이나 제스쳐를 이용하지 않는 이미지를 애니메이션 시킬때는 CoreAnimation 사용해서 간단하게 구현가능하다.


## Chapter 13: Shapes and Masks
Drawing 대신 CALayer의 path에 cgPath를 할당하는 방식으로 Shape를 만들수 있다.
CGPath 얻을때는 UIBezierPath를 사용하는게 편하다.
didMoveToWindows() 에서 레이어 계층구조 설정


#### Finishing up the avatar view
layer의 mask프로퍼티를 이용해서 mask를 통과한 영역만 레이어에 표현시키도록 할 수 있다.

#### Creating the bounce-off animation
스프링 애니메이션을 이용해 바운스 애니메이션을 구현 하는 예제

#### Morphing shapes
UIBezierPath(ovalIn: CGRect).cgPath 를 이용해서 rect에 맞는 path를 구할 수 있다. 
UIBezierPath의 생성자는 다양한 파라미터를 지원하는데, 용도에 맞게 사용해야할 것 같다.
변형시킬 프레임을 생성하고, cgPath로 변환 시킨 후  애니메이션 시켜 레이어의 모양 변형을 애니메이션 시킬 수 있다.

#### Challenges
4초뒤에 상대가 찾아지면 상대의 이미지를 설정하도록 하고, 상대가 찾아지고 4초뒤에 아바타뷰에 이미 정의된 shouldTransitionToFinishedState를 변경해서 animatedToSquare 메서드를 작성해서 path를 사각형으로 변형시키는 예제


## Chapter 14: Gradient Animations

#### Drawing your first gradient
CAGradientLayer를 통해 그라데이션을 구현할수 있다.
startPoint, endPoint는 그라데이션의 시작점, 끝점을 x,y 좌표 0~1스케일로 설정할 수 있다.
locations은 그라데이션이 적용되는 부분(startPoint - endPoint) 를 0~1스케일로 지정해서 순서에 매칭이되는 colors값을 마일스톤으로 설정한다(키프레임 애니메이션 처럼)
Locations 설정안했을때는 colors값의 갯수에 따라 균등하게 포인트지정


#### Animating gradients
location 속성을 애니메이션 시켜 그라데이션을 애니메이션 시킬 수 있다.

#### Creating a text mask
UIGraphicsImageRenderer 를 통해 텍스트를 이미지로 변환하고
그라데이션레이어의 mask 속성을 레이어의 컨텐츠를 이미지.cgImage로 설정한 레이어로 설정해서, 텍스트 마스크를 구현할 수 있다.


#### Challenges
스와이프제스쳐를 추가해서 슬라이드했을때 이미지나타나는 메서드 호출하는 예제
그라데이션 색상 변경하는예제

## Chapter 15: Stroke and Path Animations
이 장에서는 Stroke & Path 애니메이션을 배우고, 임의의 path를 따라 객체를 움직이는 특별한 키프레임 애니메이션을 배우게 된다.

#### Creating interactive stroke animations
CAShapeLayer를 만들고, path를 UIBezierPath(ovalIn:)을 이용해 설정해서 원형모양의 레이어를 만든다.
lineDashPattern 프로퍼티에 [length of the dash, length of the gap] 형태로 할당해서 선 패턴을 정의할수 있다.
strokeEnd 는 0~1 까지의값으로 선의 끝점을 설정할 수 있다(질문: 예제에서 선의 시작점이 왜 우측 인가요..?)

#### Animating both stroke ends 
strokeStart와 strokeEnd 프로퍼티를 이용해서 애니메이션 시켜 풀투리프레시 효과를 구현한다. 
이때, -값을 이용(0과 같음)해서 strokeStart와 strokeEnd의 속도차이를 이용해서 시각적인 효과를 줄 수 있다.(점점 선의 길이가 짧아짐)

#### Creating path keyframe animations
CAKeyframeAnimation에 keyPath: “position” 으로 설정했을때 path 프로퍼티를 지정해서 원형 으로 position 프로퍼티를 애니메이션 시킨다. 
비행기의 이미지가 원을따라 이동할때 이미지가 그대로 이동하므로, 원이미지를 회전하는 애니메이션을 추가해서 그룹으로 묶어 처리한다.
책에서 소개한 CAKeyframeAnimation의 rotationMode를 통해 쉽게 로테이션 시킬 수 있는데, 적용해보니 path의 수직방향으로 로테이션 하는 기능이어서, 현재설정된 이미지를 90도 틀어야 정상적으로 작동한다.

#### Section conclusion
그동안 기본레이어 애니메이션(기본 변환, Group, Keyframe, Shape, Stroke&Path)에 대해 배웠다 와우!


## Chapter 16: Replicating Animations
CAReplicatorLayer는 약간 다른 복사본을 쉽게 만들도록 도와주는 레이어다.
각 사본에 transform 적용이 가능하며, instanceDelay 프로퍼티를 이용해 인스턴스별 애니메이션 딜레이를 설정할 수 있다.

#### Starter project overview
하단버튼을 누르고 있으면 actionStartMonitoring()을 실행하고, 버튼을 떼면 actionEndMonitoring()을 실행하고 1초뒤 startSpeaking() 을 실행한다.
AI답변을 하는 Assistant 클래스와 마이크 입력 레벨을 관리하는 MicMonitor클래스가 제공된다. 

#### Setting up the replicator layer
CAReplicatorLayer에 복제할 Layer를 addSublayer하면 복제가 된다.
CAReplicatorLayer의 instanceCount를 설정해서 복제할 레이어의 갯수를 설정하고, instanceTransform을 이용해서 위치를 조정해주어야한다, 조정하지 않으면 같은자리에 복제되어 눈으로 확인할 수 없음.

#### Your first replicated animation
CAReplicatorLayer의 instanceDelay 프로퍼티는 복제될 레이어의 애니메이션이 실행될 딜레이를 설정한다.
instanceDelay를 주었다고해서 화면에 노출되는 것 자체가 delay되는 것은 아님.

#### Replicating multiple animations
CAReplicatorLayer는 content와 animation을 복제한다.
여러개의 레이어 애니메이션을 복제될 레이어에 add하고 duration을 조정하면 여러 애니메이션들이 복제되면서 멋진 애니메이션을 만들수 있다.

#### Animating CAReplicatorLayer properties
CAReplicatorLayer의 animatable Properties는 다음과 같다.
 : instanceDelay, instanceTransform, instanceColor, instanceRedOffset, instanceGreenOffset, instanceBlueOffset, instanceAlphaOffset
instanceTransform의 rotation 프로퍼티를 변경시키는 애니메이션을 생성해서 CAReplicatorLayer에 적용해서 wave를 변형시킨다.
 #### Interactive replication animations
마이크를 통해 입력받은 값을 조정해서 scale.y 값을 애니메이션 한다.

#### Challenges
actionEndMonitoring에 2개의 애니메이션을 추가해서 startSpeaking() 실행될 때 넘어가는 부분을 자연스럽게 애니메이션 하도록 하는 챌린지
scale.y를 원래대로 돌리고, 컬러를 그린 -> 마젠타로 변경하도록 하고, 컬러의경우 duration이 startSpeaking() 실행이후 까지 설정해서 자연스럽게 보이도록 함.

# Section IV: View Controller Transition Animations
이장에서는 뷰컨트롤러 애니메이션을 만드는 법을 배운다

## Chapter 17: Presentation Controller & Orientation Animations
이장에서는 기본 present 애니메이션을 대체할 커스텀 애니메이션을 만든다.

#### Looking through the start project
프로젝트 소개, 하단 스크롤뷰영역에 이미지를 탭하면 HerbDetailsViewController를 띄우는 present 메서드를 호출함, 이 애니메이션을 커스텀하게 구현예정

#### Behind the scenes of custom transitions
뷰컨트롤러를 present 할때 마다 UIKit에서는 animationController(forPresented:presenting:source:)를 호출해서 UIViewControllerAnimatedTransitioning 객체를 받으면 그 객체를 트렌지션에 사용한다. nil이라면 Built-in 트랜지션을 사용한다.
커스텀 애니메이션컨트롤러를 사용할때, 먼저 transitionDuration(using:)을 호출한뒤, animateTransition(using:) 을 호출한다.
animateTransition(using:) 함수에서 현재 뷰컨트롤러와 새로운 뷰컨트롤러에 모두 접근 가능하며, 이를 통해 fade, scale, rotate 등을 조작 할 수 있다.

#### Implementing transition delegates
UIViewControllerAnimatedTransitioning 프로토콜은 2개의 함수를 필수 구현으로 선언 되어있다.
public func transitionDuration(using transitionContext: UIViewControllerContextTransitioning?) -> TimeInterval
public func animateTransition(using transitionContext: UIViewControllerContextTransitioning)

present하고자하는 뷰컨트롤러의 transitioningDelegate를 현재 뷰컨트롤러로 설정하고, UIViewControllerTransitioningDelegate를 이용할 수 있다.

#### Creating your transitionstion animator
역방향 애니메이션도 적용하기 위해 임의의 플래그를 통해 presenting 중인지 확인하도록 한다.
transitionDuration() 에 애니메이션 duration을 설정한다.

#### Setting your transition’s context
트랜지션이 일어날때 현재 뷰는 transition container view에 add되고, 새로운 뷰컨트롤러의 뷰는 생성되지만 보이지 않는 상태가 된다.
따라서, animateTransition() 안에서 새로운 뷰를 transition container에 add하는 것을 구현해야한다. 기본적으로는 애니메이션이 끝났을 때 이전 뷰가 transition container에서 제거되고 새로운 뷰가 transition container view에 add된다.

#### Adding a fade transition
UIViewControllerContextTransitioning은 view(forKey:), viewController(forKey:) 두가지 메서드를 제공하는데, 
UITransitionContextViewControllerKey의 .from 과 .to 를 이용해 트랜지션이 일어나는 뷰/뷰컨트롤러 객체를 쉽게 얻을 수 있다.
애니메이션이 끝나면 UIViewControllerContextTransitioning 클래스의 completeTransition()을 호출해서 UIKit에 알려줘야한다.

#### Adding a pop transition
Present 할때 스프링 애니메이션을 적용한다.
탭하면 사라지는 애니메이션을 추가하는내용

#### Adding a dismiss transition
Pop 이후 이미지 숨김 애니메이션 적용

#### Device orientation transition
기기 화면 방향이 변환될 때, 뷰컨트롤러의 viewWillTransition(to size:coordinator:) 메서드를 구현하여 관련 처리를 할 수 있다.

#### Challenges
약초 설명부분을 화면전환할때 fade효과를 적용한다. 나타날때 alpha 0->1 사라질때 alpha 1->0
약초 사진 cornerRadius를 조정하는 애니메이션을 추가한다. 나타날때 cornerRadius를 없애고, 사라질때 추가한다.

## Chapter 18: UI NavigationController Custom Transition Animations

#### Introducing Logo Reveal

#### Custom navigation transitions
UIKit에서는 UINavigationControllerDelegate의 navigationController(navigationController:operation:fromVC:toVC:)를 호출하고 UIViewControllerAnimatedTransitioning 객체를 리턴하면 커스텀 네비게이션 트랜지션을 실행하고, 아니면 기본 트랜지션을 수행한다.
UIViewControllerAnimatedTransitioning 객체를 리턴받으면 present 방식과 동일하게 
transitionDuration(), animateTransition() 메서드를 수행한다.

#### The navigation controller delegate
navigationController의 파라미터는 navigationController, operation(.push, .pop 타입 지정), fromVC(현재 보여지는 뷰컨트롤러), toVC(보여질 뷰컨트롤러)로 이루어져있다.

#### Adding a custom reveal animation
애니메이션이 완료된 시점에 completeTransition()을 수행하기 위해서 현재 transitionContext를 저장해두고 animationDidStop에서 체크한다.
present방식과 동일하게 transitionContext의 컨테이너 뷰에 transition될 뷰컨트롤러의 뷰를 add하고 애니메이션이 끝난 후 completeTransition()을 수행한다.

#### Taking care of rough edges
트랜지션 애니메이션이 될때 fromVC에 있던 로고 잔상이 남아있어 이를 없애기 위해, fromVC의 로고에도 애니메이션을 추가하고, 애니메이션이 완료되었을때 로고를 리셋하는 코드를 추가한다.
현재까지 구현된 상태로 트랜지션이 완료된 후 스크롤을 하면 상단에 로고레이어가 남아 있는데,애니메이션이 완료된 후 toVC의 마스크를 초기화 해주는 코드를 추가한다.

#### Challenges
Push 할때 새로 보여질 뷰가 투명상태에서 점점 보여지는형태의 애니메이션 추가해보는 예제
스케일을 0.01로 줄어드는 Pop 애니메이션 추가하는 예제
지난 챕터에서는 toView를 transitionContext.containerView에 addSubView한뒤 bringSubview(toFront:)를 이용해서 가져왔는데, 이번챕터에서는 insertSubview(_:belowSubview:) 를 이용해서 toView를 fromView뒤에 add했다. 팝할때  fromView에서 애니메이션이 일어나기때문에 애니메이션이 일어날 뷰를 위에 보이게 해야 의도한대로 동작하게 되기때문이다.

## Chapter 19: Interactive UINavigationController Transitions

#### Creating an interactive transition
UIViewControllerAnimatedTransitioning 프로토콜과 UIViewControllerInteractiveTransitioning 프로토콜을 동시에 만족하는 애니메이션 컨트롤러를 구현한다.
UIViewControllerInteractiveTransitioning 프로토콜은 startInteractiveTransition(_:)를 필수로 구현해야한다. 
interactionController는 정기적으로 updateInteractiveTransition (_:)를 수행해서 트렌지션 진행정도를 갱신한다.(진행정도에 대한 접근은 어떻게??)

#### Handling the pan gesture
기존 탭제스쳐 로직을 제거하고 팬제스쳐를 추가한다.

#### Using interactive animator classes
빌트인 애니메이터 클래스인 UIPercentDrivenInteractiveTransition을 이용해서 트랜지션 progress를 get/set 할 수 있다.
UIPanGestureRecognizer 가 .began 상태일때 interactive 플래그를 true로 바꾸고, performSegue를 수행해서 interactive transition이 일어나도록 한다.

#### Calculating your animation’s progress
펜 제스쳐의 x좌표를 이용해서 progress를 구하고, 현재 트렌지션 애니메이션의 progress를 갱신한다.
트렌지션 애니메이션 시작할때의 시간을 timeOffset으로 지정해두고, 펜제스쳐 progress 정도에 따라 timeOffset을 늘려가며 애니메이션을 수행해서 Interactive Transition을 구현한다.

#### Handling early termination
UIPercentDrivenInteractiveTransition는 트랜지션을 복구하거나 완료하기 용이하게cancel(), finish() 등의 메서드를 제공한다.
내부적으로는 cancelInteractiveTransition(), finishInteractiveTransition()을 이용하는 것 같다.

#### Challenges
펜제스쳐를 이용한 interactive 팝 트랜지션 구현 예제
펜제스쳐를 추가하고, 현재 사용중인 네비게이션 컨트롤러 스택에 있는 MasterViewController가 RevealAnimator를 들고 있으므로 여기에 접근해서 push에 사용하는 handlePan 메서드를 재활용해서 사용자의 펜제스쳐 정도에 따라 팝 애니메이션을 수행하는 트랜지션을 구현한다.


# Section V: Animations with UIViewPropertyAnimator
UIViewPropertyAnimator는 실행중인 애니메이션을 멈출수 있고, 애니메이션의 상태에 대한 자세한 정보를 얻을 수 있다.

## Chapter 20: Getting Started with UIView Property Animator

#### Basic animations
UIViewPropertyAnimator(duration:, curve:)를 이용해 duration과 사용할 curve 종류(UIView.animate()와 같은 커브옵션)를 파라미터로 이용해 UIViewPropertyAnimator를 생성 할 수 있다.

#### Adding animations
UIViewPropertyAnimator 객체에 addAnimations(_:,delayFactor:)를 해서 애니메이션을 추가하고, delayFactor를 이용해서 잔여 duration에 대한 상대적인 delay를 적용 할 수 있다.
delay = delayFactor * remainingDuration
addAnimations()는 여러개 추가 할 수 있다.

#### Adding completions
addCompletion(_:)을 이용해서 애니메이션이 끝난 후 수행할 작업을 처리할 수 있으며, 여러개 정의가능하고, 정의한 순서대로 동작한다.
UIViewPropertyAnimator의 startAnimation() 메서드를 호출해야 애니메이션이 실행된다.

#### Abstracting animations away
UIViewPropertyAnimator를 이용하면 애니메이션을 Enumeration이나 Struct, Class 형태로 관리할 수 있다.

#### Running animators
UIViewPropertyAnimator의 클래스 메서드로 runningPropertyAnimator(withDuration:delay:options:ani 
mations:completion) 를 제공한다. (UIView.animate와 같은형태)

#### Basic keyframe animations
runningPropertyAnimator의 애니메이션 안에 UIView.animateKeyframes를 넣어 키프레임 애니메이션을 수행할 수 있다.

#### Challenges
AnimatorFactory에 fade메서드를 구현하고, searchBar 입력시작/종료 시에 fadeIn/Out 하는 애니메이션을 추가하는 예제 animator를 주입받아 아이콘이 애니메이션 중이 아닐때만 애니메이션을 실행하는 코드 추가예제

아직까지는 UIView.animate()와 큰 차이를 못느끼겠다. 남은 3장을 더 봐야할것 같다.

addAnimation, addCompletion 블럭을 여러개 추가할수 있는건 분기를 통해 코드를 구조적으로 설계할수있게 도와준다.

## Chapter 21: Intermediate Animations with UIViewPropertyAnimator

#### Built-in timing curves
UIViewPropertyAnimator의 curve 파라미터를 바꿔 애니메이션 타이밍을 조절 할 수 있다.
UIViewAnimationCurve는 .linear, .easeIn, .easeOut, .easeInOut 4가지 빌트인 커브타입을 제공한다.

#### Custom Bezier curves
점A와 점B를 연결할때 Control Point를 추가하여 시작점에서 Control Point방향으로 움직이는 점과 Control Point에서 종료점으로 움직이는 점이 만나는 선을 따라 커브를 그리는것이 BezierCurve다
UIViewPropertyAnimator는 controlPoint를 파라미터로 갖는 생성자를 제공한다. 이를 통해 커스텀 타이밍 애니메이션을 생성 할 수 있다.

#### Spring Animations
UIViewPropertyAnimator는 스프링 애니메이션 관련 생성자도 제공한다. => UIViewPropertyAnimator(duration:dampingRatio:animations:) 

#### Custom timing providers
마지막으로 소개할 UIViewPropertyAnimator의 생성자는UIViewPropertyAnimator(duration:timingParameters:) 이다.
timingParameter는 UITimingCurveProvider 프로토콜 타입으로 UICubicTimingParameters 와 UISpringTimingParameters 클래스가 이 프로토콜을 따른다.
UISpringTimingParameters클래스를 이용해서 레이어 애니메이션에서 사용했던 damping이나 initialVelocity, mass, stiffness 등을 정의하고 이를 timingParameters로 넘겨 UIViewPropertyAnimator를 생성 할 수 있다. 
#### Auto Layout animations
UIView.animate와 마찬가지로 constraint를 갱신한 후. 애니메이션 블럭에서 layoutIfNeeded()를 호출해야 한다.
Cell의 constraint를 변경했을때는 beginUpdates(), endUpdates()를 layoutIfNeeded전에 호출하면 모든 셀들이 자신의 변경된 레이아웃을 확인하고 UIKit에서 프레임을 조정해준다.

#### Built-in view transitions
UIView.transition을 addAnimations블럭안에 추가해서 transition을 구현한다.

#### Challenges
isRunning을 이용해 toggleHeightAnimator가 실행중인지 확인해서 실행중이라면 pauseAnimation() 메서드를 이용해서 멈추고 애니메이션을 add하고 continueAnimation()을 수행한다.

## Chapter 22: Interactive Animations with UIViewPropertyAnimator

#### An animation state machine
UIViewPropertyAnimator는 isRunning, isReversed, state 3개의 프로퍼티를 제공한다.
isRunning은 애니메이션이 실행중인 상태를 true, false로 반환하며, isReversed는 기본값이 false이며 true로 설정하면 애니메이션이 역방향으로 실행된다.
state는 현재 애니메이션의 상태를 inactive, active, stopped 로 나타낸다.
기본 inactive상태이며 startAnimation() 뿐만아니라 pauseAnimation() 이나 fractionComplete 프로퍼티를 설정할때 active상태로 전환되며 stopAnimation()을 실행하면 stopped로 전환된다.

#### Interactive 3D touch animation
fractionComplete 프로퍼티는 애니메이션의 완료퍼센트를 나타낸다.(0시작, 1완료) 따라서 interactive한 애니메이션을 구현할때 갱신해주어야 한다. (이 값을 바꾸면 inactive상태에서 active상태로 상태가 변경된다.)
UIViewAnimatingPosition 은 애니메이션의 진행위치를 .start, .end, .current 3가지 상태로 나타낸다.

#### Challenge
dismiss 애니메이션 추가 예제
키프레임 애니메이션을 통해 50% 진행 되었을때부터 끝날때까지 rotate 애니메이션을 추가하는 예제

## Chapter 23: UIViewPropertyAnimation ViewController Transitions

#### Static view controller transitions
UIViewPropertyAnimation에서의 ViewControllerTransition도 이전챕터에서 다루었던 방식으로 다룬다.

#### Interactive view controller transitions
Interactive transition이면 interruptibleAnimator(using:)을 호출하고,
Non-Interactive transition이면 transitionDuration(using:)을 호출한다.

지난 챕터에서 배웠던 UIPercentDrivenInteractiveTransition클래스의 메서드외에 추가적으로 timingCurve, wantsInteractiveStart, pause()에 대한 소개

wantsInteractiveStart 속성은 기본값은 true이며 false로 설정되어 있을 경우, 멈출수 있고 추후에 interactive 모드로 실행가능하게 해준다

#### Interruptible transition animations
현재 transitionContext의 pauseInteractiveTransitioning()과, UIPercentDrivenInteractiveTransition 클래스의 pause()를 호출해서 interactive 모드로 변환할수 있다.

예제에서 소개되었듯 Non-Interactive하게 애니메이션을 하다가, Interactive하게 애니메이션을 해야되는 UI쪽의 사용자 입력이 시작될때 pause()를 통해 Interactive모드로 변환하고 완료되면 finish()를 호출하는 형태로 구현하는 패턴을 알아두면 좋을 것 같다.

## Chapter 24: Simple 3D Animations

#### Creating 3D transformations
m34 프로퍼티는 z축의 perspective값을 의미한다.
3D Affine Transformation Matrix에서 4번째 Column이 Translation에 연관된 Column으로서, m14, m24, m34 는 각각 x, y, z perspective transform 을 수행할 수 있다.

#### Working with camera distance
적절한 camera distance는 750 ~ 2000을 권장함
CATransform3DRotate(t:angle:x:y:z:)를 통해 rotationTransform 을 수행할 수 있다.

#### Moving the layer’s anchor point
anchor point의 기본값은 0.5(센터)이며 0~1사이의 값으로 설정가능하며, anchor point를 축 으로 로테이트 한다.

#### Creating perspective through shading

#### Rasterizing for efficiency
코어애니메이션은 메뉴뷰가 애니메이션 될때 perspective distortion 을 다시 계산해서 리드로우 한다.
CALayer의 shoudRasterize 프로퍼티를 true로 설정하면 컨텐츠를 캐시처리해서 리드로우 이슈를 해결 할 수 있다.

#### Challenges
CATransform3DRotate를 이용해서 버튼을 회전시키는 애니메이션 적용. 이때 x, y 값을 모두 1로 설정하면 대각선축으로 회전한다.(x = 1 일 경우 x축기준 회전, y = 1 일 경우 y축기준 회전, z = 1 일 경우 시계 방향으로 회전)

## Chapter 25: Intermediate 3D Animations

#### Exploring the starter project
view.layer.sublayerTransform 프로퍼티를 통해 해당 뷰의 모든 sublayer들이 transform 할때 공통으로 사용하게 되는 프로퍼티를 지정할 수 있다.

#### Transforming the gallery
CATransform3D 인스턴스를 Translate, Scale, Rotate를 순차적으로 적용한뒤, layer.transform에 할당해서 3D Transform을 적용한다.
이때 이전에 sublayerTransform에서 적용한 m34 프로퍼티가 적용되어 3D효과를 만든다.

#### Animating the gallery
CATransform3D도 keypath: “transform” 으로 레이어 애니메이션을 적용시킬수 있다. 
#### Bringing an image to the front
이미지 선택시 UIView.animate를 이용해 선택된이미지는 원래대로 복구하는 애니메이션, 다른이미지들은 alpha = 0 애니메이션 을 수행한다.
completion에서 선택된 이미지는 bringSubview(toFront:)를 이용해 애니메이션이 끝난뒤 사진이 보이도록 하고, 다른이미지는 원래이미지로 만드는 처리를 해준다.

#### Challenges 
갤러리가 열려있을때 탭하면 닫히면서 이전상태로 이동하는 애니메이션 구현

# Section VII: Further Types of Animations

## Chapter 26: Particle Emitters
각각의 파티클은 예측불가능하고, random하기 때문에 효과를 리얼하게 잘 표현 할 수 있다.

#### Creating your emitter layer
파티클 효과를 위한 다양한 써드파티 클래스들이 있지만 일반적인 앱에서는 CAEmitterLayer가 가장 좋은 선택이다.

CAEmiitterLayer 인스턴스를 생성한뒤, frame 프로퍼티를 설정하고 보여질뷰에 레이어를 추가한다.

emitterShape는 파티클이 생성되는 타입을 지정해주는 프로퍼티이다.

#### Adding an emitter frame
emitterPosition: 파티클의 센터 값
emitterSize: 파티클이 생성될 영역크기

#### Creating an emitter cell
EmitterCell은 파티클을 표현하기위한 데이터 모델이다.
EmitterCell은 CAEmitterLayer와 분리되어있고, EmitterLayer는 한개이상의 셀을 포함한다.
EmitterCell.birthRate: 초당 n개의 파티클생성
EmitterCell.lifetime: n초 만큼 파티클 유지
CAEmitterLayer에 emitterCells 프로퍼티에 생성할 EmitterCell 들의 배열을 설정한다.

#### Chaning particle direction
EmitterCell의 xAcceleration, yAcceleration을 이용해서 파티클을 움직일 수 있다.
EmitterCell의 velocity와 emissionLongitude를 이용해서 파티클의 초기속도와 각도를 지정할 수 있다.

#### Adding randomness to your particles
EmitterCell의 특정프로퍼티+range 프로퍼티를 이용해서 해당 프로퍼티의 랜덤 범위를 지정할 수 있다.
Ex) velocity = 20 일때 velocityRange = 200 이면 -180 ~ 220값으로 설정, 음수일때는 velocity = 0 처리

#### Changing particle color
redRange, greenRage, blueRange 프로퍼티를 이용해서 색상도 랜덤값 적용이 가능하다 (0 ~ 1스케일 기준)

#### Randomizing particle appearance
Scale, alpha 값 range를 지정해 더욱 풍성한 애니메이션을 만들 수 있음

#### Adding some final polish

#### Challenges
EmitterLayer에 추가 EmitterCell 설정하는 예제
 ## Chapter 27: Frame Animations with UIImageView
Frame Animation은 Frame 안에서 애니메이션을 동작시킨다.

#### Project basics
이미지 애셋에 사진이 여러장 있는 것으로 보아 이미지뷰에 이미지들을 설정해서 애니메이션 시킬 것 같다.’

#### Setting up your frame animation
이미지뷰의 animationImages 프로퍼티에 이미지 배열을 할당하고, animationDuration을 지정한 뒤 startAnimating() 메서드를 이용해 프레임 애니메이션을 동작시킬 수 있다.
animationDuration은 개별사진의 시간이 아닌 애니메이션 한사이클의 시간이다.

#### Translating your view
버튼눌렀을때 centerX값을 조정하는 애니메이션을 이용해서 펭귄이 움직이는 효과를 추가한다.

#### Playing different frame animations
Frame animation을 시킬 이미지의 사이즈가 다르면 이상하게 보이는데, 이를 해결하기 위해 가장 쉬운 방법은 이미지뷰의 content mode를 Aspect Fill로 처리하는 것이지만, 책에서는 frame을 이미지별로 조정해서 처리했다

#### Where to go from here?
