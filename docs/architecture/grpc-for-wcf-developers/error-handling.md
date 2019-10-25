---
title: Obsługa błędów — gRPC dla deweloperów WCF
description: DO ZAPISANIA
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 2ef1a0b38d9b63af7244c6e0428c9adbcb1d6527
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846662"
---
# <a name="error-handling"></a><span data-ttu-id="6a338-103">Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="6a338-103">Error handling</span></span>

<span data-ttu-id="6a338-104">Usługa WCF używa `FaultException<T>` i `FaultContract` do udostępniania szczegółowych informacji o błędach, w tym obsługi standardu SOAP Fault.</span><span class="sxs-lookup"><span data-stu-id="6a338-104">WCF uses `FaultException<T>` and `FaultContract` to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="6a338-105">Niestety bieżąca wersja gRPC nie ma złożoności znalezionej w programie WCF i ma ograniczoną wbudowaną obsługę błędów na podstawie prostych kodów stanu i metadanych.</span><span class="sxs-lookup"><span data-stu-id="6a338-105">Unfortunately, the current version of gRPC lacks the sophistication found with WCF and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="6a338-106">Poniższa tabela zawiera krótki przewodnik po najczęściej używanych kodach stanu:</span><span class="sxs-lookup"><span data-stu-id="6a338-106">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="6a338-107">Kod stanu</span><span class="sxs-lookup"><span data-stu-id="6a338-107">Status Code</span></span> | <span data-ttu-id="6a338-108">Związane</span><span class="sxs-lookup"><span data-stu-id="6a338-108">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="6a338-109">Metoda nie została zapisywana.</span><span class="sxs-lookup"><span data-stu-id="6a338-109">Method hasn’t been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="6a338-110">Problem z całą usługą.</span><span class="sxs-lookup"><span data-stu-id="6a338-110">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="6a338-111">Nieprawidłowa odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="6a338-111">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="6a338-112">Problem z kodowaniem/dekodowaniem.</span><span class="sxs-lookup"><span data-stu-id="6a338-112">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="6a338-113">Uwierzytelnianie nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="6a338-113">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="6a338-114">Autoryzacja nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="6a338-114">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="6a338-115">Wywołanie zostało anulowane, zazwyczaj przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6a338-115">Call was canceled, usually by the caller.</span></span> |

## <a name="raising-errors-in-aspnet-core-grpc"></a><span data-ttu-id="6a338-116">Wywoływanie błędów w ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="6a338-116">Raising errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="6a338-117">Usługa ASP.NET Core gRPC może wysłać odpowiedź z błędami, zgłaszając `RpcException`, które mogą zostać przechwycone przez klienta tak, jakby były w tym samym procesie.</span><span class="sxs-lookup"><span data-stu-id="6a338-117">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="6a338-118">`RpcException` musi zawierać kod stanu i opis, a opcjonalnie może zawierać metadane i dłuższy komunikat wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6a338-118">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="6a338-119">Metadane mogą służyć do wysyłania danych pomocniczych, podobnie jak obiekty `FaultContract` mogą zawierać dodatkowe dane dla błędów WCF.</span><span class="sxs-lookup"><span data-stu-id="6a338-119">The metadata can be used to send supporting data, similar to how `FaultContract` objects could carry additional data for WCF errors.</span></span>

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

## <a name="catching-errors-in-grpc-clients"></a><span data-ttu-id="6a338-120">Przechwytywanie błędów w klientach gRPC</span><span class="sxs-lookup"><span data-stu-id="6a338-120">Catching errors in gRPC clients</span></span>

<span data-ttu-id="6a338-121">Podobnie jak klienci WCF mogą przechwytywać <xref:System.ServiceModel.FaultException%601> błędów, klient gRPC może przechwycić `RpcException`, aby obsłużyć błędy.</span><span class="sxs-lookup"><span data-stu-id="6a338-121">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="6a338-122">Ponieważ `RpcException` nie jest typem ogólnym, nie można przechwytywać różnych typów błędów w różnych blokach, ale C#można użyć funkcji *filtrów wyjątków* , aby zadeklarować oddzielne bloki`catch`dla różnych kodów stanu, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6a338-122">Since `RpcException` isn't a generic type, you can't catch different error types in different blocks, but you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="6a338-123">Gdy podajesz dodatkowe metadane dla błędów, pamiętaj, aby udokumentować odpowiednie klucze i wartości w dokumentacji interfejsu API lub w komentarzach w pliku `.proto`.</span><span class="sxs-lookup"><span data-stu-id="6a338-123">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="6a338-124">gRPC bogatszy model błędów</span><span class="sxs-lookup"><span data-stu-id="6a338-124">gRPC Richer Error Model</span></span>

<span data-ttu-id="6a338-125">Od tej C# pory firma Google opracowała [bogatszy model błędów](https://cloud.google.com/apis/design/errors#error_model) , który jest bardziej podobny do [FaultContract](xref:System.ServiceModel.FaultContractAttribute)WCF, ale nie jest jeszcze obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="6a338-125">Looking ahead, Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that is more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but isn't supported in C# yet.</span></span> <span data-ttu-id="6a338-126">Obecnie jest ona dostępna tylko dla języka go, Java, Python i C++, ale obsługa C# jest oczekiwana w następnym roku.</span><span class="sxs-lookup"><span data-stu-id="6a338-126">Currently, it's only available for Go, Java, Python and C++, but support for C# is expected to come next year.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6a338-127">[Poprzedni](metadata.md)
>[Następny](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="6a338-127">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
