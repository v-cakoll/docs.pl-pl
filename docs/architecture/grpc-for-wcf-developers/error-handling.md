---
title: Obsługa błędów — gRPC dla deweloperów WCF
description: Tematy dotyczące obsługi błędów w gRPC. Zawiera tabelę zawierającą najczęściej używane kody stanu.
ms.date: 09/02/2019
ms.openlocfilehash: c380c651f854adc97e8b2ead36d30c3b83662aac
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542796"
---
# <a name="error-handling"></a>Obsługa błędów

Windows Communication Foundation (WCF) używa <xref:System.ServiceModel.FaultException%601> i [FaultContract](xref:System.ServiceModel.FaultContractAttribute) w celu zapewnienia szczegółowych informacji o błędzie, w tym obsługi standardu SOAP Fault.

Niestety, bieżąca wersja gRPC nie ma złożoności znalezionej w programie WCF i ma ograniczoną wbudowaną obsługę błędów na podstawie prostych kodów stanu i metadanych. Poniższa tabela zawiera krótki przewodnik po najczęściej używanych kodach stanu:

| Kod stanu | Problem |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | Metoda nie została zapisywana. |
| `GRPC_STATUS_UNAVAILABLE` | Problem z całą usługą. |
| `GRPC_STATUS_UNKNOWN` | Nieprawidłowa odpowiedź. |
| `GRPC_STATUS_INTERNAL` | Problem z kodowaniem/dekodowaniem. |
| `GRPC_STATUS_UNAUTHENTICATED` | Uwierzytelnianie nie powiodło się. |
| `GRPC_STATUS_PERMISSION_DENIED` | Autoryzacja nie powiodła się. |
| `GRPC_STATUS_CANCELLED` | Wywołanie zostało anulowane, zazwyczaj przez wywołującego. |

## <a name="raise-errors-in-aspnet-core-grpc"></a>Zgłoś błędy w ASP.NET Core gRPC

Usługa ASP.NET Core gRPC może wysłać odpowiedź z błędami, zgłaszając `RpcException`, które mogą zostać przechwycone przez klienta tak, jakby były w tym samym procesie. `RpcException` musi zawierać kod stanu i opis, a opcjonalnie może zawierać metadane i dłuższy komunikat wyjątku. Metadane mogą służyć do wysyłania danych pomocniczych, podobnie jak obiekty `FaultContract` mogą przenosić dodatkowe dane dla błędów WCF.

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var user = context.GetHttpContext().User;
    if (!ValidateUser(user))
    {
        var metadata = new Metadata
        {
            { "User", user.Identity.Name }
        };
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Permission denied"), metadata);
    }
}
```

## <a name="catch-errors-in-grpc-clients"></a>Błędy przechwytywania w klientach gRPC

Podobnie jak klienci WCF mogą przechwytywać <xref:System.ServiceModel.FaultException%601> błędów, klient gRPC może przechwycić `RpcException`, aby obsłużyć błędy. Ponieważ `RpcException` nie jest typem ogólnym, nie można przechwytywać różnych typów błędów w różnych blokach. Można jednak użyć C#funkcji *filtry wyjątków* , aby zadeklarować oddzielne bloki `catch` dla różnych kodów stanu, jak pokazano w następującym przykładzie:

```csharp
try
{
    var portfolio = await client.GetPortfolioAsync(new GetPortfolioRequest { Id = id });
}
catch (RpcException ex) when (ex.StatusCode == StatusCode.PermissionDenied)
{
    var userEntry = ex.Trailers.FirstOrDefault(e => e.Key == "User");
    Console.WriteLine($"User '{userEntry.Value}' does not have permission to view this portfolio.");
}
catch (RpcException)
{
    // Handle any other error type ...
}
```

> [!IMPORTANT]
> Gdy podajesz dodatkowe metadane dla błędów, pamiętaj, aby udokumentować odpowiednie klucze i wartości w dokumentacji interfejsu API lub w komentarzach w pliku `.proto`.

## <a name="grpc-richer-error-model"></a>gRPC bogatszy model błędów

Firma Google opracowała [bogatszy model błędów](https://cloud.google.com/apis/design/errors#error_model) , który jest bardziej podobny do [FaultContract](xref:System.ServiceModel.FaultContractAttribute)WCF, ale ten model nie jest C# jeszcze obsługiwany. Obecnie jest ona dostępna tylko dla języka go, Java, Python i C++.

>[!div class="step-by-step"]
>[Poprzednie](metadata.md)
>[dalej](ws-protocols.md)
