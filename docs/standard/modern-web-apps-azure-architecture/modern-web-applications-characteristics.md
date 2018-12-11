---
title: Charakterystyka nowoczesnych aplikacji sieci web
description: Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure | Charakterystyka nowoczesnych aplikacji sieci web
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: 6c416432f10bb93ff5012d716b2d92f13efdcd9b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147339"
---
# <a name="characteristics-of-modern-web-applications"></a>Charakterystyka nowoczesnych aplikacji sieci Web

> "… w projekcie odpowiednie funkcje pochodzą niedrogo. To podejście jest uciążliwy, ale nadal zakończyło się sukcesem".  
> _\- Dennis Ritchie_

Nowoczesnych aplikacji sieci web mają wyższe oczekiwania użytkowników i większe zapotrzebowanie niż kiedykolwiek wcześniej. Współczesnych aplikacji sieci web powinny być dostępne 24/7 w dowolnym miejscu na świecie i można używać z niemal każdego urządzenia lub rozmiar ekranu. Aplikacje sieci Web musi być bezpieczny, elastyczny i skalowalne rozwiązanie spełniające skoków zapotrzebowania. Coraz większym stopniu złożonych scenariuszy powinno zostać obsłużone przez bogatej funkcjonalności użytkowej oparta na kliencie przy użyciu języka JavaScript i efektywnie komunikacji za pośrednictwem interfejsów API sieci web.

Platforma ASP.NET Core jest dostosowana do nowoczesnych aplikacji sieci web i scenariusze hostingu oparte na chmurze. Jego modułowej umożliwia aplikacjom są zależne od tylko te funkcje, które są rzeczywiście używane, poprawy zabezpieczeń aplikacji i wydajności przy jednoczesnym zmniejszeniu wymaganych do obsługi wymagań dotyczących zasobów.

## <a name="reference-application-eshoponweb"></a>Odwołania aplikacji: eShopOnWeb

Niniejsze wskazówki obejmują aplikacji referencyjnej _eShopOnWeb_, którym przedstawiono, niektóre zasady i zalecenia. Aplikacja jest proste sklep online, który obsługuje przeglądanie katalogu koszule, mukeja kawy i inne elementy marketingu. Aplikacja referencyjna jest celowo prosty, aby ułatwić zrozumienie.

**Rysunek 2-1.** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>Odwołanie do aplikacji
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Hostowana w chmurze i skalowalna

Platforma ASP.NET Core jest zoptymalizowany pod kątem cloud (chmura publiczna, Chmura prywatna, każdej chmury), ponieważ jest on małej ilości pamięci i wysoką przepływność. Mniejszych rozmiarów aplikacji platformy ASP.NET Core oznacza, że możesz hostować jeden z nich na tym samym sprzęcie, i płacisz za mniej zasobów, gdy za pomocą płatności — jako hostingu usług w chmurze. Większą przepływność oznacza, że może służyć większej liczby klientów z aplikacji podane w tym samym sprzęcie, co dodatkowo ogranicza konieczność inwestować w serwery i infrastruktury hostingu.

## <a name="cross-platform"></a>Wiele platform

Platforma ASP.NET Core jest dla wielu platform i systemem Linux i MacOS, a także Windows. Spowoduje to otwarcie wiele nowych opcji dla środowisk deweloperskich i wdrożenia aplikacji skompilowanej za pomocą platformy ASP.NET Core. Kontenery platformy docker, które zwykle z systemem Linux już dziś, może obsługiwać aplikacje platformy ASP.NET Core, umożliwiając im móc korzystać z zalet [kontenery i mikrousługi](../microservices-architecture/index.md).

## <a name="modular-and-loosely-coupled"></a>Moduły i luźno powiązane

Pakiety NuGet są najwyższej jakości obywateli w programie .NET Core oraz aplikacji platformy ASP.NET Core składają się z wielu bibliotek za pośrednictwem pakietu NuGet. Ten poziom szczegółowości funkcjonalność zapewnia tylko zależą od aplikacji i wdrożenia funkcji, które rzeczywiście wymagają one, zmniejszyć ich wpływu i zabezpieczeń luk w zabezpieczeniach obszar powierzchni.

Platforma ASP.NET Core także w pełni obsługuje wstrzykiwanie zależności, zarówno wewnętrznie, jak i na poziomie aplikacji. Interfejsy mogą mieć wiele implementacji, które mogą być wymieniane zgodnie z potrzebami. Wstrzykiwanie zależności umożliwia aplikacjom luźno kilka do tych interfejsów, dzięki czemu łatwiej można rozszerzyć, utrzymywanie i testowanie.

## <a name="easily-tested-with-automated-tests"></a>Łatwo przetestowane za pomocą testów automatycznych

