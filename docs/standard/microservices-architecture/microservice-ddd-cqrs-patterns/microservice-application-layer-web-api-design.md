---
title: Projektowanie warstwy aplikacji mikrousług i internetowego interfejsu API
description: 'Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | BRIEF: wzmianka stałych zasad projektowania warstwy aplikacji.'
ms.date: 10/08/2018
ms.openlocfilehash: 3c3b9f74e76e01deafa1f97de5d3250d57716014
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639506"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a>Projektowanie warstwy aplikacji mikrousług i internetowego interfejsu API

## <a name="use-solid-principles-and-dependency-injection"></a>Użyj stałych zasad i wstrzykiwanie zależności

STAŁE zasady są krytyczne technik, które ma być używany w dowolnej aplikacji nowoczesnych i o kluczowym znaczeniu, takich jak opracowywanie mikrousług przy użyciu wzorców DDD. STAŁE jest skrótem tej grupy pięciu podstawowych zasad:

- Zasady pojedynczej odpowiedzialności

- Zasada otwarty/zamknięty

- Zasada podstawienia Liskov

- Zasady podziału na interfejsie

- Zasada odwrócenie zależności

Więcej na temat sposobu projektowania aplikacji lub mikrousług wewnętrznego warstwy oraz oddzielenie zależności między nimi jest pełny. Nie jest powiązany z domeną, ale projekt techniczny aplikacji. Ostateczne zasady, zasady odwrócenie zależności, można rozdzielić warstwy infrastruktury od reszty warstw, co pozwala lepiej wdrożenia rozdzielonego warstw DDD.

Wstrzykiwanie zależności (DI) jest jednym ze sposobów, aby zaimplementować zasady odwrócenie zależności. Jest to technika do osiągnięcia luźne powiązanie między obiektami i ich zależności. Zamiast bezpośrednio wystąpienia współpracowników lub przy użyciu odwołań statycznych, (które przy użyciu nowego...), obiekty, które klasy potrzebuje, aby wykonać działania są udostępniane (lub "wstrzykuje") klasy. W większości przypadków klasy uzna ich zależności za pomocą ich konstruktora, umożliwiając im postępuj zgodnie z zasadą jawne zależności. Wstrzykiwanie zależności opiera się zwykle w określonych kontenerach Inwersja kontroli (IoC). Platforma ASP.NET Core udostępnia prostego, wbudowanego kontenera IoC, ale można również użyć kontenera IoC Ulubione, takich jak Autofac lub Ninject.

Postępując zgodnie z zasadami stałych, klas będą zwykle naturalnie za małe, dobrze uwarunkowaną i łatwo przetestowane. Ale jak należy znać, jeśli zbyt wiele zależności są są wprowadzane w Twoich zajęciach? Jeśli używasz DI za pośrednictwem konstruktora będzie łatwe do wykrycia, patrząc tylko na liczbę parametrów dla konstruktora. Jeśli istnieje zbyt wiele zależności, zwykle jest to znak ( [kodu zapachu](https://deviq.com/code-smells/)) próbuje wykonać zbyt dużo klasy i prawdopodobnie narusza zasadę pojedynczej odpowiedzialności.

Zajęłoby innego przewodnika, aby omówić stałe. W związku z tym ten przewodnik wymaga posiadania minimalnej znajomości tych tematów.

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **SOLID: Obiektowo podstawowych zasad** \
  <https://deviq.com/solid/>

- **Inwersja kontroli kontenerów i wzorzec wstrzykiwanie zależności** \
  <https://martinfowler.com/articles/injection.html>

- **Steve Smith. Nowością jest pośredniczącego** \
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> [Poprzednie](nosql-database-persistence-infrastructure.md)
> [dalej](microservice-application-layer-implementation-web-api.md)
