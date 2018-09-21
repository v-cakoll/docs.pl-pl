---
title: Mikrousługi .NET. Architektura konteneryzowanych aplikacji .NET
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Mikrousługi są moduły i niezależnie do wdrożenia usługi. Kontenery platformy docker (dla systemu Linux i Windows) można uprościć wdrażanie i testowanie przez tworzenie pakietów usługi i jego zależności w pojedynczą jednostkę, który następnie jest uruchamiany w środowisku izolowanym.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: 0f401f89b0a568b8dc7c3734b2f06fa3a14de110
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46519659"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a>Mikrousługi .NET: Architektura konteneryzowanych aplikacji .NET

![Okładki książki](./media/cover-small.png)

**Wersja v2.1.02** — zaktualizowano w celu platformy ASP.NET Core 2.1

Ten przewodnik stanowi wprowadzenie do tworzenia aplikacji opartych na mikrousługach i zarządzanie nimi przy użyciu kontenerów. Omówiono w nim kwestie projektowania architektonicznego i zbliża się do wdrożenia przy użyciu platformy .NET Core i kontenerów rozwiązania Docker. 

Aby ułatwić rozpoczęcie pracy, przewodnik koncentruje się na odwołanie kontenerowych nimi i aplikacji opartych na mikrousługach, która pozwala zapoznać się z. Aplikacja referencyjna jest dostępna na [ramach aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) repozytorium GitHub.

## <a name="action-links"></a>Linki akcji

* Pobierz tę książkę elektroniczną w wybranym przez Ciebie formacie: | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-epub) |

