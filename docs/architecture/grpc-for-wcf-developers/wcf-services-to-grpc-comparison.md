---
title: Porównanie funkcji WCF z gRPC-gRPC dla deweloperów WCF
description: Porównanie struktur WCF i gRPC na potrzeby tworzenia aplikacji rozproszonych.
ms.date: 09/02/2019
ms.openlocfilehash: 4f54db76c9512b770b4dd993496d95437dd89753
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503337"
---
# <a name="comparing-wcf-to-grpc"></a>Porównywanie WCF z gRPC

Poprzedni rozdział udzielił Ci dobrego wyglądu protobuf oraz sposobu, w jaki gRPC obsługuje komunikaty. Przed rozpoczęciem pracy w ramach szczegółowej konwersji z Windows Communication Foundation (WCF) na gRPC, ważne jest, aby wiedzieć, jak funkcje dostępne w ramach usługi WCF są obsługiwane w gRPC i jakie obejścia, których można użyć, gdy nie ma żadnego odpowiednika gRPC. W szczególności ten rozdział będzie obejmować następujące tematy:

- Operacje i metody
- Powiązania i transporty
- Typy wywołań RPC
- Metadane
- Obsługa błędów
- Protokoły WS-\*

## <a name="grpc-example"></a>przykład gRPC

Podczas tworzenia nowego projektu ASP.NET Core gRPC 3,0 z programu Visual Studio 2019 lub wiersza polecenia zostanie wygenerowany odpowiednik gRPC "Hello world". Składa się z pliku `greeter.proto`, który definiuje usługę i jej komunikaty, oraz plik `GreeterService.cs` z implementacją usługi.

```protobuf
syntax = "proto3";

option csharp_namespace = "HelloGrpc";

package Greet;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// The request message that contains the user's name.
message HelloRequest {
  string name = 1;
}

// The response message that contains the greetings.
message HelloReply {
  string message = 1;
}
```

```csharp
using System.Threading.Tasks;
using Grpc.Core;
using Microsoft.Extensions.Logging;

namespace HelloGrpc
{
    public class GreeterService : Greeter.GreeterBase
    {
        private readonly ILogger<GreeterService> _logger;
        public GreeterService(ILogger<GreeterService> logger)
        {
            _logger = logger;
        }

        public override Task<HelloReply> SayHello(HelloRequest request, ServerCallContext context)
        {
            return Task.FromResult(new HelloReply
            {
                Message = "Hello " + request.Name
            });
        }
    }
}
```

Ten rozdział odnosi się do tego przykładowego kodu przy objaśnianiu różnych koncepcji i funkcji gRPC.

>[!div class="step-by-step"]
>[Poprzednie](protobuf-maps.md)
>[dalej](wcf-endpoints-grpc-methods.md)
