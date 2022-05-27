
## 주요기능 구현

<br/>
<br/>

## 작품소개 보러가기

<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/1.jpg" width="700px"  alt="그림 1: 운영체제와 프로세스"></div>

<br/>
<br/>
<div align="center"> <span>그림 1 : '작품소개 보러가기' 페이지들</span></div>

<br/>
<br/>

 
'작품소개 보러가기'코너는, 작가의 작품 하나하나를 비중을 들여 보여주고, 작가를 설명하는 글등을 가끔식 넣어서 관람자에게 작가가 어떤 스토리를 가진 작가이고, 어떤 스타일의 작품을 만드는지에 대한 첫인상을 주는 코너이다. 30~40여점 정도 되는 작가의 작품들을 모두 다 보여주진 못하고 이 코너에서는 20페이지 정도의 분량으로 만들기로 했다. 그래도 20페이지도 적은 분량이 아니기 때문에 페이지에 전반적으로 적용시킬 통일성 있는 규칙이 반드시 필요하였다. 같은 형식의 페이지 다수를 컴포넌트간의 간격과 폰트 크기등에 일정한 규칙을 정하지 않고 디자인을 하게 되면 통일성이 떨어져 디자인이 전반적으로 불안한 느낌을 주기 때문이다.

'작품소개 보러가기'코너에 적용할 각 페이지의 디자인 규칙으로, 작품을 하나하나 비중있게 보여야 할 것, 보여진 작품 하나하나에 제목, 년도, 재질등의 메타데이터를 적어 놓는 것, 페이지수를 보여줄 것 정도였다. 그리고 이 모든 규칙을 적용해 아래와 같은 디자인 템플릿을 만들었다. 



<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/2.svg" width="600px"  alt="그림 2: 운영체제와 프로세스"></div>

<br/>
<br/>
<div align="center"> <span>그림 2 : '작품소개 보러가기' 페이지 디자인 템플릿</span></div>

<br/>
<br/>

위의 내용을 바탕으로 만들어진 디자인 템플릿이다. 사용방법은 매우 쉽다. 작품 이미지를 디자인 템플릿의 가이드라인에 맞춰 작품 이미지를 집어 넣어서 만들기만 하면 된다. 
모든 페이지의 작품 이미지 들은 그림 2 의 틀 안에 걸쳐져 있으며 메타데이터, 페이지 번호의 위치도 정해진 틀 안에 걸칠수 있게 만들었다. 페이지들은 각잡히고 통일된 디자인을 가지게 되었고, 더 이상 작품사진의 크기를 얼마로 정할 건지, 위치를 어디에 배치할 건지와 같은 무한대에 수렴하는 디자인 가짓수에 대해 고민하는 일은 열 몇가지 수로 확줄어 디자인하는 입장에서 훨씬 수월해졌다. 물론 이 틀로 표현할 수 있는 페이지 디자인 수는 열 몇가지 정도밖에 되지 않는다라는게 단점이 되기도 하지만 페이지 총 수는 20페이지 정도이기 때문에 몇 번 중복되는 디자인들을 서로 페이지 거리를 띄어 놓으면 충분히 쓸만하다. 


<br/>
<br/>
<div align="center"> <img src="/readme_assets/imgs/3.jpg" width="600px"  alt="그림 3: 페이지 디자인 템플릿을 사용해 페이지를 디자인한 모습"></div>

<br/>
<br/>
<div align="center"> <span>그림 3 : 디자인 템플릿을 실제로 적용한 모습</span></div>

<br/>
<br/>

다행이도 적용해보니 그림 하나하나들이 페이지 안에서 충분한 비중을 차지하고 있어서 방문객들이 작품에 집중할 수 있게 되고 작품과 글씨들 주변의 공백도 충분해서 깔끔한 느낌이 있다. 

<br/>
<br/>

## '작품소개 보러가기' 기술구현 


<br/>
<br/>


### 요약: 페이지 디자인 템플릿을 바탕으로 재사용가능한 컴포넌트를 만들어서 이를 바탕으로 21개의 페이지를 제작한다

<br/>
<br/>

### (1) 정적인 컴포넌트들 만들기

가장 기본이 되고 위치가 고정된 컴포넌트들부터 만든다(static_divs, pages)

<br/>
<br/>
<div align="center"> <img src="/assets/4.svg" width="600px"  alt="그림 4: 운영체제와 프로세스"></div>

