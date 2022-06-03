<br />

## 조용남 작가 웹사이트 주요기능 구현

<br />
<br />

지금 보고게신 ReadMe는 조용남 작가 웹사이트 ReadMe의 단락 중 한 부분인 **8. 주요기능 구현** 에 관한 내용이 따로 옮겨진 곳입니다. 

<br />
<br />

조용남 작가 웹사이트의 메인 깃허브페이지는 [**조용남 작가 웹사이트**](https://github.com/1005jsc/artist_website)에서 확인하실 수 있습니다.  

<br />
<br />
<br />


### 목차

<br />
<br />

1. [**작품소개 보러가기**](#9)
1. [**로그인**](#10)
1. [**작품 확대하여 보기**](#11)
1. [**Firebase와 Cloudinary를 고른 이유**](#12)




<br />

<div id="9"></div>

<br/>
<br/>

### 작품소개 보러가기 컨셉정리

<br/>
<br/>
<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/1.jpg" width="700px"  alt="그림 1: 운영체제와 프로세스"></div>

<br/>
<br/>
<div align="center"> <span>그림 1 : 작품소개 보러가기 페이지들</span></div>

<br/>
<br/>

 
'작품소개 보러가기' 코너는, 작가의 작품 하나하나를 비중들여 보여주고, 작가를 설명하는 글 등을 넣어서 작가가 어떤 스토리를 가진 작가이고, 어떤 스타일의 작품을 만드는지에 관한 첫 인상을 주는 코너이다. 30~40여점 정도 되는 작가의 작품들을 전부 다 보여주긴 너무 많으니 이 코너에서는 20페이지 정도의 분량으로 만들기로 했다. 그래도 20페이지도 적은 분량이 아니기 때문에 페이지에 전반적으로 적용시킬 통일성 있는 규칙이 반드시 필요하였다. 같은 형식의 페이지 다수를 컴포넌트간의 간격, 폰트, 크기,등등의 일정한 규칙없이 디자인을 하게 되면 통일성이 없어져 코너 전체에 시각적으로 불안한 느낌이 생길 수 있기 때문이다.

'작품소개 보러가기'코너에 적용할 각 페이지의 디자인 규칙으로, 작품을 하나하나 비중있게 보여야 할 것, 보여진 작품 하나하나에 제목, 년도, 재질등의 메타데이터를 적어 놓는 것, 페이지 수를 보여줄 것 등등을 정했다. 그리고 이 모든 규칙들을 적용해 에셋들의 배치 위치, 배치가능한 영역등을 정하고, 정한 결과를 바탕으로 아래와 같은 디자인 템플릿을 만들었다. 



<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/2.svg" width="600px"  alt="그림 2: 운영체제와 프로세스"></div>

<br/>
<br/>
<div align="center"> <span>그림 2 : 작품소개 보러가기 페이지 디자인 템플릿</span></div>

<br/>
<br/>

위의 내용을 바탕으로 만들어진 디자인 템플릿이다. 사용 방법은 쉽다. 작품 이미지를 디자인 템플릿의 가이드라인에 맞춰 작품 에셋들을 넣어서 만들기만 하면 된다. 
모든 페이지의 작품 이미지들은 그림 2 의 틀 안에 걸쳐져 있으며 메타데이타, 페이지 번호의 위치도 정해진 가이드라인에 걸칠수 있게 만들었다. 모든 페이지들은 각잡히고 통일된 디자인을 가지게 되고, 더 이상 작품사진의 크기를 얼마로 정할 건지, 위치를 어디에 배치할 건지와 같은 무한대에 수렴하는 디자인 가짓수에 대해 고민하는 일은 열 몇가지 수로 줄어 디자인 작업이 훨씬 수월해졌다. 물론 이 틀로 표현할 수 있는 디자인 수는 열 몇가지 정도밖에 되지 않고 총 페이지 수는 20페이지 정도이기 때문에 중복되는 디자인들이 생기게 되지만, 중복되는 디자인들의 페이지 거리를 서로 띄어 놓으면 해결된다. 


<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/3.jpg" width="600px"  alt="그림 3: 페이지 디자인 템플릿을 사용해 페이지를 디자인한 모습"></div>

<br/>
<br/>
<div align="center"> <span>그림 3 : 디자인 템플릿을 실제로 적용한 모습</span></div>

<br/>
<br/>

그림 하나하나가 페이지 안에서 충분한 비중을 차지하고 있어서 유저들이 작품에 집중할 수 있게 되고, 작품과 글씨들 주변의 공백도 충분해서 디자인적으로 깔끔한 느낌이 있다. 

<br/>
<br/>
<br/>
<br/>

### 작품소개 보러가기 구현하기




<br/>
<br/>
<br/>
<br/>

---

### 요약: 페이지 디자인 템플릿을 바탕으로 **정적인 컴포넌트**로 페이지들의 디자인 가이드라인을 정하고, **동적인 컴포넌트**로 컨텐츠들을 가이드라인에 배치시킨다 이를 바탕으로 21개의 페이지를 제작한다.


---

<br/>
<br/>
<br/>
<br/>

### (1) 정적인 컴포넌트들 만들기

컨텐츠 배치의 가이드라인이 될 위치가 고정된 컴포넌트들을 만든다(static_divs, pages)

<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/4.svg" width="600px"  alt="그림 4: 운영체제와 프로세스"></div>

<br/>
<br/>
<div align="center"> <span>그림 4 : 페이지 디자인 템플릿의 가이드라인 도식화</span></div>

<br/>
<br/>

페이지 템플릿의 가이드라인들을 재사용 컴포넌트로 만들어 준다. 그리고 페이지 수는 모든 페이지에 기본적으로 명시 되어저야 하기 때문에 페이지 컴포넌트도 정적인 컴포넌트에 포함시켜 반복적으로 사용가능하게 한다. 

제일 가장자리(제일 큰)사각형 FirstDiv는 ```width: 100%; height: 72rem;``` (html에서 ```font-size: 62.5%```로 잡았다 고로 height는 720px이 된다)으로 잡아준다. 자식 컴포넌트들에게 position이 적용될 수 있게 ```position:relative;```도 넣어 주었다. 두번째 안쪽 사각형은 SecondDiv로 스펙은 아래 표에 명시해 두었다.  또한 이 div들은 가이드라인으로서만 작용하고 유저의 화면에는 보일 일이 없다. 

그 다음으로 Page를 보여줄 Page Component들이다. 전부 SecondDiv의 하단부에 위치하고 SecondDiv의 긴 변을 기준으로 위치를 잡았다. Left, Center, Right 이렇게 3가지로 잡았다. 이 둘은 위치가 변할 일이 없는 정적 컴포넌트들이다. 


<br/>
<br/>


|컴포넌트|.tsx|.style.ts|
|:--:|:--:|:--:|
|Static_divs|<div align="center"> <img src="/readme_assets/imgs/chart1/1-1.jpg" width="600px"  alt="chart1/1-1.jpg"></div>|<div align="center"> <img src="/readme_assets/imgs/chart1/1-2.jpg" width="600px"  alt="chart1/1-2.jpg"></div>|
|Pages|<div align="center"> <img src="/readme_assets/imgs/chart1/1-3.jpg" width="600px"  alt="chart1/1-3.jpg"></div>|<div align="center"> <img src="/readme_assets/imgs/chart1/1-4.jpg" width="600px"  alt="chart1/1-4.jpg"></div>|






<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/5.jpg" width="600px"  alt="그림 5: 운영체제와 프로세스"></div>

<br/>
<br/>
<div align="center"> <span>그림 5 : 페이지 디자인 템플릿의 정적인 부분 (코드)</span></div>


<br/>
<br/>

### (2) 동적인 컴포넌트 만들기

<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/6.jpg" width="600px"  alt="그림 6: 페이지 디자인 템플릿의 정적인 부분"></div>

<br/>
<br/>
<div align="center"> <span>그림 6 : 페이지 디자인 템플릿의 동적인 부분 도식화</span></div>

<br/>
<br/>

앞에서 만든 페이지 디자인 템플릿의 정적인 부분안에 동적인 컴포넌트를 집어 넣으면 비로소 페이지 한 쪽이 완성이 된다. 

동적인 컴포넌트들은 실질적인 컨텐츠를 담는 컴포넌트들로 text container, image container, metadata container 이렇게 3종류가 있다. (1)에서 설명한 위치가 변할 일 없는 정적인 컴포넌트와 달리 이 셋은 배치에 따라 위치를 변화시켜야 하기 때문에 동적인 컴포넌트라고 불리운다. (1)의 정적인 컴포넌트들 처럼 동적인 컴포넌트들도 기본적인 css를 정해놓고 시작한다. 

Text container는 페이지안에서 Container가 차지하는 영역을 정해주기 위한 TextDiv와 실제 Text를 집어넣을 TextSpan으로 구성되어 있다. 
TextDiv에 Width에 적당한 값을 주어 글이 너무 넓게 벗어나지 않도록 하고 TextSpan에는 적당한 폰트사이즈와 줄 높이를 주었다. 

Image Container는 ImageDiv와 ImageHorizontalImg(수평으로 긴 이미지일 경우), ImageVerticalImg(수직으로 긴 이미지일 경우)로 되어있다. 
간혹 연출 상 이미지의 크기가 페이지 보다 더 클 경우가 있는 상황에 대비해 ImageDiv에 ```overflow:hidden;```을 주었다. ImageHorizontalImg에는 수평의 길이가 부모의 크기와 맞아 떨어지도록 ```width: 100%;```을 넣었고 ImageVerticalImg에는 위와 똑같은 논리로 ```height: 100%;```을 넣었다. 

MetadataContainer에는 MetadataDiv와 작품제목을 담당하는 MetadataSpan1, 크기, 재료, 년도를 담당하는 MetadataSpan2에 각자 쓰임에 맞춰 css를 작성해 주었다.

<br/>
<br/>


|컴포넌트|.tsx|.style.ts|
|:--:|:--:|:--:|
|Text container|<div align="center"> <img src="/readme_assets/imgs/chart2/2-1.jpg" width="600px"  alt="chart2/2-1.jpg"></div>|<div align="center"> <img src="/readme_assets/imgs/chart2/2-2.jpg" width="600px"  alt="chart2/2-2.jpg"></div>|
|Metadata container|<div align="center"> <img src="/readme_assets/imgs/chart2/2-3.jpg" width="600px"  alt="chart2/2-3.jpg"></div>|<div align="center"> <img src="/readme_assets/imgs/chart2/2-4.jpg" width="600px"  alt="chart2/2-4.jpg"></div>|
|Image container|<div align="center"> <img src="/readme_assets/imgs/chart2/2-5.jpg" width="600px"  alt="chart2/2-5.jpg"></div>|<div align="center"> <img src="/readme_assets/imgs/chart2/2-6.jpg" width="600px"  alt="chart2/2-6.jpg"></div>|


<br/>
<br/>


동적인 부분이 가져야할 가장 기본적인 스펙은은 위와 같이 만들었다. 동적인 컴포넌트에 에셋을 넣고, 위치에 관한 css코드만 추가적으로 넣어 배치하고자 하는 곳에 에셋 배치를 해주면 된다. 동적인 컴포넌트의 위치를 배치할 때 FirstDiv, SecondDiv의 가이드라인에 빈 틈 없이 배치하면 된다 (예: ```position:absolue; top:0;, left:0;```).
위치에 관한 추가적인 css는 한 쪽의 페이지 전체를 나타내는 페이지 컴포넌트들 안에 개별적으로 명세 해놓았다(그림 7 확인).

<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/7.jpg" width="600px"  alt="그림 7: 완료된 페이지의 코드"></div>

<br/>
<br/>
<div align="center"> <span>그림 7 : 완성된 페이지의 코드의 모습</span></div>

<br/>
<br/>

<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/8.jpg" width="600px"  alt="그림 8: 완성된 페이지"></div>

<br/>
<br/>
<div align="center"> <span>그림 8 : 완성된 페이지의 모습</span></div>

<br/>
<br/>

위와 같은 방법으로 총 21개의 페이지를 제작해 작품소개 보러가기 부분을 완성했다.
 


<br />

<div id="10"></div>

<br/>
<br/>


<br/>
<br/>

## 로그인

<br/>
<br/>

### 로그인 컨셉 정리

<br/>
<br/>


작품사진 업로드, 작품데이터 수정, 전시회 업로드 부분은 유저가 접근해서는 안되고 작가만 접근할 수 있는 private한 곳이다. 그래서 본 웹사이트에 로그인 기능을 만들어야했다. 

본 웹사이트는 백엔드를 따로 두지 않는 웹사이트지만 다행이도 **구글 파이어베이스 AuthService**에서 로그인 관련 api들을 무료로 지원해 주고 있어서 적용하였다.

파이어베이스에서는 이메일, 구글 깃허브 연동등 다양한 방법으로 계정인증을 할 수 있다. 하지만 조용남 작가님은 파이어베이스가 제공해주는 UI들이 어렵고 계정 외우고 다니기 싫다고 하셨다. 그래서 작가님 본인이 원하는 비밀번호로 로그인을 할 수 있도록 만들어야 했다. 

이에 대한 해결책으로 작가님이 제시해 준 비밀번호를 웹사이트 비밀번호로 지정하고, 그 비밀번호 입력이 올바르면 파이어베이스 로그인을 일으키게끔 코드를 작성했다. 
작가가 원하는 비밀번호로 설정하고, 파이어베이스의 AuthService도 사용하는 두 마리의 토끼가 동시에 잡히게 되었다. 
비밀번호는 .env변수로 넣고 .gitignore처리를 해 두었다. 


<br/>
<br/>


### 로그인 구현하기 

<br/>
<br/>

### 1. services/auth.js 


<br/>
<br/>

```typescript

import { myApp } from './firebase';
import { getAuth, GoogleAuthProvider, onAuthStateChanged, signInWithPopup, signOut } from "firebase/auth";


class AuthService {

  auth = getAuth(myApp)
  googleProvider = new GoogleAuthProvider();

  AuthGooglePopupLogin = () => {
    signInWithPopup(this.auth, this.googleProvider)
    
  }


  AuthGoogleLogout = (callback) => {
    signOut(this.auth).then(callback).catch(()=> {
      console.log('logout failed')
    })
  }
  
  AuthUserCheck = (callback) => {
    onAuthStateChanged(this.auth, (user) => {
      callback(user)
    })
  }


} export default AuthService


 ```




<br/>
<div align="center"> <span>그림 9 : 로그인 구현하기 - services/auth.js - </span></div>

<br/>
<br/>


Firebase에서 제공하는 Auth의 Api들을 받아와, 본 웹사이트의 로그인, 로그아웃, 사용자체크 기능을 구현했다. 


<br/>
<br/>

### 2. App.tsx


<br/>
<br/>


```typescript 

const App = ({authService, databaseService,exhibitionImageUploadService, workImageUploadService}:AppProps) =>{

  const [login, setLogin] = useState<boolean>(false)

  useEffect(() => {
    authService.AuthUserCheck((result:any) => {
      if(result){
        
        setLogin(true)
      }else{
        setLogin(false)
      }
    })
    
  
}, [login, authService])
  


const handleLogin = (password:string|number) => {
  
  if(password===process.env.REACT_APP_ART_WEBSITE_PRIVATE_ADMIN_PASSWORD){
    authService.AuthGooglePopupLogin()
    setLogin(true)
    return true
  }else{
    return false
  }
}
  return <section className={styles.myApp}>
    ~~~
    ~~~
    </section>
}
```


<br/>
<div align="center"> <span>그림 10 : 로그인 구현하기 - App.tsx - </span></div>

<br/>
<br/>

(1) [login, setLogin]: 가장 상위컴포넌트인 App.tsx에 login을 state변수로 등록하였다.

로그인 상태정보를 위에서 하위컴포넌트들에게 Props로 전달해주기 위해서이다. 

<br/>

(2) handleLogin: .env에 정의한 작가 비밀번호가 맞으면 로그인이 성공하게 하였다.   

login이 성공하면 AuthGooglePopupLogin을 실행해 파이어베이스 로그인을 실행해 준다. 파이어베이스 로그인이 완료되면 setLogin(true)를 해준다. 

<br/>

(3) useEffect : App.txt이 렌더 될 때마다 로그인 상태를 체크한다.
    login값이나 authService값이 변할 때마다 useEffect가 다시 실행 되어 즉각적으로 사용자 체크를 해준다. 



<br />

<div id="11"></div>

<br/>
<br/>


<br/>
<br/>

## 작품 확대하여 보기

<br/>
<br/>

---

### 목표: 작품 이미지를 마우스 스크롤로 확대할 수 있게 만들기

---

<br/>
<br/>


### 작품 확대하여 보기 컨셉정리
<br/>
<br/>

### 구현목표 
<br/>
<br/>

1. 마우스로 스크롤 한 만큼 작품 이미지의 scale이 커진다. 

    -> scroll 이벤트를 통해 e.deltaY로 스크롤된 값을 받은 후, 작품 이미지의 scale값에 연결시켜준다. 


<br/>
<br/>
<div align="center"> <img src="/readme_assets/gifs/11.gif" width="600px"  alt="그림 11: 마우스 스크롤을 통해 작품 이미지의 scale이 커지는 모습"></div>

<br/>
<br/>
<div align="center"> <span>그림 11 : 마우스 휠을 가함에 따라 스케일이 커지는 모습(이미지 확대 기준 설정 적용 전) gif</span></div>

<br/>
<br/>



2. 마우스 커서가 가르키는 포인트를 작품 이미지가 확대되는 기준으로 설정한다 

    -> scroll 이벤트가 생기면 event를 통해 마우스의 좌표값을 받고, 그 좌표점을 transform-origin으로 설정해준다.


<br/>
<br/>
<div align="center"> <img src="/readme_assets/gifs/12-1.gif" width="400px"  alt="그림 12: 기준점이 없이 확대되는 모습과 마우스 포인트를 기준으로 확대되는 모습의 비교 "><img src="/readme_assets/gifs/12-2.gif" width="400px"  alt="그림 12: 기준점이 없이 확대되는 모습과 마우스 포인트를 기준으로 확대되는 모습의 비교 "></div>

<br/>
<br/>
<div align="center"> <span>그림 12: 기준점이 없이 확대되는 모습과 마우스 포인트를 기준으로 확대되는 모습의 비교</span></div>

<br/>
<br/>
<br/>



### 작품 확대하여 보기 구현하기
<br/>
<br/>

### 1. 사용된 엘리먼트들

<br/>
<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/13.jpg" width="600px"  alt="그림 13: 사용된 엘리먼트들의 구성"></div>

<br/>
<br/>
<div align="center"> <span>그림 13 : 사용된 엘리먼트들의 구성</span></div>

<br/>
<br/>


1. modal_container(모달 파트) : 모달의 가장 부모 컴포넌트 

2. grey_background(뒷배경 파트) : 회색 배경, 유저의 입장으로는 무한대의 크기의 회색 배경으로 느껴진다. width, height가 각각 100%로 modal_container의 크기와 동일하다. 

3. image_container(뒷배경파트) : ```overflow: hidden;```으로 그림이 커져도 grey_background를 벗어나는 것을 방지한다. useRef를 이용해 getBoundingClientRect로 modal_container의 top과 left의 위치를 얻는다(자세한 설명은 뒤에).

4. Frame(이미지 파트): 작품 이미지의 scale 변화와 transform-origin값의 설정 조작을 여기서 한다. 
이번 장의 핵심기술이 여기에 적용된다. 

5. Picture(실제 이미지): img테그를 둘러 싼 div이고, 실제 작품이미지라고 생각할 수 있다. ```width:100%;``` 로 Frame에 가해지는 조작이 직접적으로 적용된다. 

<br/>
<br/>

> div가 쓸데없이 많지 않는가?.....
사실 Frame과 Picture는 하나의 div로 합쳐저도 무방하다. grey_background, image_container도 그렇다. 그런데 이렇게 나눈 이유는 기능별로 세세하게 분리하는 것이 나중에 유지보수하기 더 편하다고 생각했기 때문이다.

<br/>
<br/>


### 목표한 기능을 Frame에 적용하기


<br/>
<br/>


1. wheel로 스케일 조절하기

```typescript

const WorkModal = ({ modalOff, workUrl }: WorkModalProps) => {

    const [ratio, setRatio] = useState(0.5);

    const wheelHandler: React.WheelEventHandler<HTMLDivElement> = (e) => {

    const ratioValue = ratio - 0.001 * e.deltaY;

    if (ratioValue >= 0.26 && ratioValue < 0.5) {
        const slowDownRatioValue = ratioValue * 0.9;

        setRatio(slowDownRatioValue);
    } else if (ratioValue >= 0.5 && ratioValue < 2.06) {
        setRatio(ratioValue);
    }

    }
}
const Frame = styled.div`
    position: relative;
    transition: all 2s ease-out;
    transform: scale(
        ${({ ratio }: FrameProps) => {
            console.log(2.2*ratio)
            return 2.2 * ratio;
        }}
    );
`;
```

(1) ratio를 state로 관리해준다. 

(2) const ratioValue = ratio - 0.001*e.deltaY

wheelEventHandler의 event로 스크롤 한 양 e.deltaY값을 받아온다. (마우스스크롤을 위로 올릴시 e.deltaY값은 음수이다)

테스트를 진행해본 결과, 0.001을 곱해주자 이상적인 확대속도가 나왔다.

(3) setRatio(ratioValue)

if문을 넣어 이미지가 너무 작아질시 이미지 확대속도와 일반 확대속도를 구분하였다. 이렇게 계산된 ratioValue는 setRatio(ratioValue)를 통해 state를 업데이트 해주었다. 


(4) transform: scale( ~~ ) 

css-in-js(styled-component)로 scale값을 동적으로 관리해 주었다. 


<br/>
<br/>

이제 스크롤에 따라 이미지가 확대되긴 하지만, 이미지 확대의 기준점이 없어 확대시 이미지가 좌우로 크게 흔들려 유저가 불편을 느낄것으로 예상되었다.

<br/>


2. 마우스 커서의 포인트를 기준점으로 삼기

```typescript

const WorkModal = ({ modalOff, workUrl }: WorkModalProps) => {
	// 줌앤 패닝  줌 비율
const [ratio, setRatio] = useState(0.5);

const frameRef = useRef<HTMLDivElement>(null);
const imageContainerRef = useRef<HTMLDivElement>(null);



// 스크롤의 기준점

const [mouseStartX, setMouseStartX] = useState<number>(0);
const [mouseStartY, setMouseStartY] = useState<number>(0);

const wheelHandler: React.WheelEventHandler<HTMLDivElement> = (e) => {
    let imageContainer;
    let offsetX = 0;
    
    if (imageContainerRef.current) {
        imageContainer = imageContainerRef.current;
        offsetX = e.clientX - imageContainer.getBoundingClientRect().left;
        
    
    }

    let offsetY = 0;

    if (imageContainerRef.current) {
        imageContainer = imageContainerRef.current;
        offsetY = e.clientY - imageContainer.getBoundingClientRect().top;
    }

    setMouseStartX(offsetX);
    setMouseStartY(offsetY);

    const ratioValue = ratio - 0.001 * e.deltaY;

    if (ratioValue >= 0.26 && ratioValue < 0.5) {
        const slowDownRatioValue = ratioValue * 0.9;

        setRatio(slowDownRatioValue);
    } else if (ratioValue >= 0.5 && ratioValue < 2.06) {
        setRatio(ratioValue);
    }
};

const Frame = styled.div`
    position: relative;
    transition: all 2s ease-out;

    transform: scale(
        ${({ ratio }: FrameProps) => {
            return 2.2 * ratio;
        }}
    );

    transform-origin: ${({ mouseStartX }: FrameProps) => mouseStartX}px
    ${({ mouseStartY }: FrameProps) => mouseStartY}px;
    

`;

}

```



(1) 마우스 좌표를 state로 관리한다(mouseStartX, mouseStartY). 

(2) 마우스 커서의 좌표를 계산한다.

마우스 커스의 좌표는 아래와 같이 얻을 수 있다. 




<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/14.svg" width="700px"  alt="그림 14: 마우스 좌표 계산하기 "></div>
<br/>
<div align="center"> <span>그림 14 : 컴포넌트를 기준으로한 마우스 좌표 계산하기</span></div>

<br/>
<br/>


|e.clientX,<br/> e.clientY|브라우저 뷰포트(viewport) 기준으로 <br/>이벤트가 발생한 곳의 수평, 수직좌표|
|:--:|:--:|
|getBoundingClientRect().left,<br/>getBoundingClientRect().top, |브라우저 뷰포트(viewport)기준으로<br/> 이벤트가 일어난 엘리먼트의 (x,y)위치|
|offsetX,<br/> offsetY|컴포넌트를 기준으로 한 <br/> 마우스의 좌표 |

<br/>
<br/>


---

**컴포넌트를 기준으로한 마우스의 x좌표(offsetX) : e.clientX - getBoundingClientRect().left**
<br/>

**컴포넌트를 기준으로한 마우스의 y좌표(offsetY) : e.clientY - getBoundingClientRect().top**

---

<br/>
<br/>

위 처럼 Frame 컴포넌트를 기준으로 하는 마우스 커서의 좌표를 구할 수 있다. 

구한 값을 setMouseStartX, setMouseStartY에 각각 넣는다.

<br/>

(3) 앞에서 구한 좌표를 transform-origin 값으로 넣기 
<br/>

transform-origin은 엘리먼트에 transform이 적용될 때, transform이 무슨 점을 중심으로 transform되는지를 정해주는 css property이다. 

여기도 물론 css-in-js(styled-component)를 사용해 transform-origin값을 동적으로 조절한다. 

<br/>
<br/>
<div align="center"> <img src="/readme_assets/gifs/15.gif" width="1000px"  alt="그림 15: 그림 확대하기 기능 최종 결과 .gif "></div>

<br/>
<br/>
<div align="center"> <span>그림 15 : 그림 확대하기 기능 최종 결과 .gif</span></div>

<br/>
<br/>


이제 마우스 스크롤 이벤트가 일어나 scale값이 변할 때 마다, 마우스 포인터가 가리키고 있는 점을 transform-origin로 설정하게 된다. 이제 유저는 마우스 포인터가 가리키고 있는 곳을 중심으로 이미지를 확대할 수 있게되어 전보다 친절한 UI로 작품 이미지를 세부적으로 관찰할 수 있게 된다. 



<br />

<div id="12"></div>

<br/>
<br/>


<br/>
<br/>

## Firebase와 Cloudinary를 고른 이유

<br/>
<br/>




로그인, 메타데이타 저장, 고화질 이미지 저장등의 기능은 본 웹사이트에서 반드시 필요로 하는 기능이다. 

구글링을 통해 **Firebase**에서 로그인, 메타데이타 저장 기능을 동시에 지원하고 있다는 것 뿐만 아니라, Crashlytics나 Test lab등 개발자들에게 여러 유용한 Api를 제공해준다는 것을 알았다. 무료로 제공하는 스펙도 동시 접속 100대, 저장소 용량 1GB, 다운로드 제한 10GB/월 (2022년 05월 기준)으로 본 웹사이트를 운영하는데에는 충분했다. 

다만 나중에 알고보니 JSON기반이라 시각적으로는 파악하기 쉽지만, 같은 데이터가 다른 가지에 동시에 생성되는 경우에는, 데이터 관리 로직을 가지 수 만큼 만들어주는 수고를 해야했다. 

이미지 저장소로 Firebase의 storage, cloudinary를 후보로 두었다.  
Firebase Storage는 Firebase Auth와 연동하여 이미지 각각에 보안 조건을 걸 수 있었다(이미지가 노출 되는 걸 조건을 유저마다 적용 할 수 있는 보안 기능이 있다). Cloudinary는 보안조건을 걸 수는 없지만 이미지를 편집, 조작하는 Digital Asset Management Tool이 있고 10MB의 대용량 이미지가 저장이 가능하였다. 

<br/>
<br/>
<br/>

|이미지 저장소 비교|Firebase Storage|Cloudinary|
|:--:|:--:|:--:|
|가격|무료|무료|
|이미지 한장 당<br/> 최대용량|5MB|**10MB**|
|이미지 에셋<br/> 편집기능|X|O (지원은 해주나 백엔드 없이 <br/>Rest Api를 통한 서비스는 제한적임)|

<br/>
<br/>

<div align="center"> <span>표 : firebase Storage 와 Cloudinary 비교하기</span></div>


<br/>
<br/>

스펙들을 비교한 결과, **Cloudinary**사용하기로 결정했다. Firebase Storage에서 저장할 수 있는 이미지 한장 당 최대 용량이 5MB이고 Cloudinary는 10MB였다. 작가가 작품의 디지털 에셋을 저장하는 것이 본 웹사이트의 목적 중 하나인데, 작품사진들은 프로 사진사가 DSLR로 찍는 고화질 사진들로 되어 있기 때문이다(사진 한 장 당 용량이 보통 8,9MB, 10MB넘는 경우도 빈번하다). 또, 웹사이트의 기능중에 '작품 확대하여 보기'기능은 유저가 작품을 상세하게 확대하여 보는 기능인데 여기에 사용되는 작품 이미지는 최고화질을 요구하기 때문에 한 장당 최대 용량을 더 많이 지원해주는 Cloudinary를 저장소로 사용할 수 밖에 없었다.   Cloudinary는 Image transformation 기능을 제공한다. 이 기능을 사용해 고화질 이미지 용량을 400~500kb로 줄여 화면에 렌더하는게 가능했다. 

<br/>
<br/><br/>

### 결과:

<br/><br/> 

|데이터 저장소|**Firebase**|
|:--:|:--:|
|**이미지 저장소**|**Cloudinary**|

<br/><br/>
<br/><br/>
<br/><br/>




