---
title: Architektura mikrousług
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Widok 30.000 stopy architektury Mikrousług.
ms.date: 09/20/2018
ms.openlocfilehash: 3cf2a94140042d3cf76b5b63fe4e98638c56dbfe
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644843"
---
# <a name="microservices-architecture"></a>Architektura mikrousług

Jak wskazuje nazwa, architektura mikrousług jest podejście do kompilowania aplikacji serwera jako zestaw małych usług. Oznacza to, że architektura mikrousług jest zorientowany głównie na zaplecze, chociaż to podejście jest również używany fronton. Każda usługa jest uruchamiana we własnym procesie i komunikuje się z innymi procesami przy użyciu protokołów, takich jak HTTP/HTTPS, funkcja WebSockets, lub [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Każda mikrousługa implementuje określonej domeny end-to-end lub funkcję biznesową w obrębie granicy kontekstu, a każda musi być opracowana autonomicznie i być niezależnie do wdrożenia. Na koniec poszczególne mikrousługi powinny odpowiadać jej modelu danych pokrewne domeny i logika domeny (niezależność danych i zarządzania danymi zdecentralizowane) i mogą być oparte na różne technologie przechowywania danych (SQL, NoSQL) i w różnych językach programowania.

Rozmiar powinien być mikrousługi? Podczas tworzenia mikrousług, rozmiar nie powinien być istotne. Zamiast tego należy koniecznie zwrócić należy utworzyć luźno sprzężonych usług, więc trzeba autonomii programowania, wdrażania i skalowania dla każdej usługi. Oczywiście i projektowanie mikrousług, należy spróbować były tak małej, jak to możliwe tak długo, jak nie ma zbyt wiele zależności bezpośrednich za pomocą innych mikrousług. Ważniejsze niż rozmiar mikrousług jest to wewnętrzny spójności, który musi mieć oraz jego niezależność od innych usług.

Dlaczego architektura mikrousług? Krótko mówiąc zapewnia elastyczność długoterminowego. Mikrousługi Włącz lepsze łatwość konserwacji w złożonych, duże i wysoce skalowalnych systemów, umożliwiając tworzenie aplikacji na podstawie wielu usług niezależnie do wdrożenia, w których każdy może mieć cykle życia szczegółową i autonomicznych.

Jako dodatkowa korzyść mikrousługi można skalować niezależnie. Zamiast pojedynczej aplikacji monolitycznych, należy skalować jako jednostkę, można zamiast tego skalować określonych mikrousług. W ten sposób można skalować tylko obszar funkcjonalny, który wymaga więcej przetwarzania zasilania lub sieci przepustowość do obsługi żądanie, zamiast skalowania w poziomie innych obszarów aplikacji, które nie muszą być skalowane. Oznacza to oszczędności, ponieważ potrzebne mniejszą sprzętu.

![W tradycyjnych podejścia monolitycznego aplikacja jest skalowana przez Sklonowanie całej aplikacji w kilku serwerów/maszyn wirtualnych. W przypadku zastosowania podejścia mikrousług funkcje można podzielić w mniejszych usług, więc każdej usługi można skalować niezależnie.](./media/image6.png)

**Rysunek 4 – 6**. Monolityczny wdrożenia i podejście mikrousług

Jak pokazano na rysunku 4 – 6, podejście mikrousług umożliwia elastyczne zmian i iteracji szybkie poszczególne mikrousługi, ponieważ można zmienić określone, małych obszarów złożonych, duże i skalowalne aplikacje.

Tworzenie szczegółowych aplikacji mikrousług umożliwia ciągłą integrację i ciągłe dostarczanie rozwiązań. Przyspiesza również dostarczania nowych funkcji do aplikacji. Szczegółowych skład aplikacji umożliwia uruchamianie i testowanie mikrousług w izolacji i autonomicznie ewolucja przy zachowaniu wyczyść umów między nimi. Tak długo, jak nie zmieniaj interfejsy lub umowy, można zmienić wewnętrzną implementację wszystkie mikrousługi, lub Dodaj nowe funkcje bez przerywania innych mikrousług.

Poniżej przedstawiono ważne kwestie umożliwiające sukces w przejściem do środowiska produkcyjnego w systemie opartych na mikrousługach:

- Monitorowanie i kontrole kondycji usług i infrastruktury.

- Skalowalną infrastrukturę usługi (czyli chmury i koordynatorów).

- Bezpieczeństwo projektowania i implementacji, na różnych poziomach: uwierzytelnianie, autoryzacja, zarządzania wpisami tajnymi, bezpiecznej komunikacji, itp.

- Dostarczanie aplikacji szybkie, zwykle przy użyciu różnych zespołów, skupiając się na różnych mikrousług.

- Praktyki DevOps i ciągłej integracji/ciągłego Dostarczania i infrastruktury.

Z tych opcji tylko pierwsze trzy są objęte lub wprowadzone w tym przewodniku. Ostatnie dwa punkty, które są związane z cyklem życia aplikacji, są objęte dodatkowy [kontenerowych nimi Docker cyklem życia aplikacji za pomocą platformy firmy Microsoft i narzędzi](https://aka.ms/dockerlifecycleebook) książki elektronicznej.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Mark Russinovich. Mikrousługi: Rewolucja w aplikacjach obsługiwana przez chmurę** \
  <https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/>

- **Martin Fowler. Mikrousługi** \
  <https://www.martinfowler.com/articles/microservices.html>

- **Martin Fowler. Wymagania wstępne dotyczące Mikrousług** \
  <https://martinfowler.com/bliki/MicroservicePrerequisites.html>

- **Jimmy Nilsson. Chunk Cloud Computing** \
  <https://www.infoq.com/articles/CCC-Jimmy-Nilsson>

- **Torre'a de la Cesarowi. Kontenerowych nimi cykl życia aplikacji platformy Docker przy użyciu platformy firmy Microsoft i narzędzi** (do pobrania Książka elektroniczna) \
  <https://aka.ms/dockerlifecycleebook>

>[!div class="step-by-step"]
>[Poprzednie](service-oriented-architecture.md)
>[dalej](data-sovereignty-per-microservice.md)
