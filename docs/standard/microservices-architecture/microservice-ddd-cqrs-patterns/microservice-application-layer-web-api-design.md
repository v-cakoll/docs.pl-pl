---
title: "Projektowanie mikrousługi warstwy aplikacji i interfejsu API sieci Web"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Projektowanie mikrousługi warstwy aplikacji i interfejsu API sieci Web"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7509b470a30005dd48fa88eefa91f7ed241e4e09
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a>Projektowanie mikrousługi warstwy aplikacji i interfejsu API sieci Web

## <a name="using-solid-principles-and-dependency-injection"></a>Za pomocą stałych zasad i iniekcja zależności

STAŁE zasady są krytyczne technik w celu można użyć w dowolnej aplikacji modern i strategicznych, takich jak tworzenie mikrousługi wzorami DDD. STAŁE jest skrótem tej grupy pięć podstawowych zasad:

-   Pojedynczy zasady odpowiedzialności

-   Zasada otwarty/zamknięty

-   Zasada podstawienia Liskov

-   Odwracanie podział zasady

-   Zasada odwracanie zależności

STAŁE są dotyczące sposobu projektowania aplikacji lub mikrousługi wewnętrzny warstwy i oddzielenie zależności między nimi. Nie jest powiązany z domeną, ale do projektu technicznego aplikacji. Końcowe zasady zasady odwracanie zależności (Podpisane) umożliwia oddzielana od pozostałej części warstwy, dzięki czemu lepiej implementacji rozdzielonymi warstw DDD warstwę infrastruktury.

Podpisane jest jednym ze sposobów realizacji zasady odwracanie zależności. To technika osiągnięcia luźne powiązanie między obiektów i ich zależności. Zamiast bezpośrednio uruchamianiu współpracownicy lub przy użyciu statycznych odwołań, obiekty, które klasy wymaga, aby jego akcje są dostarczony do (lub "wstrzykuje") klasy. W większości przypadków klasy będzie zadeklarować ich zależności za pomocą ich konstruktora, dzięki czemu mogą być zgodna z zasadą jawne zależności. Podpisane zazwyczaj opiera się na określonym kontenery Inwersja kontroli (Inwersja kontroli). Platformy ASP.NET Core udostępnia prosty wbudowanych kontenera IoC, ale można również użyć kontenera IoC Ulubione, takich jak Autofac lub Ninject.

Wykonując stałych zasad klas będzie zazwyczaj naturalnie za mały, dobrze factored i łatwo przetestowane. Ale jak należy znać, jeśli zbyt wiele zależności są są wstrzykiwane do klas? Jeśli używasz Podpisane za pomocą konstruktora będzie łatwo wykryć który analizując tylko z liczbą parametrów dla Twojego konstruktora. Jeśli istnieją zbyt wiele zależności, zwykle jest to znak ( [kodu zapachu](http://deviq.com/code-smells/)) próbuje zrobić zbyt dużo klasy i prawdopodobnie narusza zasady pojedynczego odpowiedzialności.

Może upłynąć innego przewodnik szczegółowo stałe. W związku z tym w tym przewodniku wymaga minimalnej znajomości tych tematów.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **STAŁE: Obiektowo podstawowych zasad**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)

-   **Inwersja kontroli kontenerów i wzorzec iniekcji zależności**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)

-   **Steve Smith. Nowe jest sklejki**
    [*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)


>[!div class="step-by-step"]
[Poprzednie] (nosql-bazy danych — trwałości infrastructure.md) [dalej] (microservice-application-layer-implementation-web-api.md)
