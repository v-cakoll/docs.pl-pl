---
title: "Adresowanie Mikrousług oraz rejestr usługi"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Adresowanie Mikrousług oraz rejestr usługi"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 19a0200dadfb90a455de690d880f4eeae4772ed7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="microservices-addressability-and-the-service-registry"></a>Adresowanie Mikrousług oraz rejestr usługi

Każdy mikrousługi ma unikatową nazwę (URL), który jest używany do rozpoznawania jego lokalizacji. Twoje mikrousługi należy adresowanego wszędzie tam, gdzie jest uruchomiona. Jeśli trzeba myśleć o komputera, na którym jest uruchomiona określonego mikrousługi, rzeczy może przejść zły szybko. W taki sam sposób, że DNS rozpoznaje adres URL dla danego komputera z mikrousługi musi mieć unikatową nazwę, dzięki czemu jego bieżącej lokalizacji będzie wykrywalny. Mikrousług muszą mieć nazwy adresowanego, które stały się niezależnie od infrastruktury, które działają na. Oznacza to, że istnieje interakcji między sposób wdrażania usługi i jak okaże się, ponieważ musi istnieć [usługi rejestru](http://microservices.io/patterns/service-registry.html). W tym samym szyjnej gdy komputer ulegnie awarii, usługa Rejestr musi być może wskazywać, w którym usługa jest teraz uruchomiona.

[Usługi rejestru wzorzec](http://microservices.io/patterns/service-registry.html) jest kluczowym elementem odnajdywania usługi. Rejestr jest baza danych zawierająca lokalizacje sieciowe wystąpień usługi. Rejestr usługi musi być wysokiej dostępności i aktualne. Klientów można buforować lokalizacje sieciowe uzyskany z rejestru usługi. Jednak te informacje ostatecznie prowadzi nieaktualny i klientów nie może odnaleźć wystąpienia usługi. W rezultacie rejestru usługi składa się z klastra serwerów, które używają protokołu replikacji do zapewniania spójności.

W niektórych środowiskach wdrożenia mikrousługi (nazywane klastrami mają być uwzględnione w dalszej części artykułu) odnajdywania usługi są wbudowane. Na przykład w środowisku usługi kontenera platformy Azure Kubernetes i DC/OS, przy użyciu platformy Marathon obsługi rejestracji wystąpienia usługi i wyrejestrować. Serwer proxy one również uruchomić na każdym hoście, który pełni rolę routera odnajdywania po stronie serwera. Innym przykładem jest sieć szkieletowa usług Azure, oferujący rejestru usługi za pośrednictwem jego poza pole Naming Service.

Należy pamiętać, że niektóre nakładania się rejestr usługi i wzorzec bramy interfejsu API, który pomaga rozwiązać ten problem, a także. Na przykład [serwera Proxy usługi sieci szkieletowej wstecznego](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) jest typem wdrożenia bramy usługi interfejsu API jest oparty na Usługa nazewnictwa Fabrice i pomagające rozwiązać rozpoznawania adresów do wewnętrznych usług.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Krzysztof Richardson. Wzorzec: Usługa rejestru**
    *http://microservices.io/patterns/service-registry.html*

-   **Auth0. Rejestr usługi**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)

-   **Gabriel Schenker. Odnajdowanie usługi**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)


>[!div class="step-by-step"]
[Poprzednie] (Obsługa mikrousługi apis.md) [dalej] (microservice-based-composite-ui-shape-layout.md)
