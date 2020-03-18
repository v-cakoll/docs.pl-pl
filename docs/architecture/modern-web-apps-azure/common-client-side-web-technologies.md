---
title: Wspólne technologie internetowe po stronie klienta
description: Architekt nowoczesne aplikacje internetowe z ASP.NET Core i Azure | Wspólne technologie internetowe po stronie klienta
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 2809c8539b42e8e2250039dceed1389b3cbdcd8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449377"
---
# <a name="common-client-side-web-technologies"></a>Wspólne technologie internetowe po stronie klienta

> "Strony internetowe powinny wyglądać dobrze od wewnątrz i na zewnątrz."  
> _- Paul Cookson_

ASP.NET Aplikacje podstawowe to aplikacje internetowe i zazwyczaj opierają się na technologiach internetowych po stronie klienta, takich jak HTML, CSS i JavaScript. Oddzielając zawartość strony (HTML) od jej układu i stylu (CSS) i jej zachowania (za pośrednictwem języka JavaScript), złożone aplikacje internetowe mogą korzystać z zasady Separacja obaw. Przyszłe zmiany w strukturze, projekcie lub zachowaniu aplikacji można łatwiej, gdy te problemy nie są ze sobą powiązane.

Podczas gdy HTML i CSS są stosunkowo stabilne, JavaScript, za pomocą struktur aplikacji i narzędzi, z których deweloperzy pracują przy tworzenie aplikacji internetowych, ewoluuje z zawrotną prędkością. W tym rozdziale przeanalizowano kilka sposobów, w jakie javascript jest używany przez programistów internetowych i zawiera ogólny przegląd bibliotek po stronie klienta Angular i React.

> [!NOTE]
> Blazor stanowi alternatywę dla platform JavaScript do tworzenia rozbudowanych, interaktywnych interfejsów użytkownika klienta. Obsługa Blazorpo w wersji klienckiej jest nadal dostępna w wersji zapoznawczej, więc na razie nie ma miejsca na ten rozdział.

## <a name="html"></a>HTML

HTML jest standardowym językiem znaczników używanym do tworzenia stron internetowych i aplikacji internetowych. Jego elementy tworzą bloki konstrukcyjne stron, reprezentujące sformatowany tekst, obrazy, wejścia formularzy i inne struktury. Gdy przeglądarka zwraca żądanie do adresu URL, niezależnie od tego, czy pobiera stronę, czy aplikację, pierwszą rzeczą, która jest zwracana, jest dokument HTML. Ten dokument HTML może odwoływać się lub zawierać dodatkowe informacje na temat jego wyglądu i układu w postaci CSS lub zachowania w postaci Języka JavaScript.

## <a name="css"></a>CSS

Css (Kaskadowe arkusze stylów) służy do kontrolowania wyglądu i układu elementów HTML. Style CSS można stosować bezpośrednio do elementu HTML, zdefiniowanego oddzielnie na tej samej stronie lub zdefiniowanego w oddzielnym pliku i przywoływanego przez stronę. Style kaskadowo na podstawie sposobu, w jaki są używane do wybierania danego elementu HTML. Na przykład styl może mieć zastosowanie do całego dokumentu, ale zostanie zastąpiony przez styl, który zastosowano do określonego elementu. Podobnie styl specyficzny dla elementu zostanie zastąpiony przez styl, który został zastosowany do klasy CSS, który został zastosowany do elementu, który z kolei zostanie zastąpiony przez styl przeznaczony dla określonego wystąpienia tego elementu (za pomocą jego identyfikatora). Rysunek 6-1

![Zasady specyficzności CSS](./media/image6-1.png)

**Rysunek 6-1.** Zasady specyficzności CSS, w kolejności.

