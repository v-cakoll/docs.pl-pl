---
title: Adresowanie Mikrousług i rejestr usług
description: Poznaj rolę rejestry obrazów kontenera w architekturze mikrousług.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 60afb2e06c0c9a37104a82a74de016da5c134a61
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145848"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Adresowanie Mikrousług i rejestr usług

Każda mikrousługa ma unikatową nazwę (adres URL), który jest używany do rozpoznawania lokalizacji. Twoje mikrousług należy adresowalnych wszędzie tam, gdzie jest uruchomiony. Jeśli musisz myśleć o komputera, którym jest uruchomiona określonego mikrousług, mogą wystąpić zły szybko. W ten sam sposób, że DNS jest rozpoznawana jako adres URL dla danego komputera z mikrousług musi mieć unikatową nazwę, tak, aby jego bieżącej lokalizacji wykrywalne. Mikrousługi należy adresowalnych nazw, które były niezależnie od infrastruktury, które działają w. Oznacza to, że istnieje interakcji między jak usługa zostanie wdrożona, i jak okaże się, ponieważ musi istnieć [rejestr usług](https://microservices.io/patterns/service-registry.html). W tym samym względzie w przypadku awarii komputera Usługa rejestru musi umożliwiać wskazać, gdzie usługa jest obecnie uruchomiona.

[Wzorzec rejestru usług](https://microservices.io/patterns/service-registry.html) jest kluczowym elementem odnajdowania usług. Rejestr to baza danych zawierająca lokalizacje sieciowe wystąpień usługi. Rejestr usług musi być wysoko dostępne i aktualne. Klientów można buforować lokalizacje sieciowe uzyskany z rejestru usługi. Jednak te informacje po pewnym czasie przechodzi się nieaktualna i klientów nie może odnaleźć wystąpienia usługi. W związku z tym rejestr usług składa się z klastra serwerów, które używają protokołu replikacji do zapewniania spójności.

W niektórych środowiskach wdrożenia mikrousługi (nazywane klastrami, aby uwzględnić je w dalszej części tego tematu) odnajdowania usługi jest wbudowana. Na przykład usługi kontenera platformy Azure w środowisku Kubernetes (AKS) można obsługiwać rejestracji wystąpienie usługi i wyrejestrować. Można też uruchamiać serwera proxy na każdym hoście, który pełni rolę routera odnajdywania po stronie serwera. Innym przykładem jest usługi Azure Service Fabric, oferujący rejestr usług, za pośrednictwem jego usługi nazewnictwa poza pole.

Należy pamiętać, że nakładają się na niektórych rejestr usług i wzorzec bramy interfejsu API, która pomaga rozwiązać ten problem, a także. Na przykład [Proxy usługi Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) jest typem wdrożenia bramy interfejsu API, który zależy od usługi nazewnictwa Service Fabric i która pomaga rozwiązać rozpoznawania adresów do wewnętrznych usług.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Chris Leonard. Wzorzec: Rejestr usług** \
  [*https://microservices.io/patterns/service-registry.html*](https://microservices.io/patterns/service-registry.html)

- **Rozwiązanie Auth0. Rejestr usług** \
  [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)

- **Gabriel Schenker. Odnajdowanie usługi** \
  [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)

>[!div class="step-by-step"]
>[Poprzednie](maintain-microservice-apis.md)
>[dalej](microservice-based-composite-ui-shape-layout.md)