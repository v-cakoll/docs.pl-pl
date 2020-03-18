---
title: Charakterystyka nowoczesnych aplikacji internetowych
description: Architekt nowoczesne aplikacje internetowe z ASP.NET Core i Azure | Charakterystyka nowoczesnych aplikacji internetowych
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: d70fa54adeb505fd37807399402281dfda67cf52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451567"
---
# <a name="characteristics-of-modern-web-applications"></a>Charakterystyka nowoczesnych aplikacji internetowych

> "… z odpowiednim projektem, funkcje są tanio. Takie podejście jest żmudne, ale nadal odnosi sukcesy."  
> _\-Dennis Ritchie_

Nowoczesne aplikacje internetowe mają wyższe oczekiwania użytkowników i większe wymagania niż kiedykolwiek wcześniej. Oczekuje się, że dzisiejsze aplikacje internetowe będą dostępne 24 godziny na dobę, 7 dni w tygodniu z dowolnego miejsca na świecie i będą dostępne z praktycznie dowolnego urządzenia lub ekranu. Aplikacje sieci Web muszą być bezpieczne, elastyczne i skalowalne, aby sprostać skokom popytu. Coraz częściej złożone scenariusze powinny być obsługiwane przez bogate środowiska użytkownika zbudowane na kliencie przy użyciu języka JavaScript i efektywnie komunikować się za pośrednictwem internetowych interfejsów API.

ASP.NET Core jest zoptymalizowany pod kątem nowoczesnych aplikacji internetowych i scenariuszy hostingu opartego na chmurze. Modułowa konstrukcja umożliwia aplikacjom poleganie tylko na tych funkcjach, z których faktycznie korzystają, poprawiając bezpieczeństwo i wydajność aplikacji, jednocześnie zmniejszając wymagania dotyczące zasobów hostingowych.

## <a name="reference-application-eshoponweb"></a>Aplikacja referencyjna: eShopOnWeb

Wytyczne te obejmują aplikację _referencyjną, eShopOnWeb_, która demonstruje niektóre zasady i zalecenia. Aplikacja jest prosty sklep internetowy, który obsługuje przeglądanie katalogu koszule, kubki do kawy i innych produktów marketingowych. Aplikacja referencyjna jest celowo prosta, aby ułatwić zrozumienie.

![Sklep internetowy eShopOnWeb](./media/image2-1.png)

**Rysunek 2-1.** Sklep internetowy eShopOnWeb

> ### <a name="reference-application"></a>Aplikacja referencyjna
>
> - **Sklep internetowy eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Hostowane w chmurze i skalowalne

ASP.NET Core jest zoptymalizowany pod kątem chmury (chmura publiczna, chmura prywatna, dowolna chmura), ponieważ jest mało pamięci i wysoka przepustowość. Mniejsza powierzchnia ASP.NET podstawowych aplikacji oznacza, że możesz hostować więcej z nich na tym samym sprzęcie, a płacisz za mniej zasobów podczas korzystania z usług hostingu w chmurze typu pay-as-you go. Wyższa przepływanie oznacza, że możesz obsługiwać więcej klientów z aplikacji, biorąc pod uwagę ten sam sprzęt, co jeszcze bardziej zmniejsza potrzebę inwestowania w serwery i infrastrukturę hostingową.

## <a name="cross-platform"></a>Platforma wieloplatformowa

ASP.NET Core jest wieloplatformowy i może działać w systemach Linux, macOS i Windows. Otwiera to wiele nowych opcji zarówno dla tworzenia, jak i wdrażania aplikacji utworzonych przy ASP.NET Core. Kontenery platformy Docker — zarówno linux, jak i windows — mogą obsługiwać ASP.NET aplikacje Core, umożliwiając im korzystanie z zalet [kontenerów i mikrousług.](../microservices/index.md)

## <a name="modular-and-loosely-coupled"></a>Modułowe i luźno połączone

Pakiety NuGet są pierwszorzędnymi obywatelami w .NET Core, a ASP.NET aplikacje Core składają się z wielu bibliotek za pośrednictwem NuGet. Ta szczegółowość funkcji pomaga zapewnić, że aplikacje zależą tylko od i wdrażają funkcje, których faktycznie wymagają, zmniejszając ich ślad i obszar luki w zabezpieczeniach.

