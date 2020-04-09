---
title: Mikrousług .NET. architektura konteneryzowanych aplikacji .NET
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Mikrousługi są usługi modułowe i niezależnie wdrażalne. Kontenery platformy Docker (dla systemów Linux i Windows) upraszczają wdrażanie i testowanie, łącząc usługę i jej zależności w jedną jednostkę, która jest następnie uruchamiana w odizolowanym środowisku.
ms.date: 01/30/2020
ms.openlocfilehash: 9cdd5556f92e1acde540b647e7b68628a3ecf67f
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988794"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a>Mikrousługi .NET: architektura konteneryzowanych aplikacji .NET

![Okładka książki](./media/cover-small.png)

**EDITION v3.1** - Zaktualizowano do ASP.NET Core 3.1

Ten przewodnik jest wprowadzenie do tworzenia aplikacji opartych na mikrousług i zarządzania nimi przy użyciu kontenerów. Omówiono w nim metody projektowania i implementacji architektury przy użyciu kontenerów .NET Core i Docker.

Aby ułatwić rozpoczęcie pracy, przewodnik koncentruje się na aplikacji konteneryzowanej i opartej na mikrousługach, którą można eksplorować. Aplikacja referencyjna jest dostępna w repozytorium [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub.

## <a name="action-links"></a>Łącza akcji

- Ten e-book jest również dostępny w formacie PDF (tylko w wersji angielskiej) [Pobierz](https://aka.ms/microservicesebook)

- Klonuj/rozwidli aplikację referencyjną [eShopOnContainers w usłudze GitHub](https://github.com/dotnet-architecture/eShopOnContainers)

- Obejrzyj [film wprowadzający na kanale 9](https://aka.ms/microservices-video)

- Zapoznaj się z [architekturą mikrousług](https://aka.ms/MicroservicesArchitecture) od razu

## <a name="introduction"></a>Wprowadzenie

Przedsiębiorstwa coraz częściej zdają sobie sprawę z oszczędności kosztów, rozwiązywania problemów z wdrażaniem oraz ulepszania operacji devops i produkcyjnych przy użyciu kontenerów. Firma Microsoft wypuszcza innowacje kontenerów dla systemów Windows i Linux, tworząc produkty, takie jak usługa Azure Kubernetes i sieć szkieletowa azure, oraz współpracując z liderami branży, takimi jak Docker, Mesosphere i Kubernetes. Produkty te dostarczają rozwiązania kontenerowe, które pomagają firmom tworzyć i wdrażać aplikacje w chmurze z szybkością i skalą, niezależnie od ich wyboru platformy lub narzędzi.

Docker staje się de facto standardem w branży kontenerów, obsługiwanym przez najważniejszych dostawców w ekosystemach windows i linux. (Firma Microsoft jest jednym z głównych dostawców chmury obsługujących platformę Docker). W przyszłości docker będzie prawdopodobnie wszechobecne w dowolnym centrum danych w chmurze lub lokalnie.

Ponadto architektura [mikrousług](https://martinfowler.com/articles/microservices.html) pojawia się jako ważne podejście do rozproszonych aplikacji o znaczeniu krytycznym. W architekturze opartej na mikrousługach aplikacja jest oparta na kolekcji usług, które można opracować, przetestować, wdrożyć i wersjona niezależnie.

## <a name="about-this-guide"></a>O tym przewodniku

Ten przewodnik jest wprowadzenie do tworzenia aplikacji opartych na mikrousług i zarządzania nimi przy użyciu kontenerów. Omówiono w nim metody projektowania i implementacji architektury przy użyciu kontenerów .NET Core i Docker. Aby ułatwić rozpoczęcie pracy z kontenerów i mikrousług, przewodnik koncentruje się na odwołanie konteneryzowanych i aplikacji opartych na mikrousługach, które można eksplorować. Przykładowa aplikacja jest dostępna w repozytorium [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub.

Ten przewodnik zawiera podstawowe wskazówki dotyczące rozwoju i architektury przede wszystkim na poziomie środowiska programistycznego z naciskiem na dwie technologie: Docker i .NET Core. Naszym zamiarem jest przeczytanie tego przewodnika, gdy myślisz o projekcie aplikacji bez koncentrowania się na infrastrukturze (w chmurze lub lokalnie) środowiska produkcyjnego. Decyzje dotyczące infrastruktury podejmą później podczas tworzenia aplikacji gotowych do produkcji. W związku z tym ten przewodnik ma być niezależny od infrastruktury i bardziej zorientowane na środowisko rozwoju.

Po zapoznaniu się z tym przewodnikiem następnym krokiem będzie zapoznanie się z mikrousługami gotowymi do produkcji na platformie Microsoft Azure.

## <a name="version"></a>Wersja

Ten przewodnik został zmieniony w celu uwzględnienia wersji **.NET Core 3.1** wraz z wieloma dodatkowymi aktualizacjami związanymi z tą samą "falą" technologii (czyli platformy Azure i dodatkowych technologii innych firm) zbiegającą się w czasie z wydaniem .NET Core 3.1. Dlatego wersja książki została również zaktualizowana do wersji **3.1**.

## <a name="what-this-guide-does-not-cover"></a>Co ten przewodnik nie obejmuje

Ten przewodnik nie koncentruje się na cyklu życia aplikacji, DevOps, potoki ciągłej integracji/ciągłego wdrażania lub pracy zespołowej. Uzupełniający przewodnik [Konteneryzowany cykl życia aplikacji platformy Docker z platformą i narzędziami firmy Microsoft](https://aka.ms/dockerlifecycleebook) koncentruje się na tym temacie. Bieżący przewodnik również nie zawiera szczegółów implementacji infrastruktury platformy Azure, takich jak informacje na temat określonych koordynatorów.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Konteneryzowany cykl życia aplikacji platformy Docker za pomocą platformy Microsoft i narzędzi** (e-book do pobrania)  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a>Kto powinien korzystać z tego przewodnika

Napisaliśmy ten przewodnik dla deweloperów i architektów rozwiązań, którzy są nowicjuszami w tworzeniu aplikacji opartych na platformie Docker i architekturze opartej na mikrousługach. Ten przewodnik jest dla Ciebie, jeśli chcesz dowiedzieć się, jak projektować, projektować i implementować aplikacje proof-of-concept za pomocą technologii programisty firmy Microsoft (ze szczególnym uwzględnieniem programu .NET Core) i kontenerów platformy Docker.

Ten przewodnik jest również przydatny, jeśli jesteś decydentem technicznym, takim jak architekt przedsiębiorstwa, który chce przeglądu architektury i technologii, zanim zdecydujesz, jakie podejście wybrać dla nowych i nowoczesnych aplikacji rozproszonych.

### <a name="how-to-use-this-guide"></a>Jak korzystać z tego przewodnika

Pierwsza część tego przewodnika przedstawia kontenery platformy Docker, omówiono sposób wyboru między .NET Core i .NET Framework jako platformę rozwoju i zawiera omówienie mikrousług. Ta zawartość jest dla architektów i decydentów technicznych, którzy chcą przeglądu, ale nie trzeba skupić się na szczegóły implementacji kodu.

Druga część przewodnika rozpoczyna się od [procesu osiągnięć dla aplikacji opartych na platformie Docker.](./docker-application-development-process/index.md) Koncentruje się na rozwoju i wzorców mikrousług do implementowania aplikacji przy użyciu platformy .NET Core i platformy Docker. Ta sekcja będzie najbardziej interesujące dla deweloperów i architektów, którzy chcą skupić się na kod i wzorce i szczegóły implementacji.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>Powiązana mikrousługa i aplikacja referencyjna oparta na kontenerach: eShopOnContainers

Aplikacja eShopOnContainers jest aplikacją referencyjną typu open source dla platformy .NET Core i mikrousług, która jest przeznaczona do wdrażania przy użyciu kontenerów platformy Docker. Aplikacja składa się z wielu podsystemów, w tym kilku frontów interfejsu użytkownika sklepu internetowego (aplikacji MVC sieci Web, web SPA i natywnej aplikacji mobilnej). Zawiera również mikrousług zaplecza i kontenerów dla wszystkich wymaganych operacji po stronie serwera.

Celem aplikacji jest zaprezentowanie wzorców architektonicznych. **NIE JEST SZABLONEM GOTOWYM** DO PRODUKCJI, aby uruchamiać aplikacje w świecie rzeczywistym. W zasadzie aplikacja jest w stanie stałej wersji beta, ponieważ służy również do testowania nowych potencjalnie interesujących technologii, gdy się pojawiają.

## <a name="send-us-your-feedback"></a>Napisz do nas!

Napisaliśmy ten przewodnik, aby pomóc Ci zrozumieć architekturę konteneryzowanych aplikacji i mikrousług w .NET. Przewodnik i powiązana aplikacja referencyjna będą ewoluować, więc czekamy na Twoją opinię! Jeśli masz uwagi dotyczące tego przewodnika można <https://aka.ms/ebookfeedback>ulepszyć, prześlij opinię na .

## <a name="credits"></a>Środki

Współautorzy:

> **Cesar de la Torre**, Sr. PM, zespół produktów .NET, Microsoft Corp.
>
> **Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.
>
> **Mike Rousos**, główny inżynier oprogramowania, zespół DevDiv CAT, Microsoft

Edytory:

> **Michał Papież**
>
> **Steve Hoag**

Uczestnicy i recenzenci:

> **Jeffrey Richter**, Partner Software Eng, zespół platformy Azure, Microsoft
>
> **Jimmy Bogard**, Chief Architect w: Headspring
>
> **Udi Dahan**, założyciel & CEO, Szczególne oprogramowanie
>
> **Jimmy Nilsson**, współzałożyciel i dyrektor generalny Factor10
>
> **Glenn Condron**, Sr. Program Manager, zespół ASP.NET
>
> **Mark Fussell**, główny kierownik PM, zespół sieci szkieletowej usług Azure, Microsoft
>
> **Diego Vega**, PM Lead, zespół Entity Framework, Microsoft
>
> **Barry Dorrans**, Sr. Security Program Manager
>
> **Rowan Miller**, Sr. Program Manager, Microsoft
>
> **Ankit Asthana**, Główny Menedżer PM, zespół .NET, Microsoft
>
> **Scott Hunter**, Dyrektor Handlowy PM, zespół .NET, Microsoft
>
> **Nish Anil**, Sr. Program Manager, zespół .NET, Microsoft
>
> **Dylan Reisenberger**, Architect and Dev Lead w: Polly
>
> **Steve "ardalis" Smith** - Architekt oprogramowania i trener - [Ardalis.com](https://ardalis.com)
>
> **Ian Cooper**, Coding Architect w: Brighter
>
> **Unai Zorrilla**, Architekt i Dev Lead w Plain Concepts
>
> **Eduard Tomas**, Dev Lead w: Plain Concepts
>
> **Ramon Tomas**, Developer w: Plain Concepts
>
> **David Sanz**, Developer w: Plain Concepts
>
> **Javier Valero**, Chief Operating Officer w Grupo Solutio
>
> **Pierre Proso**, Sr. Konsultant, Microsoft
>
> **Michael Friis**, Menedżer produktu, Docker Inc
>
> **Charles Lowell**, inżynier oprogramowania, zespół VS CAT, Microsoft
>
> **Miguel Veloso**, Software Development Engineer w: Plain Concepts

## <a name="copyright"></a>Prawa autorskie

OPUBLIKOWANA PRZEZ

Zespoły produktów Microsoft Developer Division, .NET i Visual Studio

Oddział firmy Microsoft Corporation

One Microsoft Way

Redmond, Waszyngton 98052-6399

Prawa autorskie © 2020 roku przez Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część zawartości tej książki nie może być powielana ani przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Książka ta jest dostarczana "tak jak jest" i wyraża poglądy i opinie autora. Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Firma Microsoft i znaki <https://www.microsoft.com> towarowe wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Mac i macOS są znakami towarowymi firmy Apple Inc.

Logo docker wielorybów jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używany za zgodą.

Wszystkie inne znaki i logo są własnością ich odpowiednich właścicieli.

>[!div class="step-by-step"]
>[Dalej](container-docker-introduction/index.md)