Najlepiej jest zachować style we własnych oddzielnych plikach arkusza stylów i używać kaskadowego opartego na zaznaczeniu, aby zaimplementować spójne style wielokrotnego użytku w aplikacji. Należy unikać umieszczania reguł stylu w formacie HTML, a stosowanie stylów do określonych poszczególnych elementów (a nie do całych klas elementów lub elementów, które miały do nich zastosowanie określonej klasy CSS), powinno być wyjątkiem, a nie regułą.

### <a name="css-preprocessors"></a>Preprocesory CSS

Arkusze stylów CSS nie obsługują logiki warunkowej, zmiennych i innych funkcji języka programowania. Tak więc duże arkusze stylów często zawierają sporo powtórzeń, ponieważ ten sam kolor, czcionka lub inne ustawienie jest stosowane do wielu różnych odmian elementów HTML i klas CSS. Preprocesory CSS mogą pomóc arkuszom stylów przestrzegać [zasady DRY,](https://deviq.com/don-t-repeat-yourself/) dodając obsługę zmiennych i logiki.

Najpopularniejszymi preprocesorami CSS są Sass i LESS. Oba rozszerzają CSS i są z nim wstecznie kompatybilne, co oznacza, że zwykły plik CSS jest prawidłowym plikiem Sass lub LESS. Sass jest oparty na języku Ruby, a LESS jest oparty na języku JavaScript i oba są zazwyczaj uruchamiane w ramach lokalnego procesu tworzenia. Oba mają dostępne narzędzia wiersza polecenia, a także wbudowaną obsługę w programie Visual Studio do uruchamiania ich przy użyciu zadań Gulp lub Grunt.

## <a name="javascript"></a>JavaScript

JavaScript to dynamiczny, interpretowany język programowania, który został znormalizowany w specyfikacji języka ECMAScript. Jest to język programowania sieci web. Podobnie jak CSS, JavaScript można zdefiniować jako atrybuty w elementach HTML, jako bloki skryptu na stronie lub w oddzielnych plikach. Podobnie jak CSS, zaleca się zorganizowanie JavaScript w oddzielnych plikach, zachowując go oddzielnie jak najwięcej od kodu HTML znajdującego się na poszczególnych stronach internetowych lub widokach aplikacji.

Podczas pracy z javascriptem w aplikacji sieci web istnieje kilka zadań, które często należy wykonać:

- Wybranie elementu HTML oraz pobranie i/lub zaktualizowanie jego wartości.

- Wykonywanie zapytań dotyczących interfejsu API sieci Web w poszukiwaniu danych.

- Wysyłanie polecenia do interfejsu API sieci Web (i odpowiadanie na wywołanie oddzwonić z jego wynikiem).

- Wykonywanie sprawdzania poprawności.

Wszystkie te zadania można wykonywać tylko za pomocą języka JavaScript, ale istnieje wiele bibliotek, aby ułatwić wykonywanie tych zadań. Jedną z pierwszych i najbardziej udanych z tych bibliotek jest jQuery, który nadal jest popularnym wyborem do upraszczania tych zadań na stronach internetowych. W przypadku aplikacji jednostronicowych (SSO) jQuery nie udostępnia wielu żądanych funkcji oferowanych przez angular i react.

### <a name="legacy-web-apps-with-jquery"></a>Starsze aplikacje internetowe z jQuery

Mimo, że starożytne według standardów javascript framework, jQuery nadal jest powszechnie używany biblioteki do pracy z HTML / CSS i tworzenia aplikacji, które sprawiają, że ajax wywołania internetowych interfejsów API. Jednak jQuery działa na poziomie modelu obiektu dokumentu przeglądarki (DOM) i domyślnie oferuje tylko model imperatywny, a nie deklaratywny.

Załóżmy na przykład, że jeśli wartość pola tekstowego przekracza 10, element na stronie powinien być widoczny. W jQuery to zazwyczaj być realizowane przez zapis obsługi zdarzeń z kodem, który będzie sprawdzić wartość pola tekstowego i ustawić widoczność elementu docelowego na podstawie tej wartości. Jest to podejście imperatywne, oparte na kodzie. Inna struktura może zamiast tego użyć binding danych do powiązania widoczność elementu do wartości pole tekstowe deklaratywnie. Nie wymaga to pisania kodu, ale zamiast tego wymaga tylko dekorowanie elementów związanych z atrybutami wiązania danych. W miarę jak zachowania po stronie klienta stają się coraz bardziej złożone, metody wiązania danych często powodują prostsze rozwiązania o mniejszej złożoności kodu i warunkowej.

### <a name="jquery-vs-a-spa-framework"></a>jQuery vs spa framework

| **Czynnikiem** | **jQuery** | **Angular**|
|--------------------------|------------|-------------|
| Abstrakty DOM | **Tak** | **Tak** |
| Wsparcie AJAX | **Tak** | **Tak** |
| Powiązanie danych deklaratywnych | **Nie** | **Tak** |
| Routing w stylu MVC | **Nie** | **Tak** |
| Szablonów | **Nie** | **Tak** |
| Routing głęboko łączowy | **Nie** | **Tak** |

Większość funkcji jQuery brakuje iskrologicznie można dodać z dodatkiem innych bibliotek. Jednak struktura SPA, taka jak Angular, zapewnia te funkcje w bardziej zintegrowany sposób, ponieważ została zaprojektowana z myślą o nich wszystkich od samego początku. Ponadto jQuery jest biblioteką imperatywną, co oznacza, że musisz wywołać funkcje jQuery, aby zrobić coś z jQuery. Wiele pracy i funkcji, które zapewniają struktury SPA można wykonać deklaratywnie, wymagając żadnego rzeczywistego kodu do zapisania.

Powiązanie danych jest doskonałym tego przykładem. W jQuery zwykle trwa tylko jeden wiersz kodu, aby uzyskać wartość elementu DOM lub ustawić wartość elementu. Jednak należy napisać ten kod w dowolnym momencie trzeba zmienić wartość elementu, a czasami będzie to występować w wielu funkcjach na stronie. Innym typowym przykładem jest widoczność elementu. W jQuery może istnieć wiele różnych miejsc, w których można napisać kod, aby kontrolować, czy niektóre elementy były widoczne. W każdym z tych przypadków podczas korzystania z powiązania danych, żaden kod nie musi być napisane. Można po prostu powiązać wartość lub widoczność elementów, o których mowa do *viewmodel* na stronie, a zmiany do tego viewmodel automatycznie zostaną odzwierciedlone w elementach powiązanych.

### <a name="angular-spas"></a>Kątowe punkty SPA

Angular pozostaje jedną z najpopularniejszych na świecie platform JavaScript. Od kątowe 2, zespół przebudowany ramy od podstaw (za pomocą [TypeScript)](https://www.typescriptlang.org/)i przemianowane z oryginalnej nazwy AngularJS po prostu Angular. Teraz kilka lat, przeprojektowany Angular nadal jest solidną strukturą do tworzenia aplikacji jednostronicowych.

Aplikacje kątowe są zbudowane z komponentów. Składniki łączą szablony HTML ze specjalnymi obiektami i sterują częścią strony. Prosty komponent z dokumentów Angular jest pokazany tutaj:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Składniki są definiowane @Component przy użyciu funkcji dekoratora, która pobiera metadane dotyczące składnika. Właściwość selektora identyfikuje identyfikator elementu na stronie, na której będzie wyświetlany ten składnik. Właściwość szablonu jest prostym szablonem HTML, który zawiera symbol zastępczy odpowiadający właściwości name komponentu, zdefiniowanej w ostatnim wierszu.

Pracując ze składnikami i szablonami, zamiast elementów DOM, aplikacje Angular mogą działać na wyższym poziomie abstrakcji i z mniej ogólnym kodem niż aplikacje napisane przy użyciu tylko JavaScript (zwanego również "waniliowym JS") lub z jQuery. Angular nakłada również pewne zamówienie na sposób organizowania plików skryptów po stronie klienta. Zgodnie z konwencją aplikacje Angular używają wspólnej struktury folderów z plikami skryptów modułów i składników znajdującymi się w folderze aplikacji. Skrypty kątowe związane z tworzeniem, wdrażaniem i testowaniem aplikacji zazwyczaj znajdują się w folderze wyższego poziomu.

Aplikacje Angular można tworzyć przy użyciu identyfikatora CLI. Pierwsze kroki z rozwojem Angular lokalnie (zakładając, że masz już zainstalowany git i npm) `npm install` `npm start`polega na po prostu klonowaniu repo z GitHub i działa i . Poza tym Angular wysyła własne cli, który może tworzyć projekty, dodawać pliki i pomagać w testowaniu, tworzeniu pakietów i zadaniach wdrażania. Ta przyjazność dla cli sprawia, że Angular jest szczególnie kompatybilny z ASP.NET Core, który oferuje również doskonałą obsługę cli.

Firma Microsoft opracowała aplikację [referencyjną, eShopOnContainers](https://aka.ms/MicroservicesArchitecture), która zawiera implementację Angular SPA. Ta aplikacja zawiera moduły kątowe do zarządzania koszykiem zakupów sklepu internetowego, ładowania i wyświetlania elementów z katalogu oraz obsługi tworzenia zamówień. Możesz wyświetlić i pobrać przykładową aplikację z [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>React

W przeciwieństwie do Angular, który oferuje pełną implementację wzorca Model-View-Controller, React dotyczy tylko widoków. Nie jest to struktura, tylko biblioteka, więc aby utworzyć SPA, musisz korzystać z dodatkowych bibliotek. Istnieje wiele bibliotek, które są przeznaczone do użycia z React do tworzenia bogatych aplikacji jednostronicowych.

Jedną z najważniejszych cech React jest wykorzystanie wirtualnego DOM. Wirtualny DOM zapewnia React z kilkoma zaletami, w tym wydajność (wirtualny DOM może zoptymalizować, które części rzeczywistego DOM muszą zostać zaktualizowane) i możliwość testowania (nie ma potrzeby posiadania przeglądarki do testowania React i jego interakcji z wirtualnym DOM).

React jest również nietypowy w tym, jak działa z HTML. Zamiast ścisłego oddzielenia kodu od znaczników (z odwołaniami do JavaScript pojawiających się w atrybutach HTML, React dodaje HTML bezpośrednio w kodzie JavaScript jako JSX. JSX to składnia formatu HTML, która może zostać skompilowana do czystego języka JavaScript. Przykład:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

Jeśli już wiesz, JavaScript, nauka React powinna być łatwa. Nie ma prawie tyle krzywej uczenia się lub specjalnej składni zaangażowanych jak w angular lub innych popularnych bibliotek.

Ponieważ React nie jest pełną strukturą, zazwyczaj chcesz, aby inne biblioteki obsługiwały takie rzeczy, jak routing, wywołania interfejsu API sieci Web i zarządzanie zależnościami. Miłe jest to, że możesz wybrać najlepszą bibliotekę dla każdego z nich, ale wadą jest to, że musisz podjąć wszystkie te decyzje i zweryfikować, czy wszystkie wybrane biblioteki dobrze ze sobą współpracują, gdy skończysz. Jeśli chcesz mieć dobry punkt wyjścia, możesz użyć zestawu startowego, takiego jak React Slingshot, który wstępnie pakuje zestaw kompatybilnych bibliotek wraz z React.

### <a name="vue"></a>Vue

Z przewodnika "Vue jest progresywną strukturą budowania interfejsów użytkownika. W przeciwieństwie do innych monolitycznych ram, Vue jest zaprojektowany od podstaw, aby być stopniowo adoptowalny. Podstawowa biblioteka koncentruje się tylko na warstwie widoku i jest łatwa do pobrania i zintegrowania z innymi bibliotekami lub istniejącymi projektami. Z drugiej strony, Vue jest w stanie w pełni zasilać zaawansowane aplikacje jednostronicowe w połączeniu z nowoczesnymi oprzyrządowaniem i bibliotekami pomocniczymi."

Pierwsze kroki z Vue po prostu wymaga włączenia skryptu w pliku HTML:

```html
<!-- development version, includes helpful console warnings -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

Po dodaniu struktury możesz deklaratywnie renderować dane do domprzy użyciu prostej składni tworzenia szablonów Vue:

```html
<div id="app">
  {{ message }}
</div>
```

a następnie dodanie następującego skryptu:

```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```

To wystarczy, aby renderować "Hello Vue!" na stronie. Należy jednak pamiętać, że Vue nie jest po prostu renderowania wiadomości do div raz. Obsługuje aktualizacje wiązania danych i dynamiczne `message` w taki sposób, `<div>` że jeśli wartość zmian, wartość w jest natychmiast aktualizowana w celu jej odzwierciedlenia.

Oczywiście, to tylko zarysowania powierzchni, co Vue jest w stanie. W ciągu ostatnich kilku lat zyskał dużą popularność i ma dużą społeczność. Istnieje ogromna [i rosnąca lista wspierających komponentów i bibliotek,](https://github.com/vuejs/awesome-vue#redux) które współpracują z Vue, aby ją rozszerzyć. Jeśli chcesz dodać zachowanie po stronie klienta do aplikacji internetowej lub rozważa skonstruowanie pełnego SPA, Vue jest warte zbadania.

### <a name="choosing-a-spa-framework"></a>Wybór struktury SPA

Rozważając, która struktura JavaScript będzie działać najlepiej, aby obsługiwać spa, należy pamiętać o następujących zagadnieniach:

- Czy twój zespół zna strukturę i jej zależności (w tym TypeScript w niektórych przypadkach)?

- Jak uparty jest ramy, i czy zgadzasz się z jego domyślny sposób robienia rzeczy?

- Czy (lub biblioteka towarzysząca) zawiera wszystkie funkcje wymagane przez aplikację?

- Czy jest dobrze udokumentowany?

- Jak aktywna jest jego społeczność? Czy powstają z nim nowe projekty?

- Jak aktywny jest jego podstawowy zespół? Czy problemy są rozwiązywane i regularnie wysyłane są nowe wersje?

Struktury JavaScript nadal ewoluują z zawrotną prędkością. Użyj zagadnień wymienionych powyżej, aby zmniejszyć ryzyko wyboru struktury, od której później będziesz żałować, że jesteś zależny. Jeśli jesteś szczególnie niechętny ryzyku, rozważ ramy, które oferują wsparcie komercyjne i / lub jest rozwijany przez duże przedsiębiorstwo.

> ### <a name="references--client-web-technologies"></a>Referencje – Client Web Technologies
>
> - **Kod HTML i CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass kontra MNIEJ**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **Stylizacja ASP.NET podstawowych aplikacji z LESS, Sass i Font Awesome**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **Rozwój po stronie klienta w ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **React**  
> <https://reactjs.org/>
> - **Vue**  
> <https://vuejs.org/>
> - **Angular vs React vs Vue: Które ramy wybrać w 2020 roku**
> <https://www.codeinwp.com/blog/angular-vs-vue-vs-react/>
> - **Najlepsze ramy JavaScript dla rozwoju front-end w 2020 r.**  
> <https://www.freecodecamp.org/news/complete-guide-for-front-end-developers-javascript-frameworks-2019/>

>[!div class="step-by-step"]
>[Poprzedni](common-web-application-architectures.md)
>[następny](develop-asp-net-core-mvc-apps.md)
