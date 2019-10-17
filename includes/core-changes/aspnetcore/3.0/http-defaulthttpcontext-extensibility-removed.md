---
ms.openlocfilehash: 177617569a93e09f4c2a05acc21dce362edd58bc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394209"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="d2d68-101">HTTP: Usunięto rozszerzalność DefaultHttpContext</span><span class="sxs-lookup"><span data-stu-id="d2d68-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="d2d68-102">W ramach ulepszeń wydajności ASP.NET Core 3,0 została usunięta Funkcja rozszerzania `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="d2d68-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="d2d68-103">Klasa jest teraz `sealed`.</span><span class="sxs-lookup"><span data-stu-id="d2d68-103">The class is now `sealed`.</span></span> <span data-ttu-id="d2d68-104">Aby uzyskać więcej informacji, zobacz [ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="d2d68-104">For more information, see [aspnet/AspNetCore#6504](https://github.com/aspnet/AspNetCore/pull/6504).</span></span>

<span data-ttu-id="d2d68-105">Jeśli testy jednostkowe używają `Mock<DefaultHttpContext>`, zamiast tego należy użyć `Mock<HttpContext>`.</span><span class="sxs-lookup"><span data-stu-id="d2d68-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` instead.</span></span> 

<span data-ttu-id="d2d68-106">W przypadku dyskusji zobacz [ASPNET/AspNetCore # 6534](https://github.com/aspnet/AspNetCore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="d2d68-106">For discussion, see [aspnet/AspNetCore#6534](https://github.com/aspnet/AspNetCore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d2d68-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="d2d68-107">Version introduced</span></span>

<span data-ttu-id="d2d68-108">3.0</span><span class="sxs-lookup"><span data-stu-id="d2d68-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d2d68-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="d2d68-109">Old behavior</span></span>

<span data-ttu-id="d2d68-110">Klasy mogą pochodzić od `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="d2d68-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d2d68-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="d2d68-111">New behavior</span></span>

<span data-ttu-id="d2d68-112">Klasy nie mogą pochodzić od `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="d2d68-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d2d68-113">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="d2d68-113">Reason for change</span></span>

<span data-ttu-id="d2d68-114">Rozszerzalność podano początkowo, aby umożliwić buforowanie `HttpContext`, ale wprowadza niepotrzebną złożoność i utrudnia inne optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="d2d68-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d2d68-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="d2d68-115">Recommended action</span></span>

<span data-ttu-id="d2d68-116">Jeśli używasz `Mock<DefaultHttpContext>` w testach jednostkowych, zacznij korzystać z `Mock<HttpContext>`.</span><span class="sxs-lookup"><span data-stu-id="d2d68-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span> 

#### <a name="category"></a><span data-ttu-id="d2d68-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d2d68-117">Category</span></span>

<span data-ttu-id="d2d68-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d2d68-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d2d68-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d2d68-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
