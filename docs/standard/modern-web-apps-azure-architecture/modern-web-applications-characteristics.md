---
title: Właściwości nowoczesnych aplikacji sieci web
description: Projektowania nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure | właściwości nowoczesnych aplikacji sieci web
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.openlocfilehash: e01d07f4006982b21ff952b89375b0ab0d8f36b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583058"
---
# <a name="characteristics-of-modern-web-applications"></a>Właściwości nowoczesnych aplikacji sieci Web

> "… właściwy projekt funkcji pochodzić tanio. Takie podejście jest uciążliwe, ale nadal powiodło się."  
> _\- Dennis Ritchie_

## <a name="summary"></a>Podsumowanie

Nowoczesnych aplikacji sieci web mają wyższe oczekiwań użytkowników i większe wymagania niż kiedykolwiek wcześniej. Współczesnych aplikacji sieci web powinny być dostępne 24/7 z dowolnego miejsca na świecie i można używać z prawie każdego urządzenia lub rozmiaru ekranu. Aplikacje sieci Web musi być bezpieczny, elastyczne i skalowalne, aby spełnić wartości szczytowe zapotrzebowania. Coraz złożonych scenariuszy powinno zostać obsłużone przez wrażenia użytkowników zaawansowanych oparty na kliencie przy użyciu języka JavaScript i efektywnie komunikacji za pośrednictwem interfejsów API sieci web.

Platformy ASP.NET Core jest zoptymalizowana pod kątem nowoczesnych aplikacji sieci web i scenariusze hostingu oparte na chmurze. Jego modularny projekt umożliwia aplikacjom zależą tylko te funkcje, które są rzeczywiście używane, poprawy zabezpieczeń aplikacji i wydajności przy jednoczesnym zmniejszeniu zapotrzebowania na zasoby hostingu.

## <a name="reference-application-eshoponweb"></a>Odwołanie aplikacji: eShopOnWeb

Dotyczą one między innymi aplikacją odwołanie *eShopOnWeb*, który przedstawia niektóre zasady i zalecenia. Aplikacja jest proste sklepu obsługującej przeglądania katalogu koszule, mukeja kawy i innych elementów marketingu. Aplikacja referencyjna jest celowo proste, aby ułatwić zrozumienie.

**Rysunek 2-1.** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>Odwołanie do aplikacji
> - **eShopOnWeb**  
> <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Skalowalna i hostowanych w chmurze

Platformy ASP.NET Core jest zoptymalizowana pod kątem chmury (chmury publicznej, prywatnej chmury, żadną chmurą), ponieważ jest on ilości pamięci i wysokiej przepustowości. Mniejsze zużycie aplikacji platformy ASP.NET Core oznacza, że można obsługiwać jeden z nich na tym samym sprzęcie i płacisz za mniej zasobów, gdy za pomocą płatności — jako Przejdź hostingu usług w chmurze. Wyższej przepustowości oznacza, że może obsługiwać więcej klientów z aplikacji, podanych w tym samym sprzęcie, co dodatkowo zwiększa konieczności inwestowania w serwerów i infrastruktury obsługi.

## <a name="cross-platform"></a>Wiele platform

Platformy ASP.NET Core jest między platformami, a można uruchomić w systemie Linux i MacOS, a także systemu Windows. Spowoduje to otwarcie wiele nowych opcji dla rozwoju i wdrażaniu aplikacji skompilowanej za pomocą platformy ASP.NET Core. Kontenery docker, które są zazwyczaj uruchamiane Linux dzisiaj, może obsługiwać aplikacje platformy ASP.NET Core, dzięki czemu mogą korzystać z zalet [kontenery i mikrousług](../microservices-architecture/index.md).

## <a name="modular-and-loosely-coupled"></a>Moduły i luźno powiązanych

Pakiety NuGet są obywateli pierwszą klasą w .NET Core i aplikacje platformy ASP.NET Core składają się z wielu bibliotek za pośrednictwem pakietu NuGet. Ten poziom szczegółowości funkcji zapewnia aplikacji tylko zależne i wdrażanie funkcji rzeczywiście wymagają one, zmniejszenia ich wpływu i zabezpieczeń luki w zabezpieczeniach powierzchni.

Platformy ASP.NET Core obsługuje również całkowicie iniekcji zależności wewnętrznie i na poziomie aplikacji. Interfejsy może mieć wiele implementacji, które mogą być wymieniane zgodnie z potrzebami. Iniekcji zależności umożliwia aplikacjom słabo kilka do tych interfejsów, ułatwiając im rozszerzyć, obsługa i przetestowania.

## <a name="easily-tested-with-automated-tests"></a>Łatwo przetestowana testów automatycznych

