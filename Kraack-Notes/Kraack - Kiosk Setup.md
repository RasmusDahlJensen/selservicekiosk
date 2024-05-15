
Root folder:
``AppSettings`` (Kopier fra ``machineInterface``)
``AppRoutes``

``AppModels`` som sørger for export af app timers, og forcer ny version til skærmen efter update ved at opdatere den url path med et versions tal fra backend

## Struktur:

#### Views:
`Homepage`
`Order Detail`

#### Factories:
`Error handling` en funktion til hvis der forekommer en fejl på siden der skal have en modal, f.eks. at et produkt er udsolgt mens du bruger skærmen, eller mulig fejlet betaling?
eg. ``ErrorHandlerFactory.ts``

`Theme handling` en funktion som kan skifte mellem CSS filer baseret på theme.

`Payment handling` en funktion som skaffer alle betalingsmuligheder, f.eks. mobilepay/kreditkort/kontant og viser dem på betalingsskærmen, samt indeholder en cancel transaction metode.

`Accessibility factory` en funktion til at indskyde et layout til at gøre det til 'halv' skærm og eventuelt andre accessibility features som skærmen skal have.

`Language handling` en funktion der kan skifte sprog på skærmen mellem dansk og engelsk? Skal indeholde default sprog, reset sprog og sæt nyt sprog funktioner.

`Product data` en funktion som fortager sig det API kald for at hente produkt data og holde det up to date, f.eks. hvis der er udsolgt.

#### Hooks(Directives):
`InteractionBlocker` Til når man skal block en interaction hvis man f.eks. har en dialog åben, så man undgår at kunne åbne noget bag den, f.eks. en dialog mere

`Add to cart` det er en directive som man vil kunne kalde på alle produkter for at ligge dem i kurven.

#### Component 
Components bliver HTML elementer som enten går igen, eller som skal indskydes 
##### Foodcard -x
![[Pasted image 20240416115136.png]]
##### Back button -x
![[Pasted image 20240416115003.png]]
##### Navbar -x
![[Pasted image 20240416115017.png]]
##### Banner-x
![[Pasted image 20240416115040.png]]
##### Footer -x
![[Pasted image 20240416115058.png]]
##### Scroll To Bottom Arrow
![[Pasted image 20240416115112.png]]
##### Menu section -X
Hver menu section laves til et komponent, som kan tage imod et array af elementer (f.eks 
```js
var element = {
    title: "Hello World",
    price: 40,
    imageURL: "RandomURL.com"
}
```
)

![[Pasted image 20240416115150.png]]
##### item and price Summary -X
![[Pasted image 20240416115226.png]]
##### Quickview
![[Pasted image 20240416120938.png]]

### Kraack

#### Directives

##### Item counter
Da Item Counter skal bruges på rigtig mange elementer, vil det give mening, at lave dette til en Directive
![[Pasted image 20240418154710.png]]

##### Adding Items
Funktionen med at kunne klikke på "+" for at åbne en pop-ud menu, som ændres til en "Quantity Counter", kommer til at blive brugt på hver item, så for kun at skulle vedligholde koden et sted, laves dette til et directive

![[Pasted image 20240418154859.png]]


#### Components
##### Sidebar navigation
Sidebar laves til et komponent, som tager imod et array med objekter.
Hvert objekt har navn, logo og path. Der laves et for-each/for-loop, som itererer over array'et, for at lave komponenter for hvert entry.
Array kunne se ud som dette:
```js
var sideBarNav = [

    {title: "Home", redirectPath: "SSK/Home", logoPath: "Random/Local/Storage"},
    {title: "DagensRet", redirectPath: "SSK/DagensRet", logoPath: "Random/Local/Storage"},
    
    {title: "Madretter", redirectPath: "SSK/Madretter", logoPath: "Random/Local/Storage"},
    
    {title: "Frugt", redirectPath: "SSK/Frugt", logoPath: "Random/Local/Storage"},
    {title: "Drikkelse", redirectPath: "SSK/Drikkelse", logoPath: "Random/Local/Storage"},

]
```

![[Pasted image 20240418134232.png]]
##### Modify Product
Modify Modal skal kunne tage imod selve produktet som bliver klikket på.
Kunne se ud som dette:
```js
var BurgerItem = {

    title: "American Cheese Burger",
    imageURL: "RandomPath.com/burgerPicture.png"
    size: [
        { optionName: "Lille", price: 0, selected: true },
        { optionName: "Mellem", price: 5, selected: false },
        { optionName: "Stor", price: 10, selected: false },
    ],

    breadType: [
        { optionName: "Lyst", price: 0, selected: true },
        { optionName: "Mørkt", price: 10, selected: false },
    ],

    options: [
        { optionName: "bøf", price: 25, Amount: 2 },
        { optionName: "Bacon", price: 5, Amount: 1 },
        { optionName: "Tomat", price: 5, Amount: 0 },
        { optionName: "Ost", price: 5, Amount: 2 },
        { optionName: "Løg", price: 5, Amount: 0 },
        
    ],
    price: 40,
    quantity: 1
}
```


