---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7c6b326b15a2af58da9206adf28070e57fec600c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963515"
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="4654c-102">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="4654c-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="4654c-103">.NET Framework Dostawca danych dla programu Oracle obsługuje typ danych **Cursor ref** firmy Oracle.</span><span class="sxs-lookup"><span data-stu-id="4654c-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="4654c-104">Gdy dostawca danych jest używany do pracy z kursorami REF Oracle, należy wziąć pod uwagę następujące zachowania.</span><span class="sxs-lookup"><span data-stu-id="4654c-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4654c-105">Niektóre zachowania różnią się od tych Microsoft OLE DB Provider dla Oracle (MSDAORA I).</span><span class="sxs-lookup"><span data-stu-id="4654c-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
- <span data-ttu-id="4654c-106">Ze względu na wydajność Dostawca danych dla programu Oracle nie wiąże się automatycznie z typem danych **kursora referencyjnego** , tak jak MSDAORA i, chyba że jawnie je określisz.</span><span class="sxs-lookup"><span data-stu-id="4654c-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
- <span data-ttu-id="4654c-107">Dostawca danych nie obsługuje żadnych sekwencji unikowych ODBC, w tym kontrolki ucieczki {zestaw wyników} służącej do określania parametrów REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="4654c-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
- <span data-ttu-id="4654c-108">Aby wykonać procedurę przechowywaną, która zwraca kursory ref, należy zdefiniować <xref:System.Data.OracleClient.OracleParameterCollection>parametry w <xref:System.Data.OracleClient.OracleType> z kursorem i a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> .</span><span class="sxs-lookup"><span data-stu-id="4654c-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="4654c-109">Dostawca danych obsługuje Powiązywanie kursorów REFERENCYJNych jako parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4654c-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="4654c-110">Dostawca nie obsługuje REFERENCYJNych kursorów jako parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="4654c-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
- <span data-ttu-id="4654c-111"><xref:System.Data.OracleClient.OracleDataReader> Uzyskanie z wartości parametru nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="4654c-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="4654c-112">Wartości są typu <xref:System.DBNull> po wykonaniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="4654c-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
- <span data-ttu-id="4654c-113">Jedyną wartością wyliczenia **CommandBehavior** , która działa z kursorami ref (na przykład gdy wywoływanie <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) jest **CloseConnection**; wszystkie pozostałe są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="4654c-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
- <span data-ttu-id="4654c-114">Kolejność kursorów REF w **OracleDataReader** zależy od kolejności parametrów w **OracleParameterCollection**.</span><span class="sxs-lookup"><span data-stu-id="4654c-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="4654c-115"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Właściwość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="4654c-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
- <span data-ttu-id="4654c-116">Typ danych **tabeli** pl/SQL nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="4654c-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="4654c-117">Jednak kursory REF są bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="4654c-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="4654c-118">Jeśli musisz użyć typu danych **tabeli** , użyj OLE DB .NET Dostawca danych z msdaora i.</span><span class="sxs-lookup"><span data-stu-id="4654c-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4654c-119">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4654c-119">In This Section</span></span>  
 [<span data-ttu-id="4654c-120">Przykłady REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="4654c-120">REF CURSOR Examples</span></span>](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 <span data-ttu-id="4654c-121">Zawiera trzy przykłady, które demonstrują korzystanie z kursorów REF.</span><span class="sxs-lookup"><span data-stu-id="4654c-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="4654c-122">Parametry kursora REF CURSOR w OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="4654c-122">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="4654c-123">Pokazuje, jak wykonać procedurę składowaną PL/SQL, która zwraca parametr REF CURSOR i odczytuje wartość jako **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="4654c-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="4654c-124">Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="4654c-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="4654c-125">Demonstruje sposób wykonywania procedury składowanej PL/SQL, która zwraca dwa parametry REF CURSOR i odczytuje wartości przy użyciu **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="4654c-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="4654c-126">Wypełnianie zestawu danych przy użyciu przynajmniej jednego kursora REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="4654c-126">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="4654c-127">Demonstruje sposób wykonywania procedury składowanej pl/SQL, która zwraca dwa parametry kursora ref, i wypełnia <xref:System.Data.DataSet> z zwracanymi wierszami.</span><span class="sxs-lookup"><span data-stu-id="4654c-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4654c-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4654c-128">See also</span></span>

- [<span data-ttu-id="4654c-129">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4654c-129">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [<span data-ttu-id="4654c-130">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="4654c-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
