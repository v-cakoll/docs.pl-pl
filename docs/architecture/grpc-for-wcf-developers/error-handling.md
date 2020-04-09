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
# <a name="error-handling"></a><span data-ttu-id="99fd4-104">Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="99fd4-104">Error handling</span></span>

<span data-ttu-id="99fd4-105">Windows Communication Foundation (WCF) używa i <xref:System.ServiceModel.FaultException%601> [FaultContract](xref:System.ServiceModel.FaultContractAttribute) do dostarczania szczegółowych informacji o błędach, w tym obsługi standardu błędu SOAP.</span><span class="sxs-lookup"><span data-stu-id="99fd4-105">Windows Communication Foundation (WCF) uses <xref:System.ServiceModel.FaultException%601> and [FaultContract](xref:System.ServiceModel.FaultContractAttribute) to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="99fd4-106">Niestety, w obecnej wersji gRPC brakuje wyrafinowania znalezionego w WCF i ma tylko ograniczoną wbudowaną obsługę błędów w oparciu o proste kody stanu i metadane.</span><span class="sxs-lookup"><span data-stu-id="99fd4-106">Unfortunately, the current version of gRPC lacks the sophistication found with WCF, and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="99fd4-107">Poniższa tabela zawiera krótki przewodnik po najczęściej używanych kodach stanu:</span><span class="sxs-lookup"><span data-stu-id="99fd4-107">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="99fd4-108">Kod stanu</span><span class="sxs-lookup"><span data-stu-id="99fd4-108">Status code</span></span> | <span data-ttu-id="99fd4-109">Problem</span><span class="sxs-lookup"><span data-stu-id="99fd4-109">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="99fd4-110">Metoda nie została napisana.</span><span class="sxs-lookup"><span data-stu-id="99fd4-110">Method hasn't been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="99fd4-111">Problem z całą usługą.</span><span class="sxs-lookup"><span data-stu-id="99fd4-111">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="99fd4-112">Nieprawidłowa odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="99fd4-112">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="99fd4-113">Problem z kodowaniem/dekodowaniem.</span><span class="sxs-lookup"><span data-stu-id="99fd4-113">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="99fd4-114">Uwierzytelnianie nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="99fd4-114">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="99fd4-115">Autoryzacja nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="99fd4-115">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="99fd4-116">Połączenie zostało anulowane, zwykle przez rozmówcę.</span><span class="sxs-lookup"><span data-stu-id="99fd4-116">Call was canceled, usually by the caller.</span></span> |

## <a name="raise-errors-in-aspnet-core-grpc"></a><span data-ttu-id="99fd4-117">Zwiększanie liczby błędów w ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="99fd4-117">Raise errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="99fd4-118">Usługa gRPC ASP.NET Core może wysłać odpowiedź na `RpcException`błąd, rzucając , które mogą zostać przechwycone przez klienta, tak jakby były w tym samym procesie.</span><span class="sxs-lookup"><span data-stu-id="99fd4-118">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="99fd4-119">Musi `RpcException` zawierać kod stanu i opis i opcjonalnie może zawierać metadane i dłuższy komunikat wyjątku.</span><span class="sxs-lookup"><span data-stu-id="99fd4-119">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="99fd4-120">Metadane mogą służyć do wysyłania danych `FaultContract` pomocniczych, podobnie jak obiekty mogą przenosić dodatkowe dane dla błędów WCF.</span><span class="sxs-lookup"><span data-stu-id="99fd4-120">The metadata can be used to send supporting data, similar to how `FaultContract` objects can carry additional data for WCF errors.</span></span>

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

## <a name="catch-errors-in-grpc-clients"></a><span data-ttu-id="99fd4-121">Błędy catch u klientów gRPC</span><span class="sxs-lookup"><span data-stu-id="99fd4-121">Catch errors in gRPC clients</span></span>

<span data-ttu-id="99fd4-122">Podobnie jak klienci WCF można złapać <xref:System.ServiceModel.FaultException%601> błędy, klient `RpcException` gRPC można złapać do obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="99fd4-122">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="99fd4-123">Ponieważ `RpcException` nie jest typem rodzajowym, nie można złapać różnych typów błędów w różnych blokach.</span><span class="sxs-lookup"><span data-stu-id="99fd4-123">Because `RpcException` isn't a generic type, you can't catch different error types in different blocks.</span></span> <span data-ttu-id="99fd4-124">Ale można użyć funkcji *filtrów wyjątków* języka `catch` C#do deklarowania oddzielnych bloków dla różnych kodów stanu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="99fd4-124">But you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="99fd4-125">Po podaniu dodatkowych metadanych dla błędów, należy udokumentować odpowiednie klucze i `.proto` wartości w dokumentacji interfejsu API lub w komentarzach w pliku.</span><span class="sxs-lookup"><span data-stu-id="99fd4-125">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="99fd4-126">Bogatszy model błędu gRPC</span><span class="sxs-lookup"><span data-stu-id="99fd4-126">gRPC richer error model</span></span>

<span data-ttu-id="99fd4-127">Google opracowała [bogatszy model błędów,](https://cloud.google.com/apis/design/errors#error_model) który jest bardziej podobny do [FaultContract](xref:System.ServiceModel.FaultContractAttribute)WCF, ale ten model nie jest jeszcze obsługiwany w języku C#.</span><span class="sxs-lookup"><span data-stu-id="99fd4-127">Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that's more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but this model isn't supported in C# yet.</span></span> <span data-ttu-id="99fd4-128">Obecnie jest dostępna tylko dla go, Java, Python i C++.</span><span class="sxs-lookup"><span data-stu-id="99fd4-128">Currently, it's only available for Go, Java, Python, and C++.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="99fd4-129">[Poprzedni](metadata.md)
>[następny](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="99fd4-129">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