![[Pasted image 20240418130136.png]]

Dette ville virke til både spise produkter, men også drikkelse, da vi kan bruge deres størrelse som en options
```js
var selectSoda = {
    title: "Pepsi",
    imageURL: "PathToImage",  
    options: [
        { optionName: "Lille", price: 20, Amount: 0 },
        { optionName: "Mellem", price: 25, Amount: 0 },
        { optionName: "Stor", price: 30, Amount: 1 },

    ]

}
```

![[Pasted image 20240418132352.png]]
##### Allergen description
Når der klikkes på det lille info ikon på et produkt/item, skal hele beskrivelsen for produktet samt allergener.
Kunne se sådan ud: 

```js
var BurgerItem = {

    title: "American Cheese Burger",
    description: "Long Description of item",
    
    //Size
    
    //breadType
    
    //options
    
     allergenerArray: [
        { allergenName: "Gluten", allegenImage: "PathToImage" },
        { allergenName: "Soya", allegenImage: "PathToImage" },
        { allergenName: "Nødder", allegenImage: "PathToImage" },
        { allergenName: "Fisk", allegenImage: "PathToImage" },
        { allergenName: "Mælk", allegenImage: "PathToImage" },
    ]
    
}
```
![[Pasted image 20240418130103.png]]

#### "Din ordre" entries
Siden med "Din ordre" laves til et view, men selve entries på siden, laves til et komponent, som tager imod et produktModel (ses herunder)
```js
var BurgerItem = {

    title: "American Cheese Burger",
    imageURL: "RandomPath.com/burgerPicture.png"
  size: [
        { optionName: "Lille", price: 0, selected: true },
        { optionName: "Mellem", price: 5, selected: false },
        { optionName: "Stor", price: 10, selected: false },
    ],

    breadType: [
        { optionName: "Lyst", price: 0, selected: true },
        { optionName: "Mørkt", price: 10, selected: false },
    ],

    options: [
        { optionName: "bøf", price: 25, Amount: 2 },
        { optionName: "Bacon", price: 5, Amount: 1 },
        { optionName: "Tomat", price: 5, Amount: 0 },
        { optionName: "Ost", price: 5, Amount: 2 },
        { optionName: "Løg", price: 5, Amount: 0 },
    ],
    price: 40,
    quantity: 1
}
```
![[Pasted image 20240418133143.png]]

##### Betalingsmuligheder
De betalingsmuligheder som brugeren kan vælge, kan laves til et komponent, som tager imod et objekt med en title samt logoPath. Array'et kan ligge i selve controlleren til siden, så det er "bare" at køre en for-each/for-loop, og lave et komponent for hver entry
```js
var paymentOptions = [
    {title: "MobilePay", imagePath: "Some/Local/Storage"},
    {title: "NFC", imagePath: "Some/Local/Storage"},
    {title: "CreditCard", imagePath: "Some/Local/Storage"}
]
```
![[Pasted image 20240418133834.png]]




#### Models:
Payment state.

#### Content:
Content indeholder alt vores typografi, ressourcer, billeder samt vores themes og layouts.
Og partials, altså vores styling til components og views.


Eksempel på struktur.
```bash
├── App
│   ├── Components
│   │   ├── FoodCard
│	│   │   ├── FoodCard.html
│	│   │   ├── FoodCard.ts
│	│   │   ├── FoodCard.css
│   │   ├── BackButton
│	│   │   ├── BackButton.html
│	│   │   ├── BackButton.ts
│	│   │   ├── BackButton.css
│   │   ├── NavBar
│	│   │   ├── NavBar.html
│	│   │   ├── NavBar.ts
│	│   │   ├── NavBar.css
│   ├── Directives
│   ├── Factories
│   │   ├── Themes
│	│   │   ├── Themes.ts
│   ├── Models
│   │   ├── PaymentState.ts
│   ├── Views
│   │   ├── HomePage
│	│   │   ├── HomePage.html
│	│   │   ├── HomePageController.ts
│   │   ├── OrderDetail
│	│   │   ├── OrderDetail.html
│	│   │   ├── OrderDetailController.ts
│   ├── App.ts
│   ├── AppConfig.ts
│   ├── AppController.ts
│   ├── AppModels.ts
│   ├── AppRoutes.ts
│   ├── AppSettings.ts
├── Content
│   ├── Fonts
│   ├── Images
│   │   ├── Flags
│   │   ├── Logos
│   ├── Styles
│   │   ├── Layout
│   │   ├── Partials
│	│   │   ├── Layout.scss
│	│   │   ├── Body.scss
│	│   │   ├── Dialogs.scss
│   │   ├── Themes
│	│   │   ├── Randers.scss
│	│   │   ├── Kolding.scss
│   │   ├── App.scss
├── Dist
├── Templates
│   ├── Fonts
│   ├── Images
├── Views
│   ├── Home
│   │   ├── Index.cshtml
│   │   ├── Landing.cshtml
```


### Flow
