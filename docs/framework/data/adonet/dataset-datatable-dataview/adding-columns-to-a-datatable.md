---
title: Dodawanie kolumn do DataTable
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
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6107c21ed04c9c39d69c5c784244d8f6bf9560e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="be1e6-102">Dodawanie kolumn do DataTable</span><span class="sxs-lookup"><span data-stu-id="be1e6-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="be1e6-103">A <xref:System.Data.DataTable> zawiera kolekcję <xref:System.Data.DataColumn> odwołują się obiekty **kolumn** właściwość tabeli.</span><span class="sxs-lookup"><span data-stu-id="be1e6-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="be1e6-104">W tej kolekcji kolumn, wraz ze wszystkimi ograniczeniami definiuje schemat lub struktury tabeli.</span><span class="sxs-lookup"><span data-stu-id="be1e6-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="be1e6-105">Możesz utworzyć **DataColumn** obiektów w tabeli za pomocą **DataColumn** konstruktora, lub przez wywołanie metody **Dodaj** metody **kolumn**właściwości tabeli, która jest <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="be1e6-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="be1e6-106">**Dodaj** metoda przyjmuje opcjonalny **ColumnName**, **DataType**, i **wyrażenie** argumentów i tworzy nowy  **Element DataColumn** jako członka kolekcji.</span><span class="sxs-lookup"><span data-stu-id="be1e6-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="be1e6-107">Również akceptuje istniejące **DataColumn** obiektów i dodaje go do kolekcji i zwraca odwołanie do dodany **DataColumn** żądanie.</span><span class="sxs-lookup"><span data-stu-id="be1e6-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="be1e6-108">Ponieważ **DataTable** obiekty nie są specyficzne dla dowolnego źródła danych, typy .NET Framework są używane podczas określania typu danych **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="be1e6-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="be1e6-109">W poniższym przykładzie dodano cztery kolumny w celu **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="be1e6-109">The following example adds four columns to a **DataTable**.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 <span data-ttu-id="be1e6-110">W tym przykładzie należy zauważyć, że właściwości **IDKlienta** kolumny są ustawione na nie zezwalać na **DBNull** wartości i ograniczyć unikatowe wartości.</span><span class="sxs-lookup"><span data-stu-id="be1e6-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="be1e6-111">Jednak w przypadku definiowania **IDKlienta** kolumny jako kolumny klucza podstawowego tabeli **AllowDBNull** zostanie automatycznie ustawiona właściwość do **false** i **Unique** zostanie automatycznie ustawiona właściwość do **true**.</span><span class="sxs-lookup"><span data-stu-id="be1e6-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="be1e6-112">Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="be1e6-112">For more information, see [Defining Primary Keys](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="be1e6-113">Jeśli nie podano nazwy kolumn dla kolumny, kolumnie podano przyrostowe domyślną nazwę kolumny*N,* począwszy od "Kolumna1", gdy jest ona dodawana do **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="be1e6-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="be1e6-114">Firma Microsoft zaleca, aby uniknąć z konwencją nazewnictwa "kolumny*N*" gdy Podaj nazwę kolumny, ponieważ Podaj nazwę może spowodować konflikt z istniejącą nazwą kolumny domyślne w **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="be1e6-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="be1e6-115">Jeśli podanej nazwie już istnieje, jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="be1e6-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="be1e6-116">Jeśli używasz <xref:System.Xml.Linq.XElement> jako <xref:System.Data.DataColumn.DataType%2A> z <xref:System.Data.DataColumn> w <xref:System.Data.DataTable>, podczas odczytu w danych serializacji XML nie będą działać.</span><span class="sxs-lookup"><span data-stu-id="be1e6-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="be1e6-117">Na przykład, jeśli należy zapisać <xref:System.Xml.XmlDocument> za pomocą `DataTable.WriteXml` metody podczas serializacji XML jest dodatkowe nadrzędnym w <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="be1e6-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="be1e6-118">Aby obejść ten problem, należy użyć <xref:System.Data.SqlTypes.SqlXml> wpisz zamiast <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="be1e6-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="be1e6-119">`ReadXml`i `WriteXml` pracować poprawnie z <xref:System.Data.SqlTypes.SqlXml>.</span><span class="sxs-lookup"><span data-stu-id="be1e6-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be1e6-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be1e6-120">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="be1e6-121">Definicja schematu tabeli DataTable</span><span class="sxs-lookup"><span data-stu-id="be1e6-121">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="be1e6-122">DataTables</span><span class="sxs-lookup"><span data-stu-id="be1e6-122">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="be1e6-123">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="be1e6-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
