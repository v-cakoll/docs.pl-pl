---
title: Mikrousługi platformy .NET. architektura konteneryzowanych aplikacji .NET
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Mikrousługi są modularne i niezależnie do wdrożenia usługi. Kontenery platformy Docker (dla systemów Linux i Windows) upraszczają wdrażanie i testowanie poprzez zgrupowanie usługi i jej zależności w pojedynczą jednostkę, która jest uruchamiana w środowisku izolowanym.
ms.date: 01/07/2019
ms.openlocfilehash: 7fa4935fe56ca873a5311812637964083e34170e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089908"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a>Mikrousługi platformy .NET: architektura dla kontenerów aplikacji .NET

![Pokrycie książki](./media/cover-small.png)

**Wersja 2.2** — zaktualizowane do ASP.NET Core 2,2

Ten przewodnik stanowi wprowadzenie do tworzenia aplikacji opartych na mikrousługach i zarządzania nimi przy użyciu kontenerów. Omówiono podejścia projektowania i implementacji architektury przy użyciu programu .NET Core i kontenerów platformy Docker.

Aby ułatwić rozpoczęcie pracy, przewodnik koncentruje się na odniesieniu do aplikacji opartej na kontenerach i mikrousługach, które można eksplorować. Aplikacja referencyjna jest dostępna w repozytorium GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .

## <a name="action-links"></a>Linki akcji

- Pobierz tę książkę elektroniczną w wybranym formacie (tylko w języku angielskim): | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-epub) |

