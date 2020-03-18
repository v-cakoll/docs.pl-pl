---
title: Architektura mikrousług
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | 30.000 stóp widok architektury mikrousług.
ms.date: 09/20/2018
ms.openlocfilehash: d1c58d218be9e5f8c0ae8ae732f9bdd06674a2c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834385"
---
# <a name="microservices-architecture"></a>Architektura mikrousług

Jak sama nazwa wskazuje architektura mikrousług jest podejście do tworzenia aplikacji serwera jako zestaw małych usług. Oznacza to, że architektura mikrousług jest zorientowana głównie na zapleczu, mimo że podejście jest również używane dla frontonu. Każda usługa jest uruchamiana we własnym procesie i komunikuje się z innymi procesami przy użyciu protokołów, takich jak HTTP/HTTPS, WebSockets lub [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Każda mikrousługa implementuje określonej end-to-end domeny lub możliwości biznesowych w ramach określonej granicy kontekstu i każdy musi być opracowany autonomicznie i być wdrażalne niezależnie. Na koniec każda mikrousługa powinna być właścicielem powiązanego modelu danych domeny i logiki domeny (suwerenność i zdecentralizowane zarządzanie danymi) i może być oparta na różnych technologiach przechowywania danych (SQL, NoSQL) i różnych językach programowania.

Jaki rozmiar powinien mieć mikrousługi? Podczas opracowywania mikrousługi rozmiar nie powinien być ważnym punktem. Zamiast tego ważnym punktem powinno być tworzenie luźno powiązanych usług, dzięki czemu masz autonomię rozwoju, wdrażania i skalowania dla każdej usługi. Oczywiście podczas identyfikowania i projektowania mikrousług, należy spróbować uczynić je tak małe, jak to możliwe, tak długo, jak nie masz zbyt wiele bezpośrednich zależności z innymi mikrousługami. Ważniejsze niż rozmiar mikrousługi jest spójność wewnętrzna musi mieć i jego niezależności od innych usług.

Dlaczego architektura mikrousług? Krótko mówiąc, zapewnia długoterminową zwinność. Mikrousługi umożliwiają lepszą łatwość konserwacji w złożonych, dużych i wysoce skalowalnych systemach, umożliwiając tworzenie aplikacji na podstawie wielu niezależnie wdrażanych usług, z których każdy ma szczegółowe i autonomiczne cykle życia.

Jako dodatkową korzyść mikrousług można skalować w sposób niezależny. Zamiast jednej aplikacji monolityczne, które należy skalować w sposób skalowany w sposób skalowany jako jednostka, zamiast tego można skalować w sposób określony mikrousług. W ten sposób można skalować tylko obszar funkcjonalny, który wymaga większej mocy obliczeniowej lub przepustowości sieci do obsługi popytu, zamiast skalować inne obszary aplikacji, które nie muszą być skalowane. Oznacza to oszczędność kosztów, ponieważ potrzebujesz mniej sprzętu.

![Diagram różnic między dwiema metodami wdrażania.](./media/microservices-architecture/monolith-deployment-vs-microservice-approach.png)

**Rysunek 4-6**. Monolityczne wdrożenie a podejście mikrousług

Jak pokazuje rysunek 4-6, w tradycyjnym podejściu monolitycznym aplikacja skaluje się, klonując całą aplikację na kilku serwerach/maszynach wirtualnych. W podejściu mikrousług funkcjonalność jest segregowana w mniejszych usługach, dzięki czemu każda usługa może skalować niezależnie. Podejście mikrousług umożliwia elastyczne zmiany i szybką iterację każdej mikrousługi, ponieważ można zmienić konkretne, małe obszary złożonych, dużych i skalowalnych aplikacji.

Projektowanie precyzyjnych aplikacji opartych na mikrousługach umożliwia ciągłą integrację i ciągłe dostarczanie. Przyspiesza również dostarczanie nowych funkcji do aplikacji. Szczegółowy skład aplikacji umożliwia również uruchamianie i testowanie mikrousług w izolacji oraz rozwijanie ich autonomicznie przy zachowaniu wyraźnych kontraktów między nimi. Tak długo, jak nie zmienisz interfejsów lub kontraktów, można zmienić wewnętrzną implementację dowolnej mikrousługi lub dodać nowe funkcje bez przerywania innych mikrousług.

Oto ważne aspekty, aby umożliwić powodzenie w przechodzeniu do produkcji z systemem opartym na mikrousługach:

- Monitorowanie i kontrole stanu usług i infrastruktury.

- Skalowalna infrastruktura dla usług (czyli chmury i koordynatorów).

- Projektowanie i wdrażanie zabezpieczeń na wielu poziomach: uwierzytelnianie, autoryzacja, zarządzanie wtajemnicami, bezpieczna komunikacja itp.

- Szybkie dostarczanie aplikacji, zwykle z różnych zespołów koncentrujących się na różnych mikrousług.

- DevOps i CI/CD praktyk i infrastruktury.

Z nich tylko pierwsze trzy są objęte lub wprowadzone w tym przewodniku. Ostatnie dwa punkty, które są związane z cyklem życia aplikacji, są objęte dodatkowym [cyklem życia aplikacji konteneryzowanych platformy Docker z platformą Microsoft Platform i narzędziami](https://aka.ms/dockerlifecycleebook) e-book.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Marek Russinovich. Mikrousługi: rewolucja aplikacji obsługiwana przez chmurę** \
  <https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/>

- **Martin Fowler. Mikrousług** \
  <https://www.martinfowler.com/articles/microservices.html>

- **Martin Fowler. Wymagania wstępne dotyczące mikrousług** \
  <https://martinfowler.com/bliki/MicroservicePrerequisites.html>

- **Jimmy Nilsson. Przetwarzanie w chmurze w błocie** \
  <https://www.infoq.com/articles/CCC-Jimmy-Nilsson>

- **Cesar de la Torre. Cykl życia aplikacji doplatformy kontenerowej z platformą i narzędziami firmy Microsoft** (e-book do pobrania) \
  <https://aka.ms/dockerlifecycleebook>

>[!div class="step-by-step"]
>[Poprzedni](service-oriented-architecture.md)
>[następny](data-sovereignty-per-microservice.md)
