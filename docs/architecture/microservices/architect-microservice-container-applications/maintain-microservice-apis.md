---
title: Tworzenie, rozwijanie i przechowywanie wersji interfejsów API i kontaktów w mikrousługach
description: Tworzenie mikrousług interfejsów API i kontraktów, biorąc pod uwagę ewolucję i przechowywanie wersji, ponieważ wymaga zmiany.
ms.date: 09/20/2018
ms.openlocfilehash: 1972d02d8bf7935c71bfd383707ae19ea2baded9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295458"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Tworzenie, rozwijanie i przechowywanie wersji interfejsów API i kontaktów w mikrousługach

Interfejs API mikrousług jest umową między usługą a jej klientami. Będziesz mógł rozwijać mikrousługi niezależnie tylko wtedy, gdy nie złamiesz jego umowy interfejsu API, dlatego kontrakt jest tak ważne. Jeśli zmienisz umowę, będzie to miało wpływ na aplikacje klienckie lub bramę interfejsu API.

Charakter definicji interfejsu API zależy od protokołu, którego używasz. Na przykład jeśli używasz wiadomości (takich jak [AMQP),](https://www.amqp.org/)interfejs API składa się z typów komunikatów. Jeśli używasz usług HTTP i RESTful, interfejs API składa się z adresów URL oraz formatów JSON żądania i odpowiedzi.

Jednak nawet jeśli masz na uwadze początkowej umowy, interfejs API usługi będzie musiał zmienić w czasie. W takim przypadku — a zwłaszcza jeśli interfejs API jest publicznym interfejsem API używanym przez wiele aplikacji klienckich — zazwyczaj nie można wymusić na wszystkich klientach uaktualnienia do nowej umowy interfejsu API. Zazwyczaj należy stopniowo wdrażać nowe wersje usługi w taki sposób, że zarówno stare, jak i nowe wersje umowy serwisowej są uruchomione jednocześnie. Dlatego ważne jest, aby mieć strategię dla wersji usługi.

Gdy zmiany interfejsu API są małe, na przykład w przypadku dodawania atrybutów lub parametrów do interfejsu API, klienci, którzy używają starszego interfejsu API, powinni przełączać się i pracować z nową wersją usługi. Może być możliwe podanie wartości domyślnych dla wszystkich brakujących atrybutów, które są wymagane, a klienci mogą być w stanie zignorować wszelkie dodatkowe atrybuty odpowiedzi.

Jednak czasami trzeba wprowadzić główne i niezgodne zmiany w interfejsie API usługi. Ponieważ może nie być w stanie wymusić aplikacji klienckich lub usług do natychmiastowego uaktualnienia do nowej wersji, usługa musi obsługiwać starsze wersje interfejsu API przez pewien okres. Jeśli używasz mechanizmu opartego na HTTP, takiego jak REST, jednym z podejść jest osadzanie numeru wersji interfejsu API w adresie URL lub w nagłówku HTTP. Następnie można zdecydować między implementacji obu wersji usługi jednocześnie w ramach tego samego wystąpienia usługi lub wdrażania różnych wystąpień, które każdy obsługuje wersję interfejsu API. Dobrym podejściem do tego jest [wzorzec mediatora](https://en.wikipedia.org/wiki/Mediator_pattern) (na przykład [biblioteka MediatR),](https://github.com/jbogard/MediatR)aby oddzielić różne wersje implementacji do niezależnych programów obsługi.

Na koniec, jeśli używasz architektury REST, [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) jest najlepszym rozwiązaniem do wersji usług i umożliwienie evolvable interfejsów API.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Scott Hanselman. ASP.NET Core RESTful Web API przechowywanie wersji łatwe** \
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- **Przechowywanie wersji internetowego interfejsu API RESTful** \
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- **Roy Fielding. Przechowywanie wersji, hypermedia i REST** \
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

>[!div class="step-by-step"]
>[Poprzedni](asynchronous-message-based-communication.md)
>[następny](microservices-addressability-service-registry.md)
