---
title: Powody modernizacji istniejących aplikacji .NET do aplikacji zoptymalizowanych pod kątem chmury
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Powody modernizacji istniejących aplikacji .NET do aplikacji zoptymalizowanych pod kątem chmury
ms.date: 04/28/2018
ms.openlocfilehash: 55eb3fb9b0b6c91e25bcdb23056a8a8e51463ef7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093634"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Powody modernizacji istniejących aplikacji .NET do aplikacji zoptymalizowanych pod kątem chmury

Dzięki aplikacji zoptymalizowanej pod kątem chmury możesz szybko i wielokrotnie dostarczać niezawodne aplikacje swoim klientom. Zyskujesz niezbędną elastyczność i niezawodność, odraczając znaczną część złożoności operacyjnej aplikacji na platformę.

Jeśli nie możesz szybko wprowadzać aplikacji na rynek, do czasu wysłania aplikacji rynek, na który kierowano reklamy, ewoluował. Może być za późno, bez względu na to, jak dobrze aplikacja została zaprojektowana lub zaprojektowana. Być może nie osiągniesz pełnego potencjału lub nie osiągniesz pełnego potencjału, ponieważ nie możesz zsynchronizować dostarczania aplikacji z potrzebami rynku.

Potrzeba ciągłych innowacji biznesowych popycha zespoły programistyczne i operacyjne do granic możliwości. Jedynym sposobem osiągnięcia elastyczności, jakiej potrzebujesz w zakresie ciągłych innowacji biznesowych, jest modernizacja aplikacji za pomocą technologii takich jak kontenery i specyficzne zasady aplikacji zoptymalizowane pod kątem chmury.

Najważniejsze jest to, że gdy organizacja tworzy i zarządza aplikacjami, które są zoptymalizowane pod kątem chmury, może szybciej oddać rozwiązania w ręce klientów i wprowadzić nowe pomysły na rynek, gdy są one istotne.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Zoptymalizowane pod kątem chmury zasady i założenia aplikacji

Ulepszenia w chmurze koncentrują się głównie na osiągnięciu dwóch celów: zmniejszeniu kosztów i poprawie rozwoju firmy poprzez poprawę elastyczności. Cele te są osiągane poprzez uproszczenie procesów i zmniejszenie tarcia podczas zwalniania i wysyłki aplikacji.

Aplikacja jest zoptymalizowana pod kątem chmury, jeśli można w sposób zwinny rozwijać aplikację autonomicznie z innych aplikacji lokalnych, a następnie zwolnić, wdrożyć, automatyczne skalowanie, monitorowanie i rozwiązywania problemów z aplikacją w chmurze.

Kluczem jest *zwinność*. Nie można wysyłać z elastycznością, chyba że zmniejszysz do absolutnego minimum wszelkie problemy z wdrożeniem do produkcji i problemy ze środowiskiem deweloperscym/testowym. Kontenery (w szczególności docker, jako de facto standard) i usługi zarządzane zostały zaprojektowane specjalnie w tym celu.

Aby osiągnąć elastyczność, potrzebne są również zautomatyzowane procesy DevOps, które są oparte na potokach ciągłej integracji/ciągłej integracji, które zwalniają na skalowalne platformy w chmurze. Platformy ciągłej integracji/zarządzania kluczem (takie jak usługi Azure DevOps Services lub Jenkins), które wdrażają na skalowalnej i odpornej platformie w chmurze (takiej jak usługa Azure App Service lub Usługa Azure Kubernetes) to kluczowe technologie zapewniające elastyczność w chmurze.

Na poniższej liście opisano główne założenia lub praktyki dotyczące aplikacji zoptymalizowanych pod kątem chmury. Należy pamiętać, że można przyjąć wszystkie lub tylko niektóre z tych zasad, w podejściu progresywnym lub przyrostowym:

- **Pojemniki**. Kontenery daje możliwość uwzględnienia zależności aplikacji z samej aplikacji. Konteneryzacja znacznie zmniejsza liczbę problemów, które mogą wystąpić podczas wdrażania w środowiskach produkcyjnych lub testowania w środowiskach przejściowych. Ostatecznie kontenery poprawiają elastyczność dostarczania aplikacji.

- **Elastyczna i skalowalna chmura**. Chmura zapewnia platformę, która jest zarządzana, elastyczna, skalowalna i odporna. Te cechy mają podstawowe znaczenie dla uzyskania poprawy kosztów i wysyłki wysoce dostępnych i niezawodnych aplikacji w ciągłej dostawy. Usługi zarządzane, takie jak zarządzane bazy danych, zarządzana pamięć podręczna jako usługa (CaaS) i magazyn zarządzany są podstawowymi elementami w zmniejszaniu kosztów konserwacji aplikacji.

