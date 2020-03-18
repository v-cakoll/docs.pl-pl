---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198530"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="55820-101">Buforowanie: Program Microsoft.Extensions.Caching.SqlServer używa nowego pakietu SqlClient</span><span class="sxs-lookup"><span data-stu-id="55820-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="55820-102">Pakiet `Microsoft.Extensions.Caching.SqlServer` użyje nowego `Microsoft.Data.SqlClient` pakietu `System.Data.SqlClient` zamiast pakietu.</span><span class="sxs-lookup"><span data-stu-id="55820-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="55820-103">Ta zmiana może spowodować niewielkie zmiany zachowań łamanie.</span><span class="sxs-lookup"><span data-stu-id="55820-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="55820-104">Aby uzyskać więcej informacji, zobacz [Wprowadzenie do nowego klienta Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="55820-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="55820-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="55820-105">Version introduced</span></span>

<span data-ttu-id="55820-106">3.0</span><span class="sxs-lookup"><span data-stu-id="55820-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="55820-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="55820-107">Old behavior</span></span>

<span data-ttu-id="55820-108">Pakiet `Microsoft.Extensions.Caching.SqlServer` użył `System.Data.SqlClient` pakietu.</span><span class="sxs-lookup"><span data-stu-id="55820-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="55820-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="55820-109">New behavior</span></span>

<span data-ttu-id="55820-110">`Microsoft.Extensions.Caching.SqlServer`używa teraz `Microsoft.Data.SqlClient` pakietu.</span><span class="sxs-lookup"><span data-stu-id="55820-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="55820-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="55820-111">Reason for change</span></span>

<span data-ttu-id="55820-112">`Microsoft.Data.SqlClient`to nowy pakiet, który `System.Data.SqlClient`jest zbudowany z .</span><span class="sxs-lookup"><span data-stu-id="55820-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="55820-113">To miejsce, w którym wszystkie nowe funkcje będą wykonywane od teraz.</span><span class="sxs-lookup"><span data-stu-id="55820-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="55820-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="55820-114">Recommended action</span></span>

<span data-ttu-id="55820-115">Klienci nie powinni się martwić o tę przełomową zmianę, `Microsoft.Extensions.Caching.SqlServer` chyba że używali `System.Data.SqlClient` typów zwracanych przez pakiet i przesyłania ich do typów.</span><span class="sxs-lookup"><span data-stu-id="55820-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="55820-116">Na przykład jeśli ktoś `DbConnection` był rzutowanie do [starego typu SqlConnection](xref:System.Data.SqlClient.SqlConnection), musieliby zmienić rzutowania na nowy `Microsoft.Data.SqlClient.SqlConnection` typ.</span><span class="sxs-lookup"><span data-stu-id="55820-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="55820-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="55820-117">Category</span></span>

<span data-ttu-id="55820-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="55820-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="55820-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="55820-119">Affected APIs</span></span>

<span data-ttu-id="55820-120">Brak</span><span class="sxs-lookup"><span data-stu-id="55820-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
