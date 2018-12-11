---
title: Ze względu na modernizowanie istniejących aplikacji .NET do aplikacji zoptymalizowane pod kątem chmury
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Ze względu na modernizowanie istniejących aplikacji .NET do aplikacji zoptymalizowane pod kątem chmury
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 8a59a78bbf7ec38f32b14e67d4cb35a9c2375e94
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151068"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Ze względu na modernizowanie istniejących aplikacji .NET do aplikacji zoptymalizowane pod kątem chmury

Za pomocą aplikacji zoptymalizowane pod kątem chmury możesz szybko i wielokrotnie dostarczyć niezawodne aplikacje swoim klientom. Można osiągnąć essential elastyczność i niezawodność odkładania znacznie złożoność operacyjną aplikacji na platformie.

Jeśli nie można pobrać aplikacji, aby szybko wprowadzać na rynek, do czasu dostarczania aplikacji, będzie usprawniły rynku, w której zostały adresowany. Może być za późno, niezależnie od tego, jak dobrze zaprojektowana lub odtwarzane aplikacji. Użytkownik może kończy się niepowodzeniem lub nie osiągnie swój pełny potencjał, ponieważ nie można zsynchronizować dostarczania aplikacji potrzebom rynku.

Potrzeby biznesowe ciągłe wprowadzanie innowacji wypycha zespoły deweloperów i operacyjne do limitu. Jedynym sposobem uzyskania elastyczności potrzebnych w biznesowych ciągłe wprowadzanie innowacji jest modernizujesz swoje aplikacje za pomocą technologii, takich jak kontenery i zasady określonej aplikacji zoptymalizowane pod kątem chmury.

Mierzenie to, że jeśli organizacja tworzy i zarządza aplikacjami, które są zoptymalizowane pod kątem chmury, jest wcześniej umieszczanie rozwiązania w ręce klientów i wprowadzaj nowe pomysły na rynek, gdy są one odpowiednie.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Zasady aplikacji zoptymalizowane pod kątem chmury i założenia 

Ulepszenia w chmurze, przede wszystkim koncentrują się na spotkanie dwóch celów: Obniżenie kosztów i poprawy rozwoju ich firm dzięki poprawie elastyczność. Te cele są wykonywane przez uprościć procesy, redukując opór zwolnienie i dostarczaj aplikacje.

Aplikacja jest zoptymalizowane pod kątem chmury w przypadku może w agile sposób opracowywanie aplikacji niezależnie od innych aplikacji w środowisku lokalnym, a następnie zwolnij wdrożenia, automatyczne skalowanie, monitorowanie i rozwiązywanie problemów z aplikacją w chmurze.

Klucz jest *elastyczność*. Nie można wydać z elastycznością, chyba że można zmniejszyć do minimum wszelkie wdrażania do produkcji problemy i rozwiązywania problemów w środowisku tworzenia i testowania. Kontenery (w szczególności platformy Docker, jak de facto standardem) i usługi zarządzane zostały zaprojektowane specjalnie do tego celu.

Aby osiągnąć elastyczności, potrzebny jest zautomatyzowane procesy metodyki DevOps, które są oparte na potoków ciągłej integracji/ciągłego wdrażania, które wydane skalowalnej platformy w chmurze. Platformy ciągłej integracji/ciągłego wdrażania (na przykład usługom DevOps platformy Azure lub usługi Jenkins), które Wdróż na platformie chmury skalowalne i odporne na błędy (np. usługi Azure App Service, Azure Service Fabric lub usłudze Azure Kubernetes Service) to kluczowych technologii do osiągnięcia elastyczności w chmurze.

Na poniższej liście opisano założenia głównego lub rozwiązania dla aplikacji zoptymalizowane pod kątem chmury. Należy zwrócić uwagę na to, że można przyjąć wszystkie lub tylko niektóre z tych zasad, w ramach podejścia progresywnego lub przyrostowej:

-   **Kontenery**. Kontenery zapewniają możliwość uwzględnienia zależności aplikacji przy użyciu samej aplikacji. Konteneryzacji znacznie zmniejsza liczbę problemów, które mogą wystąpić podczas wdrażania na środowisko produkcyjne lub testów w środowisku przejściowym. Ostatecznie kontenery zwiększyć elastyczność dostarczanie aplikacji.

-   **Odporne na błędy i skalowalnej chmurze**. Chmura udostępnia to platforma, która jest zarządzane, elastyczne, skalowalne i odporne na błędy. Te właściwości mają zasadnicze znaczenie uzyskać ulepszenia kosztów i dostarczanie wysoce dostępnych i niezawodnych aplikacji w ciągłego dostarczania. Usługi zarządzane, takie jak zarządzanych baz danych zarządzanych jako usługi (CaaS) i magazynu zarządzanego jest podstawowych elementów złagodzenia kosztów konserwacji aplikacji w pamięci podręcznej.

