---
title: Mikrousługi tworzenie, rozwijanie i przechowywanie wersji interfejsów API i kontraktów "
description: Tworzenie mikrousług interfejsów API i kontrakty, uwzględniając rozwój i przechowywanie wersji, ponieważ ulegnie zmianie.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 5d3e031217159a695b67f67859b8cf412a4419c2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152542"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Mikrousługi tworzenie, rozwijanie i przechowywanie wersji interfejsów API i kontraktów "

Mikrousługi interfejsu API jest Umowa między usługą i swoich klientów. Będzie można rozwijać mikrousługi niezależnie, tylko wtedy, gdy nie przerywaj, jej kontrakt interfejsu API, dlatego jest tak ważny kontrakt. W przypadku zmiany umowy, wpłynie to na aplikację kliencką lub bramy interfejsu API.

Zależy od rodzaju definicji interfejsu API, używasz protokołu. Na przykład jeśli używasz komunikatów (takich jak [AMQP](https://www.amqp.org/)), interfejs API składa się z typów wiadomości. Jeśli używasz protokołu HTTP i usług RESTful, interfejs API składa się z adresów URL i formatów żądania i odpowiedzi w formacie JSON.

Jednak nawet jeśli jesteś przydatnego o początkowej umowy, interfejs API usługi należy zmieniać wraz z upływem czasu. Kiedy tak się stanie, i zwłaszcza, jeśli Twój interfejs API jest publiczny interfejs API używane przez wiele aplikacji klienckich — zwykle nie może wymusić wszystkich klientów, aby uaktualnić do swojej nowej kontrakt interfejsu API. Zazwyczaj należy stopniowo wdrażanie nowych wersji usługi w taki sposób, aby jednocześnie jest uruchomionych zarówno stare i nowe wersje kontraktu usługi. W związku z tym ważne jest zapewnienie strategię dla usługi przechowywanie wersji usługi.

Podczas zmiany interfejsu API są małe, np. Jeśli dodać atrybuty lub parametrów z interfejsem API, klientów korzystających z interfejsu API starszych należy przełączyć i pracować z nową wersję usługi. Można podać wartości domyślne dla brakujących atrybutów, które są wymagane, a klienci mogą być w stanie ignoruje wszelkie atrybuty dodatkowe odpowiedzi.

Jednak czasami musisz wprowadzić zmiany głównej lub niezgodne przez interfejs API usługi. Ponieważ nie można wymusić klienta aplikacji lub usług, aby natychmiast przeprowadzić uaktualnienie do nowej wersji, usługa musi obsługiwać starsze wersje interfejsu API przez pewien. Jeśli używasz mechanizm oparty na protokole HTTP, takich jak REST jedno z podejść jest osadzenie numer wersji interfejsu API, w adresie URL lub w nagłówku HTTP. Następnie możesz zdecydować, czy między Implementowanie obie wersje usługi jednocześnie w ramach tego samego wystąpienia usługi lub wdrażanie różnych wystąpień, że każda obsługuje wersję interfejsu API. To dobra metoda dla tego [wzorzec mediatora](https://en.wikipedia.org/wiki/Mediator_pattern) (na przykład [MediatR biblioteki](https://github.com/jbogard/MediatR)) do oddzielenia wersje inną implementację do obsługi niezależnie od.

Na koniec, jeśli użytkownik korzysta z architektury REST [Hipermediach](https://www.infoq.com/articles/mark-baker-hypermedia) jest najlepsze rozwiązanie w zakresie przechowywania wersji usługi, dzięki czemu evolvable interfejsów API.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Scott Hanselman. Przechowywanie wersji internetowy interfejs API RESTful platformy ASP.NET Core łatwe** \
  [*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

- **Przechowywanie wersji internetowego interfejsu API RESTful** \
  [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

- **Roy Fielding. Przechowywanie wersji, Hipermediach i REST** \
  [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

>[!div class="step-by-step"]
>[Poprzednie](asynchronous-message-based-communication.md)
>[dalej](microservices-addressability-service-registry.md)