# [WiP] Как развить взаимодействие Дизайнера с Разработчиком
Или как не усложнять жизнь разработчикам. Руководство к действию. [Чек-лист инклюдед](#чек-лист-дизайнера).

---

Вечному холивару разработчиков с дизайнерами посвящается.  
Этот документ представляет собой набор рекомендация __для дизайнеров от разработчиков__. 

> Если ты получил ссылку на этот документ, не обижайся пожалуйста на отправителя, тут про прокачку твоих скиллов, а не про то, что ты хреновый

### Содержание
* [Предисловие](#предисловие)
* [Глава 1. Размеры (WiP)](#глава-1-размеры)
  * [Чет или нечет?](#чет-или-нечет)
  * [Почему важны одинаковые отступы?](#почему-важны-одинаковые-отступы)
  * [Сетка](#сетка)
* [Глава 2. Порядок (WiP)](#глава-2-порядок)
* [Глава 3. Работа с SVG графикой (WiP)](#глава-3-svg)
* [Глава 4. Шрифты (WiP)](#глава-4-шрифты)
* [Глава 5. Состояния (WiP)](#глава-5-состояния)
* [Глава 6. Компоненты (WiP)](#глава-6-компоненты)
* [Глава 7. Адаптивность макета (WiP)](#глава-7-адаптивность-макета)
* [Глава 8. Pixel perfect (WiP)](#глава-8-pixel-perfect)
* [Глава 9. Коммуникация (WiP)](#глава-9-коммуникация)
* [Послесловие](#послесловие)
* [Чек-лист дизайнера](#чек-лист-дизайнера)

---

## Предисловие
> Мы сидели в одном из мессенджеров и болтали, я ныл о дизайнерах, а что если написать книгу как делать и как не делать, чтоб у разработчиков не болело?

### Кто я такой, чтоб это писать?
Роман Дворянов, дизайнер по образованию, фронтендер по призванию, шарю за веб с 2011 года.  
Все пункты этого гайда являют собой багажом боли и опыта. По аналогии со знаками дорожного движения.  

Давай договоримся, мы с тобой давно уже вместе работаем, давай на ты? В этом тексте я среднестатестический обезличенный разработчик, а ты это ты, т.е. дизайнер.

**Проверять за собой** - казалось бы очевидная вещь и все адекватные люди по умолчанию придерживаются этого принципа, в первую очередь в собственных интересах, чтоб потом не переделывать / не выслушивать / недополучать профит. Но все мы люди и допускаем ошибки, всего предусмотреть практически нереально (я как перфекционист, ответственно заявляю!).  
Уверен, что что-нибудь упущу и в этой редакции.

Работая фронтенд-разработчиком приходится взаимодействовать с разными коллегами, я взаимодействую с продактоунером, дизайнером, тестировщиком, backend-разработчиком, другими frontend-коллегами, аналитиками... много с кем. 

Сегодня я постараюсь объяснить как облегчить жизнь нам, разработчикам, если ты дизайнер. А также повысить свою эффективность и компетенцию на рынке труда, как выгодно отличатся и гордо называть себя UI архитектором, нет, даже Арт-директором, Б-гом искусства или просто как не быть овощем. 

**TL;DR**: Если коротко - не заставляй людей думать там, где можно не думать.  

Это можно отнести ко всему, но в нашем случае это относится как к отношениям между `designer <> developer` и `designer <> user`. Когда ты оставляешь элементы макета на "сойдет", этот секс скатывается на плечи тех, кто взаимодействует с твоей работой, на меня и юзера. Юзеру приходится гадать как тот или иной элемент работает и почему оно сделано так. Разработчику приходится гадать как эти же элементы должны были работать по твоей задумке и делать за тебя работу, вместо своей. __Это плохо__.

---

## Глава 1. Размеры
Что если я скажу, что все размеры макета взаимодействуют друг с другом на сайте в современном мире адаптивного интернета? Конечно, размер катастрофы раздут. Но эффект снежного кома никто не отменял.  
Мы можем контролировать размеры или дизайнить на глаз, аки настоящий импровизатор и мастер своего дела, но это единицы, делающие нестандартные, ломающие все рамки, дизайны.

### Чет или нечет?
**TL;DR**: Выбирай четные размеры.  

Почему нечетные плохо, а четные хорошо? Все дело в математике.
> Никогда не любил математику. И да, мы существуем - разработчики, не любящие математику.

Дело в том, что размер окна браузера четный, да. Я знаю, что ты можешь повозюкать браузер за край, молодец, но я верстаю, используя какое-то дефолтное разрешение экрана, потом уже накручивая адаптив. 

Ближе к делу, например:
```
Сайт с одной колонкой + 2 отступа по краям
```

#### Нечет:
Колонка: 901px (можно упростить до 1)  
Отступы: 121px (можно упростить до 1)

Размер сайта `1 + 1 * 2 = 3`, при дефолтном разрешении экрана где-то будет зазор или перекос, можно центрировать, но внутри этого контейнера у всех элементов тоже будет хаос, в общем давайте обойдемся без [энтропии](https://theoryandpractice.ru/posts/983-chto-takoe-entropiya-i-kak-s-ney-borotsya). А полупикселей в браузере, увы, нет(или не увы).  
Ситуация с двумя колонками  и тремя отступами нечетного размера не исправляют ситуацию `1 + 1 + 1 + 1 + 1 = 5`.  
В ситуации с одной колонкой и одним отступом, результат будет четный, что делает непредсказуемым дальнейшие расчеты.  
__Непредсказуемость плохо__.

#### Чет:
Колонка: 900px (упростим до 2)  
Отступ: 32px (упростим до 2)

В любом количестве колонок и отступов результат будет четный.  
__Предсказуемость хорошо__.

Все эти расчеты также работают для любого элемента сайта. Будь то форма входа или карточка товара.

**Зачем?**  
Справедливый вопрос - *Зачем мне замарачиваться на этот счет? Ведь ты просто нарисовал и забыл?*  
И да и нет. Да дизайн это еще не сайт, но и есть вероятность, что станет им не скоро, если фронтенд-разработчик будет думать еще и за тебя. Разработка в среднем занимает в 1,5 - 2 раза дольше времени, чем требуется на отрисовку дизайна, соответственно смотреть ваш дизайн и все его недочеты будут еще долгое время.

**Для чего?**  
Для ускорения процессов, конечно же, ну и чтоб тебе спалось лучше.

### Почему важны одинаковые отступы?
**TL;DR**: Отступы должны быть равны, понятны и не отвлекать.  

Это странный вопрос и если ты задаешься им, у меня плохие новости - ты лабух!  
Все в мире движется к гармонии, симметрии и логике, логика это когда слева 32 и справа 32, или по 15 или по 10, но главное, чтоб пользователь не задавался вопросами - «тут не по центру что-ли, но выглядит будто по центру 🤔», «А почему слева больше места, чем справа?» или «мне кажется или тут не помешало бы добавить пространства», это не его задача, а твоя.  
Да, это забавно троллить перфекционистов (клянусь, я так не делал, во всяком случае намеренно), но твоя задача, дизайнер, заключается в бесшовном сопровождении юзера до нужных мест, с минимальным отвлечением от цели. Все что несимметрично и несбалансировано - отвлекает. __Это плохо__.

Ведь разработчик, в большинстве случаев, это как очень дотошный инспектор и не потому, что вредный, а потому, что нам все это делать и если ты не смотришь на пиксели, то я смотрю, иначе никак. У меня нет возможности кодить на глазок, не могу перетягивать мышкой за край свои формочки, чтоб они на глаз смотрелись на «сойдет», но могу потерять отступы и могу забыть что-то допилить. И за это прошу у тебя прощения, мне нет оправдания кроме того, что я прописываю размеры и отсутпы, цвет и поведение абсолютно каждому элементу, что ты нарисовал и глазки мои замыливаются.  
Но все что не забыл, то обязательно пройдет через мои глаза и руки полный цикл разработки всех состояний, и способов взаимодействия. Такие дела.  
P.S. Я вижу все твои косяки, смекаешь? 😉

### Сетка
О сетках написано уже куча гайдов, давайте на пальцах что это и как работает:
> Сетка это визуальное разделение вашего макета на квадраты одного заданного размера.
Это значит, что в варианте здорового человека: каждый элемент вашего компонента должен делиться без остатка (по модулю) на высоту одного квадратика сетки. И в варианте курильщика: хотя бы отступы и размеры элементов делились без остатка по модулю.  
Например: 560 делится на 8-ми пиксельную сетку без остатка, а вот 540 не делиться без остатка. В этой сетке также допускаются элементы в 12 пикселов. Это также относится к градации размера шрифтов

---

## Глава 2. Порядок
Группируй и именнуй понятно слои, блеать!

---

## Глава 3. SVG
Суй в контейнеры, следи за полупикселем.

---

## Глава 4. Шрифты
Не злоупотребляй! В Figma есть [плагин](https://www.figma.com/community/plugin/734693888346260052/Able-%E2%80%93-Friction-free-accessibility), позволяющий посмотреть как видят элементы люди с ограниченным зрением

---

## Глава 5. Состояния
Не забывай! Особенно про фокус!

---

## Глава 6. Компоненты
**TL;DR**: D.R.Y. - "Don't repeat yourself" книга, которую не читал, наверное, только самый ленивый разработчик или которому уже наспойлерили главные принципы. Делай компонент, копипасть, редактируй только один. Все.  

Компонентый подход определенно превосходит классический "на глазок".  
Далее речь пойдет о редакторе Figma, но если ты сидишь в Sketch, то там тоже работает.

| Профит | Компонент | Не компонент |
| ------ | --------- | ------------ |
| Является компонентом | ✅ | 🚫 |
| Не нужно помнить про все места с этим элементом, при правках | ✅ | 🚫 |
| Можно выбирать из меню компонентов при разработке макета | ✅ | 🚫 |
| Удобно редактировать все одинаковые элементы в одном месте | ✅ | 🚫 |
| У разраба не бомбанет от разных отступов одинаковых элементов | ✅ | 🚫 |
| Сохраняет и улучшает экологию Земли | ✅ | 🚫 |
| Сдерживает выброс углекислого газа в атмосферу | ✅ | 🚫 |

Победа компонента очевидна! 🎉 Шутки шутками, а компонент экономит время прежде всего тебе.  
Компоненты это про автоматизацию процессов. Автоматизируй все, что можно автоматизировать. Пусть роботы работают, а мы отдохнем.

---

## Глава 7. Адаптивность макета
Продумывай! В т.ч. и мобилки и между мобилок.

---

## Глава 8. Pixel perfect
TL;DR: Pixel perfect это миф, а Design !== Browser. Да, твой макет в редакторе и сайт в браузере это разные вещи, поверь мы стараемся, чтоб везде все твои каракули смотрелось одинаково и хорошо. Но pixel perfect - это про фиксированный размер сайта и я надеюсь, что этот анахронизм остался далеко позади. Не стесняйся указывать нам на недочеты, которые потерялись при разработке, это лучше всего делать демонстрируя на скриншоте макета, чтоб я понимал о чем ты говоришь.

---

## Глава 9. Коммуникация
Общение важно и важно понимать, что даже если тебе кажется, что ты со мной на одной волне и мы понимаем друг-друга без слов, помни, это только так кажется, а мне в свою очередь кажется, что все что я тут пишу, тебе должно быть очевидно. Но в реальном мире мы просто два чудака, которые думают, что очевидность объективна.

---

## Заключение
W.i.P.

---

## Послесловие
### Будь проще
Поверь, твой лэндинг или формочка это не произведение искусства.  
В твоем случае дизайн это не искусство, это именно [дизайн](https://ru.wikipedia.org/wiki/Дизайн), тот смысл в который вкладывался в это слово изначально, ты архитектор, создающий схемы для реализации на производстве. И ту рюшечку, которую ты вложил в свой дизайн, видишь только ты... и я, потому что мне приходится это реализовывать, поверь, кроме нас двоих, никто больше и не заценит. Будь проще. Хочется напомнить, что веб это об передаче информации конечному пользователю, а время ваших экспериментов еще не пришло. Мир еще не готов. Если вы конечно не пилите что-то согласовано дикое.  
Градиенты, сеточки, это все конечно хорошо, но как это решает проблему клиента?

### Полезная литература
- [x] Максимально все забить в компоненты, из компонентов делать дизайн. Подробнее: ([рус.яз](https://ux.pub/luchshie-praktiki-figma-komponenty-stili-i-obschie-biblioteki/)), ([англ.яз](https://www.smashingmagazine.com/2019/06/building-component-library-figma/))
- [ ] Убедиться, что все эти вариации нескольких шрифтов на одном сайте необходимы и без них юзер пропадет.
- [x] Проверить размеры и отступы, все должны быть четные и кратные целому пикселу. Идеально сетка в 8px. Подробнее: ([рус.яз](https://habr.com/ru/company/digital-ecosystems/blog/319700/)), ([англ.яз](https://builttoadapt.io/intro-to-the-8-point-grid-system-d2573cde8632))
- [ ] Логическая структура разделов макета. Идеально по компонентам, группы с актуальным названием тоже сойдут. Статья от 2014 года для дизайнеров в фотошопе актуальна и по сей день. [Читать (рус.яз)](https://cgmag.net/photoshop-etiket-dlya-chajnikov)
- [ ] Экспортируемые свг элементы в контейнерах кратные целому пикселу
- [x] Логичное позиционирование объектов внутри компонентов и групп (Актуально для Figma, Подробнее: ([англ.яз](https://help.figma.com/hc/en-us/articles/360039957734-Apply-Constraints-to-define-how-layers-resize))), так будет быстрей и легче в дальнейшем делать макеты под разные экраны

## Чек-лист дизайнера
- [ ] все по сеточке
- [ ] Все по компонентам
- [ ] Ограниченный набор цветов, занесенный в переменные
- [ ] Одинаковые отступы
- [ ] Иконки - свг, иллюстрации пнг, убедись что все можно экспортировать, ничего не блочится, если есть вариант использовать векторную графику, вместо растра - используй. Пнг внутри контейнера свг - не свг, только если это не часть какой-то композиции, если эту часть можно заменить кривыми - меняй
- [ ] Лишние, скрытые, экспериментальные элементы дизайна удалены с финального макеты
- [ ] Разделы по группам, слои проименованы понятно
- [ ] Порядок элементов сверху вниз, если это не ломает имитацию поведения браузера фиксированный элемент, выезд за край)
- [ ] у свг есть контейнер с размерами в целых числах
- [ ] У интерактивных элементов отрисованы все состояния (ховер, эктив, фокус, дисэйблед, селектед)
- [ ] отрисованы все скрытые элементы (дропдауны, тултипы, бургеры)
- [ ] Отрисованы все обговоренные экраны приложения
- [ ] Отрисованы все оговоренные размеры браузеров, в том числе и 320
- [ ] Разработчик знает где взять шрифты и ему не придется их покупать
- [ ] Ты сделал последние правки и все утвердили и менять макет хотя бы до конца спринта не будешь
- [ ] Не использованы перекрытия, затемнители и тп, на вебе с ними все еще не ок
- [ ] Если используешь несколько градиентов в разных экспортируемых свг объектах и они будут использованы на одной странице, убедись, что разработчик в курсе этого нюанса или экспортни ему моим плагином, заменяющим схожие айдишники 
- [ ] Если есть вариант сделать прототип рабочий, покрывающий юзер флоу и максимальное количество кейсов, делай
- [ ] не злоупотребляй большим количеством шрифтов, это веб, у нас так на принято, а если злоупотребляешь, будь готов что ты рисуешь очень медленное приложение и большенство юзеров найдут нужную информацию еще до того как подтянется твой красивый шрифт и то только в том случае если разработчик учел этот момент и поставил фолбэк и грузит шрифты асинхонно
- [ ] убедись, что у тебя на макетах нет нелогичностей, которые могут озадачить юзера, все ясно и понятно
- [ ] не исправляй провалы в навигации добавлением дублирующей навигации
- [ ] Не используй маски, если это нельзя сделать без маски на вебе, на вебе нет масок, как и в твоей стране, кек)
- [ ] Если нужна анимация, рисуй или объясняй на пальцах

**Поздравляю, ты красавчик!**

---

##### ToDo:
* Добавить картинок и мемов
* Больше примеров
* Добавить Do/Don't
* Добавить ссылки для прокачки в чек-лист
* Добавить вредных советов для наглядности
* Добавить шутеек
* Дописать главы
