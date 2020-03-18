---
title: Tworzenie złożonego interfejsu opartego na mikrousługach
description: Architektura mikrousług jest nie tylko dla zaplecza. Uzyskaj wgląd do używania go w przedniej części.
ms.date: 09/20/2018
ms.openlocfilehash: 1861d3bb6e5d4a0226aa8f3f72a2e0d3e83be56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72275744"
---
# <a name="creating-composite-ui-based-on-microservices"></a>Tworzenie złożonego interfejsu opartego na mikrousługach

Architektura mikrousług często zaczyna się od danych i logiki obsługi po stronie serwera, ale w wielu przypadkach interfejsu jest nadal obsługiwane jako monolit. Jednak bardziej zaawansowane podejście, o nazwie [mikro frontonów](https://martinfowler.com/articles/micro-frontends.html), jest zaprojektowanie interfejsu użytkownika aplikacji na podstawie mikrousług, jak również. Oznacza to, że złożony interfejsu opracowanego przez mikrousług, zamiast mikrousług na serwerze i tylko monolityczne aplikacji klienckiej korzystających z mikrousług. Dzięki takiemu podejściu mikrousług, które można utworzyć można uzupełnić zarówno logiki i reprezentacji wizualnej.

Rysunek 4-20 przedstawia prostsze podejście tylko zużywa mikrousług z monolityczne aplikacji klienckiej. Oczywiście, można mieć ASP.NET usługi MVC pomiędzy produkcją HTML i JavaScript. Rysunek jest uproszczenie, które podkreśla, że masz jeden (monolityczny) interfejsu klienta klienta zużywa mikrousług, które po prostu skupić się na logiki i danych, a nie na kształt interfejsu (HTML i JavaScript).

![Diagram monolitycznego interfejsu interfejsu łączącego się z mikrousługami.](./media/microservice-based-composite-ui-shape-layout/monolith-ui-consume-microservices.png)

**Rysunek 4-20**. Monolityczne aplikacji interfejsu zużywa mikrousług zaplecza

W przeciwieństwie do złożonego interfejsu jest precyzyjnie generowane i składa się przez same mikrousług. Niektóre mikrousług dysk wizualny kształt określonych obszarów interfejsu firmy. Kluczową różnicą jest to, że masz składniki interfejsu interfejsu klienta (klasy TypeScript, na przykład) na podstawie szablonów, a model viewmodel kształtowania danych dla tych szablonów pochodzi z każdej mikrousługi.

W czasie uruchamiania aplikacji klienckiej każdy ze składników interfejsu interfejsu klienta (na przykład klasy TypeScript) rejestruje się za pomocą mikrousługi infrastruktury zdolnej do dostarczania ViewModels dla danego scenariusza. Jeśli mikrousługi zmienia kształt, interfejsu użytkownika zmienia się również.

Rysunek 4-21 przedstawia wersję tego złożonego podejścia interfejsu interfejsu. Jest to uproszczone, ponieważ może mieć inne mikrousługi, które są agregowanie części ziarnistych, które są oparte na różnych technik. To zależy od tego, czy budujesz tradycyjne podejście internetowe (ASP.NET MVC) lub SPA (Single Page Application).

![Diagram złożonego interfejsu składa się z wielu modeli widoku.](./media/microservice-based-composite-ui-shape-layout/microservice-generate-composite-ui.png)

**Rysunek 4-21**. Przykład złożonej aplikacji interfejsu na iem ukształtowany przez mikrousługi zaplecza

Each of those UI composition microservices would be similar to a small API Gateway. Ale w tym przypadku każdy z nich jest odpowiedzialny za mały obszar interfejsu.

Złożonych podejście interfejsu opartego na uwyżce, który jest napędzany przez mikrousług może być trudniejsze lub mniej tak, w zależności od tego, jakie technologie interfejsu, którego używasz. Na przykład nie będzie używać tych samych technik do tworzenia tradycyjnej aplikacji sieci web, które są używane do tworzenia SPA lub dla natywnej aplikacji mobilnej (jak podczas tworzenia aplikacji Xamarin, co może być trudniejsze dla tego podejścia).

Przykładowa aplikacja [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) używa monolitycznego podejścia interfejsu podanego z wielu powodów. Po pierwsze jest wprowadzenie do mikrousług i kontenerów. Złożony interfejsu interfejsu jest bardziej zaawansowany, ale wymaga również dalszej złożoności podczas projektowania i rozwijania interfejsu. Po drugie eShopOnContainers zapewnia również natywną aplikację mobilną opartą na\# platformie Xamarin, co sprawi, że będzie bardziej złożona po stronie klienta C.

Jednak zachęcamy do korzystania z następujących odwołań, aby dowiedzieć się więcej na temat złożonych interfejsu opartego na mikrousług.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Micro Frontends (blog Martina Fowlera)**  
  <https://martinfowler.com/articles/micro-frontends.html>
  
- **Micro Frontends (strona Michaela Geersa)**  
  <https://micro-frontends.org/>
  
- **Kompozytowy ui przy użyciu ASP.NET (Warsztat szczegółowy)**  
  <https://github.com/Particular/Workshop/tree/master/demos/asp-net-core>

- **Ruben Oostinga. Monolityczna fronton w architekturze mikrousług**  
  <https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/>

- **Mauro Servienti. Sekret lepszego składu interfejsu**  
  <https://particular.net/blog/secret-of-better-ui-composition>

- **Wiktor Farcic. W tym frontonu składników sieci Web do mikrousług**  
  <https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/>

- **Zarządzanie frontonem w architekturze mikrousług**  
  <https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html>

>[!div class="step-by-step"]
>[Poprzedni](microservices-addressability-service-registry.md)
>[następny](resilient-high-availability-microservices.md)
