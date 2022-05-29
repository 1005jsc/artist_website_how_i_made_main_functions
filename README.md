
## 주요기능 구현

### 주요기능 구현 목차

1. [**작품소개 보러가기**](#9)
1. [**로그인**](#10)
1. [**작품 확대하여 보기**](#11)
1. [**Firebase와Cloudinary를 고른 이유**](#12)




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

 
'작품소개 보러가기'코너는, 작가의 작품 하나하나를 비중을 들여 보여주고, 작가를 설명하는 글등을 가끔식 넣어서 관람자에게 작가가 어떤 스토리를 가진 작가이고, 어떤 스타일의 작품을 만드는지에 관한 첫인상을 주는 코너이다. 30~40여점 정도 되는 작가의 작품들을 모두 다 보여주진 못하고 이 코너에서는 20페이지 정도의 분량으로 만들기로 했다. 그래도 20페이지도 적은 분량이 아니기 때문에 페이지에 전반적으로 적용시킬 통일성 있는 규칙이 반드시 필요하였다. 같은 형식의 페이지 다수를 컴포넌트간의 간격과 폰트 크기등에 일정한 규칙을 정하지 않고 디자인을 하게 되면 통일성이 떨어져 디자인이 전반적으로 불안한 느낌을 주기 때문이다.

'작품소개 보러가기'코너에 적용할 각 페이지의 디자인 규칙으로, 작품을 하나하나 비중있게 보여야 할 것, 보여진 작품 하나하나에 제목, 년도, 재질등의 메타데이터를 적어 놓는 것, 페이지수를 보여줄 것 정도였다. 그리고 이 모든 규칙을 적용해 넓이와 높이를 넣어주어 아래와 같은 디자인 템플릿을 만들었다. 



<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/2.svg" width="600px"  alt="그림 2: 운영체제와 프로세스"></div>

<br/>
<br/>
<div align="center"> <span>그림 2 : 작품소개 보러가기 페이지 디자인 템플릿</span></div>

<br/>
<br/>

위의 내용을 바탕으로 만들어진 디자인 템플릿이다. 사용방법은 매우 쉽다. 작품 이미지를 디자인 템플릿의 가이드라인에 맞춰 작품 이미지를 집어 넣어서 만들기만 하면 된다. 
모든 페이지의 작품 이미지 들은 그림 2 의 틀 안에 걸쳐져 있으며 메타데이터, 페이지 번호의 위치도 정해진 가이드라인에 걸칠수 있게 만들었다. 페이지들은 각잡히고 통일된 디자인을 가지게 되고, 더 이상 작품사진의 크기를 얼마로 정할 건지, 위치를 어디에 배치할 건지와 같은 무한대에 수렴하는 디자인 가짓수에 대해 고민하는 일은 열 몇가지 수로 확줄어 디자인하는 입장에서 훨씬 수월해졌다. 물론 이 틀로 표현할 수 있는 페이지 디자인 수는 열 몇가지 정도밖에 되지 않는다라는게 단점이다. 하지만 페이지 총 수는 20페이지 정도이기 때문에 중복되는 디자인들이 생기게된다. 이 경우 중복되는 디자인들의 페이지 거리를 서로 띄어 놓으면 이 방법은 충분히 사용할 만 하다. 


<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/3.jpg" width="600px"  alt="그림 3: 페이지 디자인 템플릿을 사용해 페이지를 디자인한 모습"></div>

<br/>
<br/>
<div align="center"> <span>그림 3 : 디자인 템플릿을 실제로 적용한 모습</span></div>

<br/>
<br/>

그림 하나하나가 페이지 안에서 충분한 비중을 차지하고 있어서 방문객들이 작품에 집중할 수 있게 되고, 작품과 글씨들 주변의 공백도 충분해서 디자인적으로 깔끔한 느낌이 있다. 

<br/>
<br/>
<br/>
<br/>

### 작품소개 보러가기 코드로 구현하기




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

제일 가장자리(제일 큰)사각형 FirstDiv는 ```width: 100%; height: 72rem;``` (html에서 ```font-size: 62.5%```로 잡았다 )으로 잡아준다. 자식 컴포넌트들에게 position이 적용될 수 있게 ```position:relative;```도 넣어 주었다. 두번째 안쪽 사각형은 SecondDiv로 스펙은 아래 표에 명시해 두었다.  또한 이 div들은 가이드라인으로서만 작용하고 사용자의 눈에는 보일 일이 없다. 

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


작품사진 업로드, 작품데이터 수정, 전시회 업로드 부분은 관람자가 접근해서는 안되고 작가님만 접근할 수 있는 private한 곳이다. 그래서 본 웹사이트에 로그인 기능을 만들어야했다. 

본 웹사이트는 백엔드를 따로 두지 않는 웹사이트지만 다행이도 **구글 파이어베이스**에서 로그인 관련 api들을 무료로 지원해 주고 있어서 적용해 보기로 하였다.

파이어베이스에서는 이메일, 구글 깃허브 연동등 다양한 방법으로 계정인증을 할 수 있다. 하지만 웹사이트의 작가님은 UI가 어렵고 계정 외우고 다니기 싫다고 하셨다. 그래서 작가본인이 원하는 비밀번호로 로그인을 할 수 있도록 만들어야 했다. 

이에 대한 해결책으로 작가가 제시해준 비밀번호를 웹사이트 비밀번호로 지정하고 그 비밀번호입력이 올바르면 파이어베이스 AuthServiceLogin을 일으키게 코드를 짰다. 
웹사이트의 비밀번호는 작가가 원하는 비밀번호로 설정하고, 파이어베이스의 AuthService도 사용하는 두마리의 토끼가 동시에 잡히는 셈이 되었다. 
비밀번호는 .env변수로 넣고 .gitignore처리를 해 두었다. 


<br/>
<br/>


### 로그인 코드로 구현하기 

<br/>
<br/>

### 1. services/auth.js 


<br/>
<br/>

```

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
<div align="center"> <span>그림 9 : 로그인 코드로 구현하기 - services/auth.js - </span></div>

<br/>
<br/>


Firebase에서 제공하는 Auth의 Api들을 받아와, 본 웹사이트의 로그인, 로그아웃, 사용자체크 기능을 구현했다. 


<br/>
<br/>

### 2. App.tsx


<br/>
<br/>


``` 

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
<div align="center"> <span>그림 10 : 로그인 코드로 구현하기 - App.tsx - </span></div>

<br/>
<br/>

(1) login, setLogin: 가장 상위컴포넌트인 App.tsx에 login을 state변수로 등록하였다.

가장 위에서 위치해 하위컴포넌트들에게 Props로 전달해주기 위해서이다. 

<br/>

(2) handleLogin: .env변수로 작가가 원하는 비밀번호를 등록하였다. 

login이 성공하면 AuthGooglePopupLogin을 실행해서 파이어베이스 로그인을 실행히준다. 파이어베이스 로그인이 완료되면 setLogin(true)를 해준다. 

<br/>

(3) useEffect : App.txt이 렌더될때마다 로그인 상태를 체크한다.
    login값이나 authService값이 변할 때 마다 사용자 체크를 해준다. 























