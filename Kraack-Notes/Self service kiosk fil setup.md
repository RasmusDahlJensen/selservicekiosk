
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
``Foodcard`` 
![[Pasted image 20240416115136.png]]
``Back button``
![[Pasted image 20240416115003.png]]
``Navbar``
![[Pasted image 20240416115017.png]]
``Banner``
![[Pasted image 20240416115040.png]]
`Footer`
![[Pasted image 20240416115058.png]]
`Scroll To Bottom Arrow`
![[Pasted image 20240416115112.png]]
`Menu section`
![[Pasted image 20240416115150.png]]
`item and price Summary`
![[Pasted image 20240416115226.png]]
`Quickview`
![[Pasted image 20240416120938.png]]
`Add to order button`
![[Pasted image 20240416121010.png]]
`Cancel button`
![[Pasted image 20240416121016.png]]
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
