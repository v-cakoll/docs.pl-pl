---
title: Podejścia do architektury — aplikacje bezserwerowe
description: Wprowadzenie do architektury podejścia do tworzenia aplikacji korporacyjnych opartych na chmurze, od architektur N-warstwowych do bezserwerowych.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522899"
---
# <a name="architecture-approaches"></a>Podejścia do architektury

Zrozumienie istniejących podejścia do tworzenia aplikacji dla przedsiębiorstw pomaga wyjaśnić rolę odgrywaną przez serwer. Istnieje wiele metod i wzorców, które są rozbudowane w trakcie tworzenia oprogramowania, a wszystkie mają własne zalety i wady. W wielu przypadkach ostateczne rozwiązanie nie może polegać na wyborze jednego podejścia, ale może zintegrować kilka metod. Scenariusze migracji często obejmują zmianę z jednej architektury do innej za pośrednictwem podejścia hybrydowego.

Ten rozdział zawiera omówienie wzorców architektury logicznej i fizycznej dla aplikacji dla przedsiębiorstw.

## <a name="architecture-patterns"></a>Wzorce architektury

Nowoczesne aplikacje biznesowe są zgodne z różnymi wzorcami architektury. Ta sekcja reprezentuje przegląd wspólnych wzorców. Wzorce wymienione w tym miejscu nie zawsze są najlepszym rozwiązaniem, ale ilustrują różne podejścia.

Aby uzyskać więcej informacji, zobacz [Przewodnik po architekturze aplikacji platformy Azure](https://docs.microsoft.com/azure/architecture/guide/).

## <a name="monoliths"></a>Monolitów

Wiele aplikacji firmowych jest zgodnych ze wzorcem monolitu. Starsze aplikacje są często implementowane jako monolitów. We wzorcu monolitu wszystkie problemy dotyczące aplikacji są zawarte w jednym wdrożeniu. Wszystkie elementy z interfejsu użytkownika do wywołań bazy danych są zawarte w tej samej bazie kodu.

![Architektura monolitu](./media/monolith-architecture.png)

Istnieje kilka zalet podejścia do monolitu. Często można łatwo ściągnąć pojedynczy kod podstawowy i rozpocząć pracę. Czas zwiększania obciążenia może być mniejszy i tworzenie środowisk testowych jest proste, co zapewnia nową kopię. Monolitu może być zaprojektowana tak, aby obejmowała wiele składników i aplikacji.

Niestety, wzorzec monolituu może być podzielony na dużą skalę. Główne wady podejścia monolitu obejmują:

- Trudne równoległe działanie w tej samej bazie kodu.
- Wszelkie zmiany, niezależnie od tego, jak uproszczony, wymagają wdrożenia nowej wersji całej aplikacji.
- Refaktoryzacja może mieć wpływ na całą aplikację.
- Często jedyne rozwiązanie do skalowania polega na utworzeniu wielu kopii monolituych intensywnie korzystających z zasobów.
- Po rozwinięciu systemu lub uzyskaniu innych systemów integracja może być trudna.
- Może być trudne do przetestowania ze względu na konieczność skonfigurowania całego monolitu.
- Ponowne użycie kodu jest wyzwaniem i często inne aplikacje kończą swoje własne kopie kodu.

Wiele firm przeszukuje chmurę jako okazję do migracji aplikacji monolitu i w tym samym czasie refaktoryzacji ich do bardziej użytecznych wzorców. Często należy rozdzielić poszczególne aplikacje i składniki, aby umożliwić ich utrzymanie, wdrożenie i skalowanie osobno.

## <a name="n-layer-applications"></a>Aplikacje N-warstwowe

Warstwa aplikacji N-warstwowa partycji aplikacji w określonych warstwach. Najbardziej typowe warstwy obejmują:

- Interfejs użytkownika
- Logika biznesowa
- Dostęp do danych

Inne warstwy mogą obejmować oprogramowanie pośredniczące, przetwarzanie wsadowe i interfejs API. Ważne jest, aby zauważyć, że warstwy są logiczne. Mimo że są one opracowywane jako izolacja, mogą zostać wdrożone na tej samej platformie docelowej.

![Architektura N-warstwowa](./media/n-layer-architecture.png)

Istnieje kilka zalet podejścia do warstwy N, w tym:

- Refaktoryzacja jest izolowana dla warstwy.
- Zespoły mogą niezależnie kompilować, testować, wdrażać i konserwować oddzielne warstwy.
- Warstwy mogą być wymieniane, na przykład warstwa danych może uzyskać dostęp do wielu baz danych bez konieczności wprowadzania zmian w warstwie interfejsu użytkownika.

W celu zaimplementowania jednej lub kilku warstw może być używana bezserwerowa.

## <a name="microservices"></a>Mikrousług

Architektury **[mikrousług](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** zawierają wspólne cechy, które obejmują:

- Aplikacje składają się z kilku małych usług.
- Każda usługa jest uruchamiana we własnym procesie.
- Usługi są wyrównane do domeny biznesowej.
- Usługi komunikują się za pośrednictwem lekkich interfejsów API, zazwyczaj przy użyciu protokołu HTTP jako transportu.
- Usługi mogą być wdrażane i uaktualniane niezależnie.
- Usługi nie zależą od pojedynczego magazynu danych.
- System został zaprojektowany z myślą o awarii, a aplikacja może być uruchomiona nawet w przypadku awarii niektórych usług.

Mikrousługi nie muszą się wzajemnie wykluczać z innych metod architektury. Na przykład architektura N-warstwowa może korzystać z mikrousług dla warstwy środkowej. Istnieje również możliwość zaimplementowania mikrousług na różne sposoby, od katalogów wirtualnych na hostach IIS do kontenerów. Charakterystyki mikrousług sprawiają, że są one szczególnie idealne dla implementacji bezserwerowych.

![Architektura mikrousług](./media/microservices-architecture.png)

W architekturze mikrousług są dostępne:

- Refaktoryzacja jest często izolowana dla jednej usługi.
- Usługi można uaktualnić niezależnie od siebie.
- Odporność i elastyczność można dostrajać do wymagań poszczególnych usług.
- Programowanie może wystąpić równolegle między różnymi zespołami i platformami.
- Łatwiej jest pisać kompleksowe testy dla usług izolowanych.

Mikrousługi są związane z własnymi wyzwaniami, w tym:

- Określanie, które usługi są dostępne i jak je wywoływać.
- Zarządzanie cyklem życia usług.
- Zrozumienie, w jaki sposób usługi mieszczą się w ogólnej aplikacji.
- Pełne testowanie systemu wywołań wykonanych między różnymi usługami.

Ostatecznie istnieją rozwiązania, które należy spełnić przed wszystkimi tymi wyzwaniami, w tym w przypadku korzystania z zalet bezserwerowych, które zostały omówione w dalszej części.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[dalej](architecture-deployment-approaches.md)
