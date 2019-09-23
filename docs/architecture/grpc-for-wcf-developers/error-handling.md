---
title: Obsługa błędów — gRPC dla deweloperów WCF
description: DO ZAPISANIA
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 3535a00aad49f532eb5f5f778116454a12bfd639
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184457"
---
# <a name="error-handling"></a>Obsługa błędów

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Usługa WCF `FaultException<T>` używa `FaultContract` programu i zapewnia szczegółowe informacje o błędach, w tym obsługę standardu SOAP Fault.

Niestety bieżąca wersja gRPC nie ma złożoności znalezionej w programie WCF i ma ograniczoną wbudowaną obsługę błędów na podstawie prostych kodów stanu i metadanych. Poniższa tabela zawiera krótki przewodnik po najczęściej używanych kodach stanu:

| Kod stanu | Problem |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | Metoda nie została zapisywana. |
| `GRPC_STATUS_UNAVAILABLE` | Problem z całą usługą. |
| `GRPC_STATUS_UNKNOWN` | Nieprawidłowa odpowiedź. |
| `GRPC_STATUS_INTERNAL` | Problem z kodowaniem/dekodowaniem. |
| `GRPC_STATUS_UNAUTHENTICATED` | Uwierzytelnianie nie powiodło się. |
| `GRPC_STATUS_PERMISSION_DENIED` | Autoryzacja nie powiodła się. |
| `GRPC_STATUS_CANCELLED` | Wywołanie zostało anulowane, zazwyczaj przez wywołującego. |

## <a name="raising-errors-in-aspnet-core-grpc"></a>Wywoływanie błędów w ASP.NET Core gRPC

Usługa ASP.NET Core gRPC może wysłać odpowiedź z błędami przez wyrzucanie `RpcException`, które może zostać przechwycone przez klienta, tak jakby były w tym samym procesie. `RpcException` Musi zawierać kod stanu i opis, a opcjonalnie może zawierać metadane i dłuższy komunikat wyjątku. Metadane mogą służyć do wysyłania danych pomocniczych, podobnie jak `FaultContract` obiekty mogą przenosić dodatkowe dane dla błędów WCF.

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

Podobnie jak klienci WCF mogą przechwytywać <xref:System.ServiceModel.FaultException%601> błędy, klient gRPC może `RpcException` przechwytywać błędy. Ponieważ `RpcException` nie jest typem ogólnym, nie można przechwytywać różnych typów błędów w różnych blokach, ale C#można użyć funkcji *filtry wyjątków* , aby `catch` zadeklarować oddzielne bloki dla różnych kodów stanu, jak pokazano w poniższym przykładzie. przyklad

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
> Gdy podajesz dodatkowe metadane dla błędów, pamiętaj, aby udokumentować odpowiednie klucze i wartości w dokumentacji interfejsu API lub w komentarzach w `.proto` pliku.

## <a name="grpc-richer-error-model"></a>gRPC bogatszy model błędów

Od tej C# pory firma Google opracowała [bogatszy model błędów](https://cloud.google.com/apis/design/errors#error_model) , który jest bardziej podobny do [FaultContract](xref:System.ServiceModel.FaultContractAttribute)WCF, ale nie jest jeszcze obsługiwany. Obecnie jest ona dostępna tylko dla języka go, Java, Python i C++, ale obsługa C# jest oczekiwana w następnym roku.

>[!div class="step-by-step"]
>[Poprzedni](metadata.md)
>[Następny](ws-protocols.md)
