---
title: "Przyczyny przyrostu i shift istniejących aplikacji .NET na aplikacje gotowe do chmury opracowywania oprogramowania"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Przyczyny przyrostu i shift istniejących aplikacji .NET na aplikacje gotowe do chmury opracowywania oprogramowania"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1339264f49a065888a95e6ef6fe8575aa3c75564
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2018
---
# <a name="reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications"></a>Przyczyny przyrostu i shift istniejących aplikacji .NET na aplikacje gotowe do chmury opracowywania oprogramowania

Z aplikacją gotowe DevOps chmury można szybko i wielokrotnie dostarczać niezawodnych aplikacji dla klientów. Możesz uzyskać istotne elastyczność i niezawodność odkładanie znacznie złożoność działania aplikacji dla platformy.

Jeśli nie można pobrać aplikacji na rynek szybkie, czas wydać aplikację, będą usprawnionych rynku, które były celem. Może być za późno, niezależnie od tego, jak również zaprojektowana lub odtwarzane aplikacji. Możesz może się niepowodzeniem lub nie osiągnie Twojego potencjał, ponieważ nie można zsynchronizować dostarczania aplikacji z potrzeb rynku.

Potrzebę innowacyjnych firm ciągłego wypycha zespoły rozwoju i operacje do limitu. Jedynym sposobem uzyskania elastyczności, potrzebnych innowacyjnych firm ciągłej jest modernizacji aplikacji przy użyciu technologii, takich jak kontenery i określonej zasady aplikacji DevOps gotowe do chmury.

Mierzenie jest podczas kompilacje i zarządza aplikacjami, które są gotowe do chmury DevOps organizacji it można wcześniej umieść rozwiązań w ręce klientów i Przełącz nowe pomysły na rynek, gdy mają one zastosowanie.

## <a name="cloud-devops-ready-application-principles-and-tenets"></a>Zasady aplikacji gotowe DevOps i rozwiązań w chmurze 

Ulepszenia w chmurze są przeważnie koncentruje się na spotkania dwóch celów: pozwalają ograniczyć koszty i zwiększyć rozwoju firmy skracając elastyczność. Tych celów są osiągane dzięki uproszczeniu procesy i zmniejszeniu tarcia zwolnienie i wysłać do aplikacji.

Aplikacja jest gotowe DevOps chmury, jeśli użytkownik może w agile sposób opracowywania aplikacji autonomicznie z innymi aplikacjami lokalnymi i Zwolnij, wdrażanie, automatycznego skalowania, monitorowania i rozwiązywania problemów z aplikacją w chmurze.

Klucz jest *elastyczność*. Nie można wydać z elastyczności, chyba, że można zmniejszyć do minimum wszystkie wdrożenia do produkcji zagadnienia i problemy dotyczące środowiska i testowania. Kontenery (w szczególności Docker, jako standard faktyczne) i usług zarządzanych zostały zaprojektowane specjalnie do tego celu.

Aby osiągnąć elastyczności, potrzebne są również zautomatyzowanych procesów opracowywania oprogramowania, które są oparte na kanał CI/CD wersji skalowalne platformy w chmurze. Platformy CI/CD (na przykład Visual Studio Team Services lub Wpięć), które wdrożyć do chmury skalowalne i elastyczne platformy (na przykład sieć szkieletowa usług Azure lub Kubernetes) to kluczowych technologii do osiągnięcia elastyczność w chmurze.

Poniżej przedstawiono listę rozwiązań głównego lub wskazówki dotyczące aplikacji DevOps gotowe do chmury. Należy pamiętać, że można przyjąć wszystkie lub tylko niektóre z tych zasad w podejściu progresywnego lub przyrostowej:

-   **Kontenery**. Kontenery zapewniają możliwość uwzględnienia zależności aplikacji z samej aplikacji. Przechowywanie w kontenerach znacznie ograniczyć liczbę problemów, które mogą wystąpić podczas wdrażania w środowisku produkcyjnym lub testowania w środowiskach przejściowym. Ostatecznie kontenery zwiększyć elastyczność dostawy aplikacji.

-   **Chmura elastycznego i skalowalnego**. Chmura zawiera platformy, które jest zarządzane, elastyczne, skalowalne i odporność. Te właściwości są niezbędne, aby uzyskać ulepszenia kosztów i wysłać wysokiej dostępności i niezawodnych aplikacji w ciągłego dostarczania. Zarządzane baz danych zarządzanych usług zarządzanych, takich jak pamięci podręcznej jako usługi (CaaS) i magazynów zarządzana podstawowe elementy w złagodzenia kosztów obsługi aplikacji.

