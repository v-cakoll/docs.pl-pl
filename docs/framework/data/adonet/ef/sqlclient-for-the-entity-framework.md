---
title: SqlClient Entity Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e2d95b1c63cf751a694051e5def09e20dd7ab7a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="6f4a7-102">SqlClient Entity Framework</span><span class="sxs-lookup"><span data-stu-id="6f4a7-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="6f4a7-103">W tej sekcji opisano dostawcy danych programu .NET Framework dla programu SQL Server (SqlClient), dzięki czemu Entity Framework do pracy za pośrednictwem programu Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="6f4a7-104">Atrybut schematu dostawcy</span><span class="sxs-lookup"><span data-stu-id="6f4a7-104">Provider Schema Attribute</span></span>  
 <span data-ttu-id="6f4a7-105">`Provider`atrybut `Schema` elementu w języku definicji schematu magazynu (SSDL).</span><span class="sxs-lookup"><span data-stu-id="6f4a7-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="6f4a7-106">Użyj SqlClient, należy przypisać do ciągu "System.Data.SqlClient" `Provider` atrybutu `Schema` elementu.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="6f4a7-107">Atrybut schematu ProviderManifestToken</span><span class="sxs-lookup"><span data-stu-id="6f4a7-107">ProviderManifestToken Schema Attribute</span></span>  
 <span data-ttu-id="6f4a7-108">`ProviderManifestToken`Wymagany atrybut `Schema` elementu w pliku SSDL.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="6f4a7-109">Token ten jest używany załadować manifestu dostawcy dla scenariuszy w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="6f4a7-110">Aby uzyskać więcej informacji na temat `ProviderManifestToken` atrybutów, zobacz [elementu schematu (SSDL)](http://msdn.microsoft.com/en-us/fec75ae4-7f16-4421-9265-9dac61509222).</span><span class="sxs-lookup"><span data-stu-id="6f4a7-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](http://msdn.microsoft.com/en-us/fec75ae4-7f16-4421-9265-9dac61509222).</span></span>  
  
 <span data-ttu-id="6f4a7-111">Klient SQL może służyć jako dostawca danych dla różnych wersji [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f4a7-111">SqlClient can be used as a data provider for different versions of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6f4a7-112">Te wersje są dostępne różne możliwości.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-112">These versions have different capabilities.</span></span> <span data-ttu-id="6f4a7-113">Na przykład [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] nie obsługuje `varchar(max)` i `nvarchar(max)` typy, które zostały wprowadzone w programie [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f4a7-113">For example, [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] does not support `varchar(max)` and `nvarchar(max)` types that were introduced with [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="6f4a7-114">SqlClient tworzy i przyjmuje następujące dostawcy tokenów manifestu dla różnych wersji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="6f4a7-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="6f4a7-115">SQL Server 2000</span></span>|<span data-ttu-id="6f4a7-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="6f4a7-116">SQL Server 2005</span></span>|<span data-ttu-id="6f4a7-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="6f4a7-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="6f4a7-118">2000</span><span class="sxs-lookup"><span data-stu-id="6f4a7-118">2000</span></span>|<span data-ttu-id="6f4a7-119">2005</span><span class="sxs-lookup"><span data-stu-id="6f4a7-119">2005</span></span>|<span data-ttu-id="6f4a7-120">2008</span><span class="sxs-lookup"><span data-stu-id="6f4a7-120">2008</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="6f4a7-121">Począwszy od [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 2010, [narzędzi modelu danych jednostki ADO.NET](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527) nie obsługują programu SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-121">Starting with [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 2010, the [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="6f4a7-122">Nazwa dostawcy Namespace</span><span class="sxs-lookup"><span data-stu-id="6f4a7-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="6f4a7-123">Wszystkich dostawców musi określać przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-123">All providers must specify a namespace.</span></span> <span data-ttu-id="6f4a7-124">Ta właściwość określa, że Entity Framework, które prefiks jest używany przez dostawcę dla określonych elementów składowych, takich jak typy i funkcje.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="6f4a7-125">Przestrzeń nazw dla manifestów dostawca SqlClient jest `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="6f4a7-126">Aby uzyskać więcej informacji na temat obszarów nazw, zobacz [przestrzeni nazw](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6f4a7-126">For more information about namespaces, see [Namespaces](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="6f4a7-127">Types</span><span class="sxs-lookup"><span data-stu-id="6f4a7-127">Types</span></span>  
 <span data-ttu-id="6f4a7-128">Dostawca SqlClient Entity Framework udostępnia informacje dotyczące mapowania między typami w modelu koncepcyjnym i typów programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="6f4a7-129">Aby uzyskać więcej informacji, zobacz [SqlClient dla jednostki FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="6f4a7-129">For more information, see [SqlClient for Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="6f4a7-130">Funkcje</span><span class="sxs-lookup"><span data-stu-id="6f4a7-130">Functions</span></span>  
 <span data-ttu-id="6f4a7-131">Dostawca SqlClient Entity Framework definiuje listę funkcje obsługiwane przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="6f4a7-132">Aby uzyskać listę obsługiwanych funkcji, zobacz [SqlClient Entity Framework funkcji](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="6f4a7-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f4a7-133">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6f4a7-133">In This Section</span></span>  
 [<span data-ttu-id="6f4a7-134">Klient SQL dla funkcji programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="6f4a7-134">SqlClient for Entity Framework Functions</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="6f4a7-135">Klient SQL dla typów programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="6f4a7-135">SqlClient for Entity FrameworkTypes</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="6f4a7-136">Znane problemy klienta SQL dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="6f4a7-136">Known Issues in SqlClient for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="6f4a7-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f4a7-137">See Also</span></span>  
 [<span data-ttu-id="6f4a7-138">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="6f4a7-138">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [<span data-ttu-id="6f4a7-139">Dokumentacja języka</span><span class="sxs-lookup"><span data-stu-id="6f4a7-139">Language Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)  
 [<span data-ttu-id="6f4a7-140">Znane problemy w programie dostawca SqlClient Entity Framework</span><span class="sxs-lookup"><span data-stu-id="6f4a7-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
