---
title: Podsumowanie
description: Podsumowanie najważniejszych konkluzji z aplikacji platformy .NET natywnej w chmurze dla przewodnika/książki elektronicznej platformy Azure.
ms.date: 04/29/2020
ms.openlocfilehash: 97f20771aae73ed88d2dadefa7ba89d64eb62fcd
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82899697"
---
# <a name="summary"></a>Podsumowanie

Podsumowując, poniżej przedstawiono ważne wnioski z tego przewodnika:

- **Chmura oparta na chmurze** polega na projektowaniu nowoczesnych aplikacji, które uwzględniają szybką zmianę, dużą skalę i odporność, w nowoczesnych, dynamicznych środowiskach, takich jak chmury publiczne, prywatne i hybrydowe.

- ** [Natywna platforma obliczeniowa w chmurze](https://www.cncf.io/) (CNCF)** to wpływ konsorcjum typu "open source" o ponad 300 głównych korporacji. Jest on odpowiedzialny za wspieranie wdrażania natywnych danych w chmurze w różnych technologiach i stosach w chmurze.

- **Wytyczne CNCF** zaleca się, aby aplikacje natywne w chmurze miały sześć ważnych filarów, jak pokazano na rysunku 12-1:

  ![Natywne filary w chmurze](./media/cloud-native-foundational-pillars.png)

  **Rysunek 12-1**. Natywne filary w chmurze

- Te filary natywne w chmurze obejmują:
  - Chmura i jej model usługi bazowej
  - Nowoczesne zasady projektowania
  - Mikrousługi
  - Kontenerach i aranżacja kontenera
  - Usługi do tworzenia kopii zapasowych oparte na chmurze, takie jak bazy danych i brokerów komunikatów
  - Automatyzacja, w tym infrastruktura jako kod i wdrażanie kodu

- **Kubernetes** to środowisko hostingu wybrane dla większości aplikacji natywnych w chmurze. W przypadku mniejszych usług proste usługi są czasami hostowane na platformach bezserwerowych, takich jak Azure Functions. W wielu funkcjach automatyzacji kluczy oba środowiska zapewniają automatyczne skalowanie w celu obsługi wahań woluminów obciążeń.

- **Komunikacja z usługą** stanowi znaczącą decyzję projektową podczas konstruowania aplikacji natywnej w chmurze. Aplikacje zwykle uwidaczniają bramę interfejsu API do zarządzania komunikacją klientów frontonu. Następnie mikrousługi zaplecza dążą do komunikowania się ze sobą przy wdrażaniu wzorców komunikacji asynchronicznej, jeśli jest to możliwe.

- **gRPC** to nowoczesne środowisko o wysokiej wydajności, które powoduje rozwój starego protokołu zdalnego wywołania procedury (RPC) w wieku. Aplikacje natywne w chmurze często uwzględniają gRPC do usprawnienia obsługi komunikatów między usługami zaplecza. gRPC używa protokołu HTTP/2 do protokołu transportowego. Może to być nawet 8x szybciej niż Serializacja JSON z rozmiarem komunikatu 60-80% mniejszych. gRPC to "open source" i zarządzana przez natywne rozwiązania do obsługi rozwiązań w chmurze (CNCF).

- **Dane rozproszone** są modelem często implementowanym przez aplikacje natywne w chmurze. Aplikacje dzielą funkcje biznesowe na małe, niezależne mikrousługi. Każda mikrousługa hermetyzuje własne zależności, dane i stan. Klasyczny model udostępnionej bazy danych zmienia się w jedną z wielu mniejszych baz danych, z których każda jest dostosowywana do mikrousług. Gdy dym jest wyczyszczony, zaczynamy od projektu, który uwidacznia `database-per-microservice` model.

- **Bazy danych bez programu SQL nie** odnoszą się do magazynów o wysokiej wydajności, które nie są relacyjne. Są one w programie Excel w ich łatwość użycia, skalowalności, odporności i dostępności. Usługi o dużych ilościach, które wymagają podrzędnego czasu odpowiedzi NoSQL datastores. Nie można nadzmieniać rozprzestrzeniania się technologii NoSQL w przypadku rozproszonych systemów natywnych w chmurze.

- **NewSQL** to rozwijana technologia baz danych, która łączy rozproszoną skalowalność NoSQL oraz gwarancje dotyczące kwasów relacyjnej bazy danych. Bazy danych NewSQL — docelowe systemy biznesowe, które muszą przetwarzać duże ilości danych w środowiskach rozproszonych, z pełną zgodnością transakcyjną/KWASem. Natywna platforma obliczeniowa w chmurze (CNCF) zawiera kilka projektów bazy danych NewSQL.

- **Odporność** to zdolność systemu do reagowania na awarie i nadal pozostaje funkcjonalna. Systemy natywne w chmurze stosują architekturę rozproszoną, w której niepowodzenie jest nieuniknione. Aplikacje muszą być skonstruowane w taki sposób, aby nie reagować na błędy i szybko powrócić do stanu w pełni funkcjonalny.

- **Sieci usług** to konfigurowalna warstwa infrastruktury z wbudowanymi funkcjami do obsługi komunikacji z usługą i innych wyzwań związanych z nacinaniem. Oddzielą odpowiedzialności za przecinanie z kodu biznesowego. Te obowiązki przechodzą do serwera proxy usługi. Określany jako `Sidecar pattern`, serwer proxy jest wdrażany w osobnym procesie, aby zapewnić izolację kodu biznesowego.

- **Zauważalność** to kluczowe zagadnienia projektowe dla aplikacji natywnych w chmurze. Ponieważ usługi są dystrybuowane w klastrze węzłów, scentralizowane rejestrowanie, monitorowanie i alerty, stają się obowiązkowe. Azure Monitor to zbiór narzędzi opartych na chmurze, zaprojektowanych w celu zapewnienia widoczności stanu systemu.

- **Infrastruktura jako kod** to szeroko zaakceptowana Metoda, która automatyzuje Inicjowanie obsługi platformy. Infrastruktura i wdrożenia są zautomatyzowane, spójne i powtarzalne. Narzędzia, takie jak Azure Resource Manager, Terraform i interfejs wiersza polecenia platformy Azure, umożliwiają deklaratywne skrypt wymaganej infrastruktury chmurowej.

- **Automatyzacja kodu** jest wymagana w przypadku aplikacji natywnych w chmurze. Nowoczesne systemy ciągłej integracji/ciągłego wdrażania pomagają spełnić tę zasadę. Zapewniają one oddzielne kroki kompilacji i wdrażania, które pomagają zapewnić spójny i jakościowy kod. Etap kompilacji przekształca kod w artefakt binarny. Etap wydania pobiera artefakt binarny, stosuje konfigurację środowiska zewnętrznego i wdraża ją w określonym środowisku. Usługa Azure DevOps i GitHub to w pełni funkcjonalne środowiska DevOps.

>[!div class="step-by-step"]
>[Poprzednio](application-bundles.md)