- Klonowanie/rozwidlenie aplikacji referencyjnej [eShopOnContainers w witrynie GitHub](https://github.com/dotnet-architecture/eShopOnContainers)

- Obejrzyj [film wprowadzający w witrynie Channel 9](https://aka.ms/microservices-video)

- Uzyskaj informacje o [architekturze mikrousług](https://aka.ms/MicroservicesArchitecture) od razu

## <a name="introduction"></a>Wprowadzenie

Przedsiębiorstwa są coraz bardziej kosztowne, rozwiązując problemy z wdrażaniem i ulepszają operacje DevOps i produkcyjne przy użyciu kontenerów. Firma Microsoft wyłączyła innowacje dotyczące kontenerów dla systemów Windows i Linux, tworząc produkty takie jak Azure Kubernetes Service i Azure Service Fabric, a przez partnerskie liderów branżowych, takich jak Docker, mesosphere i Kubernetes. Te produkty dostarczają rozwiązania kontenerów, które ułatwiają firmom Kompilowanie i wdrażanie aplikacji na dużą skalę i skalowalność, niezależnie od ich wyboru platformy lub narzędzi.

Platforma Docker staje się niefaktycznym standardem w branży kontenerów, która jest obsługiwana przez najbardziej znaczących dostawców w ekosystemach systemów Windows i Linux. (Firma Microsoft jest jednym z głównych dostawców chmury obsługujących platformę Docker). W przyszłości platforma Docker będzie prawdopodobnie ogólnie oparta na dowolnym centrum danych w chmurze lub lokalnie.

Ponadto architektura [mikrousług](https://martinfowler.com/articles/microservices.html) pojawia się jako ważne podejście do rozproszonych aplikacji o krytycznym znaczeniu. W architekturze mikrousług aplikacja jest tworzona na podstawie kolekcji usług, które mogą być opracowane, przetestowane, wdrożone i niezależne od wersji.

## <a name="about-this-guide"></a>Informacje o tym przewodniku

Ten przewodnik stanowi wprowadzenie do tworzenia aplikacji opartych na mikrousługach i zarządzania nimi przy użyciu kontenerów. Omówiono podejścia projektowania i implementacji architektury przy użyciu programu .NET Core i kontenerów platformy Docker. Aby ułatwić rozpoczęcie pracy z kontenerami i mikrousług, przewodnik koncentruje się na odwołaniach do aplikacji opartych na kontenerach i mikrousługach, które można eksplorować. Przykładowa aplikacja jest dostępna w repozytorium GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .

Ten przewodnik zawiera podstawowe wskazówki dotyczące programowania i architektury w środowisku programistycznym, które koncentrują się na dwóch technologiach: Docker i .NET Core. Naszym zamiarem jest zapoznanie się z tym przewodnikiem, gdy myślisz o projekcie aplikacji bez skoncentrowania się na infrastrukturze (w chmurze lub lokalnie) w środowisku produkcyjnym. Decyzje o infrastrukturze będą podejmowane później, podczas tworzenia aplikacji gotowych do produkcji. W związku z tym ten przewodnik jest przeznaczony dla infrastruktury niezależny od i większej ilości środowiska programistycznego.

Po przeprowadzeniu tego przewodnika następnym krokiem jest zapoznanie się z mikrousługami gotowymi do produkcji na Microsoft Azure.

## <a name="version"></a>Wersja

Ten przewodnik został zmieniony w taki sposób, aby objęł **platformę .NET Core 2,2** i wiele dodatkowych aktualizacji odnoszących się do tych samych "technologii". Platformę Azure i dodatkowe technologie innych firm, które są zgodne z platformą .NET Core 2,2. Dlatego też wersja książki została zaktualizowana do wersji **2,2**.

## <a name="what-this-guide-does-not-cover"></a>Czym nie obejmuje ten przewodnik

Ten przewodnik nie koncentruje się na potoku cyklu życia aplikacji, DevOps, ciągłej integracji/ciągłego wdrażania lub pracy zespołu. Przewodnik uzupełniający [zadokowany cykl życia aplikacji platformy Docker z platformą i narzędziami firmy Microsoft](https://aka.ms/dockerlifecycleebook) koncentrują się na tym temacie. Bieżący przewodnik nie zawiera również szczegółowych informacji dotyczących implementacji infrastruktury platformy Azure, takich jak informacje dotyczące określonych koordynatorów.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Cykl życia aplikacji platformy Docker w kontenerze z platformą i narzędziami firmy Microsoft (do** pobrania książek elektronicznych)  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a>Kto powinien korzystać z tego przewodnika

Ten przewodnik został napisany dla deweloperów i architektów rozwiązań, które są nowe dla tworzenia aplikacji opartych na platformie Docker oraz architektury opartej na mikrousługach. Ten przewodnik jest przeznaczony dla Ciebie, jeśli chcesz dowiedzieć się, jak architektować, projektować i wdrażać aplikacje do weryfikacji koncepcji za pomocą technologii programistycznych firmy Microsoft (ze specjalnym skoncentrowaniem się na platformie .NET Core) i z kontenerami platformy Docker.

Ten przewodnik będzie również przydatny, jeśli jesteś specjalistą ds. decyzji, na przykład z architektem przedsiębiorstwa, który chce zapoznać się z architekturą i technologią, przed podjęciem decyzji o wyborze podejścia do nowych i nowoczesnych aplikacji rozproszonych.

### <a name="how-to-use-this-guide"></a>Jak korzystać z tego przewodnika

Pierwsza część tego przewodnika zawiera wprowadzenie do kontenerów platformy Docker, w jaki sposób można wybrać platformę .NET Core i .NET Framework jako strukturę programistyczną oraz Omówienie mikrousług. Ta zawartość jest przeznaczony dla architektów i osób podejmujących decyzje techniczne, którzy chcą zapoznać się z omówieniem, ale nie muszą skupić się na szczegółach implementacji kodu.

Druga część przewodnika rozpoczyna się od [procesu opracowywania aplikacji opartych na platformie Docker](./docker-application-development-process/index.md) . Koncentruje się na wzorcach deweloperskich i mikrousług związanych z wdrażaniem aplikacji przy użyciu oprogramowania .NET Core i Docker. Ta sekcja będzie najbardziej interesująca dla deweloperów i architektów, którzy chcą skupić się na kodzie oraz o wzorcach i szczegółach implementacji.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>Powiązana mikrousługa i aplikacja referencyjna oparta na kontenerach: eShopOnContainers

Aplikacja eShopOnContainers to aplikacja referencyjna Open Source dla platformy .NET Core i mikrousług, która została zaprojektowana do wdrożenia przy użyciu kontenerów platformy Docker. Aplikacja składa się z wielu podsystemów, w tym kilku frontonów interfejsu użytkownika w postaci elektronicznej (aplikacji sieci Web MVC, SPA sieci Web i natywnej aplikacji mobilnej). Obejmuje ona również mikrousługi i kontenery zaplecza dla wszystkich wymaganych operacji po stronie serwera.

Celem aplikacji jest zaprezentowanie wzorców architektonicznych. **Nie jest to szablon gotowy** do uruchomienia aplikacji w rzeczywistości. W rzeczywistości aplikacja jest w stanie stałego stanu beta, ponieważ jest również używana do testowania nowych potencjalnie interesujących technologii w miarę ich wyświetlania.

## <a name="send-us-your-feedback"></a>Wyślij nam swoją opinię.

Utworzyliśmy ten przewodnik, aby ułatwić zrozumienie architektury aplikacji i mikrousług w programie .NET. Przewodnik i powiązana aplikacja referencyjna będą rozwijane, więc będziemy nam powitać Twoją opinię. Jeśli masz komentarze dotyczące tego, jak można ulepszyć ten przewodnik, wyślij je do:

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a>środki

Współautorzy:

> **Cesar de La Torre**, SR. PM, zespół produktu .NET, Microsoft Corp.
>
> **Bill Wagner**, SR. Content Developer, C + E, Microsoft Corp.
>
> **Jan Rousos**, główny inżynier ds. oprogramowania, DevDiv kot, firma Microsoft

Edytory

> **Jan Pope**
>
> **Steve Hoag**

Uczestnicy i recenzenci:

> **Jeffrey Richter**, partner Software aparatu, Azure Team, Microsoft
>
> **Jimmy Bogard**, główny architekt w headspring
>
> **UDI Dahan**, założyciel & dyrektor naczelny, szczególne oprogramowanie
>
> **Jimmy Nilsson**, współzałożyciel i dyrektor naczelny Factor10
>
> **Glenn Condron**, SR. Program Manager, zespół ASP.NET
>
> **Mark Fussell**, podmiotu z potencjalnym klientem PM, Azure Service Fabric Team, Microsoft
>
> **Diego Vega**, klient PM, Entity Framework zespół, Microsoft
>
> **Marcin Dorrans**, SR. Security — Menedżer programów
>
> **Rowan Miller**, SR. Program Manager, Microsoft
>
> **Autor Ankit Asthana**, kierownik ds. platformy PM, zespół .NET, Microsoft
>
> **Scott myśliwy**, dyrektor ds. partnerów, .NET Team, Microsoft
>
> **Nish Anil**, SR. Program Manager, .NET Team, Microsoft
>
> **Dylan Reisenberger**, architekt i dev ołów w Polly
>
> **Steve "ardalis" Smith** — architekt oprogramowania i Trainer- [Ardalis.com](https://ardalis.com)
>
> **Ian Cooper**, architekt programowania na jaśniejszy
>
> **Unai Zorrilla**, architekt i dev ołów z zwykłymi pojęciami
>
> **Eduard Tomas**, dev ołów z zwykłymi pojęciami
>
> **Ramon Tomas**, deweloper z zwykłymi pojęciami
>
> **David Sanz**, deweloper z zwykłymi pojęciami
>
> **Javier Valero**, dyrektor ds. operacyjnych w Grupo Solutio
>
> **Pierre Millet**, SR. konsultant, Microsoft
>
> **Michael Friis**, menedżer produktu, Docker Inc
>
> **Charles Lowell**, inżynier ds. oprogramowania, zespół programu vs Cat, Microsoft
>
> **Miguel Veloso**, SR. konsultant z wyzwaniami Turing

## <a name="copyright"></a>Prawo

Pobieranie dostępne o: <https://aka.ms/microservicesebook>

OPUBLIKOWANO PRZEZ

Dział deweloperów firmy Microsoft, zespoły produktów .NET i Visual Studio

Dział firmy Microsoft Corporation

One Microsoft Way

Redmond, Waszyngton 98052-6399

Prawa autorskie © 2019 przez firmę Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.

Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora. Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre przykłady opisane w niniejszym dokumencie są dostępne tylko dla ilustracji i są fikcyjne. Żadne prawdziwe skojarzenie lub połączenie nie jest zamierzone ani nie powinno zostać wywnioskowane.

Firma Microsoft i znaki towarowe wymienione w <https://www.microsoft.com> na stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Komputery Mac i macOS są znakami towarowymi firmy Apple Inc.

Logo Docker Whale jest zastrzeżonym znakiem towarowym platformy Docker, Inc. używanym przez uprawnienie.

Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.

>[!div class="step-by-step"]
>[Next](container-docker-introduction/index.md)
