---
title: Kursory REF Oracle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 27351c1d47d4ad40940e5b64f257e6a59fc7403a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="08add-102">Kursory REF Oracle</span><span class="sxs-lookup"><span data-stu-id="08add-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="08add-103">.NET Framework Data Provider for Oracle obsługuje programu Oracle **REF CURSOR** — typ danych.</span><span class="sxs-lookup"><span data-stu-id="08add-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="08add-104">Przy użyciu dostawcy danych do pracy z kursorami REF Oracle, należy rozważyć następujące zachowania.</span><span class="sxs-lookup"><span data-stu-id="08add-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08add-105">Niektóre zachowania różnią się od dostawcy OLE DB firmy Microsoft dla programu Oracle (MSDAORA).</span><span class="sxs-lookup"><span data-stu-id="08add-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
-   <span data-ttu-id="08add-106">Ze względu na wydajność, dostawca danych dla Oracle nie jest automatycznie powiązana **REF CURSOR** typy danych, tak jak w przypadku MSDAORA, chyba że zostaną jawnie określone je.</span><span class="sxs-lookup"><span data-stu-id="08add-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
-   <span data-ttu-id="08add-107">Dostawca danych nie obsługuje żadnych unikowe ODBC, w tym specjalna {zestaw wyników} służy do określania parametrów REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="08add-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
-   <span data-ttu-id="08add-108">Aby wykonać procedurę składowaną, która zwraca kursory REF, należy zdefiniować parametrów w <xref:System.Data.OracleClient.OracleParameterCollection> z <xref:System.Data.OracleClient.OracleType> z **kursora** i <xref:System.Data.OracleClient.OracleParameter.Direction%2A> z **dane wyjściowe**.</span><span class="sxs-lookup"><span data-stu-id="08add-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="08add-109">Dostawca danych obsługuje powiązanie kursory REF jako parametry wyjściowe tylko.</span><span class="sxs-lookup"><span data-stu-id="08add-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="08add-110">Dostawca nie obsługuje kursory REF jako parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="08add-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
-   <span data-ttu-id="08add-111">Uzyskiwanie <xref:System.Data.OracleClient.OracleDataReader> z parametru wartość nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="08add-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="08add-112">Wartości są typu <xref:System.DBNull> po wykonaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="08add-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
-   <span data-ttu-id="08add-113">Jedynym **CommandBehavior** wartości wyliczenia, który działa z kursorami REF (na przykład podczas wywoływania metody <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) jest **metody**; pozostałe są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="08add-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
-   <span data-ttu-id="08add-114">Kolejność kursory REF w **OracleDataReader** zależy od rzędu parametrów w **OracleParameterCollection**.</span><span class="sxs-lookup"><span data-stu-id="08add-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="08add-115"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Właściwość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="08add-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
-   <span data-ttu-id="08add-116">PL/SQL **tabeli** — typ danych nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="08add-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="08add-117">Jednak REF kursory są bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="08add-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="08add-118">Jeśli musisz użyć **tabeli** typ danych, należy użyć dostawcy OLE DB .NET danych z MSDAORA.</span><span class="sxs-lookup"><span data-stu-id="08add-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08add-119">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="08add-119">In This Section</span></span>  
 [<span data-ttu-id="08add-120">Przykłady REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="08add-120">REF CURSOR Examples</span></span>](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 <span data-ttu-id="08add-121">Zawiera trzy przykłady ilustrujące przy użyciu kursory REF.</span><span class="sxs-lookup"><span data-stu-id="08add-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="08add-122">Parametry kursora REF CURSOR w OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="08add-122">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="08add-123">Pokazuje, jak można wykonać procedury przechowywanej PL/SQL, która zwraca parametr REF CURSOR i odczytuje wartość jako **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="08add-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="08add-124">Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="08add-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="08add-125">Pokazuje, jak można wykonać procedury przechowywanej PL/SQL, która zwraca dwa parametry REF CURSOR i odczytuje wartości przy użyciu **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="08add-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="08add-126">Wypełnianie zestawu danych przy użyciu przynajmniej jednego kursora REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="08add-126">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="08add-127">Pokazuje, jak można wykonać procedury przechowywanej PL/SQL, która zwraca dwa parametry REF CURSOR i wpisuje <xref:System.Data.DataSet> z wierszy, które są zwracane.</span><span class="sxs-lookup"><span data-stu-id="08add-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08add-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08add-128">See Also</span></span>  
 [<span data-ttu-id="08add-129">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="08add-129">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="08add-130">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="08add-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
