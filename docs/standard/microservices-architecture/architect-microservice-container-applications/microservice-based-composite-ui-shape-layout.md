---
title: Tworzenie złożonego interfejsu użytkownika opartego na mikrousługach, w tym kształt graficzny interfejsu użytkownika i układ generowany przez wiele mikrousług
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Tworzenie złożonego interfejsu użytkownika opartego na mikrousługach, w tym kształt graficzny interfejsu użytkownika i układ generowany przez wiele mikrousług
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 3c5f4c5a1dd1c1065be63ad916af078050c069c1
ms.sourcegitcommit: 5fd80619c760fa8c25d33a6f5661247cb65da465
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2018
ms.locfileid: "50744499"
---
# <a name="creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices"></a>Tworzenie złożonego interfejsu użytkownika opartego na mikrousługach, w tym kształt graficzny interfejsu użytkownika i układ generowany przez wiele mikrousług

Architektura Mikrousług często zaczyna się od obsługi danych i logiki po stronie serwera. Jednak bardziej zaawansowane podejście dotyczy projektowania interfejsu użytkownika oparta na mikrousługach, jak również aplikacji. Oznacza to, o złożonego interfejsu użytkownika generowany przez mikrousług, zamiast mikrousług na serwerze i po prostu aplikację kliencką monolityczne korzystanie z mikrousług. W przypadku tej metody mikrousług, które tworzysz może być wraz z zarówno logiki, jak i w formie wizualnej.

Rysunek 4-20 pokazuje prostszej metody tylko używania mikrousług z aplikacji klienckiej monolitycznego. Oczywiście może mieć usługi platformy ASP.NET MVC w zakresie od tworzenia kodu HTML i JavaScript. Rysunek jest uproszczeniem wyróżniający się, że masz jednego klienta (monolityczną) korzystanie z mikrousług, która po prostu skoncentrować się na logikę i dane, a nie na kształt interfejsu użytkownika (HTML i JavaScript) w interfejsie użytkownika.

![](./media/image20.png)

**Rysunek 4-20**. Interfejs użytkownika aplikacji monolitycznej korzystanie z mikrousług zaplecza

Z kolei złożonego interfejsu użytkownika jest dokładnie generowane i poprzez mikrousług, samodzielnie. Niektóre z mikrousług dysku visual kształt określonych obszarach interfejsu użytkownika. Główną różnicą jest składniki interfejsu użytkownika klienta (na przykład klas usług terminalowych) na podstawie szablonów, oraz ViewModel danych kształtowania-interfejsu użytkownika dla tych szablonów pochodzi z poszczególne mikrousługi.

W czasie uruchamiania aplikacji klienckich poszczególne składniki interfejsu użytkownika klienta (na przykład klasy TypeScript) rejestruje się przy użyciu mikrousług infrastruktury w stanie dostarczać modele widoków dla danego scenariusza. Mikrousługi zmienia kształt, interfejs użytkownika zostanie również zmiany.

Rysunek 4-21 zawiera wersję podejście to złożonego interfejsu użytkownika. To jest uproszczone, ponieważ może mieć inne mikrousług agregujemy szczegółową części, w oparciu o różnych technik — jest to uzależnione od tego, czy tworzysz podejście tradycyjnej sieci web (platformy ASP.NET MVC) lub SPA (aplikacja jednostronicowa).

![](./media/image21.png)

**Rysunek 4-21**. Przykład złożonego interfejsu użytkownika aplikacji w języku ukształtowane przez serwer zaplecza w mikrousługach

Każda z tych mikrousług kompozycji interfejsu użytkownika mogą być podobne do małych bramy interfejsu API. Ale w takim przypadku każdy jest odpowiedzialny za mały obszar interfejsu użytkownika.

Złożone podejście interfejsu użytkownika, który jest wymuszany przez mikrousług może być trudniejszym wyzwaniem lub mniej tak, w zależności od jakich technologii interfejsu użytkownika używasz. Na przykład nie będzie używać tych samych technik do tworzenia aplikacji sieci web tradycyjnych, którego używasz do tworzenia SPA lub dla natywnych aplikacji mobilnych (tak jak podczas opracowywania aplikacji platformy Xamarin, które mogą być trudniejsze dla tej metody).

[Ramach aplikacji eShopOnContainers](https://aka.ms/MicroservicesArchitecture) podejścia monolitycznego interfejsu użytkownika Przykładowa aplikacja korzysta z wielu powodów. Po pierwsze stanowi wprowadzenie do mikrousług i kontenerów. Złożonego interfejsu użytkownika jest bardziej zaawansowane, ale wymaga wykonania dalszych złożoność podczas projektowania i tworzenia interfejsu użytkownika. Po drugie w ramach aplikacji eShopOnContainers udostępnia również natywnych aplikacji mobilnych, oparte na środowisku Xamarin, która będzie bardziej złożonych na kliencie C\# po stronie.

Jednak firma Microsoft zachęca Dowiedz się więcej o złożonego interfejsu użytkownika oparta na mikrousługach przy użyciu następujących odwołań.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Złożonego interfejsu użytkownika za pomocą programu ASP.NET (w szczególności Workshop)**
    [*https://go.particular.net/workshop-composite-ui-demo*](https://go.particular.net/workshop-composite-ui-demo)

-   **Ruben Oostinga. Monolityczny frontonu w architekturze Mikrousług**
    [*https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/*](https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/)

-   **Mauro Servienti. Klucz tajny lepsze kompozycji interfejsu użytkownika**
    [*https://particular.net/blog/secret-of-better-ui-composition*](https://particular.net/blog/secret-of-better-ui-composition)

-   **VIKTOR Farcic. W tym składników frontonu sieci Web na Mikrousługi**
    [*https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/*](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

-   **Zarządzanie frontonu w architekturze Mikrousług**\
    [*https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html*](https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)


>[!div class="step-by-step"]
[Poprzednie](microservices-addressability-service-registry.md)
[dalej](resilient-high-availability-microservices.md)