- **Monitorowanie**. Nie można mieć niezawodnej aplikacji bez dobrego sposobu wykrywania i diagnozowania wyjątków i problemów z wydajnością aplikacji. Musisz uzyskać szczegółowe informacje, które można uzyskać za pomocą zarządzania wydajnością aplikacji i natychmiastowej analizy.

- **Kultura DevOps i ciągłe dostarczanie**. Przyjęcie praktyk DevOps wymaga zmiany kulturowej, w której zespoły nie pracują już w niezależnych silosach. Potoki ciągłej integracji/ciągłej integracji danych są możliwe tylko wtedy, gdy istnieje zwiększona współpraca między zespołami programistycznymi i operacyjnymi IT, obsługiwana przez kontenery i narzędzia ciągłej integracji/ciągłej integracji.

Rysunek 4-2 przedstawia główne opcjonalne filary aplikacji zoptymalizowanej pod kątem chmury. Im więcej filarów wdrożysz, tym bardziej czytelna będzie twoja aplikacja, aby odnieść sukces w spełniających oczekiwania klientów.

![Diagram nazewnictwa głównych filarów aplikacji zoptymalizowanej pod kątem chmury.](./media/main-pillars-cloud-optimized-application.png)

**Rysunek 4-2.** Główne filary aplikacji zoptymalizowanej pod kątem chmury

Podsumowując, aplikacja zoptymalizowana pod kątem chmury to podejście do tworzenia aplikacji i zarządzania nimi, które wykorzystuje model chmury obliczeniowej, przy użyciu kombinacji kontenerów, zarządzanej infrastruktury chmury, odpornych technik aplikacji, monitorowania, ciągłego dostarczania i devops, wszystko bez konieczności ponownego projektowania i ponownego kodowania istniejących aplikacji.

Twoja organizacja może stopniowo przyjmować te technologie i podejścia. Nie musisz ogarniać ich wszystkich, wszystkich naraz. Można je przyjmować stopniowo, w zależności od priorytetów przedsiębiorstwa i potrzeb użytkowników.

## <a name="benefits-of-a-cloud-optimized-application"></a>Zalety aplikacji zoptymalizowanej pod kątem chmury

Można uzyskać następujące korzyści, konwertując istniejącą aplikację do aplikacji zoptymalizowanej pod kątem chmury (bez ponownego projektowania lub kodowania):

- **Niższe koszty, ponieważ infrastruktura zarządzana jest obsługiwana przez dostawcę chmury**. Aplikacje zoptymalizowane pod kątem chmury czerpią korzyści z chmury dzięki wykorzystaniu elastyczności, automatycznej skalowania i wysokiej dostępności chmury. Korzyści są związane nie tylko z funkcjami obliczeniowymi (maszynami wirtualnymi i kontenerami), ale także zależą od zasobów w chmurze, takich jak DBaaS, CaaS i dowolnej infrastruktury, której może być potrzebna aplikacja.

- **Odporna aplikacja i infrastruktura**. Podczas migracji do chmury, należy objąć błędy przejściowe; wystąpią błędy w chmurze. Ponadto infrastruktura i sprzęt w chmurze są "wymienne", co zwiększa możliwości przejściowych przestojów. W tym samym czasie funkcje chmury wewnętrznej i niektórych technik tworzenia aplikacji, które implementują odporność i automatyzują odzyskiwanie, znacznie ułatwiają odzyskiwanie po nieoczekiwanych awariach w chmurze.

- **Głębszy wgląd w wydajność aplikacji**. Narzędzia do monitorowania w chmurze, takie jak usługa Azure Application Insights, zapewniają wizualizację zarządzania kondycją, rejestrowania i powiadomień. Dzienniki inspekcji ułatwiają debugowanie i inspekcję aplikacji, co ma podstawowe znaczenie dla niezawodnej aplikacji w chmurze.

- **Przenośność aplikacji z winnymi wdrożeń agile**. Kontenery (kontenery systemu Linux lub Windows oparte na aparatie platformy Docker) oferują najlepsze rozwiązanie do unikania aplikacji zablokowanej w chmurze. Za pomocą kontenerów, hostów platformy Docker i koordynatorów wielu chmur można łatwo przenosić z jednego środowiska lub chmury do innego. Kontenery eliminują tarcie, które zwykle występuje we wdrożeniach w dowolnym środowisku (etap/test/produkcja).

Wszystkie te korzyści ostatecznie zapewniają kluczowe obniżenie kosztów dla cyklu życia aplikacji typu end-to-end.

W poniższych sekcjach korzyści te są wyjaśnione bardziej szczegółowo i są połączone z określonymi technologiami.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](microsoft-technologies-in-cloud-optimized-applications.md)
