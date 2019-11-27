# angular-lab-2019_hw-2

Продолжим тему быстрого питания. Вы хозяин небольшого кафе/магазина/чего угодно (кроме магазина покемонов, прошу), и у этого заведения есть возможность сделать заказ через интернет. В вашем приложении планируется две страницы: страница со списком всех товаров и страница с корзиной, в которой пользователь может ввести свои данные и отправить заказ. В течении нескольких домашних заданий мы постепенно соберем это приложение.

### Задание к лекции "Angular Intro", 19/11
##### Основная часть
1) Определитесь с тематикой вашего заведения, названием. Cоздайте приложение с этим названием (`ng new`)
2) Создайте компонент карточки товара. Он должен выводить название товара и стоимость.
3) Создайте компонент списка товаров. Он должен просто выводить карточки всех товаров.
4) Вставьте компонент со списком товаров в app компонент. Данные, которые использует этот список, должны браться из app компонента.

Для реализации посмотрите, как работает `@Input()`(propety binding) и `*ngFor`.

##### Часть под звездочкой *(можно делать не полностью или не делать вообще)*
5) Карточка товара должна отображать количество выбранного товара с кнопкой `+`. Изначальное количество - 0, каждое нажатие на `+` должно добавлять 1 товар. Для того, чтобы это сделать, посмотрите, как работает `@Output()`(event binding).
6) Помимо кнопки `+`, добавьте кнопку `-`. Она вычитает 1 товар. Если товаров 0, то она disabled.
7) Поместите все данные о товарах в сервис.

### Задание к лекции "Angular Components", 22/11
##### Основная часть
1) Карточка товара должна отображать количество выбранного товара с кнопкой `+`. Изначальное количество - 0, каждое нажатие на `+` должно добавлять 1 товар. Для того, чтобы это сделать, посмотрите, как работает `@Output()`(event binding).
2) Если пользователь наводит курсором мыши на карточку товара, то она подсвечивается рамкой. Если пользователь уводит курсор с карточки, то выделение исчезает. Реализуйте это с помощью `@HostListener()`.
3) Для компонента списка реализуйте следующее: если он пуст, то отображается html, переданный через Content Projection. Если в него передан непустой массив, то он отображает карточки с товарами.
4) Добавьте на страницу второй список и передайте в него пустой массив. Добавьте для первого списка заголовок "Товары" (или что-то другое, что соотвествует вашему контексту), а второму "Корзина". Определите для каждого из них надписи, которые отображаются, если список пуст.

##### Часть под звездочкой
5) Реализуйте добавление товаров в корзину, т.е. кнопку `Добавить в корзину` на карточке и обновление списка с корзиной. Учите, что кнопка `Добавить в корзину` в корзине не должна отображаться.

### Задание к лекции "Angular Services", 26/11
##### Основная часть
Напишите сервис, который умеет следующее:
1) Два приватных поля: список товаров и список товаров, которые находятся в корзине
2) Методы для получения списка всех возможных товаров и для получения списка товаров, которые находятся в корзине

###### Дальше есть простая версия и сложная. Если вы отображаете на карточке только кнопку `добавить в корзину`, то нужны:
3) Метод для добавления товара в корзину 
4) Метод для удаления товара из корзины

###### Если вы отображаете на карточке кнопку `добавить в корзину` и `+`, то нужны:
3) Метод для добавления товара в корзину (учтите, что пользователь может добавить несколько единиц одного товара)
4) Метод для удаления товара из корзины (учтите, что пользователь может убрать несколько единиц одного товара)
5) Метод для кнопки `+` (тут возможны несколько вариантов, так что если дойдете и не придумаете, как это сделать/ сделать это лучше, пишите)

(можно убрать кнопку `+` и не страдать, потому что второй вариант сильно сложнее)

##### Часть под звездочкой
Приватные поля в сервисе должны быть `BehaviorSubject`|иной сабджект, который вы посчитаете подходящим (см. rxjs). Внутри сервиса они должны изменяться с помощью метода `.next()` (и быть иммутабельными соотвественно), а снаружи быть доступными только для подписки, т.е. в get методах вы должны возвращать списки как-то так: `return this.productList$.asObservable()`.

### Дополнительные требования
1) Все сущности, которые вы добавляете, должны быть сгенерированы при помощи `ng cli`
2) Выберете с самого начала css препроцессор, который вы используете/хотите попробовать, и добавьте его в опции при выполнении команды `ng new`(можно добавить и после создания проекта, если не разберетесь, как это сделать, пишите). Если вы никогда не имели дело с препроцессорами, то можно пропустить это требование
3) *(не обязательно к выполнению, в первую очередь для тех, кто уже пишет на ангуляре)* Используйте библиотеку Angular Material
