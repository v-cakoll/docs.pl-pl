---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198526"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="a140f-101">HTTP: zmiany infrastruktury treści odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="a140f-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="a140f-102">Infrastruktura do tworzenia kopii zapasowych treści odpowiedzi HTTP została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="a140f-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="a140f-103">Jeśli używasz `HttpResponse` bezpośrednio, nie musisz wprowadzać żadnych zmian w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a140f-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="a140f-104">Przeczytaj więcej w przypadku zawijania lub zamieniania `HttpResponse.Body` lub `HttpContext.Features`uzyskiwania dostępu do.</span><span class="sxs-lookup"><span data-stu-id="a140f-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a140f-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="a140f-105">Version introduced</span></span>

<span data-ttu-id="a140f-106">3.0</span><span class="sxs-lookup"><span data-stu-id="a140f-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a140f-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="a140f-107">Old behavior</span></span>

<span data-ttu-id="a140f-108">Z treścią odpowiedzi HTTP są skojarzone trzy interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="a140f-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="a140f-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="a140f-109">New behavior</span></span>

<span data-ttu-id="a140f-110">Jeśli zastąpisz `HttpResponse.Body`, zastępuje cały `IHttpResponseBodyFeature` element otoką wokół danego strumienia przy użyciu `StreamResponseBodyFeature` , aby zapewnić domyślne implementacje dla wszystkich oczekiwanych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="a140f-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="a140f-111">Ustawienie Przywróć oryginalny strumień przywraca tę zmianę.</span><span class="sxs-lookup"><span data-stu-id="a140f-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a140f-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="a140f-112">Reason for change</span></span>

<span data-ttu-id="a140f-113">Motywacja polega na połączeniu interfejsów API treści odpowiedzi w jeden nowy interfejs funkcji.</span><span class="sxs-lookup"><span data-stu-id="a140f-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a140f-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="a140f-114">Recommended action</span></span>

<span data-ttu-id="a140f-115">Użyj `IHttpResponseBodyFeature` tam, gdzie wcześniej `IHttpResponseFeature.Body`korzystano `IHttpSendFileFeature`z, `IHttpBufferingFeature`lub.</span><span class="sxs-lookup"><span data-stu-id="a140f-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="a140f-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="a140f-116">Category</span></span>

<span data-ttu-id="a140f-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a140f-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a140f-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a140f-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