-   **Monitorowanie**. Nie może mieć niezawodnych aplikacji bez konieczności dobrym sposobem na wykrywanie i diagnozowanie wyjątków i problemów z wydajnością aplikacji. Musisz możliwość uzyskania praktycznych informacji dzięki zarządzaniu wydajnością aplikacji oraz błyskawicznej analizie.

-   **DevOps kultury i ciągłe dostarczanie**. Wdrażanie metodyki DevOps wymaga zmiany kultury, w którym, zespoły nie będą działać w odosobnieniu niezależne. Potoki ciągłej integracji/ciągłego wdrażania są możliwe tylko wtedy, gdy większa współpraca między środowiskami deweloperskim i zespołów operacyjnych IT obsługiwane kontenerów i narzędzi ciągłej integracji/ciągłego wdrażania.

Rysunek 4-2 pokazuje głównych filarach opcjonalne aplikacji zoptymalizowane pod kątem chmury. Więcej filary, które należy zaimplementować, lepszą Twoja aplikacja będzie zakończyło się sukcesem spełnia oczekiwania Twoich klientów.

> ![Głównych filarach zoptymalizowane pod kątem chmury aplikacji](./media/image2.png)
>
> **Rysunek 4-2.** Głównych filarach zoptymalizowane pod kątem chmury aplikacji

Aby podsumować, zoptymalizowane pod kątem chmury aplikacji jest podejście do tworzenia aplikacji i zarządzanie nimi, który korzysta z zalet chmury obliczeniowej modelu, podczas korzystania z kombinacji kontenery, infrastruktura zarządzana usługa w chmurze, techniki aplikacji odpornych na błędy Monitorowanie, ciągłego dostarczania i metodyki DevOps, bez konieczności Przekształcanie i firmy recode istniejących aplikacji.

Twoja organizacja można przyjąć stopniowo tych technologii i metod. Nie masz wykorzystać wszystkie z nich, wszystkie na raz. Można przyjąć ich przyrostowo, w zależności od potrzeb użytkowników i priorytetów organizacji.

## <a name="benefits-of-a-cloud-optimized-application"></a>Zalety aplikacji w języku zoptymalizowane pod kątem chmury

Za pomocą konwersji istniejącej aplikacji do aplikacji zoptymalizowane pod kątem chmury (bez transformować i kodowanie), możesz uzyskać następujące korzyści:

-   **Obniżenia kosztów, ponieważ zarządzana infrastruktura jest obsługiwany przez dostawcę chmury**. Zoptymalizowane pod kątem chmury aplikacji uzyskać korzyści z chmury, za pomocą elastyczność out-of--box chmury, automatyczne skalowanie i wysoką dostępność. Korzyści dotyczą nie tylko funkcje obliczeniowe (maszyny wirtualne i kontenery), ale również są zależne od zasobów w chmurze, takich jak DBaaS, CaaS i infrastruktury aplikacji może pożądane.

-   **Odporne na błędy aplikacji i infrastruktury**. W przypadku migracji do chmury, musisz Obsługa przejściowych błędów; wystąpią błędy w chmurze. Ponadto sprzętu i infrastruktury chmury są "zastąpienia," co zwiększa możliwości przejściowy przestojów. W tym samym czasie możliwości chmury wewnętrzny i techniki tworzenia aplikacji, niektóre wdrożenia odporności i automatyzacja odzyskiwania, które ułatwiają znacznie sprawności po awarii w chmurze.

-   **Lepszy wgląd w wydajność aplikacji**. Chmury, narzędzia do monitorowania takich jak Azure Application Insights zapewnia wizualizację dla zarządzania stanem, rejestrowanie i powiadomienia. Dzienniki inspekcji ułatwić aplikacji do debugowania i inspekcji podstawowe znaczenie dla aplikacji w chmurze w wiarygodne.

-   **Przenośność aplikacji, w przypadku wdrożeń agile**. Kontenery (Linux lub Windows kontenery opartą na aparacie Docker) oferują najlepsze rozwiązanie do uniknięcia aplikacją zablokowane w chmurze. Za pomocą kontenerów, hostów platformy Docker i koordynatorów wielu chmur, można łatwo przenosić z jednego środowiska lub do innego w chmurze. Kontenery wyeliminować zajmowania się zwykle występujący w przypadku wdrożeń z dowolnym środowiskiem (etap/testowania/produkcji).

Wszystkie te korzyści zapewni redukcję kosztów klucza dla cyklu użytkowania Twojej aplikacji end-to-end.

W poniższych sekcjach te korzyści omówiona bardziej szczegółowo i są powiązane z określonymi technologiami.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](microsoft-technologies-in-cloud-optimized-applications.md)