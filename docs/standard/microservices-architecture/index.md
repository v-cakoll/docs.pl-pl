---
title: "Mikrousług .NET. Architektura aplikacji .NET konteneryzowanych"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Wstępne"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 87a4b9f2bb076eccfa79e2951e509a35461ff257
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a>Mikrousług .NET. Architektura aplikacji .NET konteneryzowanych

Pobierz dostępne pod adresem: <https://aka.ms/microservicesebook>

OPUBLIKOWANY PRZEZ

Zespoły produktu Microsoft Developer dzielenia, .NET i Visual Studio

Dział Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399, USA

Copyright © 2017 przez firmę Microsoft Corporation

Wszelkie prawa zastrzeżone. Nie części zawartości tej książki może odtworzyć lub przesyłane w jakimkolwiek formularzu, lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Ten podręcznik podano "jako — jest" i odzwierciedla widoków i opinie autora. Widoki, opinie i informacje wyrażone w tej książki, w tym adresy URL i innymi odwołaniami do witryn internetowych, mogą ulec zmianie bez uprzedzenia.

Niektóre przedstawione przykłady są udostępniane tylko do celów ilustracyjnych i są fikcyjne. Żadne rzeczywiste skojarzenia ani połączenia jest przeznaczony lub powinny być zakładane.

Microsoft i znakami, znajduje się na http://www.microsoft.com na stronie sieci Web "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Mac i system macOS są znakami towarowymi firmy Apple Inc.

Logo wieloryb Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używany przez uprawnienia.

Wszystkie inne znaczniki i logo są własnością ich prawnych właścicieli.

Współautorzy:

> **Cesarowi de la Torre**, Sr. PM zespołu produktu .NET, Microsoft Corp.
>
> **Rachunek Wagnera**, Sr. Deweloper zawartości, C + E, Microsoft Corp.
>
> **Jan Rousos**, inżynier oprogramowania podmiot zabezpieczeń, zespołu DevDiv CAT, Microsoft

Edytory:

> **Jan Pope**
>
> **Steve Hoag**

Uczestnicy i osoby dokonujące przeglądu:

> **Jeffrey Ritcher**, Eng oprogramowania partnera, zespół Azure firmy Microsoft
>
> **Jimmy Bogard**, architektów główny na Headspring
>
> **Udi Dahan**, twórcę i dyrektora generalnego, konkretnego oprogramowania
>
> **Jimmy Nilsson**, wspólnej twórcę i Dyrektora Factor10
>
> **Glenn Condron**, Sr. Menedżer programów ASP.NET zespołu
>
> **Oznacz Fussell**, realizacji PM podmiot zabezpieczeń, zespół Azure Service Fabric, Microsoft
>
> **Diego Vega**, realizacji PM, zespołu programu Entity Framework, Microsoft
>
> **Marcin Dorrans**, Sr. Menedżer programu zabezpieczeń
>
> **Tomaszewski rowan**, Sr. Menedżer programów firmy Microsoft
>
> **Ankit Asthana**, główny menedżer PM, .NET zespół firmy Microsoft
>
> **Scott myśliwego**, PM Dyrektor partnera, .NET zespół firmy Microsoft
>
> **Dylan Reisenberger**, architektów i deweloperów kierownictwo Polly
>
> **Steve Smith**, wytwarzającym oprogramowania & Trainer na ASPSmith Ltd.
>
> **Ian Cooper**, kodowania projektowania w Brighter
>
> **Unai Zorrilla**, architektów i deweloperów kierownictwo zwykły pojęcia
>
> **Tomasowi EDUARD**, deweloperów kierownictwo zwykły pojęcia
>
> **Tomasowi Ramon**, deweloper pracujący u zwykły pojęcia
>
> **Sanz Dominik**, deweloper pracujący u zwykły pojęcia
>
> **Javier Valero**, dyrektora operacyjnego urzędnika na rozwiązanie Grupo
>
> **Saint-Pierre proso**, Sr. Konsultanta firmy Microsoft
>
> **Jan Friis**, Menedżer produktu, Inc Docker
>
> **Lowell Charlesa**, inżynier oprogramowania, zespołu VS CAT, Microsoft

## <a name="introduction"></a>Wprowadzenie

Przedsiębiorstwa są coraz bardziej realizująca oszczędności, rozwiązywania problemów z wdrażaniem i poprawy DevOps i produkcji operacje przy użyciu kontenerów. Microsoft ma zostały udostępnia innowacje kontenera systemu Windows i Linux, tworząc produktów, takich jak usługi kontenera platformy Azure i usługi Azure Service Fabric i we współpracy z liderów branżowe, takie jak Docker, Mesosphere i Kubernetes. Te produkty dostarczania kontenera rozwiązania, które ułatwiają tworzenie i wdrażanie aplikacji w chmurze szybkość i skalę, niezależnie od siebie platformy lub narzędzi.

Docker staje się coraz faktyczne standardowego w branży kontenera, obsługiwanych przez dostawców najbardziej znaczących w ekosystemami systemu Windows i Linux. (Microsoft jest jeden z dostawców chmury głównego obsługi Docker). W przyszłości prawdopodobnie będzie wszechobecne w dowolnego centrum danych w chmurze lub lokalnie Docker.