-   **Monitorowanie**. Nie może mieć niezawodnych aplikacji bez konieczności dobry sposób na wykrywanie i diagnozowanie wyjątków i problemy z wydajnością aplikacji. Koniecznych do uzyskania przydatnych wyników analiz za pośrednictwem aplikacji Zarządzanie wydajnością i analiza błyskawicznych.

-   **DevOps kultury i ciągłego dostarczania**. Przyjęcie rozwiązania DevOps gotowe do chmury wymaga zmiany kultury, w którym, zespoły przestanie działać w silosach niezależne. Potoki CI/CD są możliwe tylko w przypadku zwiększonej współpracy między programowanie i zespoły operacji IT, obsługiwane przez kontenery i narzędzia CI/CD.

Rysunek 4-2 przedstawiono główne słupków opcjonalne aplikacji DevOps gotowe do chmury. Wdrożenie więcej kolumn, lepszą aplikacja będzie do pomyślnego spełnia oczekiwań klientów.

> ![Główne słupków aplikacji DevOps gotowe do chmury](./media/image2.png)
>
> **Rysunek 4-2.** Główne słupków aplikacji DevOps gotowe do chmury

Podsumowując, aplikacji gotowe DevOps chmury jest podejście do tworzenia aplikacji i zarządzanie nimi, które korzysta z przetwarzania modelu podczas przy użyciu kombinacji kontenerów, infrastruktury zarządzanej chmury, techniki odporność aplikacji w chmurze Monitorowanie, ciągłego dostarczania i opracowywania oprogramowania, bez konieczności ponownego projektowania i recode istniejących aplikacji.

Twoja organizacja może przyjąć stopniowo te technologie i metod. Nie masz uwzględnienie wszystkich z nich, jednocześnie. Można adaptować ich przyrostowo, w zależności od potrzeb użytkownika i priorytetów organizacji.

## <a name="benefits-of-a-cloud-devops-ready-application"></a>Zalety aplikacji DevOps gotowe do chmury

Konwertowanie istniejącej aplikacji do aplikacji DevOps gotowe do chmury (bez ponownego projektowania lub kodowania) można uzyskać następujące korzyści:

-   **Niższe koszty, ponieważ infrastruktury zarządzanych jest obsługiwane przez dostawcę chmury**. Aplikacje gotowe do opracowywania oprogramowania chmury Uzyskiwanie korzyści z chmury przy użyciu elastyczność poza pole z chmury, skalowania automatycznego i wysokiej dostępności. Korzyści dotyczą nie tylko funkcje obliczeniowe (maszyny wirtualne i kontenerów), ale również są zależne od zasobów w chmurze, takich jak DBaaS, CaaS i dowolnej infrastruktury aplikacji mogą wymagane.

-   **Odporność aplikacji i infrastruktury**. W przypadku migracji do chmury, musisz dążenie przejściowych awarii; wystąpią błędy w chmurze. Sprzętu i infrastruktury w chmurze jest "wymienne," co zwiększa możliwości przejściowej przestoju. W tym samym czasie funkcje dotyczące chmury wewnętrzny i niektórych techniki tworzenia aplikacji, które implementuje odporności i zautomatyzować odzyskiwania ułatwiają znacznie odzyskanie nieoczekiwanych awarii w chmurze.

-   **Lepszy wgląd w wydajność aplikacji**. Chmury narzędzi monitorowania, takich jak Azure Application Insights Podaj wizualizacji zarządzania kondycji, rejestrowania i powiadomień. Dzienniki inspekcji, Udostępnij aplikacje łatwe do debugowania i inspekcji. Jest to podstawowe dla aplikacji niezawodnej chmury.

-   **Mobilność aplikacji, z wdrożeniami agile**. Kontenery (Linux lub Windows kontenery oparty na aparacie Docker) oferuje najlepsze rozwiązanie unikanie aplikacją zablokowane w chmurze. Za pomocą kontenerów, hostach Docker i orchestrators usługi chmury, można łatwo w różnych środowiskach lub chmury do innej. Kontenery wyeliminować tarcie, który zazwyczaj występuje w przypadku wdrożeń z dowolnym środowiskiem (etapu testowego/produkcja).

Podaj wszystkie z tych zalet ostatecznie redukcję kosztów klucza dla cyklu użytkowania Twojej aplikacji na trasie.

W poniższych sekcjach te korzyści omówiono bardziej szczegółowo i są połączone z określonymi technologiami.

>[!div class="step-by-step"]
[Poprzednie](index.md)
[dalej](microsoft-technologies-in-cloud-devops-ready-applications.md)
