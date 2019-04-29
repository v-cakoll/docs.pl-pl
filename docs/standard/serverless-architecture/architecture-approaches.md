---
title: Metody dotyczące architektury — aplikacje niekorzystające z serwera
description: Wprowadzenie do architektury zbliża się do tworzenia aplikacji opartych na chmurze przedsiębiorstwa, z architektury N-warstwowej, aby bez użycia serwera.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 04ad383586f974bb2dccc4623a9a254f5668dab4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640197"
---
# <a name="architecture-approaches"></a>Podejścia do architektury

Informacje o istniejących podejścia do projektowania aplikacji dla przedsiębiorstw pomaga wyjaśnienia roli bez użycia serwera. Istnieje wiele metod i wzorce, które ewoluował za pośrednictwem dekad Wytwarzanie oprogramowania i mieć własne zalety i wady. W wielu przypadkach ostatecznego rozwiązania nie może obejmować podejmowania decyzji na temat podejścia do jednego, ale mogą integrować kilka metod. Scenariusze migracji często oznaczać między innymi przesunięcie z architektury jednej metody do drugiej za pomocą podejście hybrydowe.

W tym rozdziale omówiono obu wzorców architektury logiczne i fizyczne aplikacji dla przedsiębiorstw.

## <a name="architecture-patterns"></a>Wzorce architektury

Współczesne aplikacje biznesowe, należy wykonać różne wzorce architektury. W tej sekcji przedstawia przegląd typowych wzorców. Wzorce wymienione w tym miejscu nie są zawsze wszystkie najlepsze rozwiązania, ale pokazują różne podejścia.

Aby uzyskać więcej informacji, zobacz [przewodnik dotyczący architektury aplikacji platformy Azure](https://docs.microsoft.com/azure/architecture/guide/).

## <a name="monoliths"></a>Monolitycznych projektów

Wzorzec monolitu wielu aplikacji biznesowych, postępuj zgodnie z. Starsze aplikacje są często implementowane jako monolitycznych projektów. We wzorcu monolitu wszystkie problemy w aplikacji znajdują się w jednym wdrożeniu. Wszystko — od interfejsu użytkownika do wywołania bazy danych znajduje się w tej samej bazy kodu.

![Architektura monolitu](./media/monolith-architecture.png)

Ma kilka zalet tego podejścia monolitu. Często jest łatwo ściągnąć jednej bazy kodu i rozpocząć pracę. Zwiększania obciążenia czasu może być krótszy, a tworzenie środowisk testowych jest proste i polega na zapewnieniu nowej kopii. Monolityczna mogą być przeznaczone do obejmują wiele składników i aplikacji.

Niestety wzorzec monolitu zwykle podziału na dużą skalę. Główne wady podejścia monolitu obejmują:

* Trudno działać równolegle w tej samej bazy kodu.
* Każda zmiana, niezależnie od tego, jak prosta wymaga wdrażania nowej wersji całej aplikacji.
* Refaktoryzacja potencjalnie ma wpływ na całą aplikację.
* Często jest jedynym rozwiązaniem skalowanie do tworzenia wielu kopii monolitu dużej ilości zasobów.
* Rozwiń węzeł systemów lub innych systemów drogą kupna, integracji może być trudne.
* Może być trudne do testowania ze względu na konieczność konfigurowania całej monolitu.
* Ponowne wykorzystanie kodu staje się wyzwaniem i często inne aplikacje znajdą się o własne kopie kodu.

Wiele firm wyszukiwania w chmurze jako okazję do migrowania aplikacji monolitu i Refaktoryzuj je w tym samym czasie na więcej wzorców można używać. Są często umożliwiające rozbicie poszczególnych aplikacji i składników, aby mogła być utrzymywane, wdrożyć i skalować oddzielnie.

## <a name="n-layer-applications"></a>N warstwy aplikacji

Aplikacja N-warstwy logiki aplikacji partycji do określonej warstwy. Najbardziej typowe warstwy obejmują:

* Interfejs użytkownika
* Logika biznesowa
* Dostęp do danych

Inne warstwy mogą obejmować oprogramowanie pośredniczące, przetwarzanie wsadowe i interfejsu API. Należy zauważyć, że warstwy logiczne. Mimo że są one tworzone w izolacji, ich wszystkich można wdrażać na tej samej platformy docelowej.

![Architektura N-warstwy](./media/n-layer-architecture.png)

Ma kilka zalet podejście N warstwy, w tym:

* Refaktoryzacja jest izolowane do warstwy.
* Zespoły mogą niezależnie tworzenie, testowanie, wdrażanie i obsługa oddzielnych warstw.
* Odpowiedniki warstwy, na przykład warstwa danych mogą uzyskiwać dostęp do wielu baz danych bez konieczności wprowadzania zmian w warstwie interfejsu użytkownika.

Aplikacje niewymagające użycia serwera może służyć do zaimplementować jedną lub więcej warstw.

## <a name="microservices"></a>Mikrousługi

**[Mikrousługi](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)**  architektury zawiera typowe cechy, które obejmują:

* Aplikacje składają się z kilku małych usług.
* Każda usługa jest uruchamiana we własnym procesie.
* Usługi są wyrównane wokół domeny biznesowej.
* Usługi komunikują się za pośrednictwem interfejsów API uproszczone, zazwyczaj przy użyciu protokołu HTTP jako transportu.
* Usługi można wdrożyć i uaktualniane niezależnie.
* Usługi nie są zależne od pojedynczym magazynie danych.
* System został zaprojektowany z błędem, pamiętając, a aplikacja może nadal działać, nawet wtedy, gdy niektóre usługi nie.

Mikrousługi nie muszą być wzajemnie wykluczających się do innych metod architektury. Na przykład architektury N-warstwowej, może używać mikrousług dla warstwy środkowej. Istnieje również możliwość mikrousługi w na różne sposoby, z katalogów wirtualnych na hostach usług IIS do kontenerów. Cechy mikrousług były szczególnie idealne rozwiązanie w przypadku implementacji bez użycia serwera.

![Architektura mikrousług](./media/microservices-architecture.png)

Zalety architektury mikrousług obejmują:

* Refaktoryzacja często jest izolowane do jednej usługi.
* Usługi można uaktualnić niezależnie od siebie nawzajem.
* Elastyczność i elastyczność, mogą być dostosowane do wymagań poszczególnych usług.
* Programowanie może się zdarzyć w sposób równoległy między różnymi zespołami i platform.
* Łatwiej można pisać testy kompleksowe usługi izolowanym.

Mikrousługi są dostarczane z własnych wyzwaniom, w tym:

* Określanie, jakie usługi są dostępne i jak ich wywołania.
* Zarządzanie cyklem życia usługi.
* Zrozumienie, jak usługi współdziałają ze sobą cała aplikacja.
* Testowanie pełnego wywołań wykonanych dla różnych usług.

Ostatecznie są wszystkie te wyzwania związane z tym sięgnięcie do korzyści z bez użycia serwera, które zostały omówione w dalszej części rozwiązań.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](architecture-deployment-approaches.md)