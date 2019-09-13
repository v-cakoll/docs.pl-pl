---
title: Typowe technologie internetowe po stronie klienta
description: Tworzenie architektury nowoczesnych aplikacji sieci Web przy użyciu ASP.NET Core i platformy Azure | Typowe technologie sieci Web po stronie klienta
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 4dd747293fba4c18c2d10738d36f4d98cfd3f5b9
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926501"
---
# <a name="common-client-side-web-technologies"></a>Typowe technologie internetowe po stronie klienta

> "Witryny sieci Web powinny wyglądać od wewnątrz do zewnątrz".  
> _-Paul Cookson_

Aplikacje ASP.NET Core są aplikacjami sieci Web, a zazwyczaj polegają na technologiach sieci Web po stronie klienta, takich jak HTML, CSS i JavaScript. Dzieląc zawartość strony (kod HTML) z układu i stylów (CSS) oraz jej zachowaniem (za pośrednictwem języka JavaScript), złożone aplikacje sieci Web mogą korzystać z oddzielenia zasad. Przyszłe zmiany struktury, projektu lub zachowania aplikacji mogą być łatwiejsze, gdy nie są intertwined te problemy.

Chociaż język HTML i CSS są stosunkowo stabilne, JavaScript, za pomocą struktur aplikacji i narzędzi, deweloperzy współpracują z programem w celu kompilowania aplikacji opartych na sieci Web, rozwijając się z szybkością breakneck. W tym rozdziale przedstawiono kilka sposobów używania języka JavaScript przez deweloperów sieci Web w ramach opracowywania aplikacji, co stanowi ogólne omówienie wizualizacji i przereagowania na biblioteki po stronie klienta.

## <a name="html"></a>HTML

HTML (HyperText Markup Language) to standardowy język znaczników używany do tworzenia stron sieci Web i aplikacji sieci Web. Jego elementy tworzą bloki konstrukcyjne stron, reprezentujące sformatowany tekst, obrazy, wejścia formularzy i inne struktury. Gdy przeglądarka wysyła żądanie do adresu URL, niezależnie od tego, czy pobierana jest strona, czy aplikacja, pierwszy zwrócony element jest dokumentem HTML. Ten dokument HTML może odwoływać się do lub zawierać dodatkowe informacje na temat wyglądu i układu w formie CSS lub zachowania w formie języka JavaScript.

## <a name="css"></a>CSS

CSS (kaskadowe arkusze stylów) służy do kontrolowania wyglądu i układu elementów HTML. Style CSS mogą być stosowane bezpośrednio do elementu HTML, zdefiniowane oddzielnie na tej samej stronie lub zdefiniowane w osobnym pliku i przywoływane przez stronę. Style kaskadowo na podstawie sposobu ich używania do wybierania danego elementu HTML. Na przykład styl może dotyczyć całego dokumentu, ale zostałby zastąpiony przez styl, który ma zastosowanie do określonego elementu. Analogicznie, styl specyficzny dla elementu zostałby zastąpiony przez styl stosowany do klasy CSS, która została zastosowana do elementu, który z kolei zostałby zastąpiony przez styl przeznaczony dla określonego wystąpienia tego elementu (za pośrednictwem jego identyfikatora). Rysunek 6-1

![Reguły specyfikowania CSS](./media/image6-1.png)

**Rysunek 6-1.** Reguły specyficzne dla CSS, w kolejności.

Najlepiej zachować style w swoich oddzielnych plikach arkusza stylów, a następnie użyć kaskadowego umieszczania na podstawie zaznaczenia, aby zaimplementować style spójne i wielokrotnego użytku w aplikacji. Należy unikać umieszczania reguł stylu w kodzie HTML i stosowania stylów do określonych poszczególnych elementów (a nie całych klas elementów lub elementów, które mają określoną klasę CSS), powinien być wyjątek, a nie reguła.

### <a name="css-preprocessors"></a>Preprocesora CSS

