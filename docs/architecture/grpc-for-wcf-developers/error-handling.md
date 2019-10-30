---
title: Obsługa błędów — gRPC dla deweloperów WCF
description: DO ZAPISANIA
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 91f5789d8ed0f01f3ce2f3f9a6c6ccf14f245290
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094231"
---
# <a name="error-handling"></a>Obsługa błędów

Usługa WCF używa `FaultException<T>` i `FaultContract` do udostępniania szczegółowych informacji o błędach, w tym obsługi standardu SOAP Fault.

Niestety bieżąca wersja gRPC nie ma złożoności znalezionej w programie WCF i ma ograniczoną wbudowaną obsługę błędów na podstawie prostych kodów stanu i metadanych. Poniższa tabela zawiera krótki przewodnik po najczęściej używanych kodach stanu:

| Kod stanu | Związane |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | Metoda nie została zapisywana. |
| `GRPC_STATUS_UNAVAILABLE` | Problem z całą usługą. |
| `GRPC_STATUS_UNKNOWN` | Nieprawidłowa odpowiedź. |
| `GRPC_STATUS_INTERNAL` | Problem z kodowaniem/dekodowaniem. |
| `GRPC_STATUS_UNAUTHENTICATED` | Uwierzytelnianie nie powiodło się. |
| `GRPC_STATUS_PERMISSION_DENIED` | Autoryzacja nie powiodła się. |
| `GRPC_STATUS_CANCELLED` | Wywołanie zostało anulowane, zazwyczaj przez wywołującego. |

## <a name="raising-errors-in-aspnet-core-grpc"></a>Wywoływanie błędów w ASP.NET Core gRPC

Usługa ASP.NET Core gRPC może wysłać odpowiedź z błędami, zgłaszając `RpcException`, które mogą zostać przechwycone przez klienta tak, jakby były w tym samym procesie. `RpcException` musi zawierać kod stanu i opis, a opcjonalnie może zawierać metadane i dłuższy komunikat wyjątku. Metadane mogą służyć do wysyłania danych pomocniczych, podobnie jak obiekty `FaultContract` mogą zawierać dodatkowe dane dla błędów WCF.

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

## <a name="catching-errors-in-grpc-clients"></a>Przechwytywanie błędów w klientach gRPC

Podobnie jak klienci WCF mogą przechwytywać <xref:System.ServiceModel.FaultException%601> błędów, klient gRPC może przechwycić `RpcException`, aby obsłużyć błędy. Ponieważ `RpcException` nie jest typem ogólnym, nie można przechwytywać różnych typów błędów w różnych blokach, ale C#można użyć funkcji *filtrów wyjątków* , aby zadeklarować oddzielne bloki`catch`dla różnych kodów stanu, jak pokazano w następującym przykładzie:

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

Od tej C# pory firma Google opracowała [bogatszy model błędów](https://cloud.google.com/apis/design/errors#error_model) , który jest bardziej podobny do [FaultContract](xref:System.ServiceModel.FaultContractAttribute)WCF, ale nie jest jeszcze obsługiwany. Obecnie jest ona dostępna tylko dla języka go, Java, Python i C++, ale obsługa C# jest oczekiwana w następnym roku.

>[!div class="step-by-step"]
>[Poprzedni](metadata.md)
>[Następny](ws-protocols.md)
