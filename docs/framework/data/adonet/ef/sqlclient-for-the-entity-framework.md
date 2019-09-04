---
title: Element SqlClient programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: f7077cf9c9b8eb8a86b01e8b38431d1b9a87a80c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248360"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="c86ac-102">Element SqlClient programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c86ac-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="c86ac-103">W tej sekcji opisano Dostawca danych .NET Framework dla SQL Server (SqlClient), co umożliwia Entity Framework pracy nad Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c86ac-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="c86ac-104">Atrybut schematu dostawcy</span><span class="sxs-lookup"><span data-stu-id="c86ac-104">Provider Schema Attribute</span></span>  
 <span data-ttu-id="c86ac-105">`Provider`jest atrybutem `Schema` elementu w języku definicji schematu magazynu (SSDL).</span><span class="sxs-lookup"><span data-stu-id="c86ac-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="c86ac-106">Aby użyć programu SqlClient, przypisz ciąg "System. Data. SqlClient" do `Provider` atrybutu `Schema` elementu.</span><span class="sxs-lookup"><span data-stu-id="c86ac-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="c86ac-107">ProviderManifestToken — atrybut schematu</span><span class="sxs-lookup"><span data-stu-id="c86ac-107">ProviderManifestToken Schema Attribute</span></span>  
 <span data-ttu-id="c86ac-108">`ProviderManifestToken`jest wymaganym atrybutem `Schema` elementu w SSDL.</span><span class="sxs-lookup"><span data-stu-id="c86ac-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="c86ac-109">Ten token służy do ładowania manifestu dostawcy dla scenariuszy w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="c86ac-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="c86ac-110">Aby uzyskać więcej informacji `ProviderManifestToken` o atrybutach, zobacz [Schema element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="c86ac-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="c86ac-111">Klient SQL może być używany jako dostawca danych dla różnych wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c86ac-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="c86ac-112">Wersje te mają różne możliwości.</span><span class="sxs-lookup"><span data-stu-id="c86ac-112">These versions have different capabilities.</span></span> <span data-ttu-id="c86ac-113">Na przykład SQL Server 2000 nie obsługuje `varchar(max)` i `nvarchar(max)` typów, które zostały wprowadzone w SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="c86ac-113">For example, SQL Server 2000 does not support `varchar(max)` and `nvarchar(max)` types that were introduced with SQL Server 2005.</span></span>  
  
 <span data-ttu-id="c86ac-114">Klient SqlClient tworzy i akceptuje następujące tokeny manifestu dostawcy dla różnych wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c86ac-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="c86ac-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="c86ac-115">SQL Server 2000</span></span>|<span data-ttu-id="c86ac-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="c86ac-116">SQL Server 2005</span></span>|<span data-ttu-id="c86ac-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="c86ac-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="c86ac-118">2000</span><span class="sxs-lookup"><span data-stu-id="c86ac-118">2000</span></span>|<span data-ttu-id="c86ac-119">2005</span><span class="sxs-lookup"><span data-stu-id="c86ac-119">2005</span></span>|<span data-ttu-id="c86ac-120">2008</span><span class="sxs-lookup"><span data-stu-id="c86ac-120">2008</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c86ac-121">Począwszy od programu Visual Studio 2010 [narzędzia ADO.NET Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) nie obsługują SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="c86ac-121">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="c86ac-122">Nazwa przestrzeni nazw dostawcy</span><span class="sxs-lookup"><span data-stu-id="c86ac-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="c86ac-123">Wszyscy dostawcy muszą określać przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="c86ac-123">All providers must specify a namespace.</span></span> <span data-ttu-id="c86ac-124">Ta właściwość informuje Entity Framework którego prefiks jest używany przez dostawcę dla określonych konstrukcji, takich jak typy i funkcje.</span><span class="sxs-lookup"><span data-stu-id="c86ac-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="c86ac-125">Przestrzeń nazw manifestów dostawcy SqlClient ma wartość `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="c86ac-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="c86ac-126">Aby uzyskać więcej informacji na temat przestrzeni nazw, zobacz [przestrzenie nazw](./language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c86ac-126">For more information about namespaces, see [Namespaces](./language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="c86ac-127">Types</span><span class="sxs-lookup"><span data-stu-id="c86ac-127">Types</span></span>  
 <span data-ttu-id="c86ac-128">Dostawca SqlClient dla Entity Framework zawiera informacje dotyczące mapowania między typami modeli koncepcyjnych a typami SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c86ac-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="c86ac-129">Aby uzyskać więcej informacji, zobacz [SqlClient for Entity Framework](sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="c86ac-129">For more information, see [SqlClient for Entity FrameworkTypes](sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="c86ac-130">Funkcje</span><span class="sxs-lookup"><span data-stu-id="c86ac-130">Functions</span></span>  
 <span data-ttu-id="c86ac-131">Dostawca SqlClient dla Entity Framework definiuje listę funkcji obsługiwanych przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="c86ac-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="c86ac-132">Listę obsługiwanych funkcji można znaleźć [w temacie SqlClient for Entity Framework Functions](sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c86ac-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c86ac-133">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c86ac-133">In This Section</span></span>  
 [<span data-ttu-id="c86ac-134">Klient SQL dla funkcji programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c86ac-134">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="c86ac-135">Klient SQL dla typów programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c86ac-135">SqlClient for Entity FrameworkTypes</span></span>](sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="c86ac-136">Znane problemy klienta SQL dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c86ac-136">Known Issues in SqlClient for Entity Framework</span></span>](known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="c86ac-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c86ac-137">See also</span></span>

- [<span data-ttu-id="c86ac-138">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="c86ac-138">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="c86ac-139">Dokumentacja języka</span><span class="sxs-lookup"><span data-stu-id="c86ac-139">Language Reference</span></span>](./language-reference/index.md)
- [<span data-ttu-id="c86ac-140">Znane problemy w dostawcy SqlClient dla Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c86ac-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](sqlclient-for-the-entity-framework.md)
