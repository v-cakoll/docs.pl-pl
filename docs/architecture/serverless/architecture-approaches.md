---
title: Podejścia do architektury — aplikacje bezserwerowe
description: Wprowadzenie do podejścia do architektury do tworzenia aplikacji korporacyjnych opartych na chmurze, od architektur n-warstwowych do bezserwerowych.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522899"
---
# <a name="architecture-approaches"></a>Podejścia do architektury

Zrozumienie istniejących podejść do projektowania aplikacji dla przedsiębiorstw pomaga wyjaśnić rolę odgrywanej przez bezserwerowe. Istnieje wiele podejść i wzorców, które ewoluowały przez dziesięciolecia rozwoju oprogramowania, a wszystkie mają swoje wady i zalety. W wielu przypadkach ostateczne rozwiązanie może nie obejmować podjęcia decyzji w sprawie jednego podejścia, ale może integrować kilka podejść. Scenariusze migracji często obejmują przejście z jednego podejścia architektury do innego za pomocą podejścia hybrydowego.

Ten rozdział zawiera omówienie wzorców architektury logicznej i fizycznej dla aplikacji korporacyjnych.

## <a name="architecture-patterns"></a>Wzorce architektury

Nowoczesne aplikacje biznesowe są zgodne z różnymi wzorcami architektury. Ta sekcja przedstawia przegląd typowych wzorców. Wzorce wymienione w tym miejscu nie koniecznie wszystkie najlepsze rozwiązania, ale ilustrują różne podejścia.

Aby uzyskać więcej informacji, zobacz [Przewodnik po architekturze aplikacji platformy Azure](https://docs.microsoft.com/azure/architecture/guide/).

## <a name="monoliths"></a>Monoliths

Wiele aplikacji biznesowych jest zgodnych ze wzorem monolitu. Starsze aplikacje są często implementowane jako monolity. We wzorcu monolitu wszystkie problemy aplikacji są zawarte w jednym wdrożeniu. Wszystko, od interfejsu użytkownika do wywołań bazy danych znajduje się w tej samej bazie kodu.

![Architektura monolitu](./media/monolith-architecture.png)

Podejście monolitu ma kilka zalet. Często łatwo jest ściągnąć jedną bazę kodu i rozpocząć pracę. Czas zwiększania czasu może być krótszy, a tworzenie środowisk testowych jest tak proste, jak dostarczenie nowej kopii. Monolit może być zaprojektowany tak, aby zawierał wiele komponentów i aplikacji.

Niestety, wzór monolitu ma tendencję do rozkładu na dużą skalę. Główne wady podejścia monolitu obejmują:

- Trudne do pracy równolegle w tej samej bazie kodu.
- Wszelkie zmiany, bez względu na to, jak trywialne, wymaga wdrożenia nowej wersji całej aplikacji.
- Refaktoryzacja potencjalnie wpływa na całą aplikację.
- Często jedynym rozwiązaniem do skalowania jest tworzenie wielu, intensywnie zaopatrzony kopii monolitu.
- Wraz z rozwojem systemów lub innymi systemami integracja może być trudna.
- Może być trudne do przetestowania ze względu na konieczność skonfigurowania całego monolitu.
- Ponowne użycie kodu jest trudne i często inne aplikacje kończą się własnymi kopiami kodu.

Wiele firm patrzy na chmurę jako okazję do migracji aplikacji monolitu, a jednocześnie refaktoryzacji ich do bardziej użytecznych wzorców. Często można wyrwać poszczególne aplikacje i składniki, aby umożliwić ich utrzymanie, wdrożenie i skalowanie oddzielnie.

## <a name="n-layer-applications"></a>Aplikacje wielowarstwowe

Logika aplikacji n-warstwowej partycji do określonych warstw. Najczęstsze warstwy to:

- Interfejs użytkownika
- Logika biznesowa
- Dostęp do danych

Inne warstwy mogą obejmować pośredniczenie, przetwarzanie wsadowe i interfejs API. Ważne jest, aby pamiętać, że warstwy są logiczne. Mimo że są one opracowane w izolacji, wszystkie mogą być wdrażane na tej samej platformie docelowej.

![Architektura n-warstwowa](./media/n-layer-architecture.png)

Podejście N-Layer ma kilka zalet, w tym:

- Refaktoryzacja jest izolowana do warstwy.
- Zespoły mogą niezależnie tworzyć, testować, wdrażać i obsługiwać oddzielne warstwy.
- Warstwy można wymieniać, na przykład warstwa danych może uzyskać dostęp do wielu baz danych bez konieczności wprowadzania zmian w warstwie interfejsu użytkownika.

Bezserwerowy może służyć do zaimplementowania jednej lub więcej warstw.

## <a name="microservices"></a>Mikrousługi

**[Architektury mikrousług](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** zawierają typowe cechy, które obejmują:

- Aplikacje składają się z kilku małych usług.
- Każda usługa jest uruchamiana w swoim własnym procesie.
- Usługi są wyrównane wokół domen biznesowych.
- Usługi komunikują się za pośrednictwem lekkich interfejsów API, zazwyczaj przy użyciu protokołu HTTP jako transportu.
- Usługi można wdrażać i uaktualniać niezależnie.
- Usługi nie są zależne od pojedynczego magazynu danych.
- System został zaprojektowany z myślą o awarii, a aplikacja może nadal działać nawet wtedy, gdy niektóre usługi zawiodą.

Mikrousługi nie muszą wzajemnie się wykluczać z innymi metodami architektury. Na przykład architektura N-Tier może używać mikrousług dla warstwy środkowej. Istnieje również możliwość implementowania mikrousług na różne sposoby, od katalogów wirtualnych na hostach usług IIS do kontenerów. Właściwości mikrousług sprawiają, że są one szczególnie idealne dla implementacji bezużycia serwera.

![Architektura mikrousług](./media/microservices-architecture.png)

Zalety architektury mikrousług obejmują:

- Refaktoryzacja jest często izolowana do pojedynczej usługi.
- Usługi mogą być uaktualniane niezależnie od siebie.
- Odporność i elastyczność można dostosować do wymagań poszczególnych usług.
- Programistyka może odbywać się równolegle między różnymi zespołami i platformami.
- Łatwiej jest napisać kompleksowe testy dla izolowanych usług.

Mikrousługi pochodzą z własnych wyzwań, w tym:

- Określanie, jakie usługi są dostępne i jak do nich zadzwonić.
- Zarządzanie cyklem życia usług.
- Zrozumienie, jak usługi pasują do siebie w całej aplikacji.
- Pełne testowanie systemu połączeń wykonanych w różnych usługach.

Ostatecznie istnieją rozwiązania, aby sprostać wszystkim tym wyzwaniom, w tym wykorzystanie zalet bezserwerowych, które zostały omówione później.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](architecture-deployment-approaches.md)
