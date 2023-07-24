# معلومات حول الكورس 

كورس شرح فريم ورك Reactjs لتطوير الويب تابع لشركه ويب ليد لتطوير البرمجيات يتم شرحه بواسطه زياد شلبي
## انشاء مشروع ReactJS

بننشاء مشروع رياكت بواسطه اداه  [npm](https://www.npmjs.com/package/create-react-app) وبنكتب الكود التالي في CMD

```bash
npm i create-react-app
```

## مشروع بسيط يعرض اليه عمل رياكت

```javascript
const SampleReact =()=>{
   return(
    <div className='btn'>
        <h1>NavBar</h1>
        <img />
    </div>
    )
}
```
## شرح مفهوم ال JSX
توفِّر JSX علينا عناء إنشاء العناصر بإستخدام الدالة React.createElement(component, props, ...children). انظر إلى الشيفرة التالية في JSX:
```javascript
<MyButton color="blue" shadowSize={2}>
  انقر هنا
</MyButton>
```
تُترجَم الشيفرة السّابقة إلى:
```javascript
React.createElement(
  MyButton,
  {color: 'blue', shadowSize: 2},
  'انقر هنا'
)
```
بإمكانك أيضًا استخدام الشكل ذاتي الإغلاق للعنصر إن كان لا يحتوي على أيّة عناصر أبناء:
```javascript
<div className="sidebar" />
```
تُترجَم الشيفرة السّابقة إلى:

```javascript
React.createElement(
  'div',
  {className: 'sidebar'}
)
```
تحديد نوع عنصر React
يُحدِّد الحرف الأول في وسم JSX نوعَ عنصر React.

تُشير الأنواع التي تبدأ بحرف كبيرة (Capitalized types) إلى أنّ العنصر المذكور هو مُكوِّن React. تُترجَم هذه العناصر إلى مرجع مباشر إلى المتغيّر الذي يحمل اسمها، لذا إن استخدمت التعبير <Foo /> في JSX يجب أن يكون المتغيّر Foo في نفس المجال.

يجب على React أن تكون في نفس المجال
لمّا كانت JSX تُترجَم إلى نداءات للتابع React.createElement، فيجب على مكتبة React أن تكون في نفس المجال الذي تكون فيه شيفرة JSX.

على سبيل المثال الاستيراد التالي ضروري في هذه الشّيفرة على الرغم من أنّ React و CustomButton لا يُشار إليهما بشكل مباشر من JavaScript:

```javascript
import React from 'react';
import CustomButton from './CustomButton';

function WarningButton() {
  // return React.createElement(CustomButton, {color: 'red'}, null);
  return <CustomButton color="red" />;
}
```
إن لم تستخدم مُحزِّم JavaScript وطلبتَ React من داخل عنصر <script>، فهي موجودة مُسبقًا في نفس المدى لأنّها عامّة (global).

استخدام النقطة لأنواع JSX
بإمكانك الإشارة أيضًا إلى مُكوِّن React باستخدام النقطة من داخل JSX. وهو أمرٌ جيّد إن كانت لديك وحدة (module) وحيدة والتي تُصدِّر عدّة مُكوِّنات React. على سبيل المثال إن كان MyComponents.DatePicker مُكوِّنًا، فيُمكِنك استخدامه بشكلٍ مباشر من JSX كما يلي:
```javascript
import React from 'react';

const MyComponents = {
  DatePicker: function DatePicker(props) {
    return <div>تخيّل وجود {props.color} انتقاء للتاريخ هنا.</div>;
  }
}

function BlueDatePicker() {
  return <MyComponents.DatePicker color="blue" />;
}
```
يجب كتابة المكونات المعرفة من قبل المستخدم بأحرف كبيرة
عندما يبدأ نوع العنصر بحرف صغير، فهو يُشير إلى مُكوِّنات داخليّة مثل <div> أو <span> وينتج عنه السلسلة النصيّة 'div' أو 'span' والتي تُمرَّر إلى التّابع React.createElement. أمّا الأنواع التي تبدأ بأحرف كبيرة مثل <Foo /> فتُترجَم إلى React.createElement(Foo) وتُوافِق مُكوِّنات مُعرَّفة أو مُستوردة في ملّف JavaScript لديك.

نوصي بتسمية المُكوِّنات بأحرف كبيرة، وإن كان لديك مُكوِّن يبدأ بحرف صغير فعيّنه إلى مُتغيّر يبدأ بحرف كبير قبل استخدامه في JSX.

على سبيل المثال لن تعمل الشيفرة التالية كما هو مُتوقَّع:
```javascript
import React from 'react';

// :خطأ! هذا مُكوِّن ويجب أن يبدأ بحرف كبير
function hello(props) {
  // صحيح! هنا استخدام العنصر div صحيح كونه عنصر في HTML
  return <div>أهلًا  {props.toWhat}</div>;
}

function HelloWorld() {
  // خطأ! تعتقد React أنّ العنصر hello هو عنصر في HTML لأنّه لا يبدأ بحرف كبير
  return <hello toWhat="بالعالم" />;
}
```
```javascript
import React from 'react';

// صحيح! هذا مُكوِّن ويجب أن يبدأ بحرف كبير
function Hello(props) {
  // صحيح! هنا استخدام العنصر div صحيح كونه عنصر في HTML
  return <div>Hello {props.toWhat}</div>;
}

function HelloWorld() {
  // صحيح! تعلم React أنّ Hello هو مُكوِّن لأنّه يبدأ بحرف كبير
  return <Hello toWhat="World" />;
}
```

## بعض المواقع الي ها نستخمها في الكورس
  
  [npm](https://www.npmjs.com/)

  [oldReact](https://legacy.reactjs.org/)
  
  [newReact](https://react.dev/)


## حقوق الملكيه و البث

[WEBLED](https://webled.online)