<br/>
<br/>
<div align="center"> <span>그림 4 : 페이지 디자인 템플릿의 정적인 부분</span></div>

<br/>
<br/>

페이지 템플릿의 가장 기본적인 골격을 잡아주는 사각형들을 재사용 컴포넌트로 만들어 준다. 그리고 모든 페이지에 기본적으로 갖춰야 할 페이지 컴포넌트가 있다. 제일 가장자리(제일 큰)사각형 FirstDiv는 width: 100%; height: 72rem;으로 잡아준다. 자식 컴포넌트들이 position이 적용될 수 있게 position:relative;도 넣어 주었다. 
두번째 안쪽 사각형은 SecondDiv로 스펙은 아래 그림과 같다. 이 div들 안에 하위 컴포넌트들이 들어 올 수 있도록 children을 props로 설정하고 export를 해준다. 또한 이 div들은 틀로서만 작용하고 사용자의 눈에는 보일 일이 없다. 
그 다음으로 Page를 보여줄 Page Component들이다. 전부 SecondDiv의 하단부에 위치하고 SecondDiv의 긴 변을 기준으로 위치를 잡았다. Left, Center, Right 이렇게 3가지로 잡았다. 이 둘은 위치가 변할 일이 없는 정적 컴포넌트들이다. 


표

<br/>
<br/>
<div align="center"> <img src="/assets/5.svg" width="700px"  alt="그림 5: 운영체제와 프로세스"></div>

<br/>
<br/>
<div align="center"> <span>그림 5 : 페이지 디자인 템플릿의 정적인 부분</span></div>


<br/>
<br/>

### (2) 컨텐츠를 담을 재사용컴포넌트 만들기

<br/>
<br/>
<div align="center"> <img src="/assets/6.svg" width="700px"  alt="그림 6: 운영체제와 프로세스"></div>

<br/>
<br/>
<div align="center"> <span>그림 6 : 페이지 디자인 템플릿의 정적인 부분</span></div>

<br/>
<br/>


실질적인 컨텐츠를 담는 컴포넌트로 text container, image container, metadata container가 있다. (1)에서 설명한 위치가 변할 일 없는 (static)컴포넌트와 달리 이 셋은 배치에 따라 위치가 변하는 동적인 컴포넌트들이다. (1)의 컴포넌트들 처럼 동적인 컴포넌트들도 기본적인 css를 가지고 시작한다. 

Text container는 페이지안에서 Container가 차지하는 넓이부분을 정의해주기 위한 TextDiv와 실제 Text를 집어넣을 TextSpan으로 구성되어 있따. 
TextDiv에 Width를 주어 글이 너무 넓게 벗어나지 않도록 하고 TextSpan에는 적당한 폰트사이즈와 줄 높이를 주었다. 

Image Container는 ImageDiv와 ImageHorizontalImg(수평으로 긴 이미지일 경우), ImageVerticalImg(수직으로 긴 이미지일 경우)로 되어있다. 
혹시 모를 이미지의 삐져나옴에 대비해 ImageDiv에 overflow:hidden;을 주었다. ImageHorizontalImg에는 수평의 길이가 부모의 크기와 맞아 떨어지도록 width: 100%;을 넣었고 ImageVerticalImg에는 위와 똑같은 논리로 height: 100%;을 넣었다. 

MetadataContainer에는 MetadataDiv와 작품제목을 담당하는 MetadataSpan1, 크기, 재료, 년도를 담당하는 MetadataSpan2에 각자 쓰임에 맞춰 css를 작성해 주었다.

표


정적인 부분은 이렇게 만들었고 실제 페이지를 디자인 할때는 각 컴포넌트들에게 위치에 관한 css만 추가적으로 넣어주면 된다. 위치에 관한 추가적인 css는 각 페이지 컴포넌트들 안에 개별적으로 명세 해놓았다. 

<br/>
<br/>
<div align="center"> <img src="/assets/7.svg" width="700px"  alt="그림 7: 운영체제와 프로세스"></div>

<br/>
<br/>
<div align="center"> <span>그림 7 : 페이지 디자인 템플릿의 정적인 부분</span></div>

<br/>
<br/>

위와 같은 방법으로 총 21개의 페이지를 제작해 '작품소개 보러가기'섹션을 완성했다.



































