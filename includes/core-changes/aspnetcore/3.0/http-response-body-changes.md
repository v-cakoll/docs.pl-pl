---
ms.openlocfilehash: 22ef5d0f91a4f61ca75203f677bcc14e91d77dc1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394324"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="e2e1c-101">HTTP: zmiany infrastruktury treści odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="e2e1c-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="e2e1c-102">Infrastruktura do tworzenia kopii zapasowych treści odpowiedzi HTTP została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="e2e1c-103">Jeśli używasz bezpośrednio `HttpResponse`, nie musisz wprowadzać żadnych zmian w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="e2e1c-104">Zapoznaj się z dodatkowymi opcjami, jeśli są zawijane lub zastępowane `HttpResponse.Body` lub do `HttpContext.Features`.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e2e1c-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e2e1c-105">Version introduced</span></span>

<span data-ttu-id="e2e1c-106">3.0</span><span class="sxs-lookup"><span data-stu-id="e2e1c-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e2e1c-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="e2e1c-107">Old behavior</span></span>

<span data-ttu-id="e2e1c-108">Z treścią odpowiedzi HTTP są skojarzone trzy interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="e2e1c-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="e2e1c-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="e2e1c-109">New behavior</span></span>

<span data-ttu-id="e2e1c-110">Jeśli zastąpisz `HttpResponse.Body`, zastępuje cały `IHttpResponseBodyFeature` otoką wokół danego strumienia przy użyciu `StreamResponseBodyFeature`, aby zapewnić domyślne implementacje dla wszystkich oczekiwanych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="e2e1c-111">Ustawienie Przywróć oryginalny strumień przywraca tę zmianę.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e2e1c-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="e2e1c-112">Reason for change</span></span>

<span data-ttu-id="e2e1c-113">Motywacja polega na połączeniu interfejsów API treści odpowiedzi w jeden nowy interfejs funkcji.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e2e1c-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="e2e1c-114">Recommended action</span></span>

<span data-ttu-id="e2e1c-115">Użyj `IHttpResponseBodyFeature`, w przypadku których poprzednio użyto `IHttpResponseFeature.Body`, `IHttpSendFileFeature` lub `IHttpBufferingFeature`.</span><span class="sxs-lookup"><span data-stu-id="e2e1c-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="e2e1c-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="e2e1c-116">Category</span></span>

<span data-ttu-id="e2e1c-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e2e1c-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e2e1c-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e2e1c-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>
 
<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
