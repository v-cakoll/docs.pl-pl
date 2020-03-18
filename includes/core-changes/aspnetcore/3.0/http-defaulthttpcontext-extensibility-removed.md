---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290756"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="57735-101">HTTP: Usunięto rozszerzalność domyślnego elementu HttpContext</span><span class="sxs-lookup"><span data-stu-id="57735-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="57735-102">W ramach ASP.NET core 3.0 poprawy wydajności, rozszerzalność została usunięta. `DefaultHttpContext`</span><span class="sxs-lookup"><span data-stu-id="57735-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="57735-103">Klasa jest `sealed`teraz .</span><span class="sxs-lookup"><span data-stu-id="57735-103">The class is now `sealed`.</span></span> <span data-ttu-id="57735-104">Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="57735-104">For more information, see [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span></span>

<span data-ttu-id="57735-105">Jeśli testy jednostkowe `Mock<HttpContext>` `new DefaultHttpContext()` używają `Mock<DefaultHttpContext>`, użyj lub zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="57735-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` or `new DefaultHttpContext()` instead.</span></span>

<span data-ttu-id="57735-106">Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="57735-106">For discussion, see [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="57735-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="57735-107">Version introduced</span></span>

<span data-ttu-id="57735-108">3.0</span><span class="sxs-lookup"><span data-stu-id="57735-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="57735-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="57735-109">Old behavior</span></span>

<span data-ttu-id="57735-110">Klasy mogą pochodzić z `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="57735-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="57735-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="57735-111">New behavior</span></span>

<span data-ttu-id="57735-112">Klasy nie mogą pochodzić z `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="57735-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="57735-113">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="57735-113">Reason for change</span></span>

<span data-ttu-id="57735-114">Rozszerzalność została początkowo dostarczona, aby umożliwić łączenie `HttpContext`, ale wprowadziła niepotrzebną złożoność i utrudniła inne optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="57735-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="57735-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="57735-115">Recommended action</span></span>

<span data-ttu-id="57735-116">Jeśli używasz `Mock<DefaultHttpContext>` w testach jednostkowych, `Mock<HttpContext>` zacznij używać zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="57735-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="57735-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="57735-117">Category</span></span>

<span data-ttu-id="57735-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="57735-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="57735-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="57735-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
