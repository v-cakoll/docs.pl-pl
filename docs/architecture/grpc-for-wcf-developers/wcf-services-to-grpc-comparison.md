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
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="18d4a-103">Porównywanie WCF z gRPC</span><span class="sxs-lookup"><span data-stu-id="18d4a-103">Comparing WCF to gRPC</span></span>

<span data-ttu-id="18d4a-104">Poprzedni rozdział powinien mieć zapewnioną dobrą postać protobuf oraz sposób, w jaki gRPC obsługuje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="18d4a-104">The previous chapter should have given you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="18d4a-105">Przed rozpoczęciem pracy w ramach szczegółowej konwersji z programu WCF do gRPC należy zwrócić uwagę na to, jak zakres funkcji dostępnych obecnie w programie WCF jest obsługiwany w gRPC i jakie obejścia, których można użyć, gdy nie wydaje się, że nie jest odpowiednikiem gRPC.</span><span class="sxs-lookup"><span data-stu-id="18d4a-105">Before working through a detailed conversion from WCF to gRPC, it's important to look at how the range of features currently available in WCF are handled in gRPC and what workarounds you can use when there doesn't appear to be a gRPC equivalent.</span></span> <span data-ttu-id="18d4a-106">W szczególności ten rozdział będzie obejmować następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="18d4a-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="18d4a-107">Operacje i metody</span><span class="sxs-lookup"><span data-stu-id="18d4a-107">Operations and methods</span></span>
- <span data-ttu-id="18d4a-108">Powiązania i transporty</span><span class="sxs-lookup"><span data-stu-id="18d4a-108">Bindings and transports</span></span>
- <span data-ttu-id="18d4a-109">Typy wywołań RPC</span><span class="sxs-lookup"><span data-stu-id="18d4a-109">RPC types</span></span>
- <span data-ttu-id="18d4a-110">Metadane</span><span class="sxs-lookup"><span data-stu-id="18d4a-110">Metadata</span></span>
- <span data-ttu-id="18d4a-111">Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="18d4a-111">Error handling</span></span>
- <span data-ttu-id="18d4a-112">Protokoły WS-\*</span><span class="sxs-lookup"><span data-stu-id="18d4a-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="18d4a-113">przykład gRPC</span><span class="sxs-lookup"><span data-stu-id="18d4a-113">gRPC example</span></span>

<span data-ttu-id="18d4a-114">Podczas tworzenia nowego projektu ASP.NET Core gRPC 3,0 z programu Visual Studio 2019 lub wiersza polecenia zostanie wygenerowany odpowiednik gRPC "Hello world".</span><span class="sxs-lookup"><span data-stu-id="18d4a-114">When you create a new ASP.NET Core 3.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="18d4a-115">Składa się z pliku `greeter.proto`, który definiuje usługę i jej komunikaty, oraz plik `GreeterService.cs` z implementacją usługi.</span><span class="sxs-lookup"><span data-stu-id="18d4a-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

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

<span data-ttu-id="18d4a-116">Ten rozdział odnosi się do tego przykładowego kodu przy objaśnianiu różnych koncepcji i funkcji gRPC.</span><span class="sxs-lookup"><span data-stu-id="18d4a-116">This chapter will refer to this example code when explaining various concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="18d4a-117">[Poprzedni](protobuf-maps.md)
>[Następny](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="18d4a-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
