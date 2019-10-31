---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198530"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="f154a-101">Buforowanie: Microsoft. Extensions. buforowanie. SqlServer używa nowego pakietu SqlClient</span><span class="sxs-lookup"><span data-stu-id="f154a-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="f154a-102">Pakiet `Microsoft.Extensions.Caching.SqlServer` będzie używać nowego pakietu `Microsoft.Data.SqlClient` zamiast pakietu `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="f154a-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="f154a-103">Ta zmiana może spowodować drobne zmiany zachowań.</span><span class="sxs-lookup"><span data-stu-id="f154a-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="f154a-104">Aby uzyskać więcej informacji, zobacz [wprowadzenie do nowego elementu Microsoft. Data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="f154a-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f154a-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="f154a-105">Version introduced</span></span>

<span data-ttu-id="f154a-106">3.0</span><span class="sxs-lookup"><span data-stu-id="f154a-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f154a-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="f154a-107">Old behavior</span></span>

<span data-ttu-id="f154a-108">Pakiet `Microsoft.Extensions.Caching.SqlServer` używał pakietu `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="f154a-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f154a-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="f154a-109">New behavior</span></span>

<span data-ttu-id="f154a-110">`Microsoft.Extensions.Caching.SqlServer` używa teraz pakietu `Microsoft.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="f154a-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f154a-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="f154a-111">Reason for change</span></span>

<span data-ttu-id="f154a-112">`Microsoft.Data.SqlClient` to nowy pakiet, który jest zbudowany z `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="f154a-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="f154a-113">Jest to miejsce, w którym wszystkie nowe funkcje będą wykonywane od teraz.</span><span class="sxs-lookup"><span data-stu-id="f154a-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f154a-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="f154a-114">Recommended action</span></span>

<span data-ttu-id="f154a-115">Klienci nie muszą martwić się o tę zmianę, chyba że używali typów zwracanych przez pakiet `Microsoft.Extensions.Caching.SqlServer` i rzutowania ich do typów `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="f154a-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="f154a-116">Na przykład jeśli ktoś wyrzutuje `DbConnection` do [starego typu SqlConnection](xref:System.Data.SqlClient.SqlConnection), musi zmienić rzutowanie na nowy typ `Microsoft.Data.SqlClient.SqlConnection`.</span><span class="sxs-lookup"><span data-stu-id="f154a-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="f154a-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="f154a-117">Category</span></span>

<span data-ttu-id="f154a-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f154a-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f154a-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f154a-119">Affected APIs</span></span>

<span data-ttu-id="f154a-120">Brak</span><span class="sxs-lookup"><span data-stu-id="f154a-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
