---
title: Mapowanie typu danych w ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 45061ed18d5854092db4a8d90bc18d48e2e6e6db
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="data-type-mappings-in-adonet"></a><span data-ttu-id="c36ec-102">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c36ec-102">Data Type Mappings in ADO.NET</span></span>
<span data-ttu-id="c36ec-103">.NET Framework jest oparta na wspólny system typów, który definiuje sposób typy są zadeklarowany, używane i zarządzane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c36ec-103">The .NET Framework is based on the common type system, which defines how types are declared, used, and managed in the runtime.</span></span> <span data-ttu-id="c36ec-104">Zawiera typy wartości i typy referencyjne, które wynikają z <xref:System.Object> typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="c36ec-104">It consists of both value types and reference types, which all derive from the <xref:System.Object> base type.</span></span> <span data-ttu-id="c36ec-105">Podczas pracy ze źródłem danych, wywnioskować typu danych od dostawcy danych, jeśli nie został jawnie określony.</span><span class="sxs-lookup"><span data-stu-id="c36ec-105">When working with a data source, the data type is inferred from the data provider if it is not explicitly specified.</span></span> <span data-ttu-id="c36ec-106">Na przykład <xref:System.Data.DataSet> obiektu jest niezależna od wszelkich określonego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="c36ec-106">For example, a <xref:System.Data.DataSet> object is independent of any specific data source.</span></span> <span data-ttu-id="c36ec-107">Dane w `DataSet` jest pobierana ze źródła danych i zmiany są zachowywane do źródła danych przy użyciu `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="c36ec-107">Data in a `DataSet` is retrieved from a data source, and changes are persisted back to the data source by using a `DataAdapter`.</span></span> <span data-ttu-id="c36ec-108">Oznacza to, że w przypadku `DataAdapter` wypełnia <xref:System.Data.DataTable> w `DataSet` z wartości ze źródła danych, wynikowy typy danych kolumn w `DataTable` są [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów, zamiast specyficzne dla typów [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] danych Dostawca używany do nawiązania połączenia ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="c36ec-108">This means that when a `DataAdapter` fills a <xref:System.Data.DataTable> in a `DataSet` with values from a data source, the resulting data types of the columns in the `DataTable` are [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types, instead of types specific to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider that is used to connect to the data source.</span></span>  
  
 <span data-ttu-id="c36ec-109">Podobnie, jeśli `DataReader` zwraca wartość ze źródła danych, wynikowej wartości są przechowywane w zmiennej lokalnej, która ma [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu.</span><span class="sxs-lookup"><span data-stu-id="c36ec-109">Likewise, when a `DataReader` returns a value from a data source, the resulting value is stored in a local variable that has a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type.</span></span> <span data-ttu-id="c36ec-110">Dla obu `Fill` operacji `DataAdapter` i `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu jest wywnioskowany na podstawie wartość zwracana z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych.</span><span class="sxs-lookup"><span data-stu-id="c36ec-110">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type is inferred from the value returned from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span>  
  
 <span data-ttu-id="c36ec-111">Zamiast polegania na typ danych wykrywany, możesz użyć metody typizowane metody dostępu `DataReader` gdy znasz określonego typu wartości zwracanych.</span><span class="sxs-lookup"><span data-stu-id="c36ec-111">Instead of relying on the inferred data type, you can use the typed accessor methods of the `DataReader` when you know the specific type of the value being returned.</span></span> <span data-ttu-id="c36ec-112">Metody dostępu typu osiągnięcie większej wydajności przez zwrócenie wartości jako określony [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu, co eliminuje konieczność dodatkowy typ konwersji.</span><span class="sxs-lookup"><span data-stu-id="c36ec-112">Typed accessor methods give you better performance by returning a value as a specific [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type, which eliminates the need for additional type conversion.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c36ec-113">Wartości null [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy danych dostawcy danych są reprezentowane przez `DBNull.Value`.</span><span class="sxs-lookup"><span data-stu-id="c36ec-113">Null values for [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider data types are represented by `DBNull.Value`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c36ec-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c36ec-114">In This Section</span></span>  
 [<span data-ttu-id="c36ec-115">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="c36ec-115">SQL Server Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 <span data-ttu-id="c36ec-116">Wyświetla wywnioskować mapowanie typu danych i danych metod typu accessor dla <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="c36ec-116">Lists inferred data type mappings and data accessor methods for <xref:System.Data.SqlClient>.</span></span>  
  
 [<span data-ttu-id="c36ec-117">Mapowanie typu danych OLE DB</span><span class="sxs-lookup"><span data-stu-id="c36ec-117">OLE DB Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 <span data-ttu-id="c36ec-118">Wyświetla wywnioskować mapowanie typu danych i danych metod typu accessor dla <xref:System.Data.OleDb>.</span><span class="sxs-lookup"><span data-stu-id="c36ec-118">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OleDb>.</span></span>  
  
 [<span data-ttu-id="c36ec-119">Mapowanie typu danych ODBC</span><span class="sxs-lookup"><span data-stu-id="c36ec-119">ODBC Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 <span data-ttu-id="c36ec-120">Wyświetla wywnioskować mapowanie typu danych i danych metod typu accessor dla <xref:System.Data.Odbc>.</span><span class="sxs-lookup"><span data-stu-id="c36ec-120">Lists inferred data type mappings and data accessor methods for <xref:System.Data.Odbc>.</span></span>  
  
 [<span data-ttu-id="c36ec-121">Mapowanie typu danych Oracle</span><span class="sxs-lookup"><span data-stu-id="c36ec-121">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="c36ec-122">Wyświetla wywnioskować mapowanie typu danych i danych metod typu accessor dla <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="c36ec-122">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OracleClient>.</span></span>  
  
 [<span data-ttu-id="c36ec-123">Liczby zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="c36ec-123">Floating-Point Numbers</span></span>](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 <span data-ttu-id="c36ec-124">W tym artykule opisano problemy napotykane przez programistów często podczas pracy z liczb zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="c36ec-124">Describes issues that developers frequently encounter when working with floating-point numbers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c36ec-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c36ec-125">See Also</span></span>  
 [<span data-ttu-id="c36ec-126">Typy danych programu SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c36ec-126">SQL Server Data Types and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="c36ec-127">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="c36ec-127">Configuring Parameters and Parameter Data Types</span></span>](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="c36ec-128">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="c36ec-128">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="c36ec-129">System typu wspólnego</span><span class="sxs-lookup"><span data-stu-id="c36ec-129">Common Type System</span></span>](../../../../docs/standard/base-types/common-type-system.md)  
 [<span data-ttu-id="c36ec-130">Konwertowanie typów</span><span class="sxs-lookup"><span data-stu-id="c36ec-130">Converting Types</span></span>](http://msdn.microsoft.com/en-us/6038316e-bdaf-4f55-8006-407f591ce156)  
 [<span data-ttu-id="c36ec-131">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="c36ec-131">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
