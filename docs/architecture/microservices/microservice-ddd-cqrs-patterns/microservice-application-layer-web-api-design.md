---
title: Projektowanie warstwy aplikacji mikrousług i internetowego interfejsu API
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Krótka wzmianka o zasadach SOLID dotyczących projektowania warstwy aplikacji.
ms.date: 10/08/2018
ms.openlocfilehash: 3c3b9f74e76e01deafa1f97de5d3250d57716014
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296739"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a>Projektowanie warstwy aplikacji mikrousług i interfejsu API sieci Web

## <a name="use-solid-principles-and-dependency-injection"></a>Korzystanie z zasad SOLID i wstrzykiwanie zależności

Zasady SOLID są krytyczne techniki, które mają być używane w dowolnej aplikacji nowoczesnej i krytycznej, takich jak tworzenie mikrousługi z wzorców DDD. SOLID jest akronimem, który grupuje pięć podstawowych zasad:

- Zasada jednolitej odpowiedzialności

- Zasada otwarcia/zamknięcia

- Zasada zastąpienia Liskowa

- Zasada segregacji interfejsu

- Zasada inwersji zależności

SOLID jest bardziej o tym, jak projektować warstwy wewnętrzne aplikacji lub mikrousług i o oddzielenie zależności między nimi. Nie jest to związane z domeną, ale z projektem technicznym aplikacji. Ostatnia zasada, zasada odwrócenia zależności, pozwala na oddzielenie warstwy infrastruktury od reszty warstw, co pozwala na lepszą implementację warstw DDD.

Iniekcji zależności (DI) jest jednym ze sposobów zaimplementowania zasady inwersji zależności. Jest to technika osiągania luźne sprzężenie między obiektami i ich zależności. Zamiast bezpośrednio tworzenia wystąpień współpracowników lub przy użyciu odwołań statycznych (czyli przy użyciu new...), obiekty, które klasa potrzebuje w celu wykonania swoich działań są dostarczane do (lub "wstrzykuje się do") klasy. Najczęściej klasy deklarują swoje zależności za pośrednictwem ich konstruktora, umożliwiając im przestrzeganie zasady Jawne zależności. Iniekcji zależności jest zwykle na podstawie określonych inwersji kontroli (IoC) kontenerów. ASP.NET Core zapewnia prosty wbudowany pojemnik IoC, ale można również użyć ulubionego pojemnika IoC, takiego jak Autofac lub Ninject.

Postępując zgodnie z zasadami SOLID, twoje zajęcia będą naturalnie małe, dobrze wyfactored, i łatwo przetestowane. Ale skąd możesz wiedzieć, czy zbyt wiele zależności są wstrzykiwane do klas? Jeśli używasz DI za pośrednictwem konstruktora, będzie łatwo wykryć, że po prostu patrząc na liczbę parametrów dla konstruktora. Jeśli istnieje zbyt wiele zależności, jest to zazwyczaj znak [(zapach kodu),](https://deviq.com/code-smells/)że klasa próbuje zrobić zbyt wiele i prawdopodobnie narusza zasadę pojedynczej odpowiedzialności.

Zajęłoby to inny przewodnik na pokrycie SOLID w szczegółach. W związku z tym ten przewodnik wymaga mieć tylko minimalną wiedzę na te tematy.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **SOLID: Podstawowe zasady OOP** \
  <https://deviq.com/solid/>

- **Odwrócenie kontenerów kontroli i wzorzec iniekcji zależności** \
  <https://martinfowler.com/articles/injection.html>

- **Steve Smith. Nowością jest klej** \
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> [Poprzedni](nosql-database-persistence-infrastructure.md)
> [następny](microservice-application-layer-implementation-web-api.md)
