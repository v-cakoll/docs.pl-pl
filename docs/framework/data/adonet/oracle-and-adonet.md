---
title: Oracle i ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: a49634f712e32f873df8e47fbcb0c91dbe33fa94
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039821"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="16bed-102">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="16bed-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="16bed-103">Typy w <xref:System.Data.OracleClient> są przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="16bed-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="16bed-104">Typy pozostają obsługiwane w bieżącej wersji of.NET Framework, ale zostaną usunięte w przyszłej wersji.</span><span class="sxs-lookup"><span data-stu-id="16bed-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="16bed-105">Firma Microsoft zaleca użycie dostawcy Oracle innej firmy.</span><span class="sxs-lookup"><span data-stu-id="16bed-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="16bed-106">W tej sekcji opisano funkcje i zachowania, które są specyficzne dla Dostawca danych .NET Framework dla programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="16bed-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="16bed-107">.NET Framework Dostawca danych dla programu Oracle zapewnia dostęp do bazy danych Oracle przy użyciu interfejsu wywołania Oracle (OCI) dostarczonego przez oprogramowanie klienckie Oracle.</span><span class="sxs-lookup"><span data-stu-id="16bed-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="16bed-108">Funkcja dostawcy danych została zaprojektowana tak, aby była podobna do .NET Framework dostawców danych dla SQL Server, OLE DB i ODBC.</span><span class="sxs-lookup"><span data-stu-id="16bed-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="16bed-109">Aby użyć Dostawca danych .NET Framework dla programu Oracle, aplikacja musi odwoływać się do przestrzeni nazw <xref:System.Data.OracleClient> w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="16bed-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="16bed-110">Podczas kompilowania kodu należy również dodać odwołanie do biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="16bed-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="16bed-111">Na przykład, Jeśli kompilujesz C# program, wiersz polecenia powinien zawierać:</span><span class="sxs-lookup"><span data-stu-id="16bed-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="16bed-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="16bed-112">In This Section</span></span>  
 [<span data-ttu-id="16bed-113">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="16bed-113">System Requirements</span></span>](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="16bed-114">W tym artykule opisano wymagania dotyczące korzystania z Dostawca danych .NET Framework dla programu Oracle oraz opisano różne problemy, które należy wziąć pod uwagę podczas korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="16bed-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="16bed-115">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="16bed-115">Oracle BFILEs</span></span>](oracle-bfiles.md)  
 <span data-ttu-id="16bed-116">Opisuje klasę <xref:System.Data.OracleClient.OracleBFile>, która jest używana do pracy z typem danych Oracle bInformacje.</span><span class="sxs-lookup"><span data-stu-id="16bed-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="16bed-117">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="16bed-117">Oracle LOBs</span></span>](oracle-lobs.md)  
 <span data-ttu-id="16bed-118">Opisuje klasę <xref:System.Data.OracleClient.OracleLob>, która jest używana do pracy z typami danych LOB firmy Oracle.</span><span class="sxs-lookup"><span data-stu-id="16bed-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="16bed-119">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="16bed-119">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)  
 <span data-ttu-id="16bed-120">Opisuje obsługę typu danych kursora usługi Oracle REF.</span><span class="sxs-lookup"><span data-stu-id="16bed-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="16bed-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="16bed-121">OracleTypes</span></span>](oracletypes.md)  
 <span data-ttu-id="16bed-122">Opisuje struktury, których można użyć do pracy z typami danych Oracle, w tym <xref:System.Data.OracleClient.OracleNumber> i <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="16bed-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="16bed-123">Sekwencje Oracle</span><span class="sxs-lookup"><span data-stu-id="16bed-123">Oracle Sequences</span></span>](oracle-sequences.md)  
 <span data-ttu-id="16bed-124">Opisuje obsługę pobierania wartości sekwencji programu Oracle klucza generowanej przez serwer.</span><span class="sxs-lookup"><span data-stu-id="16bed-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="16bed-125">Mapowanie typu danych Oracle</span><span class="sxs-lookup"><span data-stu-id="16bed-125">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="16bed-126">Wyświetla listę typów danych Oracle i ich mapowania do <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="16bed-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="16bed-127">Transakcje rozproszone Oracle</span><span class="sxs-lookup"><span data-stu-id="16bed-127">Oracle Distributed Transactions</span></span>](oracle-distributed-transactions.md)  
 <span data-ttu-id="16bed-128">Opisuje sposób automatycznego rejestrowania obiektu <xref:System.Data.OracleClient.OracleConnection> w istniejącej transakcji rozproszonej, jeśli określa, że transakcja jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="16bed-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="16bed-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="16bed-129">Related Sections</span></span>  
 [<span data-ttu-id="16bed-130">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="16bed-130">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="16bed-131">Zawiera opis bezpiecznych praktyk kodowania w przypadku korzystania z ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="16bed-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="16bed-132">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="16bed-132">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)  
 <span data-ttu-id="16bed-133">Opisuje sposób tworzenia i używania `DataSets`, wpisanych `DataSets`, `DataTables`i `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="16bed-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="16bed-134">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="16bed-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="16bed-135">Opisuje sposób pracy z danymi w ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="16bed-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="16bed-136">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="16bed-136">SQL Server and ADO.NET</span></span>](./sql/index.md)  
 <span data-ttu-id="16bed-137">Opisuje sposób pracy z funkcjami i funkcjami, które są specyficzne dla SQL Server.</span><span class="sxs-lookup"><span data-stu-id="16bed-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="16bed-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="16bed-138">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="16bed-139">Opisuje klasy ogólne, które umożliwiają pisanie kodu niezależnego od dostawcy w ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="16bed-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16bed-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16bed-140">See also</span></span>

- [<span data-ttu-id="16bed-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="16bed-141">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="16bed-142">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="16bed-142">ADO.NET Overview</span></span>](ado-net-overview.md)
