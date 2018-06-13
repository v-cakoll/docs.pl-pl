---
title: Typowe technologie sieci web po stronie klienta
description: Projektowania nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure | Typowe technologie sieci web po stronie klienta
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.openlocfilehash: 96bafce9c81a3a0486b7b8930367cf47ec5cbcb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592070"
---
# <a name="common-client-side-web-technologies"></a>Typowe technologie sieci Web po stronie klienta

> "Witryn sieci Web powinien wyglądać wewnątrz i out."  
> _-Pawła Cookson_

## <a name="summary"></a>Podsumowanie

Aplikacje platformy ASP.NET Core są aplikacji sieci web i są one zwykle oparte na technologii sieci web po stronie klienta, takich jak HTML, CSS i JavaScript. Oddzielając zawartości strony (HTML) od jej układu i stylów (CSS) i jego zachowanie (za pośrednictwem kodu JavaScript), aplikacje sieci web złożonych można wykorzystać zasady separacji problemy. Przyszłe zmiany struktury, projektu lub zachowania aplikacji będzie możliwe więcej łatwo podczas tych problemów nie jest sprzężony.

HTML i CSS są stosunkowo stabilny, JavaScript, za pomocą platformy aplikacji a deweloperom narzędzia do tworzenia aplikacji opartych na sieci web, ewoluuje breakneck szybkością. W tym rozdziale analizuje na kilka sposobów, JavaScript jest używana przez deweloperów sieci web w ramach tworzenia aplikacji, ponieważ zawiera ogólne omówienie kątową i platformy React bibliotek po stronie klienta.

## <a name="html"></a>HTML

HTML (HyperText Markup Language) to standardowy język używany do tworzenia strony sieci web i aplikacji sieci web. Jego elementy tworzą bloków konstrukcyjnych stron, reprezentujący sformatowanego tekstu, obrazów, dane wejściowe formularza i inne struktury. Gdy przeglądarką wysyła żądanie do adresu URL, czy pobierania strony lub aplikacji, po pierwsze jest zwracana jest dokumentu HTML. Ten dokument HTML może odwoływać się lub dołączania dodatkowych informacji o jego wygląd i układu w postaci CSS lub zachowanie w formie JavaScript.

## <a name="css"></a>CSS

CSS (kaskadowych arkuszy stylów) służy do kontrolowania wygląd i układ elementów HTML. Style CSS można stosowane bezpośrednio do elementu HTML, określane oddzielnie na tej samej stronie, lub zdefiniowane w osobnym pliku i odwołuje się strony. Style cascade oparte na korzystania z nich do wybrania danego elementu HTML. Na przykład stylu mogą być stosowane do całego dokumentu, ale może zostać zastąpiona przez styl stosowany do określonego elementu. Podobnie styl specyficzne dla elementu zostanie przesłonięte przez styl, który dotyczy klasy CSS, która została zastosowana do elementu, który z kolei może zostać zastąpiona przez styl przeznaczonych dla określonego wystąpienia tego elementu (za pomocą jego identyfikatora). Rysunek 6-1

**Rysunek 6-1.** Reguły CSS szczegółowością w kolejności.

![](./media/image6-1.png)

Najlepiej, aby zachować style w swoich plików oddzielne arkusza stylów, a także do użycia na podstawie wyboru kaskadowych do zaimplementowania style spójne i do ponownego użycia w aplikacji. Należy unikać wprowadzania do reguły stylu w pliku HTML i stosowanie stylów do określonych poszczególne elementy (a nie całej klasy elementów lub elementów, które miały określonej klasy CSS stosowana do nich) powinna być wyjątek nie reguły.

### <a name="css-preprocessors"></a>CSS Preprocessors

