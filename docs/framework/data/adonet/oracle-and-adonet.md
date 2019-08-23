---
title: Oracle i ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 381f796bec31bece354001ad46bf5079381d1b3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914560"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="a458f-102">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a458f-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="a458f-103">Typy w <xref:System.Data.OracleClient> są przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="a458f-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="a458f-104">Typy pozostają obsługiwane w bieżącej wersji of.NET Framework, ale zostaną usunięte w przyszłej wersji.</span><span class="sxs-lookup"><span data-stu-id="a458f-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="a458f-105">Firma Microsoft zaleca użycie dostawcy Oracle innej firmy.</span><span class="sxs-lookup"><span data-stu-id="a458f-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="a458f-106">W tej sekcji opisano funkcje i zachowania, które są specyficzne dla Dostawca danych .NET Framework dla programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="a458f-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="a458f-107">.NET Framework Dostawca danych dla programu Oracle zapewnia dostęp do bazy danych Oracle przy użyciu interfejsu wywołania Oracle (OCI) dostarczonego przez oprogramowanie klienckie Oracle.</span><span class="sxs-lookup"><span data-stu-id="a458f-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="a458f-108">Funkcja dostawcy danych została zaprojektowana tak, aby była podobna do .NET Framework dostawców danych dla SQL Server, OLE DB i ODBC.</span><span class="sxs-lookup"><span data-stu-id="a458f-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="a458f-109">Aby użyć dostawca danych .NET Framework dla programu Oracle, aplikacja musi odwoływać się <xref:System.Data.OracleClient> do przestrzeni nazw w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a458f-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="a458f-110">Podczas kompilowania kodu należy również dodać odwołanie do biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="a458f-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="a458f-111">Na przykład, Jeśli kompilujesz C# program, wiersz polecenia powinien zawierać:</span><span class="sxs-lookup"><span data-stu-id="a458f-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="a458f-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a458f-112">In This Section</span></span>  
 [<span data-ttu-id="a458f-113">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="a458f-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="a458f-114">W tym artykule opisano wymagania dotyczące korzystania z Dostawca danych .NET Framework dla programu Oracle oraz opisano różne problemy, które należy wziąć pod uwagę podczas korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="a458f-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="a458f-115">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="a458f-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="a458f-116"><xref:System.Data.OracleClient.OracleBFile> Opisuje klasę, która jest używana do pracy z typem danych Oracle bInformacje.</span><span class="sxs-lookup"><span data-stu-id="a458f-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="a458f-117">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="a458f-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="a458f-118"><xref:System.Data.OracleClient.OracleLob> Opisuje klasę, która jest używana do pracy z typami danych LOB firmy Oracle.</span><span class="sxs-lookup"><span data-stu-id="a458f-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="a458f-119">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="a458f-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="a458f-120">Opisuje obsługę typu danych kursora usługi Oracle REF.</span><span class="sxs-lookup"><span data-stu-id="a458f-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="a458f-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="a458f-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="a458f-122">Opisuje struktury, których można użyć do pracy z typami danych Oracle, <xref:System.Data.OracleClient.OracleNumber> w <xref:System.Data.OracleClient.OracleString>tym i.</span><span class="sxs-lookup"><span data-stu-id="a458f-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="a458f-123">Sekwencje Oracle</span><span class="sxs-lookup"><span data-stu-id="a458f-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="a458f-124">Opisuje obsługę pobierania wartości sekwencji programu Oracle klucza generowanej przez serwer.</span><span class="sxs-lookup"><span data-stu-id="a458f-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="a458f-125">Mapowanie typu danych Oracle</span><span class="sxs-lookup"><span data-stu-id="a458f-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="a458f-126">Wyświetla listę typów danych Oracle i ich mapowania na <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="a458f-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="a458f-127">Transakcje rozproszone Oracle</span><span class="sxs-lookup"><span data-stu-id="a458f-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="a458f-128">Opisuje, jak <xref:System.Data.OracleClient.OracleConnection> obiekt automatycznie jest zarejestrowany w istniejącej transakcji rozproszonej, jeśli określa, że transakcja jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="a458f-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a458f-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a458f-129">Related Sections</span></span>  
 [<span data-ttu-id="a458f-130">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a458f-130">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="a458f-131">Zawiera opis bezpiecznych praktyk kodowania w przypadku korzystania z ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a458f-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="a458f-132">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="a458f-132">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="a458f-133">Opisuje sposób tworzenia `DataSets`i używania, `DataTables`wpisywania `DataSets`, i `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="a458f-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="a458f-134">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a458f-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="a458f-135">Opisuje sposób pracy z danymi w ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a458f-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="a458f-136">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a458f-136">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 <span data-ttu-id="a458f-137">Opisuje sposób pracy z funkcjami i funkcjami, które są specyficzne dla SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a458f-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="a458f-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="a458f-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="a458f-139">Opisuje klasy ogólne, które umożliwiają pisanie kodu niezależnego od dostawcy w ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a458f-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a458f-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a458f-140">See also</span></span>

- [<span data-ttu-id="a458f-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a458f-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="a458f-142">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="a458f-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
