---
title: Oracle i ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f77d5c98c96bd4b6085c30b6d1dd713bd324fbad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="83bbb-102">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="83bbb-102">Oracle and ADO.NET</span></span>
> [!NOTE]
>  <span data-ttu-id="83bbb-103">Typy w <xref:System.Data.OracleClient> są przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="83bbb-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="83bbb-104">Typy w dalszym ciągu obsługiwany w bieżącym of.NET wersji Framework, ale zostanie usunięta w przyszłej wersji.</span><span class="sxs-lookup"><span data-stu-id="83bbb-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="83bbb-105">Firma Microsoft zaleca użycie dostawca programu Oracle innych firm.</span><span class="sxs-lookup"><span data-stu-id="83bbb-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="83bbb-106">W tej sekcji opisano funkcje i zachowania, które są specyficzne dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="83bbb-106">This section describes features and behaviors that are specific to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="83bbb-107">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Dostawcy danych programu Oracle zapewnia dostęp do bazy danych Oracle przy użyciu programu Oracle Call Interface (OCI) zgodnie z oprogramowania klienta Oracle.</span><span class="sxs-lookup"><span data-stu-id="83bbb-107">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="83bbb-108">Funkcje dostawcy danych jest bardzo podobny do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych dla [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], OLE DB i ODBC.</span><span class="sxs-lookup"><span data-stu-id="83bbb-108">The functionality of the data provider is designed to be similar to that of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers for [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="83bbb-109">Aby użyć [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych dla programu Oracle, aplikacja musi odwoływać się <xref:System.Data.OracleClient> przestrzeni nazw w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="83bbb-109">To use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="83bbb-110">Należy również dołączyć odwołanie do biblioteki DLL podczas kompilowania kodu.</span><span class="sxs-lookup"><span data-stu-id="83bbb-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="83bbb-111">Na przykład jeśli są kompilowanie programu C#, powinny zawierać wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="83bbb-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="83bbb-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="83bbb-112">In This Section</span></span>  
 [<span data-ttu-id="83bbb-113">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="83bbb-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="83bbb-114">W tym artykule opisano wymagania dotyczące korzystania z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych programu Oracle i opisano różne problemy pod uwagę podczas korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="83bbb-114">Describes requirements for using the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="83bbb-115">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="83bbb-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="83bbb-116">W tym artykule opisano <xref:System.Data.OracleClient.OracleBFile> klasy, która jest używana do pracy z typem danych Oracle BPLIK.</span><span class="sxs-lookup"><span data-stu-id="83bbb-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="83bbb-117">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="83bbb-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="83bbb-118">W tym artykule opisano <xref:System.Data.OracleClient.OracleLob> klasy, która jest używana do pracy z typami danych Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="83bbb-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="83bbb-119">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="83bbb-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="83bbb-120">W tym artykule opisano obsługę typ danych Oracle REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="83bbb-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="83bbb-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="83bbb-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="83bbb-122">Zawiera opis struktury, można użyć do pracy z typów danych Oracle, w tym <xref:System.Data.OracleClient.OracleNumber> i <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="83bbb-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="83bbb-123">Sekwencje Oracle</span><span class="sxs-lookup"><span data-stu-id="83bbb-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="83bbb-124">W tym artykule opisano obsługę pobierania wartości generowanych przez serwer kluczy sekwencji Oracle.</span><span class="sxs-lookup"><span data-stu-id="83bbb-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="83bbb-125">Mapowanie typu danych Oracle</span><span class="sxs-lookup"><span data-stu-id="83bbb-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="83bbb-126">Wyświetla listę typów danych Oracle i ich mapowania <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="83bbb-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="83bbb-127">Transakcje rozproszone Oracle</span><span class="sxs-lookup"><span data-stu-id="83bbb-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="83bbb-128">Opisuje sposób <xref:System.Data.OracleClient.OracleConnection> obiektu automatycznie rejestruje w istniejącej transakcji rozproszonej, gdy ustali, że transakcja jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="83bbb-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="83bbb-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="83bbb-129">Related Sections</span></span>  
 [<span data-ttu-id="83bbb-130">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="83bbb-130">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="83bbb-131">Opisuje bezpieczne praktyk kodowania, korzystając z [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83bbb-131">Describes secure coding practices when using [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 [<span data-ttu-id="83bbb-132">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="83bbb-132">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="83bbb-133">Opisuje sposób tworzenia i używania `DataSets`, typizowanych `DataSets`, `DataTables`, i `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="83bbb-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="83bbb-134">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="83bbb-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="83bbb-135">Opisuje sposób pracy z danymi programu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="83bbb-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="83bbb-136">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="83bbb-136">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 <span data-ttu-id="83bbb-137">Opisuje sposób pracy z funkcjami i funkcje, które są specyficzne dla [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83bbb-137">Describes how to work with features and functionality that are specific to [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="83bbb-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="83bbb-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="83bbb-139">Zawiera opis klas rodzajowych, dzięki którym można napisać kod niezależny od dostawcy [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83bbb-139">Describes generic classes that allow you to write provider-independent code in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83bbb-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83bbb-140">See Also</span></span>  
 [<span data-ttu-id="83bbb-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="83bbb-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="83bbb-142">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="83bbb-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