ASP.NET Core w pełni obsługuje również [wstrzykiwanie zależności](https://deviq.com/dependency-injection/), zarówno wewnętrznie, jak i na poziomie aplikacji. Interfejsy mogą mieć wiele implementacji, które można zamienić w razie potrzeby. Iniekcji zależności umożliwia aplikacjom luźno para do tych interfejsów, a nie określonych implementacji, dzięki czemu łatwiej je rozszerzyć, utrzymać i przetestować.

## <a name="easily-tested-with-automated-tests"></a>Łatwe testowanie z automatycznymi testami

ASP.NET Podstawowe aplikacje obsługują testowanie jednostek, a ich luźne sprzężenie i obsługa wstrzykiwania zależności ułatwia zamianę problemów z infrastrukturą z fałszywymi implementacjami do celów testowych. ASP.NET Core jest również dostarczany z serwerem testowym, który może służyć do hostować aplikacje w pamięci. Testy funkcjonalne mogą następnie wysyłać żądania do tego serwera w pamięci, wykonując pełny stos aplikacji (w tym pośredniczenie, routing, powiązanie modelu, filtry itp.) i odbieranie odpowiedzi, a wszystko to w ułamku czasu, jaki zajęłoby hostowanie aplikacji na prawdziwym serwerze i składać żądania za pośrednictwem warstwy sieciowej. Testy te są szczególnie łatwe do napisania i cenne dla interfejsów API, które są coraz ważniejsze w nowoczesnych aplikacjach sieci Web.

## <a name="traditional-and-spa-behaviors-supported"></a>Obsługiwane zachowania tradycyjne i SPA

Tradycyjne aplikacje sieci web obejmowały małe zachowanie po stronie klienta, ale zamiast tego polegały na serwerze dla wszystkich nawigacji, zapytań i aktualizacji, które aplikacja może wymagać. Każda nowa operacja wykonana przez użytkownika zostanie przetłumaczona na nowe żądanie sieci Web, w wyniku czego zostanie załadowana pełna strona w przeglądarce użytkownika końcowego. Struktury klasycznego kontrolera widoku modelu (MVC) zazwyczaj postępują zgodnie z tym podejściem, a każde nowe żądanie odpowiada innej akcji kontrolera, która z kolei będzie działać z modelem i zwracać widok. Niektóre pojedyncze operacje na danej stronie mogą zostać wzbogacone o funkcje AJAX (Asynchronous JavaScript i XML), ale ogólna architektura aplikacji używała wielu różnych widoków MVC i punktów końcowych adresu URL. Ponadto ASP.NET Core MVC obsługuje również razor pages, prostszy sposób organizowania stron w stylu MVC.

Z kolei aplikacje jednostronicowe (SPI) obejmują bardzo niewiele dynamicznie generowanych obciążeń stron po stronie serwera (jeśli istnieją). Wiele dodatków SPA jest inicjowanych w obrębie statycznego pliku HTML, który ładuje niezbędne biblioteki JavaScript do uruchamiania i uruchamiania aplikacji. Te aplikacje znacznie korzysta z interfejsów API sieci Web dla ich potrzeb w zakresie danych i mogą zapewnić znacznie bogatsze środowisko użytkownika.

Wiele aplikacji sieci web obejmują kombinację tradycyjnezachowanie aplikacji sieci web (zazwyczaj dla zawartości) i spas (dla interaktywności). ASP.NET Core obsługuje zarówno MVC (Widoki lub Page based) i internetowych interfejsów API w tej samej aplikacji, przy użyciu tego samego zestawu narzędzi i podstawowych bibliotek framework.

## <a name="simple-development-and-deployment"></a>Proste tworzenie i wdrażanie

ASP.NET Podstawowe aplikacje mogą być zapisywane przy użyciu prostych edytorów tekstu i interfejsów wiersza polecenia lub w pełni funkcjonalnych środowisk programistycznych, takich jak Visual Studio. Aplikacje monolityczne są zazwyczaj wdrażane w jednym punkcie końcowym. Wdrożenia można łatwo zautomatyzować w ramach ciągłej integracji (CI) i ciągłego dostarczania (CD). Oprócz tradycyjnych narzędzi ciągłej integracji/ciągłego wdrażania platformy Microsoft Azure ma zintegrowaną obsługę repozytoriów git i może automatycznie wdrażać aktualizacje w określonej gałęzi lub tagu git. Azure DevOps zapewnia w pełni funkcjonalny potoku kompilacji i wdrażania ciągłego wdrażania ciągłego wdrażania, a akcje usługi GitHub udostępniają inną opcję dla projektów hostowanych w tym miejscu.

## <a name="traditional-aspnet-and-web-forms"></a>Tradycyjne ASP.NET i formularze internetowe

Oprócz ASP.NET Core, tradycyjne ASP.NET 4.x nadal jest solidną i niezawodną platformą do tworzenia aplikacji internetowych. ASP.NET obsługuje modele tworzenia interfejsów API MVC i Web API, a także formularze sieci Web, które są dobrze dostosowane do tworzenia aplikacji opartych na rozbudowanych stronach i mają bogaty ekosystem składników innych firm. Platforma Microsoft Azure ma doskonałą obsługę od dawna dla aplikacji ASP.NET 4.x, a wielu deweloperów zna tę platformę.

## <a name="blazor"></a>Blazor

Blazor jest dołączony do ASP.NET Core 3.0 i nowszych. Zapewnia nowy mechanizm tworzenia rozbudowanych interaktywnych aplikacji klienckich sieci web przy użyciu razor, C# i ASP.NET Core. Oferuje inne rozwiązanie do rozważenia przy opracowywaniu nowoczesnych aplikacji internetowych. Istnieją dwie wersje Blazor do rozważenia: po stronie serwera i po stronie klienta.

Serwer-side Blazor został wydany w 2019 roku z ASP.NET Core 3.0. Jak sama nazwa wskazuje, działa na serwerze, renderowania zmian w dokumencie klienta z powrotem do przeglądarki za pomocą sieci. Blazor po stronie serwera zapewnia bogate środowisko klienta bez konieczności obsługi javascript po stronie klienta i bez konieczności wczytywania oddzielnych stron dla każdej interakcji ze stroną klienta. Zmiany na załadowanej stronie są wymagane i przetwarzane przez serwer, a następnie wysyłane z powrotem do klienta za pomocą SignalR.

Blazor po stronie klienta ukaże się w 2020 roku i wyeliminuje konieczność renderowania zmian na serwerze. Zamiast tego będzie korzystać z WebAssembly do uruchamiania kodu .NET w kliencie. Klient nadal może wykonywać wywołania interfejsu API do serwera, jeśli jest to konieczne do żądania danych, ale wszystkie zachowanie po stronie klienta jest uruchamiane w kliencie za pośrednictwem WebAssembly, który jest już obsługiwany przez wszystkie główne przeglądarki i jest tylko biblioteką JavaScript.

> ### <a name="references--modern-web-applications"></a>Referencje – nowoczesne aplikacje internetowe
>
> - **Wprowadzenie do programu ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **Testowanie w ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Blazor - Zacznij**  
>   <https://blazor.net/docs/get-started.html>

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](choose-between-traditional-web-and-single-page-apps.md)
