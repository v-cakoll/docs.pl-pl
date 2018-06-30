---
title: Projektowanie mikrousługi warstwy aplikacji i interfejsu API sieci Web
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Projektowanie mikrousługi warstwy aplikacji i interfejsu API sieci Web
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: e5c7e0acb0496aebce4d9cbe8cb51ced0c7166a2
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106609"
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a>Projektowanie mikrousługi warstwy aplikacji i interfejsu API sieci Web

## <a name="using-solid-principles-and-dependency-injection"></a>Za pomocą stałych zasad i iniekcja zależności

STAŁE zasady są krytyczne technik w celu można użyć w dowolnej aplikacji modern i strategicznych, takich jak tworzenie mikrousługi wzorami DDD. STAŁE jest skrótem tej grupy pięć podstawowych zasad:

-   Pojedynczy zasady odpowiedzialności

-   Zasada otwarty/zamknięty

-   Zasada podstawienia Liskov

-   Zasada podział — interfejs

-   Zasada odwracanie zależności

STAŁE są dotyczące sposobu projektowania aplikacji lub mikrousługi wewnętrzny warstwy i oddzielenie zależności między nimi. Nie jest powiązany z domeną, ale do projektu technicznego aplikacji. Końcowe zasady zasady odwracanie zależności (Podpisane) umożliwia oddzielana od pozostałej części warstwy, dzięki czemu lepiej implementacji rozdzielonymi warstw DDD warstwę infrastruktury.

Podpisane jest jednym ze sposobów realizacji zasady odwracanie zależności. To technika osiągnięcia luźne powiązanie między obiektów i ich zależności. Zamiast bezpośrednio uruchamianiu współpracownicy lub przy użyciu statycznych odwołań, obiekty, które klasy wymaga, aby jego akcje są dostarczony do (lub "wstrzykuje") klasy. W większości przypadków klasy będzie zadeklarować ich zależności za pomocą ich konstruktora, dzięki czemu mogą być zgodna z zasadą jawne zależności. Podpisane zazwyczaj opiera się na określonym kontenery Inwersja kontroli (Inwersja kontroli). Platformy ASP.NET Core udostępnia prosty wbudowanych kontenera IoC, ale można również użyć kontenera IoC Ulubione, takich jak Autofac lub Ninject.

Wykonując stałych zasad klas będzie zazwyczaj naturalnie za mały, dobrze factored i łatwo przetestowane. Ale jak należy znać, jeśli zbyt wiele zależności są są wstrzykiwane do klas? Jeśli używasz Podpisane za pomocą konstruktora będzie łatwo wykryć który analizując tylko z liczbą parametrów dla Twojego konstruktora. Jeśli istnieją zbyt wiele zależności, zwykle jest to znak ( [kodu zapachu](http://deviq.com/code-smells/)) próbuje zrobić zbyt dużo klasy i prawdopodobnie narusza zasady pojedynczego odpowiedzialności.

Może upłynąć innego przewodnik szczegółowo stałe. W związku z tym w tym przewodniku wymaga minimalnej znajomości tych tematów.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **STAŁE: Zasady podstawowych Obiektowo**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)

-   **Inwersja kontroli kontenerów i wzorzec iniekcji zależności**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)

-   **Steve Smith. Nowe jest sklejki**
    [*https://ardalis.com/new-is-glue*](https://ardalis.com/new-is-glue)


>[!div class="step-by-step"]
[Poprzednie](nosql-database-persistence-infrastructure.md)
[dalej](microservice-application-layer-implementation-web-api.md)
