---
title: Oracle i ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 9a60499674f0192bb7589f227bffb6f907f682d9
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084601"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="48ec0-102">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="48ec0-102">Oracle and ADO.NET</span></span>
> [!NOTE]
>  <span data-ttu-id="48ec0-103">Typy w <xref:System.Data.OracleClient> są przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="48ec0-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="48ec0-104">Typy w dalszym ciągu obsługiwany w bieżącym of.NET wersji Framework, ale zostanie usunięta w przyszłej wersji.</span><span class="sxs-lookup"><span data-stu-id="48ec0-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="48ec0-105">Firma Microsoft zaleca się, że używasz innego dostawcy Oracle.</span><span class="sxs-lookup"><span data-stu-id="48ec0-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="48ec0-106">W tej sekcji opisano funkcji i zachowań, które są specyficzne dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle.</span><span class="sxs-lookup"><span data-stu-id="48ec0-106">This section describes features and behaviors that are specific to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="48ec0-107">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle zapewnia dostęp do bazy danych Oracle przy użyciu Oracle wywołania interfejsu (OCI), zgodnie z postanowieniami przez oprogramowanie klienckie Oracle.</span><span class="sxs-lookup"><span data-stu-id="48ec0-107">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="48ec0-108">Funkcje dostawcy danych jest bardzo podobny do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych programu SQL Server, OLE DB i ODBC.</span><span class="sxs-lookup"><span data-stu-id="48ec0-108">The functionality of the data provider is designed to be similar to that of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="48ec0-109">Aby użyć [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider Pro Oracle, aplikacja musi odwoływać się do <xref:System.Data.OracleClient> przestrzeni nazw w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="48ec0-109">To use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="48ec0-110">Możesz również musi zawierać odwołanie do biblioteki DLL, podczas kompilowania kodu.</span><span class="sxs-lookup"><span data-stu-id="48ec0-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="48ec0-111">Na przykład jeśli kompilujesz program C# powinien zawierać wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="48ec0-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="48ec0-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="48ec0-112">In This Section</span></span>  
 [<span data-ttu-id="48ec0-113">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="48ec0-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="48ec0-114">W tym artykule opisano wymagania dotyczące korzystania z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle i opisuje określone problemy, które należy wiedzieć podczas korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="48ec0-114">Describes requirements for using the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="48ec0-115">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="48ec0-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="48ec0-116">W tym artykule opisano <xref:System.Data.OracleClient.OracleBFile> klasy, która jest używana do pracy z typem danych BPLIK Oracle.</span><span class="sxs-lookup"><span data-stu-id="48ec0-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="48ec0-117">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="48ec0-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="48ec0-118">W tym artykule opisano <xref:System.Data.OracleClient.OracleLob> klasy, która jest używana do pracy z Oracle LOB typów danych.</span><span class="sxs-lookup"><span data-stu-id="48ec0-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="48ec0-119">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="48ec0-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="48ec0-120">W tym artykule opisano obsługę dla typu danych Oracle REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="48ec0-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="48ec0-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="48ec0-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="48ec0-122">W tym artykule opisano struktury, można użyć do pracy z typów danych Oracle, w tym <xref:System.Data.OracleClient.OracleNumber> i <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="48ec0-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="48ec0-123">Sekwencje Oracle</span><span class="sxs-lookup"><span data-stu-id="48ec0-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="48ec0-124">W tym artykule opisano obsługę pobierania wartości generowanych przez serwer Oracle sekwencja klucza.</span><span class="sxs-lookup"><span data-stu-id="48ec0-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="48ec0-125">Mapowanie typu danych Oracle</span><span class="sxs-lookup"><span data-stu-id="48ec0-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="48ec0-126">Wyświetla listę typów danych Oracle i ich mapowań <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="48ec0-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="48ec0-127">Transakcje rozproszone Oracle</span><span class="sxs-lookup"><span data-stu-id="48ec0-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="48ec0-128">W tym artykule opisano sposób, w jaki <xref:System.Data.OracleClient.OracleConnection> obiektu pozyskuje automatycznie w ramach istniejącej transakcji rozproszonej, gdy ustali, że jest aktywna transakcja.</span><span class="sxs-lookup"><span data-stu-id="48ec0-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="48ec0-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="48ec0-129">Related Sections</span></span>  
 [<span data-ttu-id="48ec0-130">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="48ec0-130">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="48ec0-131">Opisuje bezpiecznego kodowania, korzystając z [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="48ec0-131">Describes secure coding practices when using [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 [<span data-ttu-id="48ec0-132">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="48ec0-132">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="48ec0-133">Opisuje sposób tworzenia i używania `DataSets`, wpisane `DataSets`, `DataTables`, i `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="48ec0-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="48ec0-134">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="48ec0-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="48ec0-135">W tym artykule opisano sposób pracy z danymi programu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="48ec0-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="48ec0-136">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="48ec0-136">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 <span data-ttu-id="48ec0-137">W tym artykule opisano sposób pracy z funkcjami specyficznymi dla programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="48ec0-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="48ec0-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="48ec0-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="48ec0-139">Zawiera opis klas ogólnych, które umożliwiają pisanie kodu niezależnych od dostawcy w [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="48ec0-139">Describes generic classes that allow you to write provider-independent code in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ec0-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48ec0-140">See Also</span></span>  
 [<span data-ttu-id="48ec0-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="48ec0-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="48ec0-142">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="48ec0-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
