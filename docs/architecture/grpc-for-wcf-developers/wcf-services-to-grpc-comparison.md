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
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="8c7a7-103">Porównywanie WCF z gRPC</span><span class="sxs-lookup"><span data-stu-id="8c7a7-103">Comparing WCF to gRPC</span></span>

<span data-ttu-id="8c7a7-104">Poprzedni rozdział udzielił Ci dobrego wyglądu protobuf oraz sposobu, w jaki gRPC obsługuje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-104">The previous chapter gave you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="8c7a7-105">Przed rozpoczęciem pracy w ramach szczegółowej konwersji z Windows Communication Foundation (WCF) na gRPC, ważne jest, aby wiedzieć, jak funkcje dostępne w ramach usługi WCF są obsługiwane w gRPC i jakie obejścia, których można użyć, gdy nie ma żadnego odpowiednika gRPC.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-105">Before you work through a detailed conversion from Windows Communication Foundation (WCF) to gRPC, it's important know how the features available in WCF are handled in gRPC and what workarounds you can use when there's no gRPC equivalent.</span></span> <span data-ttu-id="8c7a7-106">W szczególności ten rozdział będzie obejmować następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="8c7a7-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="8c7a7-107">Operacje i metody</span><span class="sxs-lookup"><span data-stu-id="8c7a7-107">Operations and methods</span></span>
- <span data-ttu-id="8c7a7-108">Powiązania i transporty</span><span class="sxs-lookup"><span data-stu-id="8c7a7-108">Bindings and transports</span></span>
- <span data-ttu-id="8c7a7-109">Typy wywołań RPC</span><span class="sxs-lookup"><span data-stu-id="8c7a7-109">RPC types</span></span>
- <span data-ttu-id="8c7a7-110">Metadane</span><span class="sxs-lookup"><span data-stu-id="8c7a7-110">Metadata</span></span>
- <span data-ttu-id="8c7a7-111">Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="8c7a7-111">Error handling</span></span>
- <span data-ttu-id="8c7a7-112">Protokoły WS-\*</span><span class="sxs-lookup"><span data-stu-id="8c7a7-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="8c7a7-113">przykład gRPC</span><span class="sxs-lookup"><span data-stu-id="8c7a7-113">gRPC example</span></span>

<span data-ttu-id="8c7a7-114">Podczas tworzenia nowego projektu ASP.NET Core gRPC 3,0 z programu Visual Studio 2019 lub wiersza polecenia zostanie wygenerowany odpowiednik gRPC "Hello world".</span><span class="sxs-lookup"><span data-stu-id="8c7a7-114">When you create a new ASP.NET Core 3.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="8c7a7-115">Składa się z pliku `greeter.proto`, który definiuje usługę i jej komunikaty, oraz plik `GreeterService.cs` z implementacją usługi.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

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

<span data-ttu-id="8c7a7-116">Ten rozdział odnosi się do tego przykładowego kodu przy objaśnianiu różnych koncepcji i funkcji gRPC.</span><span class="sxs-lookup"><span data-stu-id="8c7a7-116">This chapter will refer to this example code when explaining different concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8c7a7-117">[Poprzednie](protobuf-maps.md)
>[dalej](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="8c7a7-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
