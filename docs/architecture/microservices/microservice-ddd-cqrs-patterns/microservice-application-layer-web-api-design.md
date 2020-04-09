---
title: Projektowanie warstwy aplikacji mikrousług i internetowego interfejsu API
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Krótka wzmianka o zasadach SOLID do projektowania warstwy aplikacji.
ms.date: 10/08/2018
ms.openlocfilehash: 491aa7bd90910c7f6c1d0ab56edfe0ae057ca006
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988456"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a>Projektowanie warstwy aplikacji mikrousług i interfejsu API sieci Web

## <a name="use-solid-principles-and-dependency-injection"></a>Użyj zasad SOLID i iniekcji zależności

Zasady SOLID są krytyczne techniki, które mają być używane w każdej nowoczesnej i krytycznej aplikacji, takich jak tworzenie mikrousługi z wzorców DDD. SOLID to akronim, który grupuje pięć podstawowych zasad:

- Zasada jednolitej odpowiedzialności

- Zasada otwarcia/zamknięcia

- Zasada zastępowania Liskova

- Zasada segregacji interfejsu

- Zasada inwersji zależności

SOLID jest bardziej o tym, jak projektować warstwy wewnętrzne aplikacji lub mikrousług i o oddzielenie zależności między nimi. Nie jest to związane z domeną, ale z projektem technicznym aplikacji. Ostateczna zasada, zasada Inwersji zależności, pozwala na oddzielenie warstwy infrastruktury od pozostałych warstw, co pozwala na lepszą implementację oddzielonych warstw DDD.

Iniekcja zależności (DI) jest jednym ze sposobów zaimplementowania zasady inwersji zależności. Jest to technika osiągnięcia luźnego sprzężenia między obiektami i ich zależnościami. Zamiast bezpośrednio tworzenia wystąpienia współpracowników lub przy użyciu odwołań statycznych (czyli przy użyciu nowych ...), obiekty, które klasa potrzebuje w celu wykonania jego akcji są dostarczane do (lub "wstrzykuje się do") klasy. Najczęściej klasy deklaruje ich zależności za pośrednictwem ich konstruktora, umożliwiając im przestrzeganie zasady jawne zależności. Iniekcja zależności jest zwykle oparta na określonych kontenerach inwersji kontroli (IoC). ASP.NET Core zapewnia prosty wbudowany kontener IoC, ale można również użyć ulubionego kontenera IoC, takiego jak Autofac lub Ninject.

Zgodnie z zasadami SOLID, twoje klasy będą naturalnie małe, dobrze uwzględnione i łatwo przetestowane. Ale skąd wiesz, czy zbyt wiele zależności są wstrzykiwane do klas? Jeśli używasz DI za pośrednictwem konstruktora, będzie łatwo wykryć, że po prostu patrząc na liczbę parametrów dla konstruktora. Jeśli istnieje zbyt wiele zależności, jest to zazwyczaj znak [(zapach kodu),](https://deviq.com/code-smells/)że klasa próbuje zrobić zbyt wiele i prawdopodobnie narusza zasadę pojedynczej odpowiedzialności.

Zajęłoby inny przewodnik, aby pokryć SOLID w szczegółach. W związku z tym ten przewodnik wymaga, aby mieć tylko minimalną wiedzę na te tematy.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **SOLID: Podstawowe zasady OOP** \
  <https://deviq.com/solid/>

- **Inwersja kontenerów kontrolnych i wzorzec iniekcji zależności** \
  <https://martinfowler.com/articles/injection.html>

- **Steve Smith. Nowy jest klej** \
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> [Poprzedni](nosql-database-persistence-infrastructure.md)
> [następny](microservice-application-layer-implementation-web-api.md)
