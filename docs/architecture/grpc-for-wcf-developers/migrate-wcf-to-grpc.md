---
title: Migrowanie rozwiązania WCF do gRPC-gRPC dla deweloperów WCF
description: Jak migrować różne typy usług WCF do równoważnej w gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 12e724ab46a33547d352da7a604a5a994e617bc2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628517"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a>Migrowanie rozwiązania WCF do usługi gRPC

W tym rozdziale opisano sposób pracy z projektami ASP.NET Core gRPC 3,0 i zademonstrowanie migracji różnych typów usług Windows Communication Foundation (WCF) do gRPC równoważnej:

- Utwórz projekt ASP.NET Core 3,0 gRPC.
- Proste operacje typu żądanie-odpowiedź do gRPC jednoargumentowego wywołania procedury (RPC).
- Jednokierunkowa operacja gRPC RPC przesyłania strumieniowego klienta.
- Usługi pełnego dupleksu do gRPC dwukierunkowego wywoływania procedur RPC.

Istnieje również porównanie dotyczące korzystania z usług przesyłania strumieniowego i powtarzających się pól w celu zwrócenia zestawów danych i istnieje dyskusja na temat używania bibliotek klienckich na końcu rozdziału.

Przykładowa aplikacja WCF jest minimalnym elementem zastępczym zestawu giełdowych usług handlowych. Używa ona biblioteki kontenerów kontroli (IoC) typu open source o nazwie Autofac na potrzeby iniekcji zależności. Obejmuje ona trzy usługi, po jednej dla każdego typu usługi WCF. Usługi zostaną omówione bardziej szczegółowo w poniższych sekcjach. Możesz pobrać rozwiązania z programu [dotnet-Architecture/GRPC-for-WCF — deweloperzy](https://github.com/dotnet-architecture/grpc-for-wcf-developers) w serwisie GitHub. Usługi wykorzystują fałszywe dane, aby zminimalizować zależności zewnętrzne.

Przykłady obejmują implementacje WCF i gRPC każdej usługi.

>[!div class="step-by-step"]
>[Poprzednie](ws-protocols.md)
>[dalej](create-project.md)