Aplikacje platformy ASP.NET Core obsługują testy jednostkowe i ich luźne powiązania i obsługi iniekcji zależności ułatwia wymiany infrastruktury problemy z implementacjami fałszywych do celów testowych. Platforma ASP.NET Core jest również dostarczany elementu TestServer, który może służyć do hostowania aplikacji w pamięci. Testy funkcjonalne następnie mogą wysyłać żądania do tego serwera w pamięci, wykonywania stosu pełnej aplikacji (w tym oprogramowania pośredniczącego, routing, wiązaniem modelu, filtrami itp.) i odbierania odpowiedzi, wszystko w ułamku czasu jaki zajęłoby do hostowania tej aplikacji na serwerze rzeczywistych i wysyłanie żądań za pośrednictwem warstwy sieci. Te testy są szczególnie ułatwia pisanie i cenne dla interfejsów API, które są coraz ważniejsze w nowoczesnych aplikacji sieci web.

## <a name="traditional-and-spa-behaviors-supported"></a>Zachowania tradycyjnego i SPA obsługiwane

Aplikacje sieci web tradycyjnych mają brać nieco zachowania po stronie klienta, ale zamiast tego ma opiera się na serwerze dla nawigacji, zapytań i aktualizacji, które aplikacja może być konieczne. Każdej nowej operacji wprowadzone przez użytkownika będzie tłumaczona na nowe żądanie sieci web z wynikiem jest załadowanie pełnej strony w przeglądarce użytkownika końcowego. Klasyczny Model-View-Controller (MVC) struktur zazwyczaj postępuj zgodnie z takim podejściu z każdego nowego żądania odpowiadający działania innego kontrolera, który z kolei może pracować z modelem i zwrócenia widoku. Niektóre poszczególne operacje na danej stronie mogą być dołączane funkcji AJAX (asynchronicznego języka JavaScript i XML), ale ogólna Architektura aplikacji używane w wielu różnych widoków MVC i punkty końcowe adresu URL.

Aplikacje jednostronicowe (źródła), natomiast obejmują bardzo mało ładowania dynamicznie generowanym strony po stronie serwera (jeśli istnieje). Wiele aplikacji jednostronicowych są inicjowane w ciągu statyczny plik HTML, który ładuje wymagane biblioteki JavaScript do uruchomienia aplikacji. Te aplikacje mocno użycia interfejsów API sieci Web odpowiadające ich potrzebom dane i może zapewnić, że znacznie bogatsze podejrzewać.

Wiele aplikacji sieci web obejmują kombinacją tradycyjnej sieci web aplikacji zachowanie (zwykle zawartość) i aplikacji jednostronicowych (na potrzeby interakcyjności). Platforma ASP.NET Core obsługuje zarówno MVC (widoki i/lub stron Razor) i interfejsów API w tej samej aplikacji przy użyciu tego samego zestawu narzędzi i bazowych bibliotek platformy sieci web.

## <a name="simple-development-and-deployment"></a>Proste tworzenie i wdrażanie

Aplikacje platformy ASP.NET Core mogą być napisane przy użyciu zwykłego tekstu, edytory i interfejsy wiersza polecenia lub środowisk deweloperskich w pełni funkcjonalne, np. program Visual Studio. Aplikacje monolityczne są zazwyczaj wdrożone w jednym punkcie końcowym. Wdrożeń można łatwo być wykonywane automatycznie w ramach ciągłej integracji (CI) i ciągłe dostarczanie (CD) potoku. Oprócz tradycyjnych narzędzi ciągłej integracji/ciągłego wdrażania usługi Windows Azure została zintegrowana obsługa repozytoriów git i można automatycznie wdrażać aktualizacje, ponieważ są one git określonej gałęzi lub tagu.

## <a name="traditional-aspnet-and-web-forms"></a>Tradycyjne ASP.NET i formularzy sieci Web

Oprócz platformy ASP.NET Core tradycyjnych ASP.NET 4.x w dalszym ciągu być niezawodna platforma do budowania aplikacji sieci web. Program ASP.NET obsługuje modele programowania MVC i interfejs API sieci Web, a także formularzy sieci Web, która dobrze nadaje się do tworzenia rozbudowanych aplikacji opartej na stronach i funkcji z ekosystemem sformatowanego składników innych firm. Windows Azure została od doskonałą obsługę aplikacji programu ASP.NET 4.x i wielu programistów i dopiero zaczynasz z tą platformą.

> ### <a name="references--modern-web-applications"></a>Odwołania — nowoczesnych aplikacji sieci Web
>
> - **Wprowadzenie do platformy ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **Sześć klucz korzyści z platformy ASP.NET Core co różne i lepsze**  
>   <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **Testowanie w programie ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](choose-between-traditional-web-and-single-page-apps.md)