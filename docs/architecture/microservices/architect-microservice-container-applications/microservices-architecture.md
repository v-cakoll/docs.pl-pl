---
title: Architektura mikrousług
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Widok 30,000 metrów architektury mikrousług.
ms.date: 09/20/2018
ms.openlocfilehash: d1c58d218be9e5f8c0ae8ae732f9bdd06674a2c2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834385"
---
# <a name="microservices-architecture"></a>Architektura mikrousług

Jako że nazwa oznacza, architektura mikrousług jest podejściem do tworzenia aplikacji serwera jako zestawu małych usług. Oznacza to, że architektura mikrousług jest głównie ukierunkowana na zaplecza, chociaż podejście jest również używane na potrzeby frontonu. Każda usługa jest uruchamiana we własnym procesie i komunikuje się z innymi procesami przy użyciu protokołów takich jak HTTP/HTTPS, WebSockets lub [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Każda mikrousługa implementuje określoną kompleksową domenę lub możliwość biznesową w ramach określonej granicy kontekstu, a każdy z nich musi być opracowywany autonomicznie i może być wdrażany niezależnie. Na koniec każda mikrousługa powinna być własnością powiązanego modelu danych domeny i logiki domeny (z niezależnym i zdecentralizowanym zarządzaniem danymi) i może opierać się na różnych technologiach magazynowania danych (SQL, NoSQL) i różnych językach programowania.

Jakiego rozmiaru powinna być mikrousługa? Podczas tworzenia mikrousługi rozmiar nie powinien być ważnym punktem. Zamiast tego należy utworzyć luźno powiązane usługi, aby zapewnić autonomię rozwoju, wdrażania i skalowania dla każdej usługi. Oczywiście w przypadku identyfikowania i projektowania mikrousług należy próbować je tak długo, jak to możliwe, dopóki nie masz zbyt wielu bezpośrednich zależności z innymi mikrousługami. Ważniejsze niż rozmiar mikrousługi jest wewnętrzną spójnością, którą musi mieć, oraz jej niezależność od innych usług.

Dlaczego architektura mikrousług? Krótko mówiąc, zapewnia elastyczność długoterminową. Mikrousługi zapewniają lepszą łatwość utrzymania w złożonych, dużych i wysoko skalowalnych systemach, umożliwiając tworzenie aplikacji na podstawie wielu niezależnie wdrażanych usług, które mają szczegółowe i niezależne cykle życia.

Dodatkową korzyścią jest możliwość niezależnego skalowania mikrousług. Zamiast korzystać z pojedynczej monolitycznej aplikacji, którą trzeba skalować w poziomie jako jednostki, można zamiast tego skalować konkretne mikrousługi. Dzięki temu można skalować tylko obszar funkcjonalny wymagający większej mocy obliczeniowej lub przepustowości sieci, aby obsługiwać zapotrzebowanie, zamiast skalować inne obszary aplikacji, które nie muszą być skalowane. Oznacza to oszczędność kosztów, ponieważ potrzeba mniej sprzętu.

![Diagram różnic między dwoma metodami wdrażania.](./media/microservices-architecture/monolith-deployment-vs-microservice-approach.png)

**Rysunek 4-6**. Niemonolityczne wdrożenie a podejście mikrousług

Jak pokazano na rysunku 4-6, w tradycyjnych podejścia monolitycznego aplikacja skaluje się przez klonowanie całej aplikacji na kilku serwerach/maszynach wirtualnych. W podejściu mikrousług funkcje są segregowane w mniejszych usługach, więc każda usługa może być skalowana niezależnie. Podejście mikrousługowe umożliwia zmiany Agile i szybką iterację każdej mikrousługi, ponieważ można zmienić konkretne, małe obszary złożonych, dużych i skalowalnych aplikacji.

Projektowanie szczegółowych aplikacji opartych na mikrousługach pozwala na ciągłą integrację i ciągłe dostarczanie. Przyspiesza również dostarczanie nowych funkcji do aplikacji. Szczegółowe składanie aplikacji umożliwia również uruchamianie i testowanie mikrousług w izolacji oraz niezależne programowanie z zachowaniem wyraźnych umów między nimi. Dopóki nie zmienisz interfejsów lub kontraktów, możesz zmienić wewnętrzną implementację dowolnej mikrousługi lub dodać nowe funkcje bez przerywania innych mikrousług.

Poniżej przedstawiono ważne aspekty umożliwiające pomyślne przechodzenie do produkcji przy użyciu systemu opartego na mikrousługach:

- Monitorowanie i sprawdzanie kondycji usług i infrastruktury.

- Skalowalna infrastruktura dla usług (czyli chmur i koordynatorów).

- Projektowanie i wdrażanie zabezpieczeń na wielu poziomach: uwierzytelnianie, autoryzacja, zarządzanie kluczami tajnymi, Bezpieczna komunikacja itp.

- Szybkie dostarczanie aplikacji, zwykle z różnymi zespołami skoncentrowanymi na różnych mikrousługach.

- DevOps i infrastruktura ciągłej integracji i ciągłego wdrażania.

Z tych wskazówek tylko pierwsze trzy zostały omówione lub wprowadzone w tym przewodniku. Ostatnie dwa punkty, które są związane z cyklem życia aplikacji, zostały omówione w dodatkowym [cyklu życia aplikacji platformy Docker z platformą i narzędziami firmy Microsoft](https://aka.ms/dockerlifecycleebook) .

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Oznacz Russinovich. Mikrousługi: obroty aplikacji obsługiwane przez @no__t w chmurze**— 1
  <https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/>

- **Fowlera Martin. Mikrousługi** \
  <https://www.martinfowler.com/articles/microservices.html>

- **Fowlera Martin. Wymagania wstępne mikrousług** \
  <https://martinfowler.com/bliki/MicroservicePrerequisites.html>

- **Jimmy Nilsson. Przetwarzanie w chmurze fragmentu** \
  <https://www.infoq.com/articles/CCC-Jimmy-Nilsson>

- **Cesar de La Torre. Cykl życia aplikacji platformy Docker w kontenerze z platformą i narzędziami firmy Microsoft (do** pobrania książek elektronicznych) \
  <https://aka.ms/dockerlifecycleebook>

>[!div class="step-by-step"]
>[Poprzedni](service-oriented-architecture.md)
>[dalej](data-sovereignty-per-microservice.md)
