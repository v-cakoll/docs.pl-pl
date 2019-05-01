---
title: Typowe technologie internetowe po stronie klienta
description: Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure | Typowe technologie sieci web po stronie klienta
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 36bb18d21740f406d33306c212195fa5dbb25ee1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019463"
---
# <a name="common-client-side-web-technologies"></a>Typowe technologie internetowe po stronie klienta

> "Witryny sieci Web powinna wyglądać wewnątrz i out".  
> _— Paul Cookson_

Aplikacje platformy ASP.NET Core to aplikacje sieci web i zwykle korzystają z technologii sieci web po stronie klienta, takich jak HTML, CSS i JavaScript. Oddzielając zawartości strony (HTML) od jego układu i stylów (CSS) i jego zachowanie (przy użyciu języka JavaScript), zasada oddzielenie obaw można używać w aplikacjach złożonej sieci. Przyszłe zmiany struktury, projektu lub zachowania aplikacji będzie możliwe więcej łatwo podczas tych problemów nie jest sprzężony.

Mimo że HTML i CSS stosunkowo czasu trwania stanu stabilnego, JavaScript, za pomocą struktury aplikacji a deweloperom narzędzia do kompilowania aplikacji opartych na sieci web, ewoluuje breakneck szybkością. W tym rozdziale patrzy na kilka sposobów, JavaScript jest używana przez deweloperów sieci web jako część tworzenia aplikacji, ponieważ zawiera ogólne omówienie usługi Angular i języka React bibliotek po stronie klienta.

## <a name="html"></a>HTML

HTML (HyperText Markup Language) to standardowy język używany do tworzenia stron sieci web i aplikacji sieci web. Jego elementy tworzą bloki konstrukcyjne stron, reprezentujący sformatowany tekst, obrazy, dane wejściowe formularza i innych struktur. Podczas przeglądarce wysyła żądanie do adresu URL, czy pobierania strony sieci lub aplikacji, czyli po pierwsze zwrócony jest dokumentu HTML. Ten dokument HTML może odwoływać się lub zawierają dodatkowe informacje na temat jego wygląd i układu w formie CSS lub zachowanie w postaci kodu JavaScript.

## <a name="css"></a>CSS

CSS (kaskadowe arkusze stylów) jest używane do kontrolowania, to wygląd i układ elementy HTML. Style CSS można stosować bezpośrednio do elementu HTML, określane oddzielnie na tej samej stronie lub zdefiniowane w oddzielnym pliku i przywoływany przez stronę. Style cascade, w oparciu o ich używania do wybrania danego elementu HTML. Na przykład stylu mogą być stosowane do całego dokumentu, ale może być zastąpiona przez stylu, które są stosowane do określonego elementu. Podobnie styl specyficzne dla elementu może być zastąpiona przez styl, który dotyczy klasy CSS, która została zastosowana do elementu, który z kolei może być zastąpiona przez styl przeznaczonych dla określonego wystąpienia tego elementu (za pomocą jego identyfikatora). Rysunek 6-1

**Rysunek 6-1.** Reguły CSS specyficzności w kolejności.

![](./media/image6-1.png)

Najlepiej przechowywać style w swoich plików oddzielny arkusz stylów i przy użyciu na podstawie wyboru cascading style spójnego i wielokrotnego użytku w aplikacji. Należy unikać wprowadzania do reguł stylu w pliku HTML, a stosowanie stylów do określonych poszczególne elementy (a nie całej klasy elementów lub elementów, których konkretnej klasy CSS stosowany do nich) powinna być wyjątek nie reguły.

### <a name="css-preprocessors"></a>Preprocesorami standardów CSS

