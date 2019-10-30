---
title: Przyczyny modernizacji istniejących aplikacji .NET do aplikacji zoptymalizowanych pod kątem chmury
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Przyczyny modernizacji istniejących aplikacji .NET do aplikacji zoptymalizowanych pod kątem chmury
ms.date: 04/28/2018
ms.openlocfilehash: 55eb3fb9b0b6c91e25bcdb23056a8a8e51463ef7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73093634"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Przyczyny modernizacji istniejących aplikacji .NET do aplikacji zoptymalizowanych pod kątem chmury

Aplikacja zoptymalizowana pod kątem chmury umożliwia szybkie i wielokrotne dostarczanie niezawodnych aplikacji klientom. Możesz uzyskać istotną elastyczność i niezawodność, przenosząc większość operacyjnej złożoności aplikacji na platformę.

Jeśli nie możesz szybko dołączać aplikacji do rynku, w czasie, gdy aplikacja jest dostarczana, Twój rynek, na którym jesteś ukierunkowana, zostanie rozwijający. Może być zbyt późno, niezależnie od tego, w jaki sposób aplikacja została poddana zaprojektowana lub skonstruowana. Może się zdarzyć, że nastąpi awaria lub nie dotarcie do pełnego potencjału, ponieważ nie można zsynchronizować dostarczania aplikacji z potrzebami rynku.

Konieczność ciągłego tworzenia innowacji w biznesie umożliwia wypchnięcie zespołów deweloperskich i operacyjnych do limitu. Jedynym sposobem osiągnięcia elastyczności potrzebnej do ciągłej innowacji biznesowej jest modernizacja aplikacji przy użyciu technologii, takich jak kontenery, oraz określonych zasad aplikacji zoptymalizowanych pod kątem chmury.

Dolna linia polega na tym, że gdy organizacja kompiluje i zarządza aplikacjami, które są zoptymalizowane pod kątem chmury, może szybciej wprowadzać rozwiązania do klientów i wprowadzać nowe pomysły na rynek, gdy mają one zastosowanie.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Zasady aplikacji zoptymalizowane pod kątem chmury i założenia

Ulepszenia w chmurze są głównie skoncentrowane na spełnieniu dwóch celów: redukcja kosztów i poprawa rozwoju firmy dzięki ulepszaniu elastyczności. Cele te są osiągane przez uproszczenie procesów i zmniejszenie liczby problemów podczas dostarczania i wysyłania aplikacji.

Twoja aplikacja jest zoptymalizowana pod kątem chmury, jeśli możesz w sposób Agile — opracowywać aplikację autonomicznie z innych aplikacji lokalnych, a następnie wydawanie, wdrażanie, automatyczne skalowanie, monitorowanie i rozwiązywanie problemów z aplikacją w chmurze.

Klucz to *elastyczność*. Nie można dostarczać sprawności z elastycznością, chyba że ograniczy się do bezwzględnego minimum wszelkich problemów z wdrażaniem do produkcji i środowiska deweloperskiego/testowego. Kontenery (w konkretnym przypadku platformy Docker, jako de facto) i zarządzane usługi zostały przeznaczone specjalnie do tego celu.

Aby osiągnąć elastyczność, potrzebne są również zautomatyzowane procesy DevOps, które są oparte na potokach ciągłej integracji/ciągłego dostarczania na skalowalne platformy w chmurze. Platformy ciągłej integracji/ciągłego wdrażania (na przykład Azure DevOps Services lub Jenkins), które wdrażają na skalowalnej i odpornej platformie w chmurze (na przykład Azure App Service lub usługa Azure Kubernetes Service), to kluczowe technologie zapewniające elastyczność w chmurze.

Poniższa lista zawiera opis głównych założenia lub praktyk dla aplikacji zoptymalizowanych pod kątem chmury. Należy pamiętać, że można przyjąć wszystkie lub tylko niektóre z tych zasad, w ujęciu progresywnym lub przyrostowym:

- **Kontenery**. Kontenery umożliwiają dołączenie zależności aplikacji do samej aplikacji. Kontenerach znacząco zmniejsza liczbę problemów, które mogą wystąpić podczas wdrażania w środowiskach produkcyjnych lub testowania w środowiskach przejściowych. Ostatecznie kontenery zwiększają elastyczność dostarczania aplikacji.

- **Odporne i skalowalne chmury**. Chmura zapewnia platformę, która jest zarządzana, elastyczna, skalowalna i odporna. Te cechy mają podstawowe znaczenie dla poprawy kosztów i dostarczania wysoce dostępnych i niezawodnych aplikacji w ciągłej dostawie. Zarządzane usługi, takie jak zarządzane bazy danych, Zarządzana pamięć podręczna jako usługa (CaaS) i magazyn zarządzany to podstawowe elementy w celu zmniejszenia kosztów konserwacji aplikacji.

