---
title: Tworzenie złożonego interfejsu użytkownika opartego na mikrousługach
description: Architektura Mikrousług jest nie tylko dla zaplecza. Uzyskaj obraz podglądu przy jego użyciu frontonu.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: b481a76052efdd1ce0da406732230d41701ac354
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464843"
---
# <a name="creating-composite-ui-based-on-microservices"></a>Tworzenie złożonego interfejsu użytkownika opartego na mikrousługach

Architektura Mikrousług często zaczyna się od danych obsługę po stronie serwera i logiki. Jednak bardziej zaawansowane podejście dotyczy projektowania interfejsu użytkownika oparta na mikrousługach, jak również aplikacji. Oznacza to, o złożonego interfejsu użytkownika generowany przez mikrousług, zamiast mikrousług na serwerze i po prostu aplikację kliencką monolityczne korzystanie z mikrousług. W przypadku tej metody mikrousług, które tworzysz może być wraz z zarówno logiki, jak i w formie wizualnej.

Rysunek 4-20 pokazuje prostszej metody tylko używania mikrousług z aplikacji klienckiej monolitycznego. Oczywiście może mieć usługi platformy ASP.NET MVC w zakresie od tworzenia kodu HTML i JavaScript. Rysunek jest uproszczeniem wyróżniający się, że masz jednego klienta (monolityczną) korzystanie z mikrousług, która po prostu skoncentrować się na logikę i dane, a nie na kształt interfejsu użytkownika (HTML i JavaScript) w interfejsie użytkownika.

![Interfejs użytkownika aplikacji monolitycznej nawiązywania połączenia z poszczególne mikrousługi.](./media/image20.png)

**Rysunek 4-20**. Interfejs użytkownika aplikacji monolitycznej korzystanie z mikrousług zaplecza

Z kolei złożonego interfejsu użytkownika jest dokładnie generowane i poprzez mikrousług, samodzielnie. Niektóre z mikrousług dysku visual kształt określonych obszarach interfejsu użytkownika. Główną różnicą jest składniki interfejsu użytkownika klienta (na przykład klasy TypeScript) oparte na szablonach, oraz ViewModel danych kształtowania-interfejsu użytkownika dla tych szablonów pochodzi z poszczególne mikrousługi.

W czasie uruchamiania aplikacji klienckich poszczególne składniki interfejsu użytkownika klienta (na przykład klasy TypeScript) rejestruje się przy użyciu mikrousług infrastruktury w stanie dostarczać modele widoków dla danego scenariusza. Mikrousługi zmienia kształt, interfejs użytkownika zostanie również zmiany.

Rysunek 4-21 zawiera wersję podejście to złożonego interfejsu użytkownika. Jest to uproszczone, ponieważ może mieć inne mikrousług agregujemy szczegółową części, które są oparte na różnych technik. To zależy od tego, czy tworzysz, to podejście tradycyjnej sieci web (platformy ASP.NET MVC) lub SPA (aplikacja jednostronicowa).

![W złożonego interfejsu użytkownika aplikacji każda sekcja interfejsu użytkownika jest generowany przez mikrousług kompozycji interfejsu użytkownika, który zachowuje się jak minimalna bramy.](./media/image21.png)

**Rysunek 4-21**. Przykład złożonego interfejsu użytkownika aplikacji w języku ukształtowane przez serwer zaplecza w mikrousługach

Każda z tych mikrousług kompozycji interfejsu użytkownika mogą być podobne do małych bramy interfejsu API. Ale w takim przypadku każdy z nich jest odpowiedzialny za mały obszar interfejsu użytkownika.

Złożone podejście interfejsu użytkownika, który jest wymuszany przez mikrousług może być trudniejszym wyzwaniem lub mniej tak, w zależności od jakich technologii interfejsu użytkownika używasz. Na przykład nie będzie stosować te same metody do tworzenia aplikacji sieci web tradycyjnych, którego używasz do tworzenia SPA lub dla natywnych aplikacji mobilnych (tak jak podczas opracowywania aplikacji platformy Xamarin, które mogą być trudniejsze dla tej metody).

[Ramach aplikacji eShopOnContainers](https://aka.ms/MicroservicesArchitecture) podejścia monolitycznego interfejsu użytkownika Przykładowa aplikacja korzysta z wielu powodów. Po pierwsze stanowi wprowadzenie do mikrousług i kontenerów. Złożonego interfejsu użytkownika jest bardziej zaawansowane, ale wymaga wykonania dalszych złożoność podczas projektowania i tworzenia interfejsu użytkownika. Po drugie w ramach aplikacji eShopOnContainers udostępnia również natywnych aplikacji mobilnych, oparte na środowisku Xamarin, która będzie bardziej złożonych na kliencie C\# po stronie.

Jednak firma Microsoft zachęca Dowiedz się więcej o złożonego interfejsu użytkownika oparta na mikrousługach przy użyciu następujących odwołań.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Złożonego interfejsu użytkownika za pomocą programu ASP.NET (w szczególności Workshop)** \
  [https://github.com/Particular/Workshop/tree/master/demos/asp-net-core](https://github.com/Particular/Workshop/tree/master/demos/asp-net-core)

- **Ruben Oostinga. Monolityczny frontonu w architekturze Mikrousług** \
  [https://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/](https://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/)

- **Mauro Servienti. Klucz tajny lepsze kompozycji interfejsu użytkownika** \
  [https://particular.net/blog/secret-of-better-ui-composition](https://particular.net/blog/secret-of-better-ui-composition)

- **VIKTOR Farcic. W tym składników frontonu sieci Web na Mikrousługi** \
  [https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

- **Zarządzanie frontonu w architekturze Mikrousług** \
  [https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html](https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)

>[!div class="step-by-step"]
>[Poprzednie](microservices-addressability-service-registry.md)
>[dalej](resilient-high-availability-microservices.md)