Arkusze stylów CSS nie obsługują logikę warunkową, zmienne i innych funkcji języków programowania. W związku z tym duże arkusze stylów często zawierają dużo powtórzeń, jak ten sam kolor, czcionki lub inne ustawienie jest stosowane do wielu różnych wariantów elementów kodu HTML i CSS klas. Preprocesorami standardów CSS może pomóc Twojej arkusze stylów, postępuj zgodnie z [susz zasady](https://deviq.com/don-t-repeat-yourself/) przez dodanie obsługi zmiennych i logiki.

Najbardziej popularne preprocesorami standardów CSS są Sass i KRÓTSZY. Oba rozszerzenia CSS i są zgodne z poprzednimi wersjami, co oznacza, że zwykły plik CSS prawidłowe Sass lub pliku języka LESS. Sass jest oparty na Ruby mniejsza jest w języku JavaScript i zarówno zazwyczaj uruchamiane w ramach procesu tworzenia aplikacji lokalnej. Istnieją polecenia wiersza narzędzia dostępne, a także wbudowaną obsługę w programie Visual Studio do uruchamiania ich przy użyciu zadań Gulp ani Grunt.

## <a name="javascript"></a>JavaScript

JavaScript jest dynamiczny, interpretowanych języka programowania, którego normalizowane w specyfikacji języka ECMAScript. To język programowania sieci web. Podobnie jak CSS JavaScript można zdefiniować jako atrybutów w obrębie elementów HTML jako bloki skryptu na stronie lub w oddzielnych plikach. Podobnie jak CSS ogólnie zaleca się organizowania kodu JavaScript w osobnych plikach, utrzymywanie jej rozdzielonych możliwie z kodu HTML na stronach sieci web albo widoki aplikacji.

Podczas pracy z użyciem języka JavaScript w aplikacji sieci web, istnieje kilka zadań, które będzie najczęściej należy wykonać:

- Wybieranie elementu HTML i pobierania i/lub aktualizowanie jego wartości.

- Wykonywanie zapytania do internetowego interfejsu API danych.

- Wysyłanie polecenia do internetowego interfejsu API (i reagowanie na nie z jego wynikiem wywołania zwrotnego).

- Wykonywanie sprawdzania poprawności.

Mogą wykonywać wszystkie te zadania za pomocą języka JavaScript samodzielnie, ale istnieje wiele bibliotek, aby ułatwić te zadania. Pierwsze i najbardziej popularnych tych bibliotek on jQuery, która nadal jest to popularne wybór dla uproszczenia te zadania na stronach sieci web. Aplikacje jednostronicowe (źródła), aby uzyskać jQuery nie zapewnia wiele żądanych funkcji, które oferują usługi Angular i języka React.

### <a name="legacy-web-apps-with-jquery"></a>Aplikacje internetowe w starszej wersji za pomocą technologii jQuery

Chociaż starożytnych przez standardy framework JavaScript, jQuery jest nadal Biblioteka bardzo często używane do pracy z HTML/CSS oraz tworzenia aplikacji, które wykonywanie wywołań AJAX do interfejsów API sieci web. Jednak jQuery działa na poziomie przeglądarka document object model (DOM) i domyślnie oferuje tylko imperatywnego, zamiast deklaratywnym, model.

Załóżmy na przykład, jeśli wartość w polu tekstowym przekracza 10, element na stronie powinny być widoczne. W jQuery to będzie zwykle można zaimplementować, pisząc program obsługi zdarzeń z kodem, które może sprawdzić wartość w polu tekstowym, a następnie Ustaw widoczność elementu docelowego, na podstawie tej wartości. Jest to podejścia imperatywnego, oparte na kodzie. Framework innego zamiast tego użyć wiązania danych widoczności elementu można powiązać wartości pola tekstowego deklaratywnie. Nie wymaga pisania żadnego kodu, ale zamiast tego wymaga jedynie urządzanie elementy związane z atrybutów powiązania danych. Ponieważ coraz bardziej złożonych zachowań po stronie klienta powiązanie danych zbliża się często wynik w rozwiązaniach prostsze mniej kodu i złożonością warunkowe.

### <a name="jquery-vs-a-spa-framework"></a>vs jQuery SPA Framework

| **współczynnik** | **jQuery** | **Angular**|
|--------------------------|------------|-------------|
| Przenosi modelu DOM | **Tak** | **Tak** |
| Obsługa technologii AJAX | **Tak** | **Tak** |
| Powiązanie dane deklaratywne | **Brak** | **Tak** |
| MVC styl routingu | **Brak** | **Tak** |
| Tworzenie szablonów | **Brak** | **Tak** |
| Głębokie łącze routingu | **Brak** | **Tak** |

Większość funkcji, które jQuery brakuje wewnętrznie można dodawać dodając inne biblioteki. SPA framework, takich jak Angular zapewnia jednak te funkcje w sposób bardziej zintegrowaną, ponieważ jest on zaprojektowany przy użyciu wszystkich z nich pamiętać od samego początku. Ponadto jQuery jest bardzo imperatywne biblioteki, co oznacza, trzeba wywoływać funkcje jQuery, aby można było korzystać z technologii jQuery. Większość pracy i funkcji, które oferują struktur SPA może odbywać się w sposób deklaratywny, wymaganie nie rzeczywisty kod do zapisania.

Wiązanie danych jest doskonałym przykładem. W jQuery zwykle trwa tylko jeden wiersz kodu, można pobrać wartości elementu modelu DOM lub ustaw wartość elementu. Jednak trzeba napisać ten kod w dowolnym momencie należy zmienić wartość elementu, a czasami będzie to miało miejsce w wiele funkcji, na stronie. Innym typowym przykładem jest widoczności elementu. W jQuery może być wielu różnych miejsc, gdzie należy napisać kod do kontroli czy niektóre elementy były widoczne. W każdym z tych przypadków, gdy za pomocą powiązania danych żaden kod należałoby do zapisania. Czy po prostu powiązania wartości lub widoczność elementów danego *viewmodel* na stronie i zmiany do tego viewmodel będzie automatycznie odzwierciedlone w powiązanych elementów.

### <a name="angular-spas"></a>Platformy angular aplikacji jednostronicowych

Moduł AngularJS szybko stało się jedną z najbardziej popularnych struktur JavaScript na świecie. Przy użyciu usługi Angular 2, zespół odbudować się framework od podstaw (przy użyciu [TypeScript](https://www.typescriptlang.org/)) i przemianowane z AngularJS, można po prostu Angular. Obecnie w wersji 4, usługi Angular jest nadal niezawodna architektura służąca do tworzenia aplikacji.

Aplikacje angular są tworzone za pomocą składników. Składniki łączyć szablony HTML przy użyciu specjalnych obiektów i kontrolować części strony. Prostego składnika Angular dokumentach przedstawiono poniżej:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Składniki są definiowane przy użyciu @Component funkcji dekoratora, które pobiera metadane dotyczące składnika. Właściwość selektor identyfikuje identyfikator elementu na stronie, gdzie zostaną wyświetlone tego składnika. Właściwości szablonu to prosty szablon HTML, który zawiera symbol zastępczy, który odpowiada właściwości nazwy składnika, zdefiniowane w ostatnim wierszu.

Praca z elementami i szablonów, zamiast elementów DOM aplikacji Angular może działać na wyższym poziomie abstrakcji i mniejszej ilości kodu ogólny niż aplikacje napisane przy użyciu tylko JavaScript (zwane również "vanilla JS") lub z jQuery. Platformy Angular nakłada również niektóre kolejność, w jaki sposób organizowania plików skryptu po stronie klienta. Zgodnie z Konwencją aplikacji Angular za pomocą wspólnej struktury folderów, moduł, jak i składnika pliki skryptów znajdujących się w folderze aplikacji. Platformy angular skrypty zaniepokojona tworzenie, wdrażanie i testowanie aplikacji zwykle znajdują się w folderze wyższego poziomu.

Platformy Angular sprawia, że doskonałe korzystanie z narzędzi interfejsu wiersza polecenia (CLI). Wprowadzenie do usługi Angular programowanie lokalnie (przy założeniu, masz już git i narzędzia npm zainstalowane) składa się z po prostu klonowanie repozytorium z serwisu GitHub i uruchamianie `npm install` i `npm start`. Poza tym Angular jest dostarczany własne narzędzie interfejsu wiersza polecenia, można tworzyć projekty, dodanie plików, która uzyskanymi zadań testowania, tworzenie pakietów i wdrażanie. Ten interfejs wiersza polecenia narzędzia łatwość zastosowania sprawia, że Angular jest szczególnie zgodnych z platformą ASP.NET Core, która obejmuje także doskonałą obsługę interfejsu wiersza polecenia.

Firma Microsoft opracowała aplikację odwołanie [ramach aplikacji eShopOnContainers](https://aka.ms/MicroservicesArchitecture), który zawiera implementację Angular SPA. Ta aplikacja zawiera Angular modułów, aby zarządzać sklepu internetowego zakupy koszyka, ładowanie i wyświetlanie elementów ze swojego katalogu i obsługa tworzenia zamówienia. Możesz wyświetlić i pobrać przykładową aplikację z [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>React

Inaczej niż w przypadku szablonów Angular, która zapewnia pełnej implementacji wzorca Model-View-Controller, React dotyczy jedynie widoków. Nie jest framework, po prostu bibliotekę, aby tworzyć SPA należy korzystać z dodatkowych bibliotek.

Jedną z najważniejszych funkcji React firmy jest możliwość używania wirtualnej modelu DOM. DOM wirtualnego zapewnia kilka korzyści, takich jak wydajność, (DOM wirtualnych można zoptymalizować części rzeczywiste modelu DOM, które muszą zostać zaktualizowane) i testowania (nie trzeba mieć przeglądarki, aby przetestować platformy React i jego interakcje z jego wirtualnego modelu DOM) React.

React jest również w jak współdziałają z kodu HTML. Zamiast strict separacji między kodem i znaczników (z odwołaniami do języka JavaScript znajdujących się w atrybutach HTML, być może), React dodaje HTML bezpośrednio w ramach jego kod JavaScript jako JSX. JSX to składnia przypominająca HTML, który może kompilować czystego kodu JavaScript. Na przykład:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

Jeśli znasz już język JavaScript, nauka platformy React powinno być łatwe. Nie ma prawie tak dużej ilości nauki lub specjalnej składni zaangażowani jako przy użyciu usług Angular i innych popularnych bibliotek.

Ponieważ React nie jest pełną strukturę, zazwyczaj należy innych bibliotek do obsługi elementów, takich jak routing, sieci web interfejsu API i zarządzanie zależnościami. Korzyścią jest, możesz wybrać najlepsze biblioteki dla każdego z nich, ale wadą jest konieczność wszystkie te decyzje i sprawdź, czy z wybranym bibliotek współdziałają również gdy wszystko będzie gotowe. Jeśli chcesz dobry punkt wyjścia, można użyć startowy, takich jak Slingshot reagować, który jednostkowych zestawu zgodnych bibliotek wraz z platformy React.

### <a name="choosing-a-spa-framework"></a>Wybieranie SPA Framework

Podczas biorąc pod uwagę platformy JavaScript, która będzie działać najlepiej do obsługi usługi SPA, należy uwzględnić następujące kwestie:

- Czy zespół jest zapoznać się z programu framework oraz jego zależności (takie jak TypeScript w niektórych przypadkach)

- Jak ceniona jest strukturą, i są zgodne z jego domyślnej w sposób?

- On (lub biblioteki pomocnika) zawiera wszystkie funkcje, których wymaga aplikacja?

- Jest to dobrze udokumentowane?

- Jak aktywny jest jego społeczności? Czy nowe projekty tworzenia są tworzone za pomocą jej?

- Jak aktywny jest jego podstawowego zespołu? Problemy są rozwiązane i nowe wersje są dostarczane regularnie?

Będą dalej rozwijać się z szybkością breakneck platformy JavaScript. Użyj zagadnień wymienionych powyżej w celu zmniejszenia ryzyka framework, który będzie później Zrezygnuj jest zależne od wyboru. Jeśli masz szczególnie nielubiącym ryzyka, należy wziąć pod uwagę strukturę, która oferuje obsługę komercyjnych i/lub jest opracowywany dużych przedsiębiorstw.

> ### <a name="references--client-web-technologies"></a>Odwołania — technologii sieci Web klienta
> - **HTML i CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass programu vs. LESS**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **Ustawianie stylów aplikacji platformy ASP.NET Core za pomocą LESS, Sass i Font Awesome**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **Programowanie po stronie klienta w programie ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **React**  
> <https://facebook.github.io/react/>
> - **React Slingshot**  
> <https://github.com/coryhouse/react-slingshot>
> - **Vs react porównanie usługi Angular 2**  
> <https://www.codementor.io/codementorteam/react-vs-angular-2-comparison-beginners-guide-lvz5710ha>
> - **5 najlepszych platformy JavaScript 2017 r.**  
> <https://hackernoon.com/5-best-javascript-frameworks-in-2017-7a63b3870282>

>[!div class="step-by-step"]
>[Poprzednie](common-web-application-architectures.md)
>[dalej](develop-asp-net-core-mvc-apps.md)