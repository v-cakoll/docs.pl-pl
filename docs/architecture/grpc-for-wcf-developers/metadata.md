---
title: Metadata — gRPC dla deweloperów WCF
description: Jak metadane są używane w programie gRPC, aby przekazać dodatkowy kontekst między klientami i serwerami.
ms.date: 09/02/2019
ms.openlocfilehash: 64fa94d1e63af480cbc7363631de161c5b8b8fb8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628582"
---
# <a name="metadata"></a><span data-ttu-id="fc727-103">Metadane</span><span class="sxs-lookup"><span data-stu-id="fc727-103">Metadata</span></span>

<span data-ttu-id="fc727-104">*Metadane* dotyczą dodatkowych danych, które mogą być przydatne podczas przetwarzania żądań i odpowiedzi, ale nie są częścią rzeczywistych danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fc727-104">*Metadata* refers to additional data that might be useful during the processing of requests and responses but that’s not part of the actual application data.</span></span> <span data-ttu-id="fc727-105">Metadane mogą obejmować tokeny uwierzytelniania, identyfikatory żądań i Tagi do celów monitorowania oraz informacje o danych, takie jak liczba rekordów w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="fc727-105">Metadata might include authentication tokens, request identifiers and tags for monitoring purposes, and information about the data, like the number of records in a dataset.</span></span>

<span data-ttu-id="fc727-106">Istnieje możliwość dodania ogólnych nagłówków klucz/wartość do komunikatów Windows Communication Foundation (WCF) przy użyciu <xref:System.ServiceModel.OperationContextScope> i właściwości <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> i obsłużenia ich przy użyciu <xref:System.ServiceModel.Channels.MessageProperties>.</span><span class="sxs-lookup"><span data-stu-id="fc727-106">It's possible to add generic key/value headers to Windows Communication Foundation (WCF) messages by using an <xref:System.ServiceModel.OperationContextScope> and the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> property and handle them by using <xref:System.ServiceModel.Channels.MessageProperties>.</span></span>

<span data-ttu-id="fc727-107">wywołania gRPC i odpowiedzi mogą również zawierać metadane podobne do nagłówków HTTP.</span><span class="sxs-lookup"><span data-stu-id="fc727-107">gRPC calls and responses can also include metadata that's similar to HTTP headers.</span></span> <span data-ttu-id="fc727-108">Te metadane są w większości niewidoczne do gRPC i są przesyłane przez program, aby były przetwarzane przez kod aplikacji lub oprogramowanie pośredniczące.</span><span class="sxs-lookup"><span data-stu-id="fc727-108">This metadata is mostly invisible to gRPC itself and is passed through to be processed by your application code or middleware.</span></span> <span data-ttu-id="fc727-109">Metadane są reprezentowane jako pary klucz/wartość, gdzie klucz jest ciągiem, a wartością jest ciąg lub dane binarne.</span><span class="sxs-lookup"><span data-stu-id="fc727-109">Metadata is represented as key/value pairs, where the key is a string and the value is either a string or binary data.</span></span> <span data-ttu-id="fc727-110">Nie musisz określać metadanych w pliku `.proto`.</span><span class="sxs-lookup"><span data-stu-id="fc727-110">You don’t need to specify metadata in the `.proto` file.</span></span>

<span data-ttu-id="fc727-111">Metadane są obsługiwane przez klasę `Metadata` pakietu NuGet [GRPC. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) .</span><span class="sxs-lookup"><span data-stu-id="fc727-111">Metadata is handled by the `Metadata` class of the [Grpc.Core.Api](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet package.</span></span> <span data-ttu-id="fc727-112">Ta klasa może być używana z składnią inicjatora kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fc727-112">This class can be used with collection initializer syntax.</span></span>

<span data-ttu-id="fc727-113">Ten przykład pokazuje, jak dodać metadane do wywołania z C# klienta:</span><span class="sxs-lookup"><span data-stu-id="fc727-113">This example shows how to add metadata to a call from a C# client:</span></span>

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

<span data-ttu-id="fc727-114">usługi gRPC mogą uzyskać dostęp do metadanych przy użyciu właściwości `RequestHeaders` `ServerCallContext` argumentu:</span><span class="sxs-lookup"><span data-stu-id="fc727-114">gRPC services can access metadata from the `ServerCallContext` argument's `RequestHeaders` property:</span></span>

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

<span data-ttu-id="fc727-115">Usługi mogą wysyłać metadane do klientów za pomocą właściwości `ResponseTrailers` `ServerCallContext`:</span><span class="sxs-lookup"><span data-stu-id="fc727-115">Services can send metadata to clients by using the `ResponseTrailers` property of `ServerCallContext`:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="fc727-116">[Poprzednie](rpc-types.md)
>[dalej](error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="fc727-116">[Previous](rpc-types.md)
[Next](error-handling.md)</span></span>
