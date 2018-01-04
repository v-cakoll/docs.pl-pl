---
title: "Tworzenie, rozwijającymi i przechowywanie wersji mikrousługi interfejsów API i kontrakty"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Tworzenie, rozwijającymi i przechowywanie wersji mikrousługi interfejsów API i kontrakty"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3aaa7eaa8bc535874369cf08414f2211cae1bed9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Tworzenie, rozwijającymi i przechowywanie wersji mikrousługi interfejsów API i kontrakty

Mikrousługi interfejsu API jest Umowa między usługą i klientów. Można sformułować mikrousługi niezależnie tylko wtedy, gdy nie dzielone jej kontrakt interfejsu API, dlatego tak ważne jest kontraktu. W przypadku zmiany umowy, będzie miało wpływ Twoje aplikacje klienckie lub bramy interfejsu API.

Rodzaj definicji interfejsu API zależy od tego, na który protokół używasz. Na przykład jeśli używasz obsługi komunikatów (takich jak [AMQP](https://www.amqp.org/)), interfejsu API składa się z typów komunikatów. Jeśli korzystasz z usług RESTful i HTTP, interfejs API składa się z adresów URL i formatów żądania i odpowiedzi w formacie JSON.

Jednak nawet jeśli jesteś przemyślane o początkowej umowy, interfejs API usługi należy zmieniać wraz z upływem czasu. Jeśli tak się stanie — i szczególnie w przypadku interfejsu API publiczny interfejs API, używane przez aplikacje klienckie wielu — zwykle nie może wymusić wszystkich klientów do uaktualnienia do kontraktu do interfejsu API. Zazwyczaj konieczne przyrostowo wdrażanie nowych wersji usługi w taki sposób, aby starych i nowych wersji kontraktu usługi są uruchomione jednocześnie. W związku z tym należy mieć strategii dla Twojej wersji usługi.

Podczas zmiany interfejsu API są małe, takich jak Jeśli musisz dodać atrybuty lub parametry do interfejsu API, klientów, którzy używają interfejsu API starszych należy przełącznika i korzystać z nowych wersji usługi. Można podać wartości domyślnej dla brakujących atrybutów, które są wymagane, a klienci można zignorować wszelkie atrybuty dodatkowe odpowiedzi.

Jednak czasami trzeba wprowadzić zmiany głównych i niezgodna z interfejsem API usługi. Ponieważ nie można wymusić klienta aplikacji lub usług, aby natychmiast uaktualnić do nowej wersji, usługa musi obsługiwać starszych wersji interfejsu API dla pewnym okresie. Jeśli używane są oparte na protokole HTTP mechanizmu, takiego jak REST, jednym z podejść jest osadzić numer wersji interfejsu API w adresie URL lub w nagłówku HTTP. Następnie można zdecydować, między implementowania obie wersje usługi jednocześnie w ramach tego samego wystąpienia usługi lub wdrażanie różnych wystąpień, czy obsługują wersja interfejsu API. Dobrym rozwiązaniem dla tego jest [wzorzec mediatora](https://en.wikipedia.org/wiki/Mediator_pattern) (na przykład [biblioteki MediatR](https://github.com/jbogard/MediatR)) rozdzielenie do obsługi niezależnie od wersji inną implementację.

Na koniec, w przypadku korzystania z architektury REST [hipermedialnych](https://www.infoq.com/articles/mark-baker-hypermedia) jest najlepszym rozwiązaniem dla wersji usług, dzięki czemu evolvable interfejsów API.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Scott Hanselman. Przechowywanie wersji interfejsu API sieci Web RESTful Core ASP.NET łatwe**
    <http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

-   **Przechowywanie wersji interfejs API sieci web RESTful**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Fielding Royowi. Przechowywanie wersji, hipermedialnych i REST**
    <https://www.infoq.com/articles/roy-fielding-on-versioning>


>[!div class="step-by-step"]
[Poprzednie] (asynchroniczne wiadomości — na podstawie communication.md) [dalej] (mikrousług adresowanie usług registry.md)
