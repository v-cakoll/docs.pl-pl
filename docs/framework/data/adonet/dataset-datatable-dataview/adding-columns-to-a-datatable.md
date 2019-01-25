---
title: Dodawanie kolumn do DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 892c0488588e9a5b59650f4a815ba9819493a610
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538274"
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="bd0e2-102">Dodawanie kolumn do DataTable</span><span class="sxs-lookup"><span data-stu-id="bd0e2-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="bd0e2-103">A <xref:System.Data.DataTable> zawiera zbiór <xref:System.Data.DataColumn> obiektów, odwołuje się **kolumn** właściwości tabeli.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="bd0e2-104">Ta kolekcja kolumn, wraz ze wszystkimi ograniczeniami definiuje schemat lub strukturę tabeli.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="bd0e2-105">Możesz utworzyć **DataColumn** obiektów w tabeli za pomocą **DataColumn** konstruktora, lub przez wywołanie **Dodaj** metody **kolumn**właściwości tabeli, który jest <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="bd0e2-106">**Dodaj** metoda przyjmuje opcjonalny **ColumnName**, **DataType**, i **wyrażenie** argumentów i tworzy nową  **DataColumn** jako członka kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="bd0e2-107">Akceptuje ona również, istniejące **DataColumn** obiektu i dodaje go do kolekcji i zwraca odwołanie do dodany **DataColumn** Jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="bd0e2-108">Ponieważ **DataTable** obiekty nie są specyficzne dla dowolnego źródła danych, typów programu .NET Framework są używane podczas określania typu danych **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="bd0e2-109">W poniższym przykładzie dodano cztery kolumny w celu **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-109">The following example adds four columns to a **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="bd0e2-110">W tym przykładzie należy zauważyć, że właściwości **CustID** kolumna są ustawione na Zezwalaj **DBNull** wartości i ograniczyć wartości, które mają być unikatowe.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="bd0e2-111">Jednak jeśli zdefiniujesz **CustID** kolumny jako kolumny klucza podstawowego tabeli **AllowDBNull** właściwość zostanie automatycznie ustawiony w pozycji **false** i **Unikatowe** właściwość zostanie automatycznie ustawiony w pozycji **true**.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="bd0e2-112">Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="bd0e2-112">For more information, see [Defining Primary Keys](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="bd0e2-113">Jeśli nie podano nazwy kolumny dla kolumny, kolumna jest otrzymuje nazwę przyrostowe domyślne kolumny*N,* począwszy od "Kolumna1", gdy jest ona dodawana do **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="bd0e2-114">Firma Microsoft zaleca, aby unikać konwencji nazewnictwa "kolumna*N*" po użytkownik poda nazwę kolumny, ponieważ nazwa podana może spowodować konflikt z istniejącą nazwą kolumny domyślne w **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="bd0e2-115">Jeśli podana nazwa już istnieje, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="bd0e2-116">Jeśli używasz <xref:System.Xml.Linq.XElement> jako <xref:System.Data.DataColumn.DataType%2A> z <xref:System.Data.DataColumn> w <xref:System.Data.DataTable>, serializacji XML nie będzie działać podczas odczytywania danych.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="bd0e2-117">Na przykład, jeśli możesz zapisać <xref:System.Xml.XmlDocument> przy użyciu `DataTable.WriteXml` metoda po serializacji XML jest dodatkowe nadrzędnym w <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="bd0e2-118">Aby obejść ten problem, należy użyć <xref:System.Data.SqlTypes.SqlXml> wpisz zamiast <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="bd0e2-119">`ReadXml` i `WriteXml` działają prawidłowo z <xref:System.Data.SqlTypes.SqlXml>.</span><span class="sxs-lookup"><span data-stu-id="bd0e2-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd0e2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd0e2-120">See also</span></span>
- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="bd0e2-121">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="bd0e2-121">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="bd0e2-122">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="bd0e2-122">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="bd0e2-123">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="bd0e2-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
