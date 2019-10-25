---
title: Porównanie funkcji WCF z gRPC-gRPC dla deweloperów WCF
description: Porównanie struktur WCF i gRPC na potrzeby tworzenia aplikacji rozproszonych.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5ab1380d4ded52abff08c35c430adf2f3ed7c58b
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846067"
---
# <a name="comparing-wcf-to-grpc"></a>Porównywanie WCF z gRPC

Poprzedni rozdział powinien mieć zapewnioną dobrą postać protobuf oraz sposób, w jaki gRPC obsługuje komunikaty. Przed rozpoczęciem pracy w ramach szczegółowej konwersji z programu WCF do gRPC należy zwrócić uwagę na to, jak zakres funkcji dostępnych obecnie w programie WCF jest obsługiwany w gRPC i jakie obejścia, których można użyć, gdy nie wydaje się, że nie jest odpowiednikiem gRPC. W szczególności ten rozdział będzie obejmować następujące tematy:

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

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings.
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
>[Poprzedni](protobuf-maps.md)
>[Następny](wcf-endpoints-grpc-methods.md)