Testy jednostkowe obsługuje aplikacje platformy ASP.NET Core, a ich luźne powiązanie i obsługę iniekcji zależności ułatwia wymiany infrastruktury problemy z implementacjami fałszywych do celów testowych. Platformy ASP.NET Core jest także dostarczany elementu TestServer, który może służyć do aplikacji hosta w pamięci. Testy funkcjonalne następnie mogą wysyłać żądania do tego serwera w pamięci, wykonywania stosu pełnej aplikacji (w tym oprogramowanie pośredniczące, routingu, model powiązanie, filtrami itp.) i odbierania odpowiedzi, w ułamku czasu, może potrwać do hostowania aplikacji na serwerze rzeczywistych i wysyłanie żądań za pośrednictwem warstwy sieci. Te testy są szczególnie łatwe do zapisu, a cenne dla interfejsów API, które są coraz bardziej ważne dla nowoczesnych aplikacji sieci web.

## <a name="traditional-and-spa-behaviors-supported"></a>Tradycyjne i zachowania SPA obsługiwane

Aplikacje sieci web tradycyjnych ma związane z małego zachowanie po stronie klienta, ale zamiast tego ma polegać na serwerze dla nawigacji, kwerendy i aktualizacji aplikacji może być konieczne. Każdej nowej operacji wprowadzonych przez użytkownika będzie można przetłumaczyć jej na żądanie nowej sieci web z wynikiem Trwa ponowne załadowanie całą stronę w przeglądarce użytkownika końcowego. Klasyczny Model-widok-kontroler (MVC) struktury wykonaj zazwyczaj takie podejście, z każdego nowego żądania odpowiadający akcji innego kontrolera, który z kolei może pracować z modelu i zwrócić widok. Niektóre operacje poszczególnych na danej stronie mogą być dołączane funkcjonalności interfejsu AJAX (asynchronicznego JavaScript i XML), ale ogólna Architektura aplikacji używane w wielu różnych widoków MVC i adres URL punktów końcowych.

Aplikacje jednostronicowe (źródła), natomiast obejmują bardzo mało obciążeń dynamicznie generowanym strony po stronie serwera (jeśli istnieje). Wiele źródła są inicjowane w obrębie statyczne pliki HTML, który jest ładowany wymagane biblioteki JavaScript do uruchomienia aplikacji. Te aplikacje upewnij duże użycie interfejsów API sieci web na potrzeby swoich danych i zapewniają bardziej rozbudowane użytkownikami napotka.

Wiele aplikacji sieci web obejmują kombinacją zachowanie aplikacji sieci web tradycyjnych (zazwyczaj dla zawartości) i źródła (na potrzeby interakcyjności). Platformy ASP.NET Core obsługuje MVC i interfejsów API w tej samej aplikacji przy użyciu tego samego zestawu narzędzi i bazowy bibliotek platformy sieci web.

## <a name="simple-development-and-deployment"></a>Proste opracowywania i wdrażania

Aplikacje platformy ASP.NET Core można pisać przy użyciu zwykłego tekstu edytory i interfejsy wiersza polecenia lub środowisk deweloperskich oferujący wszystkie funkcje, takie jak Visual Studio. Wbudowanymi aplikacje są zwykle wdrażane na jeden punkt końcowy. Wdrożeń można łatwo być wykonywane automatycznie w ramach ciągłej integracji (CI) i potoku ciągłego dostarczania (CD). Oprócz tradycyjnego narzędzia CI/CD systemu Windows Azure ma zintegrowanej obsłudze dla repozytoriów git i automatycznie wdrażać aktualizacje były wprowadzane gałęzi git określonego lub znacznik.

## <a name="traditional-aspnet-and-web-forms"></a>Tradycyjny ASP.NET i formularzy sieci Web

Oprócz platformy ASP.NET Core tradycyjnych ASP.NET 4.x jest nadal niezawodna platforma do tworzenia aplikacji sieci web. Program ASP.NET obsługuje modele programowania MVC i interfejsu API sieci Web, a także formularzy sieci Web, który dobrze nadaje się do opracowywania zaawansowanych aplikacji na stronie i funkcje ekosystemu sformatowanego składników innych firm. Windows Azure ma dużą dawna obsługę aplikacji programu ASP.NET 4.x i wielu deweloperów zapoznali się z tą platformą.

> ### <a name="references--modern-web-applications"></a>Odwołania — nowoczesnych aplikacji sieci Web
> - **Wprowadzenie do platformy ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/>
> - **Sześć klucza korzyści z platformy ASP.NET Core umożliwiających różne i lepsze**  
> <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **Testowanie w platformy ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
[Poprzednie] (index.md) [dalej] (choose-between-traditional-web-and-single-page-apps.md)
