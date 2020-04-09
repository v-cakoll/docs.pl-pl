---
title: Obsługa błędów - gRPC dla programistów WCF
description: Tematy związane z obsługą błędów w gRPC. Zawiera tabelę najczęściej używanych kodów stanu.
ms.date: 09/02/2019
ms.openlocfilehash: 64a2355a8bd608c074f9bc420312b23aba0c1fb2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988950"
---
# <a name="error-handling"></a>Obsługa błędów

Windows Communication Foundation (WCF) używa i <xref:System.ServiceModel.FaultException%601> [FaultContract](xref:System.ServiceModel.FaultContractAttribute) do dostarczania szczegółowych informacji o błędach, w tym obsługi standardu błędu SOAP.

Niestety, w obecnej wersji gRPC brakuje wyrafinowania znalezionego w WCF i ma tylko ograniczoną wbudowaną obsługę błędów w oparciu o proste kody stanu i metadane. Poniższa tabela zawiera krótki przewodnik po najczęściej używanych kodach stanu:

| Kod stanu | Problem |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | Metoda nie została napisana. |
| `GRPC_STATUS_UNAVAILABLE` | Problem z całą usługą. |
| `GRPC_STATUS_UNKNOWN` | Nieprawidłowa odpowiedź. |
| `GRPC_STATUS_INTERNAL` | Problem z kodowaniem/dekodowaniem. |
| `GRPC_STATUS_UNAUTHENTICATED` | Uwierzytelnianie nie powiodło się. |
| `GRPC_STATUS_PERMISSION_DENIED` | Autoryzacja nie powiodła się. |
| `GRPC_STATUS_CANCELLED` | Połączenie zostało anulowane, zwykle przez rozmówcę. |

## <a name="raise-errors-in-aspnet-core-grpc"></a>Zwiększanie liczby błędów w ASP.NET Core gRPC

Usługa gRPC ASP.NET Core może wysłać odpowiedź na `RpcException`błąd, rzucając , które mogą zostać przechwycone przez klienta, tak jakby były w tym samym procesie. Musi `RpcException` zawierać kod stanu i opis i opcjonalnie może zawierać metadane i dłuższy komunikat wyjątku. Metadane mogą służyć do wysyłania danych `FaultContract` pomocniczych, podobnie jak obiekty mogą przenosić dodatkowe dane dla błędów WCF.

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

## <a name="catch-errors-in-grpc-clients"></a>Błędy catch u klientów gRPC

Podobnie jak klienci WCF można złapać <xref:System.ServiceModel.FaultException%601> błędy, klient `RpcException` gRPC można złapać do obsługi błędów. Ponieważ `RpcException` nie jest typem rodzajowym, nie można złapać różnych typów błędów w różnych blokach. Ale można użyć funkcji *filtrów wyjątków* języka `catch` C#do deklarowania oddzielnych bloków dla różnych kodów stanu, jak pokazano w poniższym przykładzie:

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
> Po podaniu dodatkowych metadanych dla błędów, należy udokumentować odpowiednie klucze i `.proto` wartości w dokumentacji interfejsu API lub w komentarzach w pliku.

## <a name="grpc-richer-error-model"></a>Bogatszy model błędu gRPC

Google opracowała [bogatszy model błędów,](https://cloud.google.com/apis/design/errors#error_model) który jest bardziej podobny do [FaultContract](xref:System.ServiceModel.FaultContractAttribute)WCF, ale ten model nie jest jeszcze obsługiwany w języku C#. Obecnie jest dostępna tylko dla go, Java, Python i C++.

>[!div class="step-by-step"]
>[Poprzedni](metadata.md)
>[następny](ws-protocols.md)