* Klon/rozwidlenia aplikacja referencyjna [ramach aplikacji eShopOnContainers w witrynie GitHub](https://github.com/dotnet-architecture/eShopOnContainers)
 
* Obejrzyj [klip wideo w witrynie Channel 9](http://aka.ms/microservices-video)

* Ustal, jakimi [architektury Mikrousług](http://aka.ms/MicroservicesArchitecture) natychmiast

## <a name="introduction"></a>Wprowadzenie

Przedsiębiorstwa są coraz bardziej zawierającemu oszczędności kosztów, rozwiązywania problemów z wdrażaniem i poprawy operacje operacji deweloperskich i produkcyjnych przy użyciu kontenerów. Microsoft ma zostały udostępnia innowacje kontenera dla Windows i Linux, tworząc produktów, takich jak Azure Container Service i Azure Service Fabric i Zostań partnerem liderów branży, takich jak Docker, Mesosphere i Kubernetes. Te produkty dostarczanie rozwiązań do obsługi kontenerów, które ułatwiają tworzenie i wdrażanie aplikacji w chmurze prędkość i skalę, niezależnie od wybranych przez nich platformy lub narzędzia.

Docker staje się de facto standardem w branży kontenera, obsługiwane przez najważniejszych dostawców w ekosystemów Windows i Linux. (Firma Microsoft jest jeden z dostawców chmury głównego obsługi platformy Docker). W przyszłości Docker prawdopodobnie będzie wszechobecne w dowolnych centrach danych w chmurze lub lokalnie.

Ponadto [mikrousług](https://martinfowler.com/articles/microservices.html) architektury jest pojawiających się jako ważne podejście do rozproszonych aplikacji o kluczowym znaczeniu. W przypadku opartych na mikrousługach architektury aplikacji bazuje na zbiór usług, które mogą być tworzone, przetestowane, wdrożone i kontrolą wersji niezależnie.

## <a name="about-this-guide"></a>Przewodnik — informacje

Ten przewodnik stanowi wprowadzenie do tworzenia aplikacji opartych na mikrousługach i zarządzanie nimi przy użyciu kontenerów. Omówiono w nim kwestie projektowania architektonicznego i zbliża się do wdrożenia przy użyciu platformy .NET Core i kontenerów rozwiązania Docker. Aby ułatwić rozpoczęcie korzystania z kontenerów i mikrousług, przewodnik koncentruje się na odwołanie kontenerowych nimi i aplikacji opartych na mikrousługach, która pozwala zapoznać się z. Przykładowa aplikacja jest dostępna w [ramach aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) repozytorium GitHub.

Ten przewodnik zawiera podstawowe rozwoju i wskazówki dotyczące architektury, przede wszystkim na poziomie środowiska programowania skupiając się na dwie technologie: platforma Docker i platformy .NET Core. Zamierzone jest, że przeczytaniem tego przewodnika, jeśli zastanawiasz się nad projektu aplikacji bez konieczności zajmowania się infrastrukturą (w chmurze lub lokalnie) środowiska produkcyjnego. Będzie decyzje dotyczące infrastruktury później, podczas tworzenia aplikacji gotowych do produkcji. W związku z tym ten przewodnik jest przeznaczony jako niezależny od infrastruktury bardziej rozwoju środowiska — skoncentrowane na.

Po mają materiałami tego przewodnika, następnym krokiem jest więcej informacji na temat mikrousług gotowe do produkcji w systemie Microsoft Azure.

## <a name="version"></a>Wersja

Ten przewodnik został zaktualizowany w celu pokrycia **platformy .NET Core 2.1** wersji oraz wiele dodatkowe aktualizacje związane z takie same "wave" technologii (czyli. Azure wraz z dodatkowymi 3 innych firm technologii) odpowiedzialnego w czasie za pomocą platformy .NET Core 2.1. Dlatego wersji książki został także zaktualizowany do wersji **2.1**. 

## <a name="what-this-guide-does-not-cover"></a>Co ten przewodnik nie obejmuje

Ten przewodnik koncentruje się na cykl życia aplikacji, infrastruktury DevOps i potoków ciągłej integracji/ciągłego wdrażania lub pracy zespołu. Przewodnik uzupełniający [kontenerowych nimi Docker cyklem życia aplikacji za pomocą platformy firmy Microsoft i narzędzi](https://aka.ms/dockerlifecycleebook) koncentruje się na ten temat. Przewodnik bieżącego nie udostępniają szczegółów implementacji w infrastrukturze platformy Azure, takich jak informacje o określonych koordynatorów.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Kontenerowych nimi cykl życia aplikacji platformy Docker przy użyciu platformy firmy Microsoft i narzędzi** (do pobrania Książka elektroniczna)  
    [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

## <a name="who-should-use-this-guide"></a>Kto powinien używać tego przewodnika

Napisaliśmy ten przewodnik dla deweloperów i architektów rozwiązań, którzy są nowe, do tworzenia aplikacji opartych na platformie Docker i opartych na mikrousługach architektury. Ten przewodnik jest przeznaczony dla możesz Jeśli chcesz dowiedzieć się, jak zaprojektować, projektowania i implementacji aplikacji weryfikacji koncepcji przy użyciu technologii firmy Microsoft (kładąc szczególny nacisk na platformie .NET Core) i z kontenerami aparatu Docker.

Można również znaleźć w przewodniku przydatne, jeśli jesteś osobą podejmującą decyzje techniczne, np. architektury przedsiębiorstwa, który chce architekturę i omówienie technologii przed zdecyduj, jakie podejście do wybrania dla nowych i nowoczesnych aplikacji rozproszonych.

### <a name="how-to-use-this-guide"></a>Jak używać tego przewodnika

Pierwszej części tego przewodnika wprowadza kontenerów platformy Docker, w tym artykule omówiono jak dokonać wyboru między programem.NET Core i .NET Framework jako architektura deweloperska i zawiera omówienie mikrousług. Ta zawartość jest dla architektów i technicznych inne osoby podejmujące decyzje, którzy mają Przegląd, ale nie muszą skoncentrować się na szczegóły implementacji kodu.

Druga sekcja przewodnika zaczyna się od [aplikacji opartych na proces programistyczny dla platformy Docker](./docker-application-development-process/index.md) sekcji. Koncentruje się ona na rozwój i mikrousług wzorce dotyczące wdrażania aplikacji przy użyciu platformy .NET Core i Docker. W tej sekcji będzie najbardziej przydatnych dla deweloperów i architektów, którzy chcą skupić się na kodzie, a także na wzorców i szczegółów implementacji.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>Związanych z mikrousług i aplikacji opartych na kontenerach referencyjnej: ramach aplikacji eShopOnContainers

Aplikacji w ramach aplikacji eShopOnContainers to aplikacja typu open-source odwołania dla platformy .NET Core i mikrousług, który jest przeznaczony do wdrożenia przy użyciu kontenerów platformy Docker. Aplikacja składa się z wiele podsystemów, w tym kilka Sklep internetowy interfejs użytkownika Frontony (aplikacji sieci Web MVC, SPA internetowych i natywnych aplikacji mobilnych). Zawiera także zaplecza mikrousług i kontenerów wszystkich wymaganych operacji po stronie serwera. 

Aplikacja ma na celu prezentowania wzorców architektonicznych. **GOTOWE do produkcji szablonu dla IT nie jest** do uruchamiania aplikacji w rzeczywistych warunkach. W rzeczywistości aplikacja jest w stanie stałe w wersji beta, także jest używane do testowania nowych technologii potencjalnie interesujące, ponieważ są one wyświetlane.

## <a name="send-us-your-feedback"></a>Wyślij nam swoją opinię!

Napisaliśmy tego przewodnika, aby lepiej zrozumieć architekturę konteneryzowane aplikacje i mikrousług na platformie .NET. Przewodnik i powiązane odwołania aplikacji będzie można rozwijają, więc chętnie poznamy Twoją opinię! Jeśli masz komentarze na temat sposobu ten przewodnik można zwiększyć, wyślij je do:

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a>Środki na korzystanie z

Współautorzy:

> **Torre'a de la Cesarowi**, Stanowisko kierownicze wyższego PM, zespół produktu platformy .NET, Microsoft Corp.
>
> **Bill Wagnera**, Stanowisko kierownicze wyższego Deweloper zawartości C + E, Microsoft Corp.
>
> **Mike Rousos**, inżynier ds. oprogramowania jednostki, zespołu DevDiv CAT, Microsoft

Edytory:

> **Mike Pope**
>
> **Steve Hoag**

Uczestnicy i osób dokonujących przeglądu:

> **Jeffrey Richter**, rozwoju oprogramowania partnerem, zespół platformy Azure, Microsoft
>
> **Jimmy Bogard**, Dyrektor ds. architektury w Headspring
>
> **Udi Dahan**, założyciel i Dyrektor Generalny, konkretnego oprogramowania
>
> **Jimmy Nilsson**, współzałożyciel i Dyrektor Generalny firmy z Factor10
>
> **Glenn Condron**, Stanowisko kierownicze wyższego Menedżer programu, zespół programu ASP.NET
>
> **Oznacz Fussell**, Kierownik jednostki PM, zespół usługi Azure Service Fabric, Microsoft
>
> **Diego Vega**, kierownik PM, platformy Entity Framework zespołu firmy Microsoft
>
> **Marcin Dorrans**, Stanowisko kierownicze wyższego Menedżer programów zabezpieczeń
>
> **Rowan Miller**, Sr. Menedżer programów firmy Microsoft
>
> **Ankit Asthana**, główny menedżer PM, zespołem platformy .NET, Microsoft
>
> **Scott Hunter**, Dyrektor ds. partnerów PM, zespołem platformy .NET, Microsoft
>
> **Dylan Reisenberger**, architekt i Kierownik Dev w Polly
>
> **Steve Smith**, wytwarzającym oprogramowanie & Trainer na ASPSmith Ltd.
>
> **Ian Cooper**, kodowania architektury w Brighter
>
> **Unai Zorrilla**, architekt i Kierownik Dev w Plain Concepts
>
> **Tomasowi EDUARD**, kierownictwo Dev Plain Concepts
>
> **Tomasowi Ramon**, deweloper pracujący u Plain Concepts
>
> **David Sanz**, deweloper pracujący u Plain Concepts
>
> **Javier Valero**, Dyrektor operacyjny ds. na rozwiązanie Grupo
>
> **Pierre proso**, Stanowisko kierownicze wyższego Consultant, Microsoft
>
> **Michael Friis**, Menedżer produktu, Inc platformy Docker
>
> **Charles Lowell**, inżynier ds. oprogramowania, zespołu CAT programu VS, Microsoft
>
> **Miguel Veloso**, Stanowisko kierownicze wyższego Konsultant na żądanie Turing


## <a name="copyright"></a>Prawa autorskie

Pobierz dostępne pod adresem: <https://aka.ms/microservicesebook>

OPUBLIKOWANE PRZEZ

Zespoły produktu Microsoft Developer Division, .NET i Visual Studio

Dzielenie firmy Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2018 Microsoft Corporation

Wszelkie prawa zastrzeżone. Nie części zawartości tej książki może odtworzyć lub przenoszone w jakiejkolwiek formie lub za pomocą jakichkolwiek środków bez pisemnej zgody wydawcy.

Ten podręcznik jest dostarczany "jako — jest" i wyraża, widoki i opinie od autora. Widoki, opinie i informacje wyrażone w tym podręczniku, w tym adresy URL i inne odnośniki do witryn internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre przedstawione przykłady znajdują się wyłącznie do celów informacyjnych i są fikcyjne. Nie rzeczywiste skojarzenia ani powiązania nie są zamierzone ani powinny być zakładane.

Firma Microsoft i znaków towarowych, opisane w temacie http://www.microsoft.com na stronie sieci Web "Znakami" są znakami towarowymi grupy firm Microsoft.

Komputery Mac i z systemem macOS są znakami towarowymi firmy Apple Inc.

Logo whale platformy Docker jest zastrzeżonym znakiem towarowym firmy Docker, Inc. Używane przez uprawnienia.

Wszystkie inne znaki i logo są własnością ich prawnych właścicieli.


>[!div class="step-by-step"]
[Next](container-docker-introduction/index.md)
