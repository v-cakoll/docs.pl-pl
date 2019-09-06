---
title: Tworzenie, rozwijanie i przechowywanie wersji interfejsów API i kontaktów w mikrousługach
description: Tworzenie mikrousług API i kontraktów uwzględniających ewolucję i przechowywanie wersji, ponieważ wymagają zmiany.
ms.date: 09/20/2018
ms.openlocfilehash: 1972d02d8bf7935c71bfd383707ae19ea2baded9
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295458"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Tworzenie, rozwijanie i przechowywanie wersji interfejsów API i kontaktów w mikrousługach

Interfejs API mikrousług to kontrakt między usługą i jej klientami. Można wypróbować mikrousługi niezależnie tylko wtedy, gdy nie uda się przerwać jej kontraktu interfejsu API, co oznacza, że kontrakt jest tak ważny. Jeśli zmienisz kontrakt, wpłynie to na aplikacje klienckie lub bramę interfejsu API.

Charakter definicji interfejsu API zależy od używanego protokołu. Na przykład jeśli korzystasz z komunikatów (takich jak [AMQP](https://www.amqp.org/)), interfejs API składa się z typów komunikatów. W przypadku korzystania z usług HTTP i RESTful interfejs API składa się z adresów URL i formatów JSON żądania i odpowiedzi.

Jednak nawet jeśli jesteś przydatnego o początkowym kontrakcie, interfejs API usługi będzie musiał ulec zmianie z upływem czasu. Gdy tak się stanie, a zwłaszcza jeśli interfejs API jest publicznym interfejsem API używanym przez wiele aplikacji klienckich — zazwyczaj nie można wymusić uaktualnienia wszystkich klientów do nowego kontraktu interfejsu API. Zwykle należy wdrożyć nowe wersje usługi w taki sposób, aby jednocześnie działały zarówno stare, jak i nowe wersje kontraktu usługi. W związku z tym ważne jest, aby mieć strategię obsługi wersji usługi.

Gdy zmiany interfejsu API są niewielkie, podobnie jak w przypadku dodawania atrybutów lub parametrów do interfejsu API, klienci korzystający ze starszego interfejsu API powinni przełączać i korzystać z nowej wersji usługi. Może być możliwe podanie wartości domyślnych dla wszelkich brakujących atrybutów, które są wymagane, a klienci mogą ignorować wszelkie dodatkowe atrybuty odpowiedzi.

Niemniej jednak czasami trzeba wprowadzić istotne i niezgodne zmiany w interfejsie API usługi. Ponieważ nie można wymusić natychmiastowego uaktualnienia aplikacji lub usług klienta do nowej wersji, usługa musi obsługiwać starsze wersje interfejsu API przez pewien okres. Jeśli używasz mechanizmu opartego na protokole HTTP, takiego jak REST, jedno podejście polega na osadzeniu numeru wersji interfejsu API w adresie URL lub w nagłówku HTTP. Następnie można zdecydować się na wdrożenie obu wersji usługi jednocześnie w ramach tego samego wystąpienia usługi lub wdrożenie różnych wystąpień, które obsługują wersję interfejsu API. Dobrym rozwiązaniem dla tego jest [wzorzec mediator](https://en.wikipedia.org/wiki/Mediator_pattern) (na przykład [Biblioteka MediatR](https://github.com/jbogard/MediatR)), aby oddzielić różne wersje implementacji na niezależne programy obsługi.

Na [koniec, jeśli](https://www.infoq.com/articles/mark-baker-hypermedia) używasz architektury REST, najlepszym rozwiązaniem jest udostępnienie wersji usług i umożliwienie rozwijania interfejsów API.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Scott Hanselman. Łatwość ASP.NET Core RESTful internetowego interfejsu API** \
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- **Przechowywanie wersji interfejsu API sieci Web RESTful** \
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- **Roy. Przechowywanie wersji, nośniki i REST** \
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

>[!div class="step-by-step"]
>[Poprzedni](asynchronous-message-based-communication.md)Następny
>[](microservices-addressability-service-registry.md)
