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
# <a name="error-handling"></a><span data-ttu-id="2079d-104">Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="2079d-104">Error handling</span></span>

<span data-ttu-id="2079d-105">Windows Communication Foundation (WCF) używa <xref:System.ServiceModel.FaultException%601> i [FaultContract](xref:System.ServiceModel.FaultContractAttribute) w celu zapewnienia szczegółowych informacji o błędzie, w tym obsługi standardu SOAP Fault.</span><span class="sxs-lookup"><span data-stu-id="2079d-105">Windows Communication Foundation (WCF) uses <xref:System.ServiceModel.FaultException%601> and [FaultContract](xref:System.ServiceModel.FaultContractAttribute) to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="2079d-106">Niestety, bieżąca wersja gRPC nie ma złożoności znalezionej w programie WCF i ma ograniczoną wbudowaną obsługę błędów na podstawie prostych kodów stanu i metadanych.</span><span class="sxs-lookup"><span data-stu-id="2079d-106">Unfortunately, the current version of gRPC lacks the sophistication found with WCF, and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="2079d-107">Poniższa tabela zawiera krótki przewodnik po najczęściej używanych kodach stanu:</span><span class="sxs-lookup"><span data-stu-id="2079d-107">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="2079d-108">Kod stanu</span><span class="sxs-lookup"><span data-stu-id="2079d-108">Status code</span></span> | <span data-ttu-id="2079d-109">Problem</span><span class="sxs-lookup"><span data-stu-id="2079d-109">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="2079d-110">Metoda nie została zapisywana.</span><span class="sxs-lookup"><span data-stu-id="2079d-110">Method hasn’t been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="2079d-111">Problem z całą usługą.</span><span class="sxs-lookup"><span data-stu-id="2079d-111">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="2079d-112">Nieprawidłowa odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="2079d-112">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="2079d-113">Problem z kodowaniem/dekodowaniem.</span><span class="sxs-lookup"><span data-stu-id="2079d-113">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="2079d-114">Uwierzytelnianie nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="2079d-114">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="2079d-115">Autoryzacja nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="2079d-115">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="2079d-116">Wywołanie zostało anulowane, zazwyczaj przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2079d-116">Call was canceled, usually by the caller.</span></span> |

## <a name="raise-errors-in-aspnet-core-grpc"></a><span data-ttu-id="2079d-117">Zgłoś błędy w ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="2079d-117">Raise errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="2079d-118">Usługa ASP.NET Core gRPC może wysłać odpowiedź z błędami, zgłaszając `RpcException`, które mogą zostać przechwycone przez klienta tak, jakby były w tym samym procesie.</span><span class="sxs-lookup"><span data-stu-id="2079d-118">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="2079d-119">`RpcException` musi zawierać kod stanu i opis, a opcjonalnie może zawierać metadane i dłuższy komunikat wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2079d-119">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="2079d-120">Metadane mogą służyć do wysyłania danych pomocniczych, podobnie jak obiekty `FaultContract` mogą przenosić dodatkowe dane dla błędów WCF.</span><span class="sxs-lookup"><span data-stu-id="2079d-120">The metadata can be used to send supporting data, similar to how `FaultContract` objects can carry additional data for WCF errors.</span></span>

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

## <a name="catch-errors-in-grpc-clients"></a><span data-ttu-id="2079d-121">Błędy przechwytywania w klientach gRPC</span><span class="sxs-lookup"><span data-stu-id="2079d-121">Catch errors in gRPC clients</span></span>

<span data-ttu-id="2079d-122">Podobnie jak klienci WCF mogą przechwytywać <xref:System.ServiceModel.FaultException%601> błędów, klient gRPC może przechwycić `RpcException`, aby obsłużyć błędy.</span><span class="sxs-lookup"><span data-stu-id="2079d-122">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="2079d-123">Ponieważ `RpcException` nie jest typem ogólnym, nie można przechwytywać różnych typów błędów w różnych blokach.</span><span class="sxs-lookup"><span data-stu-id="2079d-123">Because `RpcException` isn't a generic type, you can't catch different error types in different blocks.</span></span> <span data-ttu-id="2079d-124">Można jednak użyć C#funkcji *filtry wyjątków* , aby zadeklarować oddzielne bloki `catch` dla różnych kodów stanu, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2079d-124">But you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="2079d-125">Gdy podajesz dodatkowe metadane dla błędów, pamiętaj, aby udokumentować odpowiednie klucze i wartości w dokumentacji interfejsu API lub w komentarzach w pliku `.proto`.</span><span class="sxs-lookup"><span data-stu-id="2079d-125">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="2079d-126">gRPC bogatszy model błędów</span><span class="sxs-lookup"><span data-stu-id="2079d-126">gRPC richer error model</span></span>

<span data-ttu-id="2079d-127">Firma Google opracowała [bogatszy model błędów](https://cloud.google.com/apis/design/errors#error_model) , który jest bardziej podobny do [FaultContract](xref:System.ServiceModel.FaultContractAttribute)WCF, ale ten model nie jest C# jeszcze obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="2079d-127">Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that's more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but this model isn't supported in C# yet.</span></span> <span data-ttu-id="2079d-128">Obecnie jest ona dostępna tylko dla języka go, Java, Python i C++.</span><span class="sxs-lookup"><span data-stu-id="2079d-128">Currently, it's only available for Go, Java, Python, and C++.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2079d-129">[Poprzednie](metadata.md)
>[dalej](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="2079d-129">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
