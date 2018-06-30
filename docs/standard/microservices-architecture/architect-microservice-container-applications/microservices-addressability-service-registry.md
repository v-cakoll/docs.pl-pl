---
title: Adresowanie Mikrousług oraz rejestr usługi
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Adresowanie Mikrousług oraz rejestr usługi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ec3ccdd823e00d148bb8a97e906132f44e7fa727
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106674"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Adresowanie Mikrousług oraz rejestr usługi

Każdy mikrousługi ma unikatową nazwę (URL), który jest używany do rozpoznawania jego lokalizacji. Twoje mikrousługi należy adresowanego wszędzie tam, gdzie jest uruchomiona. Jeśli trzeba myśleć o komputera, na którym jest uruchomiona określonego mikrousługi, rzeczy może przejść zły szybko. W taki sam sposób, że DNS rozpoznaje adres URL dla danego komputera z mikrousługi musi mieć unikatową nazwę, dzięki czemu jego bieżącej lokalizacji będzie wykrywalny. Mikrousług muszą mieć nazwy adresowanego, które stały się niezależnie od infrastruktury, które działają na. Oznacza to, że istnieje interakcji między sposób wdrażania usługi i jak okaże się, ponieważ musi istnieć [usługi rejestru](https://microservices.io/patterns/service-registry.html). W tym samym szyjnej gdy komputer ulegnie awarii, usługa Rejestr musi być może wskazywać, w którym usługa jest teraz uruchomiona.

[Usługi rejestru wzorzec](https://microservices.io/patterns/service-registry.html) jest kluczowym elementem odnajdywania usługi. Rejestr jest baza danych zawierająca lokalizacje sieciowe wystąpień usługi. Rejestr usługi musi być wysokiej dostępności i aktualne. Klientów można buforować lokalizacje sieciowe uzyskany z rejestru usługi. Jednak te informacje ostatecznie prowadzi nieaktualny i klientów nie może odnaleźć wystąpienia usługi. W rezultacie rejestru usługi składa się z klastra serwerów, które używają protokołu replikacji do zapewniania spójności.

W niektórych środowiskach wdrożenia mikrousługi (nazywane klastrami mają być uwzględnione w dalszej części artykułu) odnajdywania usługi są wbudowane. Na przykład w środowisku usługi kontenera platformy Azure Kubernetes i DC/OS, przy użyciu platformy Marathon obsługi rejestracji wystąpienia usługi i wyrejestrować. Serwer proxy one również uruchomić na każdym hoście, który pełni rolę routera odnajdywania po stronie serwera. Innym przykładem jest sieć szkieletowa usług Azure, oferujący rejestru usługi za pośrednictwem jego poza pole Naming Service.

Należy pamiętać, że niektóre nakładania się rejestr usługi i wzorzec bramy interfejsu API, który pomaga rozwiązać ten problem, a także. Na przykład [serwera Proxy usługi sieci szkieletowej wstecznego](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) jest typem wdrożenia bramy usługi interfejsu API jest oparty na Usługa nazewnictwa Fabrice i pomagające rozwiązać rozpoznawania adresów do wewnętrznych usług.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Krzysztof Richardson. Wzorca: Rejestr usługi**
    *https://microservices.io/patterns/service-registry.html*

-   **Auth0. Rejestr usługi**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)

-   **Gabriel Schenker. Odnajdowanie usługi**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)


>[!div class="step-by-step"]
[Poprzednie](maintain-microservice-apis.md)
[dalej](microservice-based-composite-ui-shape-layout.md)
