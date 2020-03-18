---
title: Mikrousług .NET. architektura konteneryzowanych aplikacji .NET
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Mikrousługi są modułowe i niezależnie wdrażane usługi. Kontenery platformy Docker (dla systemów Linux i Windows) upraszczają wdrażanie i testowanie, łącząc usługę i jej zależności w jedną jednostkę, która jest następnie uruchamiana w izolowanym środowisku.
ms.date: 01/30/2020
ms.openlocfilehash: 1337fe56e78e03a85627737bd52a089fd946b842
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543537"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a>Microservices .NET: Architektura konteneryzowanych aplikacji .NET

![Okładka książki](./media/cover-small.png)

**EDITION v3.1** - Zaktualizowano do ASP.NET Core 3.1

Ten przewodnik jest wprowadzenie do tworzenia aplikacji opartych na mikrousługach i zarządzanie nimi za pomocą kontenerów. Omówiono projekt architektoniczny i podejścia implementacji przy użyciu .NET Core i kontenerów platformy Docker.

Aby ułatwić rozpoczęcie pracy, przewodnik koncentruje się na aplikacji konteneryzowanej i opartej na mikrousługach, którą można eksplorować. Aplikacja referencyjna jest dostępna w [reppo github eShopOnContainers.](https://github.com/dotnet-architecture/eShopOnContainers)

## <a name="action-links"></a>Łącza akcji

- Ten e-book jest również dostępny w formacie PDF (tylko wersja [angielska) Pobierz](https://aka.ms/microservicesebook)

- Klonuj/Rozwidlić aplikacji referencyjnej [eShopOnContainers w GitHub](https://github.com/dotnet-architecture/eShopOnContainers)

- Obejrzyj [film wprowadzający na kanale 9](https://aka.ms/microservices-video)

- Poznaj [architekturę mikrousług](https://aka.ms/MicroservicesArchitecture) od razu

## <a name="introduction"></a>Wprowadzenie

Przedsiębiorstwa coraz częściej realizują oszczędności kosztów, rozwiązują problemy z wdrażaniem i ulepszają operacje DevOps i produkcji za pomocą kontenerów. Firma Microsoft udostępnia innowacje kontenerów dla systemów Windows i Linux, tworząc produkty takie jak usługa Azure Kubernetes i sieć szkieletowa usług Azure oraz współpracując z liderami branży, takimi jak Platforma Docker, Mezosfera i Kubernetes. Produkty te dostarczają rozwiązania kontenerowe, które pomagają firmom tworzyć i wdrażać aplikacje z dużą szybkością i skalowaniem w chmurze, niezależnie od ich wyboru platformy lub narzędzi.

Docker staje się de facto standardem w branży kontenerów, wspieranym przez najpoważniejszych dostawców w ekosystemach Windows i Linux. (Firma Microsoft jest jednym z głównych dostawców chmury obsługujących platformę Docker). W przyszłości platforma Docker będzie prawdopodobnie wszechobecna w dowolnym centrum danych w chmurze lub lokalnie.

Ponadto architektura [mikrousług](https://martinfowler.com/articles/microservices.html) pojawia się jako ważne podejście dla rozproszonych aplikacji o znaczeniu krytycznym. W architekturze opartej na mikrousługach aplikacja jest zbudowana na kolekcji usług, które mogą być opracowywane, testowane, wdrażane i wersjonowane niezależnie.

## <a name="about-this-guide"></a>O tym przewodniku

Ten przewodnik jest wprowadzenie do tworzenia aplikacji opartych na mikrousługach i zarządzanie nimi za pomocą kontenerów. Omówiono projekt architektoniczny i podejścia implementacji przy użyciu .NET Core i kontenerów platformy Docker. Aby ułatwić rozpoczęcie pracy z kontenerami i mikrousługami, przewodnik koncentruje się na aplikacji konteneryzowanej i opartej na mikrousługach, którą można eksplorować. Przykładowa aplikacja jest dostępna w [reppo github eShopOnContainers.](https://github.com/dotnet-architecture/eShopOnContainers)

Ten przewodnik zawiera podstawowe wskazówki dotyczące rozwoju i architektury przede wszystkim na poziomie środowiska programistycznego, koncentrując się na dwóch technologiach: platformie Docker i .NET Core. Naszym zamiarem jest przeczytanie tego przewodnika podczas myślenia o projekcie aplikacji bez skupiania się na infrastrukturze (w chmurze lub lokalnie) środowiska produkcyjnego. Decyzje dotyczące infrastruktury będą podejmowane później podczas tworzenia aplikacji gotowych do produkcji. W związku z tym ten przewodnik ma być niezależne od infrastruktury i bardziej zorientowane na środowisko rozwoju.

Po przestudiowaniu tego przewodnika następnym krokiem będzie zapoznanie się z mikrousługami gotowymi do produkcji na platformie Microsoft Azure.

## <a name="version"></a>Wersja

Ten przewodnik został zaktualizowany w celu objęcia wersji **.NET Core 3.1** wraz z wieloma dodatkowymi aktualizacjami związanymi z tą samą "falą" technologii (czyli platformy Azure i dodatkowych technologii innych firm) zbiegających się w czasie z wersją .NET Core 3.1. Dlatego wersja książki została również zaktualizowana do wersji **3.1**.

## <a name="what-this-guide-does-not-cover"></a>Co ten przewodnik nie obejmuje

Ten przewodnik nie koncentruje się na cyklu życia aplikacji, DevOps, potokach ciągłej integracji/ciągłej integracji ani pracy zespołowej. Uzupełniający przewodnik [Konteneryzowany cykl życia aplikacji platformy dokowania z platformą i narzędziami firmy Microsoft](https://aka.ms/dockerlifecycleebook) koncentruje się na tym temacie. Bieżący przewodnik również nie zawiera szczegółów implementacji infrastruktury platformy Azure, takich jak informacje na temat określonych koordynatorów.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Cykl życia aplikacji do platformy dokowania kontenerowego z platformą i narzędziami firmy Microsoft** (e-book do pobrania)  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a>Kto powinien skorzystać z tego przewodnika

Napisaliśmy ten przewodnik dla deweloperów i architektów rozwiązań, którzy są nowicjuszami w tworzeniu aplikacji opartych na platformie Docker i architekturze opartej na mikrousługach. Ten przewodnik jest dla Ciebie, jeśli chcesz dowiedzieć się, jak zaprojektować, zaprojektować i zaimplementować aplikacje proof-of-concept z technologii rozwoju firmy Microsoft (ze szczególnym uwzględnieniem .NET Core) i kontenerów platformy Docker.

Ten przewodnik jest również przydatny, jeśli jesteś decydentem technicznym, takim jak architekt przedsiębiorstwa, który chce przeglądu architektury i technologii, zanim zdecydujesz się na to, jakie podejście wybrać dla nowych i nowoczesnych aplikacji rozproszonych.

### <a name="how-to-use-this-guide"></a>Jak korzystać z tego przewodnika

Pierwsza część tego przewodnika wprowadza kontenery platformy Docker, omówiono sposób wyboru między .NET Core i .NET Framework jako framework rozwoju i zawiera przegląd mikrousług. Ta zawartość jest dla architektów i decydentów technicznych, którzy chcą przeglądu, ale nie muszą koncentrować się na szczegółach implementacji kodu.

Druga część przewodnika rozpoczyna się od [procesu rozwoju dla aplikacji opartych na platformie Docker](./docker-application-development-process/index.md) sekcji. Koncentruje się na wzorce rozwoju i mikrousług do implementowania aplikacji przy użyciu .NET Core i Docker. Ta sekcja będzie najbardziej interesująca dla deweloperów i architektów, którzy chcą skupić się na kodzie oraz na wzorcach i szczegółach implementacji.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>Powiązana mikrousługa i aplikacja referencyjna oparta na kontenerach: eShopOnContainers

Aplikacja eShopOnContainers jest aplikacją referencyjną typu open source dla .NET Core i mikrousług, która jest przeznaczona do wdrożenia przy użyciu kontenerów platformy Docker. Aplikacja składa się z wielu podsystemów, w tym kilku frontonów interfejsu użytkownika sklepu internetowego (aplikacja Web MVC, web SPA i natywna aplikacja mobilna). Obejmuje również mikrousług zaplecza i kontenerów dla wszystkich wymaganych operacji po stronie serwera.

Celem aplikacji jest prezentacja wzorców architektonicznych. **TO NIE JEST SZABLON GOTOWY DO PRODUKCJI,** aby uruchomić rzeczywiste aplikacje. W rzeczywistości aplikacja jest w stanie stałej wersji beta, ponieważ jest również używana do testowania nowych potencjalnie interesujących technologii, gdy się pojawiają.

## <a name="send-us-your-feedback"></a>Prześlij nam swoją opinię!

Napisaliśmy ten przewodnik, aby ułatwić zrozumienie architektury konteneryzowanych aplikacji i mikrousług w .NET. Przewodnik i związana z nim aplikacja referencyjna będą ewoluować, więc czekamy na Państwa opinie! Jeśli masz uwagi na temat tego, jak można <https://aka.ms/ebookfeedback>poprawić ten przewodnik, prześlij opinię na .

## <a name="credits"></a>Środki

Współautorzy:

> **Cesar de la Torre**, Sr. PM, zespół produktów .NET, Microsoft Corp.
>
> **Bill Wagner**, Sr. Content Developer, C +E, Microsoft Corp.
>
> **Mike Rousos**, główny inżynier oprogramowania, zespół DevDiv CAT, Microsoft

Edytory:

> **Mike Papież**
>
> **Steve Hoag**

Uczestnicy i recenzenci:

> **Jeffrey Richter**, Partner Software Eng, Zespół platformy Azure, Microsoft
>
> **Jimmy Bogard**, Chief Architect w: Headspring
>
> **Udi Dahan**, Założyciel & CEO, Particular Software
>
> **Jimmy Nilsson**, współzałożyciel i dyrektor generalny Factor10
>
> **Glenn Condron**, Sr. Program Manager, zespół ASP.NET
>
> **Mark Fussell**, główny główny główny klient PM, zespół sieci szkieletowej usług Azure, Microsoft
>
> **Diego Vega**, PM Lead, Zespół Entity Framework, Microsoft
>
> **Barry Dorrans**, Sr. Security Program Manager
>
> **Rowan Miller**, Sr. Program Manager, Microsoft
>
> **Ankit Asthana**, Główny menedżer PM, zespół .NET, Microsoft
>
> **Scott Hunter**, Dyrektor Partnera PM, zespół .NET, Microsoft
>
> **Nish Anil**, Sr. Program Manager, zespół .NET, Microsoft
>
> **Dylan Reisenberger**, Architect and Dev Lead w: Polly
>
> **Steve "ardalis" Smith** - Architekt oprogramowania i trener - [Ardalis.com](https://ardalis.com)
>
> **Ian Cooper**, Coding Architect w: Brighter
>
> **Unai Zorrilla**, Architekt i Dev Lead w: Plain Concepts
>
> **Eduard Tomas**, Dev Lead w: Plain Concepts
>
> **Ramon Tomas**, Developer w: Plain Concepts
>
> **David Sanz**, Developer w: Plain Concepts
>
> **Javier Valero**, Chief Operating Officer w Grupo Solutio
>
> **Pierre Millet**, Konsultant s.
>
> **Michael Friis**, Menedżer produktu, Docker Inc
>
> **Charles Lowell**, Inżynier oprogramowania, zespół VS CAT, Microsoft
>
> **Miguel Veloso**, Software Development Engineer w: Plain Concepts

## <a name="copyright"></a>Prawa autorskie

OPUBLIKOWANA PRZEZ

Zespoły produktów Microsoft Developer Division, .NET i Visual Studio

Oddział Firmy Microsoft Corporation

One Microsoft Way

Redmond (Waszyngton) 98052-6399

Prawa autorskie © 2020 r. przez Firmę Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część treści tej książki nie może być powielana lub przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Ta książka jest "tak jak jest" i wyraża poglądy i opinie autora. Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Microsoft i znaki towarowe <https://www.microsoft.com> wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Mac i macOS są znakami towarowymi firmy Apple Inc.

Logo wieloryba Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używanym za zgodą.

Wszystkie inne znaki i logo są własnością ich właścicieli.

>[!div class="step-by-step"]
>[Dalej](container-docker-introduction/index.md)
