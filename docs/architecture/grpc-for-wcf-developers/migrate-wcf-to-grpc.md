---
title: Migrowanie rozwiązania WCF do gRPC-gRPC dla deweloperów WCF
description: Jak migrować różne typy usługi WCF do wartości równoważnej w gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 65c30b777d9981cb3291b846f698f2a69b4498fc
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846592"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a>Migrowanie rozwiązania WCF do usługi gRPC

W tym rozdziale zawarto informacje na temat pracy z projektami ASP.NET Core gRPC 3,0 i zademonstrowania migracji różnych typów usług WCF do gRPC równoważnej:

- Utwórz projekt ASP.NET Core 3,0 gRPC.
- Proste operacje typu żądanie-odpowiedź do gRPC jednoargumentowego wywołania procedury (RPC).
- Jednokierunkowa operacja gRPC RPC przesyłania strumieniowego klienta.
- Usługi pełnego dupleksu do gRPC dwukierunkowego wywołania RPC.

Istnieje również porównanie dotyczące korzystania z usług przesyłania strumieniowego i powtarzających się pól w celu zwracania zestawów danych i używania bibliotek klienckich na końcu rozdziału.

Przykładowa aplikacja WCF jest minimalnym elementem zastępczym zestawu giełdowych usług handlowych przy użyciu biblioteki kontenerów typu Open Source (IoC) o nazwie *Autofac* na potrzeby iniekcji zależności. Obejmuje ona trzy usługi, po jednej dla każdego typu usługi WCF. Usługi zostaną omówione bardziej szczegółowo w poniższych sekcjach. Rozwiązania można pobrać z programu [dotnet-Architecture/GRPC-for-WCF — deweloperzy](https://github.com/dotnet-architecture/grpc-for-wcf-developers) w serwisie GitHub. Usługi wykorzystują fałszywe dane, aby zminimalizować zależności zewnętrzne.

Przykłady obejmują implementacje WCF i gRPC każdej usługi.

>[!div class="step-by-step"]
>[Poprzedni](ws-protocols.md)
>[Następny](create-project.md)
