# 라이브러리 사용했던 예시를 하나 상세하게 설명
```js
import { Navigation, Pagination, Scrollbar, A11y } from 'swiper';

import { Swiper, SwiperSlide } from 'swiper/react';

// Import Swiper styles
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';
import 'swiper/css/scrollbar';

export default () => {
  return (
    <Swiper
      // install Swiper modules
      modules={[Navigation, Pagination, Scrollbar, A11y]}
      spaceBetween={50}
      slidesPerView={3}
      navigation
      pagination={{ clickable: true }}
      scrollbar={{ draggable: true }}
      onSwiper={(swiper) => console.log(swiper)}
      onSlideChange={() => console.log('slide change')}
    >
      <SwiperSlide>Slide 1</SwiperSlide>
      <SwiperSlide>Slide 2</SwiperSlide>
      <SwiperSlide>Slide 3</SwiperSlide>
      <SwiperSlide>Slide 4</SwiperSlide>
      ...
    </Swiper>
  );
};
```
### swiper/react 라이브러리를 이용하여 슬라이드 구현
npm i swiper 라이브러리 설치   
Swiper, SwiperSlide 를 import 하여 슬라이드 구현
- spaceBetween 슬라이드간 간격 조정
- slidesPerView 한 눈에 볼 수 있는 슬라이드 개수 조정
- navigation 슬라이드 전환 화살표
- pagination 슬라이드 아래에 개수 순서 표현
- clickable : true 를 이용하여 navigation, pagination 버튼 클릭 가능하게 함
- autoplay 자동 전환
