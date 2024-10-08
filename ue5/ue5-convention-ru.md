# avrsllc-convention
# Руководство по стилю проекта UE5, создано Advanced VR Solutions.

Данное руководство основанно на переводе общей конвенции [ShadowPKx](https://github.com/ShadowPKx/ue4-style-guide-rus). В нем представлена более широкая информация по неймингу и логике структуры проектов на Unreal Engine.

<a name="main-terms"></a>
## Основные термины

<a name="terms-level-map"></a>
##### Карты/Уровни (Levels/Maps)

Слово 'карта' в основном используется в обозначении слова 'уровень' — эти слова считаются равноценными, аналогично английскими Level и Map. Но в работе будут так же применяться Level Instance, что в свою очередь приводит к тому, что предпочтитель говорить об 'уровнях' и 'экземплярах уровней'. 

<a name="terms-cases"></a>
##### Использование верхнего и нижнего регистра в нейминге ассетов.

Есть несколько разных способов, как называть вещи. Вот самые популярные методики:

> ###### ДельфиСтиль
>
> Каждое слово начинается с большой буквы, а всё слово пишется без пробелов, нижних пробелов, дефисов и т.п. Например: `DesertEagle`, `StyleGuide`, `ASeriesOfWords`.
> 
> ###### верблюжийСтиль
>
> Похож на ДельфиСтиль, но первая буква пишется в нижнем регистре. Например: `desertEagle`, `styleGuide`, `aSeriesOfWords`.
>
> ###### Змеиный_стиль (а.к.а. snake_case)
>
> Использование регистра в начале слов не определено, но слова разделяются нижним пробелом. Например: `desert_Eagle`, `Style_Guide`, `a_Series_of_Words`.

В нашем пайплайне применятеся комбинация из "ДельфиСтиля" и "Змеиного_стиля", т.е. `StreetLight`, `Building_Curch`,  `T_Door_Old_D.png`, `S_Terrain_Grass`. Это означает, что написание имени всегда начинается с большой буквы, не важно, начиная с начала слова или после символа нижнего подчеркивания `_`.


<a name="0"></a>
## 0. Принципы и идеи

<a name="0.1"></a>
### 0.1 Для общего понимания того, как в целом устроены руководства стилей, в частности в UE4\5, рекомендуется ознакомиться с оригинальным текстом в начале этого гайда. Но для работы следует следовать конкретно данному гайдлайну.

<a name="0.2"></a>
### 0.2 Вся структура проекта, материалы для разработки, код в любом Unreal Engine проекте должны выглядеть так, будто всё это создано одним человеком — не важно, как много людей на самом деле участвует.

Данное руководство по стилю созданно для того, чтобы повысить продуктивность создателей контента и управляемость проектом с стороны руководства.

<a name="0.3"></a>
### 0.3 Мы помогаем друзьям следовать хорошему стилю

Хорошей практикой является помогать товарищам с поддержанием порядка в проекте согласно гайдлайну.
Если вы видите, что кто-то работает не по руководству стиля, или вовсе без какого-либо — объясните это тому человеку.

При работе в комаде и во время обсуждений в Дискорде или на Зуме постоянство стиля также помогает быстро найти отклик и решение на возникший вопрос или проблему. 

> #### "Никому не хочется рыться в неопознаном нагромождении файлов, разношерстном нейминге мешей и изучать непонятные названия материалов в проекте."

Если вы увидили, что этот кто-то не следует какому-либо руководству стиля, отправьте ему ссылку на этот документ.

<a name="0.4"></a>
### 0.4 Убирайте за собой 

Во время разработки вполне могут возникнуть так назваемые мусорные файлы - старые меши, не актуальные варианты текстур, автоматически созданные материалы от импортированных ресурсов. Все это захламляет проект и навигацию в нем. Старайтесь заниматься очисткой от ненужного сразу(!), не оставляйте все на финальные стадии проекта. Через месяц работы над проектом вы можете просто не вспомнить, что где есть и для чего оно было нужно.

>#### Чтобы проверить ассет на его актуальность в проекте можно использовать инструмент Reference Viewer. Достаточно выбрать необходимые для проверки ассеты и в контекстном меню (`ПКМ`) выбрать пункт Reference Viewer.

<a name="toc"></a>
## Содержание

> 0. [Основные термины](#main-terms)
> 1. [Соглашение о наименованиях](#anc)
> 1. [Структура папок проекта](#structure)

<a name="anc"></a>
<a name="1"></a>
## 1. Соглашение о наименованиях 

Соглашение о наименованиях должно восприниматься как закон. В проекте, следующем соглашению о наименованиях, легко управлять ассетами, искать и обрабатывать их.

В большинстве случаев, ассетам присваивается префикс-аббревиатура на основе названия типа этого ассета + нижний пробел `_`.

<a name="prohibited-languages"></a>
<a name="1.0"></a>
### 1.0 Русский и иные языки
Использование русских и иных языков в названиях ассетов строго запрещается.

*Не бойтесь пользоваться переводчиком*. Лучше чудаковатое название на английском, нежели написанное транслитом слово `Lavka`, или, того хуже, так и оставленное на русском `Лавка`.
Исключением является использование записи латиницей имен собственных, например `Kazan`, `Alushtinskaya`, `Stariy_Pokrov`.

Суть данного ограничения связана с проблемами не-латинских символов при компиляции проектов, преобразовании и в ходе других внутренних процессов UE и сторонних плагинов — такие ошибки будет трудно отловить и исправить, так что лучше не делайте их вообще.

<a name="base-asset-name"></a>
<a name="1.1"></a>
### 1.1 Базовое название - `Префикс_БазовоеНазвание_Вариант_Суффикс`

У каждого ассета должно быть своё _базовое название_. Оно используется как средство логической группировки материалов разработки. Любой ассет, являющийся частью определённой логической группы, должен следовать стандарту  `Префикc_БазовоеНазвание_Вариация_Суффикс`.

Использование схемы `Префикc_БазовоеНазвание_Вариация_Суффикс` с её осознанием уже гарантирует создание "хороших" имён. Вот подробные правила по использованию этой схемы:

* `Префикс` и `Суффикс` определяется типом ассета, исходя из таблиц [Модификаторов имён ассетов](#base-asset-name).
* `Базовое название` определяется коротким и легко отличимым названием касательно предметной области вашей группы ассетов. Например, если у вас есть скульптура льва, то все ассеты для льва должны содержать `БазовоеНазвание` = `Lion`.
* Для особенных или уникальных вариантов ассета используйте `Вариант` — короткое и легко различимое имя, отражающее логическую группировку ассетов, образующих подмножество на основе базового имя ассета. Например, если у льва есть несколько вариантов текстур, то у этих текстур должно быть всё то же базовое имя `Lion`, но также и `Вариант`. "Гранжевый" вариант можно назвать `Lion_Grunge`, а обновленный "Fresh"— `Lion_Fresh`.
* Для уникальных но схожих ассетов, относящихся к одной группе, добавляется нумерующий `Вариант` — двузначное число, нумерация которого начинается с `01`. Например, если вы занимаетесь задачами по созданию окружения и генерирует валуны, которые нельзя просто так взять и назвать, то их можно назвать как `Rock_01`, `Rock_02`, `Rock_03`, и т.д. За исключением редких случаев, не используйте трёхзначное число. Если у вас более 100 ассетов в одной группе, вам следует разбить её на несколько других, используя другие базовые названия или варианты.
* В зависимости от того, как у вас создаются ассеты, вы можете использовать несколько имён-вариантов, друг за другом. Например, если вы создаёте ассеты для пола, вам будет нужно использовать базовое имя `Flooring` с вариантами вроде `Flooring_Marble_01`, `Flooring_Maple_01`, `Flooring_Tile_Squares_01`.

<a name="1.1-examples"></a>
#### 1.1 Примеры

##### 1.1.1 Здание

| Тип ассета (RU)          |Тип ассета (EN)           | Название ассета                |
| ------------------------ | ------------------------ | ------------------------------ |
| Статичный меш            | Static Mesh              | S_Building                     |
| Материал                 | Material                 | M_Building                     |
| Текстура (Diffuse/Albedo)| Texture (Diffuse/Albedo) | T_Building_D                   |
| Текстура (Normal)        | Texture (Normal)         | T_Building_N                   |
| Текстура (Старый Diffuse)| Texture (Старый Diffuse) | T_Building_Old_D               |

##### 1.1.2 Фонари

| Тип ассета (RU)           | Тип ассета (EN)         | Название ассета                |
| ------------------------- | ----------------------- | ------------------------------ |
| Статичный меш (01)        | Static Mesh (01)        | S_StreetLight_01               |
| Статичный меш (02)        | Static Mesh (02)        | S_StreetLight_02               |
| Статичный меш (03)        | Static Mesh (03)        | S_StreetLight_03               |
| Материал                  | Material                | M_StreetLight                  |
| Экземпляр материала (Снег)| Material Instance (Snow)| MI_StreetLight_Snow            |

### 1.2 Модификаторы имён ассетов

Используйте эту таблицу для [базовых названий](#base-asset-name), когда именуете ассеты.

<a name="base-asset-name"></a>



| Тип ассета (RU)      | Тип ассета (EN)    | Префикс      | Суффикс    | Примечания                          |
| -------------------- | ------------------ | ------------ | ---------- | ----------------------------------- |
| Уровень              | Level              |              |            |                                     |
| Уровень (освещение)  | Level (Lighting)   |              | _Lighting  |                                     |
| Уровень (запакованный)| Packed Level      | BPP_         |            |                                     |
| Блупринт             | Blueprint          | BP_          |            |                                     |
| Материал             | Material           | M_           |            |Мастер материалы будут имееть префикс M_MS_|
| Экземпляр материала  | Material Instance  | MI_          |            |                                     |
| Функция материалов   | Material Function  | MF_          |            |                                     |
| Статичный меш        | Static Mesh        | S_           |            |                                     |
| Скелетный меш        | Skeletal Mesh      | SM_          |            |                                     |
| Текстура             | Texture            | T_           | _?         | См. [Текстуры](#anc-textures)       |
| Система частиц       | Particle System    | PS_          |            |                                     |


### Материалы

| Тип ассета (RU)               | Тип ассета (En)               | Префикс      | Суффикс | Примечания                |
| ----------------------------- | ----------------------------- | ------------ | ------- | ------------------------- |
| Материал                      | Material                      | M_           |         |                           |
| Материал пост-обработки       | Material (Post Process)       | PP_          |         |                           |
| Функция материалов            | Material Function             | MF_          |         |                           |
| Экземпляр материала           | Material Instance             | MI_          |         |                           |
| Материал Parameter Collection | Material Parameter Collection | MPC_         |         |                           |
| Профиль подповерхности        | Subsurface Profile            | SP_ или SSP_ |         | Выберите одно. Лучше SP_ |
| Физический материал           | Physical Materials            | PM_          |         |                           |

### Текстуры 
| Тип ассета (RU)                  | Тип ассета (EN)             | Префикс      | Суффикс    | Примечания                       |
| -------------------------------- | --------------------------- | ------------ | ---------- | -------------------------------- |
| Текстура                         | Texture                     | T_           |            |                                  |
| Текстура (Diffuse/Альбедо/Основной цвет)| Texture (Diffuse/Albedo/Base Color)| T_ | _D      |                                  |
| Текстура (Нормаль)               | Texture (Normal)            | T_           | _N         |                                  |
| Текстура (Шерховатость)          | Texture (Roughness)         | T_           | _R         |                                  |
| Текстура (Металлик)              | Texture (Metallic)          | T_           | _M         |                                  |
| Текстура (Alpha/Прозрачность)    | Texture (Alpha/Opacity)     | T_           | _A         |                                  |
| Текстура (Нейтральный свет)      | Texture (Ambient Occlusion) | T_           | _O или _AO | Выберите одно. Лучше _O          |
| Текстура (Неровность)            | Texture (Bump)              | T_           | _B         |                                  |
| Текстура (Излучение)             | Texture (Emissive)          | T_           | _E         |                                  |
| Текстура (Маска)                 | Texture (Mask)              | T_           | _Mask      |                                  |
| Текстура (Блеск)                 | Texture (Specular)          | T_           | _S         |                                  |
| Текстура (упакованная)           | Texture (Packed)            | T_           | _*         | См. примечание об упаковке текстур ниже. |


#### Упаковка текстур
Упаковка сразу нескольких слоёв информации в одну текстуру — стандартная практика. Примером служит упаковка текстур Ambient Occlusion, Roughness, Metallic как красный, зелёный и синий каналы одной текстуры. Чтобы построить суффикс для таких текстур, просто последовательно запишите суффиксы отдельных масок из таблицы выше, напр. `_ORM`.

> Часто альфа-канал включают в карту Diffuse/Альбедо. Так как это стандартная практика, добавлять суффикс `A` в суффикс `_D` необязательно.

Упаковывать сразу 4 канала информации в одну текстуру (в RGBA) не рекомендуется, за исключением использования канала A как Alpha вместе с картой Diffuse/Альбедо.

<a name="anc-misc"></a>
<a name="1.2.7"></a>
### Разное 

| Тип ассета (RU)         | Тип ассета (EN)         | Префикс    | Суффикс    | Примечания                       |
| ----------------------- | ----------------------- | ---------- | ---------- | -------------------------------- |
| Композиция звуков       | Sound Cue               | A_         | _Cue       |                                  |
| Микс звуков             | Sound Mix               | Mix_       |            |                                  |
| Звукозапись             | Sound Wave              | A_         |            |                                  |
| Таблица данных          | Data Table              | DT_        |            |                                  |
| Тип растительности      | Foliage Type            | FT_        |            |                                  |
| Тип растительности      | Landscape Grass Type    | LG_        |            |                                  |
| Слой ландшафта          | Landscape Layer         | LL_        |            |                                  |
| Виджет-блупринт         | Widget Blueprint        | WBP_       |            |                                  |


### 1.3 Требования к текстурам. Правильная настройка текстур. 

> 1. Текстуры должны строго соответствовать вышеприведенным правилам именования.
> 2. Текстуры должны быть переведены в режим __Virtual Texture__.
> 3. Разрешение текстур должно строиться по приципу __кратности степени 2__, т.е. 128, 256, 512, 1024, 2048 и т.д.
> 4. Корректным является соотношение сторон 1 к 1,(прим. 1024х1024). Соотношение 1 к 2, 1 к 4 (прим. 512х1024 или 1024 х 4096) __следует привести к соотношению 1 к 1__, т.к. виртуальные текстуры могут работать только с квадратными текстурами.
> 5. Текстуры, несущие в себе не цветовую информацию (GreyScale, Linear Color), такие как карта шерховатости, металлик, либо упакованные карты (_ORM, _EDO) должны быть включены как Virtual Linear Color (в параметрах текстуры отключен чекбокс sRGB)


<a name="2"></a>
<a name="structure"><a>
## 2. Структура папок проекта 

Структура папок также должна восприниматься как закон. Она так же важна для проекта, как и соглашение о наименованиях. Они тесно связаны, и нарушение правил любого из них приводит к ненужному хаосу в проекте.

Приведенная ниже структура и способ организации контента основываются на возможности поиска и фильтрации в Content Browser'e. Данный подход позволяет сократить количество подпапок и привести общий вид проектов к единообразию. 

> Если вы используете [соглашение о наименованиях](#1.2) выше, то использование папок вроде `Meshes`, `Textures`, и `Materials` будет избыточным действием, т.к. все ассеты уже отсортированы по префиксу и могут быть отфильтрованы в Content Browser.


### 2.1 Пример организации папок проекта
<pre>
├── Content/
│   ├── Framework
│   └── Park_Kyzminki/
│       ├── Environment/
│       │   ├── Junks
│       │   ├── Cars
│       │   ├── Props
│       │   └── Sits
│       ├── Building_Curch/
│       │   ├── Building
│       │   └── Props/
│       │       ├── Mosaic
│       │       └── Icons
│       ├── Building_Clinic/
│       │   ├── Building
│       │   └── Props/
│       │       ├── Lions         
│       │       ├── Well
│       │       ├── Tablet
│       │       └── Pictures
│       └── Building...
└── Plugins/
    └── Library/
        └── Content/
            ├── Environment
            └── Vegetation
                └── Trees
                    └── Tree_Birch_01
                └── Bushes
</pre>

Правила формирования именно такой структуры проекта описаны ниже.

### Подразделы

> 2.1 [Названия папок](#structure-folder-names)

> 2.2 [Папки верхнего уровня](#structure-top-level)

> 2.3 [Работа с Level\Map](#structure-maps)

> 2.4 [Дополнительные требования](#additional_que)

<a name="2.1"></a>
<a name="structure-folder-names"><a>
### 2.1 Названия папок 

Все названия папок подчиняются единому набору правил.

<a name="2.1.1"></a>
#### 2.1.1 Всегда используйте соглашение [о стиле](#terms-cases)

Предпочтительно применять ДельфиСтиль для единых (по логике применения) наименований. (прим. `StreetLights`, `ConstructSet`)
Если предполагается вариативность вида, то применяется Змеиный_Стиль. (прим. `Latern_01`, `Fence_Old_Rust`)

См. [Использование верхнего и нижнего регистра](#terms-cases).

<a name="2.1.2"></a>
#### 2.1.2 Никогда не ставьте пробелы 

В дополнение к [2.1.1](#2.1.1), не используйте пробелы. Пробелы могут вызвать падения различных средств компиляции и пакетной обработки. В идеале, путь к самому проекту тоже не должен содержать пробелы и быть расположен в папке вроде `D:\Projects`, а не `C:\Пользователи\Моё имя\Мои документы\Unreal Projects`.

<a name="2.1.3"></a>
#### 2.1.3 Никогда не используйте символы юникода

Если одно из ваших зданий/пропсов именуется 'Кёльн Тауер', его папка должна называться `KolnTower`. Варианты по типу `KölnTower`, `КельнТауер` не допускаются. Символы юникода могут быть хуже [пробелов](#2.1.2) для инженерных инструментов, а некоторые инструменты UE не поддерживают символы юникода и в путях к файлам.

> #### Если ваш проект страдает по [необъяснимым причинам](https://answers.unrealengine.com/questions/101207/undefined.html) от непонятных ошибок, а имя пользователя вашего компьютера содержит символы юникода (в т.ч. и русские буквы), то любой проект в папке `Мои документы` будет страдать аналогичным образом. Чаще всего достаточно переместить папку проекта в, скажем, `D:\Project`, и эти загадочные ошибки исчезнут.

Использование символов, отличных от `a-z`, `A-Z`, и `0-9`, напр. `@`, `-`, `_`, `,`, `*`, и `#` тоже может привести к неожиданным и трудно отслеживаемым последствиям на других платформах, в системах контроля версиями и неотшлифованных средствах разработки.

<a name="2.2"></a>
<a name="structure-top-level"><a>
### 2.2 Используйте папку верхнего уровня для всех ассетов вашего проекта </a>

Все те материалы, что вы создаете в проекте должны располагаться в папке, названной согласно самому проекту. Например, если проект называется 'Sobor_Nevskogo', то _всё_ его содержимое должно лежать в папке `Content/Sobor_Nevskogo`.

> Папка `Framework` не предназначена для хранения контентной части проекта, и потому недопустимо вносить в нее какие либо изменения без конкретной цели или поставленной задачи.

<a name="2.2.1"></a>
#### 2.2.1 Библиотека ассетов

По мере надобности в дополнительных ассетах будет подключаться папка `Library` (в разделе `Plugins`). В ней будут храниться готовые ассеты, сама папка является постоянно пополняющейся библиотекой материалов.  

<a name="2.2.2"></a>
#### 2.2.2 Перенос контента из одного проекта в другой

При работе над несколькими проектами нередко возникает необходимость переноса ассетов из проекта в проект. В таких случаях лучше произвести копию ресурсов через инструмент Migrate в Content Browser, т.к. он не только копирует сам ассет, но и все его зависимые ресурсы.

 >Эти зависимости легко генерируют проблемы при слиянии. Если у ваших двух проектов нет одноимённых с названием проекта папок в верхнем уровне контента, то ассеты с аналогичным названием (а то и уже адаптированные из другого проекта) могут быть уничтожены инструментом миграции.

 >После миграции, безопасное слияние ассетов может быть сделано через инструмент 'Replace References' content browser-а. После завершения миграции и слияния, лишняя папка на верхнем уровне проекта должна быть удалена. Это гарантирует _100%_ безопасность ваших миграций.

<a name="2.2.3"></a>
##### 2.2.3 Организация пользования проектом и импортом контента

Задачи могут подразделяться на __глобальные__ и __частные__. Под глобальными подразумевается создание цельного комплекса здания, конкретного объекта, чье описание выходит за рамки понятия 'Props'. В таком случае в папке с наименованием проекта создается папка для данного объекта. (прим. `Content/Sobor_Nevskogo/Building_Church`). Внутри этой папки должно находиться все, что относится конкретно к данному зданию. 

+ Папка `Building` должна содержать весь контент(статик меши, текстуры, материал инстансы), относящийся непосредственно к глобальному объекту.
+ Все дополнительные объекты, например скамейки, урны, водостоки, которые используются только в этом здании (но являются отдельным оперируемым объектом) - должны попадать в папку `Props` и уже в ней использовать свои папки, названные согласно наименованию объекта.

Под частными (или *конкретными*) задачами подразумевается создание общих для проекта ассетов, которые не относятся ни к какому либо конкретному объекту. Примерами обычно служат различные бордюры, лампы уличного освещения, растительность в виде деревьев, кустов и пр. Для хранения подобного контента служит папка  `Environment` в папке с названием проекта. В ней так же создается папка с добавляемым ассетом.

В качестве визуального примера структура папок при работе над условным "Центральным Собором Невского" будет выглядеть следующим образом.
<pre>
├── Content/
│   └── Sobor_Nevskogo/
│       ├── Environment/
│       │   ├── Laterns
│       │   ├── Bushes
│       │   └── Trees/
│       │       ├── Maple_01
│       │       └── Maple_02
│       ├── Building_Curch/
│       │   ├── Building
│       │   └── Props/
│       │       └── WoodenSits
</pre>

<a name="2.2.4"></a>
#### 2.2.4 Сторонние ассеты, плагины с Маркета

В случае, если возникнет задача добавить кастомный контент из Маркета, ассеты гарантированно не будут пересекаться с файлами вашего проекта, т.к. у них всех есть своя папка верхнего уровня.

Во избежание проблем с зависимостями, а так же в качестве поддержания порядка в структуре проекта папка импортированного контента должна быть перемещена в папку `Environment`. Это нужно сделать сразу после импорта стороннего контента.

>Это правило касается и контента, полученного с помощью стороннего контент-плагина, полученного, к примеру, от другого члена команды. К примеру, если вам передали особый вид скамеек контент плагином, следует добавить плагин в проект, перенести содержимое плагина в папку  `Environment` с корректным по логике пользования названием, за тем отключить полученный плагин и удалить его из проекта в Explorer'e.



<a name="2.3"></a>
<a name="structure-maps"></a>
### 2.3 Менеджмент Level и Level Instance[<sup>*</sup>](#structure)

В проекте существует основная карта\уровень - `base-map`. Она находится `/Content/Project_name/`. На этой карте происходит общая сборка всего проекта. Изменять местоположение этой папки запрещается, ровно как и изменять имя файла. 

В случае решения глобальной задачи, т.е. создания комплексного объекта, его сборка (а так же нанесение декалей и пр.) производится на отдельной карте\уровне, который сохраняется в папке с самим объектом и его исходниками. 

При решении частной задачи, создание отдельной карты\уровня не требуется.


<a name="2.4"></a>
<a name="additional_que"></a>
### 2.4 Дополнительные требования.

> + Не создавайте папки `Assets` или `AssetTypes`
> + Создание папки `Assets` является избыточным действием. Все ассеты и так являются ассетами.
> + Создание папок `Meshes`, `Textures`, или `Materials` — лишнее. Все ассеты именуются с учётом их типа, и их названия уже включают указание типа в префиксе. Такие папки только добавляют избыточности в проект и легко заменяются фильтрами в Content Browser.
> + Очень большие наборы ассетов получают свою собственную иерархию. Если в проекте оказалось большое разнообразие, к примеру, светильников, с разнообразным набором текстур и типов материалов, то хорошим решением будет выделить им отдельную папку `Lamps` в папке `Environment`.