Arkusze stylów CSS nie obsługują logiki warunkowej, zmiennych i innych funkcji języka programowania. W ten sposób duże arkusze stylów często zawierają wiele powtórzeń, tak samo jak kolor, czcionka lub inne ustawienie jest stosowane do wielu różnych odmian elementów HTML i klas CSS. Preprocesora CSS mogą ułatwić arkuszom stylów zastosowanie [suchej zasady](https://deviq.com/don-t-repeat-yourself/) przez dodanie obsługi zmiennych i logiki.

Najpopularniejsze preprocesora CSS to Sass i mniejsze. Zarówno w przypadku rozszerzeń CSS, jak i są zgodne z poprzednimi wersjami, co oznacza, że zwykły plik CSS jest prawidłowym plikiem Sass lub LESS. Sass jest oparty na języku Ruby i mniej jest oparty na kodzie JavaScript, a oba są zwykle uruchamiane jako część lokalnego procesu tworzenia. Dostępne są zarówno narzędzia wiersza polecenia, jak i wbudowana obsługa programu Visual Studio do uruchamiania ich przy użyciu zadań Gulp lub grunt.

## <a name="javascript"></a>JavaScript

JavaScript to dynamiczny, interpretowany język programowania, który został znormalizowany w specyfikacji języka ECMAScript. Jest to język programowania w sieci Web. Podobnie jak w przypadku CSS, skrypty JavaScript można definiować jako atrybuty wewnątrz elementów HTML, jako bloki skryptu na stronie lub w oddzielnych plikach. Podobnie jak w przypadku CSS, zazwyczaj zaleca się zorganizowanie kodu JavaScript w osobnych plikach, tak jak to możliwe, z poziomu kodu HTML znalezionego na poszczególnych stronach sieci Web lub w widokach aplikacji.

Podczas pracy z JavaScript w aplikacji sieci Web, istnieje kilka zadań, które zwykle trzeba wykonać:

- Zaznaczanie elementu HTML i pobieranie i/lub aktualizowanie jego wartości.

- Wykonywanie zapytań do internetowego interfejsu API w celu uzyskania danych.

- Wysyłanie polecenia do internetowego interfejsu API (i reagowanie na wywołanie zwrotne z jego wynikiem).

- Wykonywanie walidacji.

Wszystkie te zadania można wykonać wyłącznie JavaScript, ale wiele bibliotek istnieje, aby ułatwić wykonywanie tych zadań. Jedną z pierwszych i najbardziej pomyślnych bibliotek jest jQuery, która jest w dalszym ciągu popularną opcją uproszczenia tych zadań na stronach sieci Web. W przypadku aplikacji jednostronicowych (aplikacji jednostronicowych), jQuery nie oferuje wielu wymaganych funkcji, które są związane ze współdziałaniem i ofertą reagowania.

### <a name="legacy-web-apps-with-jquery"></a>Starsze aplikacje sieci Web za pomocą platformy jQuery

Chociaż Ancient przez standardy języka JavaScript, platforma jQuery nadal jest bardzo używaną biblioteką do pracy z HTML/CSS i kompilowania aplikacji, które tworzą wywołania AJAX do interfejsów API sieci Web. Jednak system jQuery działa na poziomie modelu DOM (Document Object Model), a domyślnie oferuje tylko bezwzględny, a nie deklaratywny model.

Załóżmy na przykład, że jeśli wartość pola tekstowego przekracza 10, element na stronie powinien być widoczny. W platformie jQuery zwykle jest to implementowane przez zapisanie obsługi zdarzeń z kodem, który sprawdzi wartość pola tekstowego i ustawi widoczność elementu docelowego na podstawie tej wartości. Jest to bezwzględne podejście oparte na kodzie. Inna platforma może zamiast tego użyć zapytania wiązania, aby powiązać widoczność elementu z wartością pola tekstowego. Nie wymaga to pisania żadnego kodu, ale tylko wymaga dekorowania nazwy elementów związanych z atrybutami powiązania danych. Gdy zachowania po stronie klienta zwiększają się bardziej złożone, podejścia do powiązań danych często powodują prostsze rozwiązania z mniejszą ilością kodu i złożoności warunkowej.

### <a name="jquery-vs-a-spa-framework"></a>jQuery a platforma SPA

| **1U** | **jQuery** | **Angular**|
|--------------------------|------------|-------------|
| Abstrakcyjny model DOM | **Tak** | **Tak** |
| Obsługa technologii AJAX | **Tak** | **Tak** |
| Deklaratywne powiązanie danych | **Znaleziono** | **Tak** |
| Routing w stylu MVC | **Znaleziono** | **Tak** |
| Tworzenia szablonów | **Znaleziono** | **Tak** |
| Routing linków | **Znaleziono** | **Tak** |

Większość funkcji jQuery nie może zostać dodana w sposób wewnętrzny z dodaniem innych bibliotek. Jednak mechanizm SPA, taki jak kątowy, udostępnia te funkcje w bardziej zintegrowany sposób, ponieważ został zaprojektowany ze wszystkimi z nich na myśli od samego początku. Ponadto jQuery jest bardzo bezwzględną biblioteką, co oznacza, że trzeba wywoływać funkcje jQuery w celu wykonywania jakichkolwiek czynności za pomocą jQuery. Większość pracy i funkcji, które zapewnia platforma SPA, może być wprowadzana w sposób deklaratywny, co nie wymaga faktycznego zapisania kodu.

Powiązanie danych to doskonałe przykładowe rozwiązanie. W platformie jQuery zwykle przyjmuje tylko jeden wiersz kodu, aby uzyskać wartość elementu DOM lub ustawić wartość elementu. Jednak należy napisać ten kod w dowolnym momencie, gdy trzeba zmienić wartość elementu, a czasami występuje w wielu funkcjach na stronie. Innym typowym przykładem jest widoczność elementu. W platformie jQuery może istnieć wiele różnych miejsc, w których można napisać kod, aby kontrolować, czy niektóre elementy były widoczne. W każdym z tych przypadków, gdy korzystasz z powiązania danych, nie trzeba pisać kodu. Po prostu powiążesz wartość lub widoczność elementów na *ViewModel* na stronie, a zmiany w tym ViewModel zostaną automatycznie odzwierciedlone w elementach powiązanych.

### <a name="angular-spas"></a>Aplikacji jednostronicowych kątowy

AngularJS szybko stało się jednym z najpopularniejszych platform języka JavaScript. W przypadku wystąpienia kątowego 2 zespół odbudował strukturę od podstaw (przy użyciu języka [TypeScript](https://www.typescriptlang.org/)) i od AngularJS do samego kątowego. Obecnie w wersji 4, kątowy nadal jest solidną strukturą do tworzenia aplikacji jednostronicowych.

Aplikacje kątowe są kompilowane ze składników. Składniki łączą szablony HTML z obiektami specjalnymi i kontrolują część strony. Poniżej przedstawiono prosty składnik z dokumentów o skośności:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Składniki są definiowane za pomocą @Component funkcji dekoratora, która pobiera metadane dotyczące składnika. Właściwość selektora identyfikuje identyfikator elementu na stronie, w którym zostanie wyświetlony ten składnik. Właściwość szablonu to prosty szablon HTML, który zawiera symbol zastępczy, który odpowiada właściwości nazwy składnika zdefiniowanej w ostatnim wierszu.

Pracując ze składnikami i szablonami, a nie elementami modelu DOM, aplikacje kątowe mogą działać na wyższym poziomie abstrakcji i z mniej ogólnym kodem niż aplikacje zapisywane przy użyciu tylko języka JavaScript (nazywanego również "Wanili JS") lub jQuery. Kątowy nakłada również pewne kolejność organizowania plików skryptów po stronie klienta. Zgodnie z Konwencją aplikacje kątowe używają wspólnej struktury folderów z plikami skryptów modułów i składników znajdującymi się w folderze aplikacji. Skrypty kątowe związane z kompilowaniem, wdrażaniem i testowaniem aplikacji zwykle znajdują się w folderze wyższego poziomu.

Kątowy sprawia również doskonałe użycie narzędzi interfejsu wiersza polecenia (CLI). Wprowadzenie do programowania kątowego lokalnie (przy założeniu, że masz już zainstalowaną usługę git i npm), składa się z `npm install` prostego `npm start`klonowania repozytorium z usługi GitHub i uruchamiania i. Poza tym, kątowy dostarcza własne narzędzie interfejsu wiersza polecenia, które może tworzyć projekty, dodawać pliki i pomagać w testowaniu, tworzeniu i wdrażaniu zadań. Ta wygodę dla narzędzi interfejsu wiersza polecenia sprawia, że jest to kątowe szczególnie zgodne z ASP.NET Core, które również oferuje doskonałą obsługę interfejsu wiersza polecenia.

Firma Microsoft opracowała aplikację referencyjną [eShopOnContainers](https://aka.ms/MicroservicesArchitecture), która obejmuje implementację spa. Ta aplikacja obejmuje moduły kątowe służące do zarządzania koszykiem zakupów online, ładowania i wyświetlania elementów z wykazu oraz do obsługi tworzenia zamówień. Przykładową aplikację można wyświetlić i pobrać z witryny [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>React

W przeciwieństwie do elementu kątowego, który oferuje pełną implementację wzorca typu Model-View-Controller, reagowanie dotyczy tylko widoków. Nie jest to struktura, tylko biblioteka, więc aby utworzyć SPA, należy użyć dodatkowych bibliotek.

Jedną z najważniejszych funkcji reakcji jest użycie wirtualnego modelu DOM. Wirtualny DOM zapewnia kilka korzyści, w tym wydajność (wirtualny DOM, można zoptymalizować, które części rzeczywistego modelu DOM wymagają aktualizacji) i możliwość testowania (nie trzeba mieć przeglądarki do testowania reakcji i interakcji z jej wirtualnym modelem DOM).

Reagowanie jest również nietypowe w sposobie działania z kodem HTML. Zamiast mieć ścisłe rozdzielenie kodu i znaczników (z odwołaniami do języka JavaScript, które prawdopodobnie są wyświetlane w atrybutach HTML), reaguje dodaje kod HTML bezpośrednio w jego kodzie JavaScript jako JSX. JSX jest składnią podobną do języka HTML, która może kompilować do czystego kodu JavaScript. Na przykład:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

Jeśli znasz już język JavaScript, reagowanie na uczenie powinno być proste. Nie ma niemal dużej krzywej szkoleniowej lub specjalnej składni, która jest powiązana ze kątową lub innymi popularnymi bibliotekami.

Ponieważ reagowanie nie jest pełną strukturą, zazwyczaj chcesz, aby inne biblioteki obsługiwały takie elementy, jak routing, wywołania interfejsu API sieci Web i zarządzanie zależnościami. W tym celu można wybrać najlepszą bibliotekę dla każdej z nich, ale wadą jest to, że należy podjąć wszystkie te decyzje i sprawdzić, czy wszystkie wybrane biblioteki działają prawidłowo, gdy wszystko będzie gotowe. Jeśli chcesz uzyskać dobry punkt początkowy, możesz użyć zestawu startowego, takiego jak Slingshot reaguje, który składa się z zestawu zgodnych bibliotek wraz z reagowaniem.

### <a name="choosing-a-spa-framework"></a>Wybieranie struktury SPA

Biorąc pod uwagę, która struktura języka JavaScript będzie najlepiej działała, należy pamiętać o następujących kwestiach:

- Czy Twój zespół zna strukturę i jej zależności (w tym w niektórych przypadkach TypeScript)?

- Jak ceniona jest struktura i czy zgadzasz się z jej domyślnym sposobem wykonywania zadań?

- Czy to (czy biblioteka towarzysząca) zawiera wszystkie funkcje wymagane przez aplikację?

- Czy jest to dobrze udokumentowane?

- Jak działa Twoja społeczność? Czy skompilowano nowe projekty?

- Jak aktywny jest Twój rdzeń zespołu? Czy problemy są rozwiązywane i są regularnie wysyłane nowe wersje?

Struktury JavaScript w dalszym ciągu rozwijają się z szybkością breakneck. Skorzystaj z wymienionych powyżej zagadnień, aby pomóc w ograniczeniu ryzyka wyboru struktury, z której będziesz później korzystać z programu. Jeśli jesteś szczególnie narażony na averse, weź pod uwagę platformę, która oferuje komercyjną pomoc techniczną i/lub opracowaną przez duże przedsiębiorstwo.

> ### <a name="references--client-web-technologies"></a>Odwołania — technologie sieci Web klienta
>
> - **HTML i CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass a LESS**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **Ustawianie stylów ASP.NET Core aplikacji z czcionką LESS, Sass i Font awesome**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **Programowanie po stronie klienta w ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **React**  
> <https://facebook.github.io/react/>
> - **Slingshot Reaguj**  
> <https://github.com/coryhouse/react-slingshot>
> - **Odreaguj a porównanie kątowe 2**  
> <https://www.codementor.io/codementorteam/react-vs-angular-2-comparison-beginners-guide-lvz5710ha>
> - **5 najlepszych platform JavaScript 2017**  
> <https://hackernoon.com/5-best-javascript-frameworks-in-2017-7a63b3870282>

>[!div class="step-by-step"]
>[Poprzedni](common-web-application-architectures.md)Następny
>[](develop-asp-net-core-mvc-apps.md)
