---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198526"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="ea2f2-101">HTTP: zmiany infrastruktury treści odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="ea2f2-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="ea2f2-102">Infrastruktura do tworzenia kopii zapasowych treści odpowiedzi HTTP została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="ea2f2-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="ea2f2-103">Jeśli używasz bezpośrednio `HttpResponse`, nie musisz wprowadzać żadnych zmian w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ea2f2-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="ea2f2-104">Zapoznaj się z dodatkowymi opcjami, jeśli są zawijane lub zastępowane `HttpResponse.Body` lub do `HttpContext.Features`.</span><span class="sxs-lookup"><span data-stu-id="ea2f2-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ea2f2-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="ea2f2-105">Version introduced</span></span>

<span data-ttu-id="ea2f2-106">3.0</span><span class="sxs-lookup"><span data-stu-id="ea2f2-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ea2f2-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="ea2f2-107">Old behavior</span></span>

<span data-ttu-id="ea2f2-108">Z treścią odpowiedzi HTTP są skojarzone trzy interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="ea2f2-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="ea2f2-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="ea2f2-109">New behavior</span></span>

<span data-ttu-id="ea2f2-110">Jeśli zastąpisz `HttpResponse.Body`, zastępuje cały `IHttpResponseBodyFeature` otoką wokół danego strumienia przy użyciu `StreamResponseBodyFeature`, aby zapewnić domyślne implementacje dla wszystkich oczekiwanych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="ea2f2-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="ea2f2-111">Ustawienie Przywróć oryginalny strumień przywraca tę zmianę.</span><span class="sxs-lookup"><span data-stu-id="ea2f2-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ea2f2-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="ea2f2-112">Reason for change</span></span>

<span data-ttu-id="ea2f2-113">Motywacja polega na połączeniu interfejsów API treści odpowiedzi w jeden nowy interfejs funkcji.</span><span class="sxs-lookup"><span data-stu-id="ea2f2-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ea2f2-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="ea2f2-114">Recommended action</span></span>

<span data-ttu-id="ea2f2-115">Użyj `IHttpResponseBodyFeature`, w przypadku których poprzednio użyto `IHttpResponseFeature.Body`, `IHttpSendFileFeature` lub `IHttpBufferingFeature`.</span><span class="sxs-lookup"><span data-stu-id="ea2f2-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="ea2f2-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="ea2f2-116">Category</span></span>

<span data-ttu-id="ea2f2-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea2f2-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ea2f2-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="ea2f2-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
