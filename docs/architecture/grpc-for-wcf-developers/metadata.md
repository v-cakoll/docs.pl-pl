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
# <a name="metadata"></a>Metadane

*Metadane* dotyczą dodatkowych danych, które mogą być przydatne podczas przetwarzania żądań i odpowiedzi, ale nie są częścią rzeczywistych danych aplikacji. Metadane mogą obejmować tokeny uwierzytelniania, identyfikatory żądań i Tagi do celów monitorowania oraz informacje o danych, takie jak liczba rekordów w zestawie danych.

Istnieje możliwość dodania ogólnych nagłówków klucz/wartość do komunikatów Windows Communication Foundation (WCF) przy użyciu <xref:System.ServiceModel.OperationContextScope> i właściwości <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> i obsłużenia ich przy użyciu <xref:System.ServiceModel.Channels.MessageProperties>.

wywołania gRPC i odpowiedzi mogą również zawierać metadane podobne do nagłówków HTTP. Te metadane są w większości niewidoczne do gRPC i są przesyłane przez program, aby były przetwarzane przez kod aplikacji lub oprogramowanie pośredniczące. Metadane są reprezentowane jako pary klucz/wartość, gdzie klucz jest ciągiem, a wartością jest ciąg lub dane binarne. Nie musisz określać metadanych w pliku `.proto`.

Metadane są obsługiwane przez klasę `Metadata` pakietu NuGet [GRPC. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) . Ta klasa może być używana z składnią inicjatora kolekcji.

Ten przykład pokazuje, jak dodać metadane do wywołania z C# klienta:

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

usługi gRPC mogą uzyskać dostęp do metadanych przy użyciu właściwości `RequestHeaders` `ServerCallContext` argumentu:

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

Usługi mogą wysyłać metadane do klientów za pomocą właściwości `ResponseTrailers` `ServerCallContext`:

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
>[Poprzednie](rpc-types.md)
>[dalej](error-handling.md)