Ponadto [mikrousług](https://martinfowler.com/articles/microservices.html) architektury jest pojawiających się jako rozwiązaniem ważne dla aplikacji rozproszonych krytycznym. W architekturze na podstawie mikrousługi aplikacji jest oparty na zbiór usług, które mogą być opracowane, przetestowane, wdrożone i numerów wersji niezależnie.

## <a name="about-this-guide"></a>O tym przewodniku

Ten przewodnik jest wprowadzenie do tworzenia aplikacji opartych na mikrousług oraz zarządzania nimi przy użyciu kontenerów. Zawarto informacje projektowania architektonicznego i implementacja zbliża się przy użyciu kontenerów .NET Core i Docker. Aby ułatwić wprowadzenie kontenery i mikrousług przewodnik koncentruje się na odwołanie konteneryzowanych i aplikacji na podstawie mikrousługi Ci poznać platformę. Przykładowa aplikacja jest dostępna w [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) repozytorium GitHub.

Ten przewodnik zawiera podstawowych rozwoju i wskazówki architektury przede wszystkim na poziomie środowisko rozwoju nacisk na dwie technologie: Docker i .NET Core. Zamierzone jest przeczytaniu tego przewodnika, w przypadku o projektu aplikacji bez koncentrujących się na infrastrukturę (chmurze lub lokalnie) środowiska produkcyjnego. Zostanie podejmowaniu decyzji dotyczących infrastruktury później, podczas tworzenia aplikacji gotowych do produkcji. W związku z tym niniejszy przewodnik jest przeznaczony jako infrastruktury o niesprecyzowanym i bardziej programowanie środowiska skoncentrowane na.

Po ma badać w tym przewodniku, następnym krokiem jest więcej informacji na temat mikrousług gotowe do produkcji w systemie Microsoft Azure.

## <a name="what-this-guide-does-not-cover"></a>Czego ten przewodnik nie obejmuje

Ten przewodnik nie skupić się na cyklu życia aplikacji, metodyki DevOps, potoki CI/CD lub pracy zespołu. Przewodnik uzupełniający [konteneryzowanych cyklem życia aplikacji Docker z platformy firmy Microsoft i narzędziami](https://aka.ms/dockerlifecycleebook) koncentruje się na ten temat. Przewodnik bieżącego również nie szczegółowo wdrożenia infrastruktury platformy Azure, takich jak informacje o określonym orchestrators.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Konteneryzowanych cyklem życia aplikacji Docker z platformy firmy Microsoft i narzędziami** (do pobrania Książka elektroniczna) [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

## <a name="who-should-use-this-guide"></a>Kto powinien używać ten przewodnik

Napisaliśmy ten przewodnik dla deweloperów i architekci rozwiązań, nowi do tworzenia aplikacji opartych na Docker i architektura oparta na mikrousług. Ten przewodnik jest, aby dowiedzieć się, jak zaprojektować, projektowania i wdrażania aplikacji Weryfikacja koncepcji przy użyciu technologii rozwoju firmy Microsoft (z szczególną uwagę na .NET Core) i z kontenerami Docker.

Zostanie również znaleźć przydatne tego przewodnika, jeśli jesteś osobą podejmującą decyzje technicznych, takich jak architekta organizacji, którzy chcą architekturę i omówienie technologii przed zdecyduj, jakie podejście, aby wybrać nowy i nowoczesne aplikacje rozproszone.

### <a name="how-to-use-this-guide"></a>Jak używać tego przewodnika

Pierwsza część tego przewodnika wprowadza kontenery Docker omówiono sposób wybrać oprogramowanie .NET Core i .NET Framework jako platforma programistyczna i zawiera omówienie mikrousług. Ta zawartość jest dla architektów i technicznych inne osoby podejmujące decyzje potrzebują Przegląd, ale który nie ma potrzeby skupić się na szczegóły implementacji kodu.

Rozpoczyna się od drugiej części przewodnika [aplikacji opartych na proces Docker](#ch_dev_process_for_docker_based_apps) sekcji. Głównie wzorce programowania i mikrousługi wdrażania aplikacji przy użyciu platformy .NET Core i Docker. W tej sekcji będzie najbardziej przydatnych dla deweloperów i architektów, którzy mają być fokus na kod i wzorce i szczegóły implementacji.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>Związane z mikrousługi i aplikacji na podstawie kontenera odwołania: eShopOnContainers

Aplikacja eShopOnContainers jest aplikacja odwołania dla platformy .NET Core i mikrousług przeznaczonego do wdrożenia przy użyciu kontenerów Docker. Aplikacja składa się z wielu podsystemami, łącznie z kilku Sklep internetowy interfejsu użytkownika frontonu zakończenia (aplikacja sieci Web i natywnych aplikacji mobilnej). Zawiera także mikrousług zaplecza i kontenerami dla wszystkich wymaganych operacji po stronie serwera.

Ten mikrousługi i aplikacja kontenera kod źródłowy jest typu open source dostępny na [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) repozytorium GitHub.

## <a name="send-us-your-feedback"></a>Wyślij nam swoją opinię!

Napisaliśmy tego przewodnika, aby ułatwić zrozumienie architektury konteneryzowanych aplikacji i mikrousług w .NET. Przewodnik i powiązanego odwołania aplikacji będzie można rozwijają, więc chętnie poznamy Twoją opinię! Jeśli masz komentarze na temat sposobu w tym przewodniku można zwiększyć, wyślij je do:

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
[Next] (kontenera — docker — wprowadzenie/index.md)
