---
title: Metadata — gRPC dla deweloperów WCF
description: Jak metadane są używane w gRPC do przekazywania dodatkowego kontekstu między klientami i serwerami
ms.date: 09/02/2019
ms.openlocfilehash: 723d877bfbf0c2b0785949ff15939aedbac4d4e9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971975"
---
# <a name="metadata"></a>Metadane

"Metadane" to dodatkowe dane, które mogą być przydatne podczas przetwarzania żądań i odpowiedzi, ale nie są częścią rzeczywistych danych aplikacji. Metadane mogą obejmować tokeny uwierzytelniania, identyfikatory żądań i Tagi do celów monitorowania lub informacje o danych, takie jak liczba rekordów w zestawie danych.

Istnieje możliwość dodania ogólnych nagłówków klucz/wartość do komunikatów WCF przy użyciu <xref:System.ServiceModel.OperationContextScope> i właściwości <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> i obsłużenia ich przy użyciu <xref:System.ServiceModel.Channels.MessageProperties>.

wywołania gRPC i odpowiedzi mogą również zawierać metadane podobne do nagłówków HTTP. Są one w większości niewidoczne do gRPC i są przenoszone przez program w celu przetworzenia przez kod aplikacji lub oprogramowanie pośredniczące. Metadane są reprezentowane jako pary klucz/wartość, gdzie klucz jest ciągiem, a wartością jest ciąg lub dane binarne. Nie musisz określać metadanych w pliku `.proto`.

Metadane są obsługiwane za pomocą klasy `Metadata` z pakietu NuGet [GRPC. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) . Ta klasa może być używana z składnią inicjatora kolekcji.

Poniższy przykład pokazuje, jak dodać metadane do wywołania z C# klienta:

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

Usługi mogą wysyłać metadane do klientów przy użyciu właściwości `ResponseTrailers` `ServerCallContext`:

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
>[Poprzedni](rpc-types.md)
>[Następny](error-handling.md)
