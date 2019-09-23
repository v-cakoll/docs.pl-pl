---
title: Migrowanie rozwiązania WCF do gRPC-gRPC dla deweloperów WCF
description: Jak migrować różne typy usługi WCF do wartości równoważnej w gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a9cfb87361194d998a3c4dfff4fe434be64f0d65
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184296"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a>Migrowanie rozwiązania WCF do gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W tym rozdziale zawarto informacje na temat pracy z projektami ASP.NET Core gRPC 3,0 i zademonstrowania migracji różnych typów usług WCF do gRPC równoważnej:

- Utwórz projekt ASP.NET Core 3,0 gRPC.
- Proste operacje typu żądanie-odpowiedź do gRPC jednoargumentowego wywołania procedury (RPC).
- Jednokierunkowa operacja gRPC RPC przesyłania strumieniowego klienta.
- Usługi pełnego dupleksu do gRPC dwukierunkowego wywołania RPC.

Istnieje również porównanie dotyczące korzystania z usług przesyłania strumieniowego i powtarzających się pól w celu zwracania zestawów danych i używania bibliotek klienckich na końcu rozdziału.

Przykładowa aplikacja WCF jest minimalnym elementem zastępczym zestawu giełdowych usług handlowych przy użyciu biblioteki kontenerów typu Open Source (IoC) o nazwie *Autofac* na potrzeby iniekcji zależności. Obejmuje ona trzy usługi, po jednej dla każdego typu usługi WCF. Usługi zostaną omówione bardziej szczegółowo w poniższych sekcjach. Rozwiązania można pobrać z [RendleLabs/GRPC-for-WCF — dla deweloperów](https://github.com/dotnet-architecture/grpc-for-wcf-developers) w serwisie GitHub. Usługi wykorzystują fałszywe dane, aby zminimalizować zależności zewnętrzne.

Przykłady obejmują implementacje WCF i gRPC każdej usługi.

>[!div class="step-by-step"]
>[Poprzedni](ws-protocols.md)
>[Następny](create-project.md)