Arkusze stylów CSS nie obsługują logikę warunkową, zmienne i inne funkcje języka programowania. W związku z tym duże arkusze stylów często obejmują aktualnymi, kolor czcionki i inne ustawienie jest stosowane do wielu różnych wariantów elementów HTML i klas CSS. CSS preprocessors mogą pomóc Twojej arkusze stylów, postępuj zgodnie z [suchej zasady](http://deviq.com/don-t-repeat-yourself/) przez dodanie obsługi logiki i zmienne.

Najbardziej popularnym preprocessors CSS są Sass i mniejsza. Oba rozszerzenia CSS i są zgodne z poprzednimi wersjami, co oznacza, że zwykły plik CSS jest prawidłowy Sass lub MNIEJSZY plik. Sass jest oparta na protokole Ruby jest oparty na języku JavaScript i obie są zazwyczaj uruchamiane jako część procesu wdrożenia lokalnego. Mają polecenie wiersza narzędzia dostępne, a także wbudowana obsługa w programie Visual Studio do uruchamiania ich za pomocą Gulp lub Grunt zadań.

## <a name="javascript"></a>JavaScript

JavaScript jest dynamiczny, interpretacji języka programowania, które w specyfikacji języka ECMAScript. Jest język programowania sieci Web. Podobnie jak CSS JavaScript można zdefiniować jako atrybuty w obrębie elementów HTML jako bloki skryptu na stronie lub w oddzielnym pliku. Podobnie jak CSS ogólnie zaleca się organizowania JavaScript w oddzielnych plików, wówczas zachowanie oddzielone możliwie z kodu HTML, znaleziono na stronach sieci web lub aplikacji widoków.

Podczas pracy z JavaScript w aplikacji sieci web, istnieje kilka zadań, które należy zwykle wykonać:

-   Wybranie elementu HTML i pobierania i/lub zaktualizowanie jego wartości

-   Interfejs API sieci Web dla danych zapytań

-   Reagowanie na wywołanie zwrotne na jej wynik (i wysyłania polecenia do interfejsu API sieci Web)

-   Wykonywanie sprawdzania poprawności

Mogą wykonywać wszystkie te zadania JavaScript samodzielnie, ale istnieje wiele bibliotek ułatwiają te zadania. Jednym z pierwsze i najbardziej popularnych bibliotek tych jest jQuery, który jest nadal popularnych wybór dla uproszczenia te zadania na stronach sieci web. Aplikacje jednostronicowe (źródła) jQuery nie zapewniają wiele żądanych funkcji, które oferują kątową i bibliotece React.

### <a name="legacy-web-apps-with-jquery"></a>Starsze aplikacje sieci Web z jQuery

Mimo że starożytnych według standardów framework JavaScript, jQuery jest nadal bardzo często używane biblioteki do pracy z HTML/CSS i tworzenia aplikacji, które wywołań AJAX do interfejsów API sieci web. Jednak jQuery działa na poziomie przeglądarki document object model (DOM) i domyślnie oferuje tylko nadrzędnych, a nie deklaratywne, model.

Na przykład załóżmy, że jeśli pole tekstowe wartość przekracza 10, elementu na stronie powinny być widoczne. W jQuery to będzie zwykle realizowane przez pisanie programu obsługi zdarzeń z kodem, który będzie Sprawdź wartość w polu tekstowym, a następnie ustawić widoczności elementu docelowego na podstawie tej wartości. To podejście imperatywnych, opartych na kodzie. Framework innej zamiast tego użyć wiązania z danymi deklaratywnie powiązać widoczności elementu na wartość pola tekstowego. Nie wymagają pisania żadnego kodu, ale zamiast tego tylko wymaga dekoracji elementy związane z atrybutami powiązania danych. Wzrostem bardziej złożonych zachowań po stronie klienta wiązania z danymi zbliża się często wynik w rozwiązaniach prostsze mniej kodu i złożonością warunkowego.

### <a name="jquery-vs-a-spa-framework"></a>vs jQuery SPA Framework

| **Współczynnik** | **jQuery** | **dyrektywy angular**|
|--------------------------|------------|-------------|
| Abstracts modelu DOM | **Tak** | **Tak** |
| Obsługa technologii AJAX | **Tak** | **Tak** |
| Powiązanie danych deklaratywne | **Brak** | **Tak** |
| Styl MVC routingu | **Brak** | **Tak** |
| Tworzenia szablonów | **Brak** | **Tak** |
| Głębokie łącze routingu | **Brak** | **Tak** |

Większość funkcji, które jQuery nie ma bardzo można dodać z uwzględnieniem innych bibliotek. Framework SPA, takich jak kątową zapewnia jednak te funkcje w sposób integracji, ponieważ jest on przeznaczony wszystkich z nich na uwadze od początku. Ponadto jQuery jest bardzo ważnych biblioteki, co oznacza konieczność wywoływać funkcje jQuery, aby można było wykonywać żadnych czynności z jQuery. Większość pracy i funkcje, które zapewniają struktur SPA można deklaratywnie, wymagających bez rzeczywistego kodu do zapisania.

Powiązanie danych jest doskonałym przykładem. W jQuery zwykle potrwa to tylko jeden wiersz kodu można uzyskać wartość elementu DOM lub ustawić wartości elementu. Niemniej jednak należy napisać ten kod w dowolnej chwili należy zmienić wartość elementu, a czasami będzie to miało miejsce wiele funkcji na stronie. Innym typowym przykładem jest widoczności elementu. W jQuery może być wielu różnych miejscach, w którym piszesz kodu do kontroli czy niektóre elementy były widoczne. W każdym z tych przypadków, gdy używanie powiązania danych żaden kod potrzebny do zapisania. Czy po prostu powiązać wartości lub widoczność elementów danego *viewmodel* na stronie i zmiany w tym viewmodel będzie automatycznie odzwierciedlane w elementów powiązania.

### <a name="angular-spas"></a>Dyrektywy angular źródła

AngularJS szybko stał się jedną z najbardziej popularnych struktur JavaScript na świecie. Z 2 kątowego zespołu odbudować się framework od podstaw (przy użyciu [TypeScript](https://www.typescriptlang.org/)) i rebranded z AngularJS, aby po prostu kąta. Obecnie w wersji 4 kątową jest nadal niezawodne framework do tworzenia jednej strony aplikacji.

Dyrektywy angular aplikacji są tworzone na podstawie składników. Składniki łączyć szablony HTML z obiektami specjalne i kontrolować części strony. Proste składnika z dokumentów firmy kątową jest następujący:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Składniki są definiowane przy użyciu @Component funkcji dekoratora, który ma w metadanych dotyczących składnika. Właściwość selektora identyfikuje identyfikator elementu na stronie, gdy ten składnik będzie wyświetlany. Właściwości szablonu jest proste szablonu HTML, który zawiera symbol zastępczy odpowiadające właściwości name elementu, zdefiniowane w ostatnim wierszu.

Praca z elementami i szablony, zamiast elementy modelu DOM kątowego aplikacji może działać na wyższym poziomie abstrakcji z mniej ogólny kodu niż w przypadku aplikacji napisanych przy użyciu tylko języka JavaScript (zwane również "waniliowe JS") lub z jQuery. Kątową nakłada także niektóre kolejności, w jaki sposób organizowania plików skryptu po stronie klienta. Według Konwencji kątowego aplikacji za pomocą wspólnej struktury folderów, module i składnik plików skryptów znajdujących się w folderze aplikacji. Skrypty kątowego związane z tworzenie, wdrażanie i testowanie aplikacji znajdują się zwykle w folderze wyższego poziomu.

Kątową powoduje dużą korzystanie z narzędzi wiersza polecenia (CLI). Wprowadzenie do korzystania z dyrektywy Angular programowanie lokalnie (przy założeniu, masz już git i npm zainstalowany) składa się z po prostu klonowanie repozytorium GitHub i działa \`instalacji narzędzia npm\` i \`npm start\`. Poza tym kątową dostarczany własne narzędzia interfejsu wiersza polecenia, które można tworzyć projekty, Dodaj pliki i ułatwić testowanie, tworzenie pakietów i wdrożenia zadania. Ten interfejs wiersza polecenia narzędzia łatwość zastosowania sprawia, że kątową szczególnie zgodne z platformy ASP.NET Core, które również funkcje dużą Obsługa interfejsu wiersza polecenia.

Firma Microsoft opracowała aplikację odwołanie [eShopOnContainers](http://aka.ms/MicroservicesArchitecture), w tym implementację kątowego SPA. Ta aplikacja zawiera kątowego modułów do zarządzania Sklep internetowy zakupy koszyka, obciążenia i wyświetlania elementów z jego katalogu i obsługa tworzenia zamówienia. Można wyświetlić i pobrać przykładową aplikację z [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>Reakcji

W odróżnieniu od kątową, która zapewnia pełnej implementacji wzorca Model-View-Controller platformy React dotyczy jedynie widoków. Nie jest framework, po prostu biblioteki, tak aby utworzyć SPA musisz korzystać z dodatkowych bibliotek.

Jedną z najważniejszych funkcji w bibliotece React jest możliwość używania wirtualnej modelu DOM. DOM wirtualnych zapewnia platformy React wiele korzyści, w tym wydajności (DOM wirtualnych można zoptymalizować części rzeczywiste modelu DOM, które muszą zostać zaktualizowane) i testowania (nie trzeba mieć przeglądarkę do testowania platformy React i jego interakcje z jego DOM wirtualnego).

Platformy react jest również w sposób działania kodu HTML. Zamiast zareagować strict separacji między kodem i znaczników (z odwołaniami do języka JavaScript znajdujących się w atrybutach HTML prawdopodobnie), dodaje HTML bezpośrednio w ramach jego kod JavaScript jako JSX. JSX jest składnia notacji języka HTML, który umożliwia kompilację do czystych JavaScript. Na przykład:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

Jeśli znasz już język JavaScript, powinno być łatwe uczenia platformy React. Nie ma prawie więcej naukę lub specjalnej składni zaangażowanych jako kątową lub innych popularnych bibliotek.

Ponieważ platformy React nie jest pełną strukturę, zazwyczaj należy innych bibliotek do obsługi elementów, jak routingu, sieci web interfejsu API i zarządzania zależności. Dodatkową korzyścią jest najlepszym biblioteki można wybrać dla każdego z nich, ale wadą jest konieczność wszystkie te decyzje i sprawdź, czy wszystkie wybrane bibliotek siebie gdy wszystko będzie gotowe. Jeśli chcesz dobry punkt wyjścia, można użyć startowy, takich jak reagować Slingshot, który jednostkowych zestawu zgodnych bibliotek wraz z platformy React.

### <a name="choosing-a-spa-framework"></a>Wybieranie SPA Framework

Przy uwzględnieniu architektury JavaScript, które będzie najlepiej do obsługi sieci SPA, należy pamiętać następujące kwestie:

-   Czy zespół zna platformę i jego zależności (takie jak TypeScript w niektórych przypadkach)?

-   Jak opinionated jest strukturą, i są zgodne z jego domyślny sposób działania?

-   On (lub biblioteka pomocnika) zawiera wszystkie funkcje, które wymaga aplikacji?

-   Jest to dobrze udokumentowane?

-   Jak aktywny jest jego społeczności? Nowe projekty tworzenia są tworzone z nim?

-   Jak aktywny jest jego zespół core? Problemy rozwiązane i nowej wersji jest są dostarczane regularnie?

Struktury JavaScript nadal podlegać ewolucji o prędkości breakneck. Użyj zagadnienia wymienionych powyżej w celu zmniejszenia ryzyka Wybieranie framework, który zostanie później Zrezygnuj jest zależne. Jeśli masz szczególnie ryzyka averse, należy wziąć pod uwagę platforma, która zapewnia obsługę handlowych i/lub jest opracowany przez dużych przedsiębiorstw.

> ### <a name="references--client-web-technologies"></a>Odwołania — technologii sieci Web klienta
> - **HTML i CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass vs. LESS**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **Ustawianie stylów aplikacji platformy ASP.NET Core jest mniejsza, Sass i świetny czcionki**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **Programowanie po stronie klienta w platformy ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **dyrektywy angular**  
> <https://angular.io/>
> - **Reakcji**  
> <https://facebook.github.io/react/>
> - **Zareagować Slingshot**  
> <https://github.com/coryhouse/react-slingshot>
> - **Zareagować vs kątowego porównania 2**  
> <https://www.codementor.io/codementorteam/react-vs-angular-2-comparison-beginners-guide-lvz5710ha>
> - **5 najlepsze platformach JavaScript 2017**  
> <https://hackernoon.com/5-best-javascript-frameworks-in-2017-7a63b3870282>

>[!div class="step-by-step"]
[Previous] (common-web-application-architectures.md) [Next] (develop-asp-net-core-mvc-apps.md)
