---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 4dd0a78fafe63197987938021195723e3eed0885
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740999"
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="f92c6-102">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="f92c6-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="f92c6-103">.NET Framework Data Provider for Oracle obsługuje programu Oracle **REF CURSOR** typu danych.</span><span class="sxs-lookup"><span data-stu-id="f92c6-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="f92c6-104">Przy użyciu dostawcy danych do pracy z Oracle REF CURSOR, należy rozważyć następujące zachowania.</span><span class="sxs-lookup"><span data-stu-id="f92c6-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f92c6-105">Niektóre zachowania różnią się od dostawcy Microsoft OLE DB dla Oracle (MSDAORA i).</span><span class="sxs-lookup"><span data-stu-id="f92c6-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
-   <span data-ttu-id="f92c6-106">Ze względu na wydajność Data Provider Pro Oracle nie jest automatycznie powiązana **REF CURSOR** typy danych, podobnie jak MSDAORA i, chyba że jawnie określisz je.</span><span class="sxs-lookup"><span data-stu-id="f92c6-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
-   <span data-ttu-id="f92c6-107">Dostawca danych nie obsługuje żadnych sekwencje unikowe ODBC, w tym znak ucieczki {resultset} używane do określania parametrów REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="f92c6-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
-   <span data-ttu-id="f92c6-108">Aby wykonać procedurę składowaną, która zwraca kursora REF CURSOR, należy zdefiniować parametry w <xref:System.Data.OracleClient.OracleParameterCollection> z <xref:System.Data.OracleClient.OracleType> z **kursora** i <xref:System.Data.OracleClient.OracleParameter.Direction%2A> z **dane wyjściowe**.</span><span class="sxs-lookup"><span data-stu-id="f92c6-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="f92c6-109">Dostawca danych obsługuje powiązanie kursora REF CURSOR jako parametry wyjściowe tylko.</span><span class="sxs-lookup"><span data-stu-id="f92c6-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="f92c6-110">Dostawca nie obsługuje kursora REF CURSOR jako parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f92c6-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
-   <span data-ttu-id="f92c6-111">Uzyskiwanie <xref:System.Data.OracleClient.OracleDataReader> z parametru wartość nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="f92c6-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="f92c6-112">Wartości są typu <xref:System.DBNull> po wykonaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="f92c6-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
-   <span data-ttu-id="f92c6-113">Tylko **commandbehavior ustawiono** wartości wyliczenia, która współdziała z kursora REF CURSOR (na przykład w przypadku, gdy wywołanie <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) jest **metody**; pozostałe są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f92c6-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
-   <span data-ttu-id="f92c6-114">Kolejność kursora REF CURSOR w **Element OracleDataReader** zależy od rzędu kilku parametrów w **OracleParameterCollection**.</span><span class="sxs-lookup"><span data-stu-id="f92c6-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="f92c6-115"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Właściwość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="f92c6-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
-   <span data-ttu-id="f92c6-116">PL/SQL **tabeli** typ danych nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="f92c6-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="f92c6-117">Jednak kursora REF CURSOR są bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="f92c6-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="f92c6-118">Jeśli musisz użyć **tabeli** typ danych, należy użyć z MSDAORA i dostawcy OLE DB .NET danych.</span><span class="sxs-lookup"><span data-stu-id="f92c6-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f92c6-119">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f92c6-119">In This Section</span></span>  
 [<span data-ttu-id="f92c6-120">Przykłady REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="f92c6-120">REF CURSOR Examples</span></span>](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 <span data-ttu-id="f92c6-121">Zawiera trzy przykłady demonstrujące użycie kursora REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="f92c6-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="f92c6-122">Parametry kursora REF CURSOR w OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="f92c6-122">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="f92c6-123">Pokazuje, jak wykonać procedury przechowywanych PL/SQL, zwraca parametr REF CURSOR, która odczytuje wartość jako **Element OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="f92c6-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="f92c6-124">Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="f92c6-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="f92c6-125">Pokazuje, jak można wykonać procedury przechowywanej PL/SQL, która zwraca dwa parametry REF CURSOR, a następnie odczytuje wartości za pomocą **Element OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="f92c6-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="f92c6-126">Wypełnianie zestawu danych przy użyciu przynajmniej jednego kursora REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="f92c6-126">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="f92c6-127">Pokazuje, jak można wykonać procedury przechowywanej PL/SQL, która zwraca dwa parametry REF CURSOR i wypełnia <xref:System.Data.DataSet> wierszy, które są zwracane.</span><span class="sxs-lookup"><span data-stu-id="f92c6-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f92c6-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f92c6-128">See also</span></span>
- [<span data-ttu-id="f92c6-129">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f92c6-129">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [<span data-ttu-id="f92c6-130">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="f92c6-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
