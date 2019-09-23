---
title: Metadata — gRPC dla deweloperów WCF
description: Jak metadane są używane w gRPC do przekazywania dodatkowego kontekstu między klientami i serwerami
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1a2131fa3ee3112eaa3c3e7f7c97017fea6b1004
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184331"
---
# <a name="metadata"></a><span data-ttu-id="e131d-103">Metadane</span><span class="sxs-lookup"><span data-stu-id="e131d-103">Metadata</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e131d-104">"Metadane" to dodatkowe dane, które mogą być przydatne podczas przetwarzania żądań i odpowiedzi, ale nie są częścią rzeczywistych danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e131d-104">"Metadata" refers to additional data that may be useful while processing requests and responses but is not part of the actual application data.</span></span> <span data-ttu-id="e131d-105">Metadane mogą obejmować tokeny uwierzytelniania, identyfikatory żądań i Tagi do celów monitorowania lub informacje o danych, takie jak liczba rekordów w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="e131d-105">Metadata might include authentication tokens, request identifiers and tags for monitoring purposes, or information about the data like the number of records in a dataset.</span></span>

<span data-ttu-id="e131d-106">Istnieje możliwość dodania ogólnych nagłówków klucz/wartość do komunikatów WCF przy użyciu <xref:System.ServiceModel.OperationContextScope> <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> i i obsłużenia ich przy użyciu <xref:System.ServiceModel.Channels.MessageProperties>.</span><span class="sxs-lookup"><span data-stu-id="e131d-106">It's possible to add generic key/value headers to WCF messages using an <xref:System.ServiceModel.OperationContextScope> and the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> property, and handle them using <xref:System.ServiceModel.Channels.MessageProperties>.</span></span>

<span data-ttu-id="e131d-107">wywołania gRPC i odpowiedzi mogą również zawierać metadane podobne do nagłówków HTTP.</span><span class="sxs-lookup"><span data-stu-id="e131d-107">gRPC calls and responses can also include metadata similar to HTTP headers.</span></span> <span data-ttu-id="e131d-108">Są one w większości niewidoczne do gRPC i są przenoszone przez program w celu przetworzenia przez kod aplikacji lub oprogramowanie pośredniczące.</span><span class="sxs-lookup"><span data-stu-id="e131d-108">These are mostly invisible to gRPC itself and are passed through to be processed by your application code or middleware.</span></span> <span data-ttu-id="e131d-109">Metadane są reprezentowane jako pary klucz/wartość, gdzie klucz jest ciągiem, a wartością jest ciąg lub dane binarne.</span><span class="sxs-lookup"><span data-stu-id="e131d-109">Metadata is represented as key/value pairs where the key is a string and the value is either a string or binary data.</span></span> <span data-ttu-id="e131d-110">Nie musisz określać metadanych w `.proto` pliku.</span><span class="sxs-lookup"><span data-stu-id="e131d-110">You don’t need to specify metadata in the `.proto` file.</span></span>

<span data-ttu-id="e131d-111">Metadane są obsługiwane przy użyciu `Metadata` klasy z pakietu NuGet [GRPC. Core](https://www.nuget.org/packages/Grpc.Core/) .</span><span class="sxs-lookup"><span data-stu-id="e131d-111">Metadata is handled using the `Metadata` class from the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core/) NuGet package.</span></span> <span data-ttu-id="e131d-112">Ta klasa może być używana z składnią inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e131d-112">This class can be used with collection initializer syntax.</span></span>

<span data-ttu-id="e131d-113">Poniższy przykład pokazuje, jak dodać metadane do wywołania z C# klienta:</span><span class="sxs-lookup"><span data-stu-id="e131d-113">The following example shows how to add metadata to a call from a C# client:</span></span>

```csharp
var metadata = new Metadata
{
    { "Requester", _clientName }
};

var request = new GetPortfolioRequest
{
    Id = portfolioId
};

var response = await client.GetPortfolioAsync(request, metadata);
```

<span data-ttu-id="e131d-114">usługi gRPC mogą uzyskać dostęp do metadanych `ServerCallContext` przy użyciu `RequestHeaders` właściwości argumentu:</span><span class="sxs-lookup"><span data-stu-id="e131d-114">gRPC services can access metadata from the `ServerCallContext` argument's `RequestHeaders` property:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var requesterHeader = context.RequestHeaders.FirstOrDefault(e => e.Key == "Requester");
    if (requesterHeader != null)
    {
        _logger.LogInformation($"Request from {requesterHeader.Value}");
    }
    // ...
}
```

<span data-ttu-id="e131d-115">Usługi mogą wysyłać metadane do klientów przy użyciu `ResponseTrailers` `ServerCallContext`właściwości:</span><span class="sxs-lookup"><span data-stu-id="e131d-115">Services can send metadata to clients using the `ResponseTrailers` property of `ServerCallContext`:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="e131d-116">[Poprzedni](rpc-types.md)
>[Następny](error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="e131d-116">[Previous](rpc-types.md)
[Next](error-handling.md)</span></span>