- **Monitorowanie**. Nie jest możliwe posiadanie niezawodnej aplikacji bez dobrego sposobu wykrywania i diagnozowania wyjątków oraz problemów z wydajnością aplikacji. Musisz uzyskać szczegółowe informacje umożliwiające podejmowanie działań dzięki zarządzaniu wydajnością aplikacji oraz błyskawicznej analizie.

- **DevOps kulturę i ciągłe dostarczanie**. Przyjmowanie praktyk DevOps wymaga zmiany kulturowej, w której zespoły nie działają już w niezależnych silosach. Potoki ciągłej integracji/ciągłego wdrażania są możliwe tylko wtedy, gdy istnieje zwiększona Współpraca między zespołami operacji programistycznych i IT, które są obsługiwane przez kontenery i narzędzia ciągłej integracji/ciągłego dostarczania.

Rysunek 4-2 przedstawia główne, opcjonalne filary aplikacji zoptymalizowanej pod kątem chmury. Im więcej filarów zaimplementowano, tym readier, że aplikacja będzie działać pomyślnie w zaspokajaniu oczekiwań klientów.

![Tworzenie diagramów z nazwami głównych filarów aplikacji zoptymalizowanej pod kątem chmury.](./media/main-pillars-cloud-optimized-application.png)

**Rysunek 4-2.** Główne filary aplikacji zoptymalizowanej pod kątem chmury

W celu podsumowania Aplikacja zoptymalizowana pod kątem chmury to podejście do kompilowania aplikacji, które wykorzystują model przetwarzania w chmurze, a przy użyciu kombinacji kontenerów, zarządzanej infrastruktury chmurowej, odpornych technik aplikacji, monitorowanie, ciągłe dostarczanie i DevOps, bez konieczności ponownej architektury i firmy Recode istniejących aplikacji.

Organizacja może wdrażać te technologie i stopniowo podejść. Nie trzeba wdrażać wszystkich elementów jednocześnie. Można je wdrożyć przyrostowo, w zależności od priorytetów przedsiębiorstwa i potrzeb użytkowników.

## <a name="benefits-of-a-cloud-optimized-application"></a>Zalety aplikacji zoptymalizowanej pod kątem chmury

Możesz uzyskać następujące korzyści, konwertując istniejącą aplikację na aplikacje zoptymalizowane pod kątem chmury (bez konieczności ponownego tworzenia architektury lub kodowania):

- **Niższe koszty, ponieważ zarządzana infrastruktura jest obsługiwana przez dostawcę chmury**. Aplikacje zoptymalizowane pod kątem chmury uzyskują zalety chmury przy użyciu wbudowanej elastyczności chmury, automatycznego skalowania i wysokiej dostępności. Korzyści są związane nie tylko z funkcjami obliczeniowymi (maszyn wirtualnych i kontenerów), ale również są zależne od zasobów w chmurze, takich jak DBaaS, CaaS i wszelkie infrastruktury, których aplikacja może potrzebować.

- **Odporna aplikacja i infrastruktura**. Podczas migracji do chmury należy wdrożyć błędy przejściowe; Błędy wystąpią w chmurze. Ponadto infrastruktura i sprzęt chmury są "wymienne", co zwiększa szanse na przestoje przejściowe. Jednocześnie możliwości chmury wewnętrznej i niektóre techniki programowania aplikacji, które implementują odporność i automatyzuje odzyskiwanie, znacznie ułatwiają odzyskiwanie po nieoczekiwanych awariach w chmurze.

- **Dokładniejsze informacje o wydajności aplikacji**. Narzędzia do monitorowania chmury, takie jak Azure Application Insights, udostępniają wizualizację do zarządzania, rejestrowania i powiadamiania o kondycji. Dzienniki inspekcji ułatwiają debugowanie i inspekcję aplikacji, a dla niezawodnych aplikacji w chmurze.

- **Przenośność aplikacji z wdrożeniami Agile**. Kontenery (kontenery systemu Linux lub Windows oparte na aparacie platformy Docker) oferują najlepsze rozwiązanie umożliwiające uniknięcie aplikacji zablokowanej w chmurze. Korzystając z kontenerów, hostów platformy Docker i programu Orchestrator z obsługą wielu chmur, można łatwo przejść między środowiskami lub chmurą. Kontenery eliminują tarcie, które zazwyczaj występują we wdrożeniach w dowolnym środowisku (etap/test/produkcja).

Wszystkie te korzyści ostatecznie zapewniają kluczowe obniżenie kosztów dla całego cyklu życia aplikacji.

W poniższych sekcjach te korzyści zostały omówione bardziej szczegółowo i są one połączone z konkretnymi technologiami.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[Następny](microsoft-technologies-in-cloud-optimized-applications.md)
