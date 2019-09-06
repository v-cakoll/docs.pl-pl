---
title: Projektowanie warstwy aplikacji mikrousług i internetowego interfejsu API
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Krótkie informacje o PEŁNYch zasadach projektowania warstwy aplikacji.
ms.date: 10/08/2018
ms.openlocfilehash: 3c3b9f74e76e01deafa1f97de5d3250d57716014
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296739"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a>Projektowanie warstwy aplikacji mikrousług i internetowego interfejsu API

## <a name="use-solid-principles-and-dependency-injection"></a>Korzystanie z PEŁNYch zasad i iniekcji zależności

SOLIDNe zasady są technikami krytycznymi, które mają być używane w dowolnej nowoczesnej i o znaczeniu strategicznym, takich jak tworzenie mikrousług za pomocą wzorów DDD. SOLID to akronim, który grupuje pięć podstawowych zasad:

- Reguła pojedynczego odpowiedzialności

- Zasada Otwórz/zamknięty

- Zasada podstawienia Liskov

- Zasada segregowania interfejsu

- Zasada niewersji zależności

W pełni zawarto więcej informacji o projektowaniu aplikacji lub mikrousług wewnętrznych warstw oraz o rozdzieleniu zależności między nimi. Nie jest on powiązany z domeną, ale z projektem technicznym aplikacji. Zasada końcowa, reguła niezależna od wersji, umożliwia oddzielenie warstwy infrastruktury od reszty warstw, co pozwala na lepszą rozłączoną implementację warstw DDD.

Iniekcja zależności (DI) jest jednym ze sposobów implementacji zasady Inversion zależności. Jest to technika do osiągnięcia swobodnego sprzężenia między obiektami i ich zależnościami. Zamiast bezpośrednio tworzyć wystąpienia współpracowników lub używać odwołań statycznych (to jest przy użyciu nowego...), obiekty, które są potrzebne do wykonania swoich akcji (lub "wstrzykiwane do") klasy. Najczęściej klasy deklarują swoje zależności za pośrednictwem ich konstruktorów, umożliwiając im przestrzeganie zasad jawnych zależności. Iniekcja zależności jest zwykle oparta na określonych kontenerach IoC (Inversion of Control). ASP.NET Core udostępnia prosty wbudowany kontener IoC, ale można również użyć ulubionego kontenera IoC, takiego jak Autofac lub Ninject.

Dzięki zastosowaniu stałych zasad klasy mogą być w naturalny sposób bardzo małe, dobrze przygotowane i łatwe do przetestowania. Ale jak sprawdzić, czy zbyt wiele zależności jest wstrzykiwanych do klas? Jeśli używasz funkcji DI przez konstruktora, będzie ona łatwo wykrywać, sprawdzając, czy tylko liczba parametrów dla konstruktora. Jeśli istnieje zbyt wiele zależności, zwykle jest to znak ( [zapach kodu](https://deviq.com/code-smells/)), który Klasa próbuje wykonać zbyt wiele, i prawdopodobnie narusza zasadę pojedynczej odpowiedzialności.

Zajmiemy się kolejnymi szczegółami. W związku z tym ten przewodnik wymaga posiadania tylko minimalnej wiedzy o tych tematach.

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **WYPEŁNIONE Podstawowe zasady OOP** \
  <https://deviq.com/solid/>

- **Niewersja kontenerów sterowania i wzorzec iniekcji zależności** \
  <https://martinfowler.com/articles/injection.html>

- **Steve Smith. Nowy jest przyklejany** \
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> [Poprzedni](nosql-database-persistence-infrastructure.md)Następny
> [](microservice-application-layer-implementation-web-api.md)
