---
title: Dodawanie kolumn do elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 77bf117b8835623d768f8b8b0ec3e4195174cad7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043948"
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="c6c6a-102">Dodawanie kolumn do elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="c6c6a-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="c6c6a-103">A <xref:System.Data.DataTable> zawiera<xref:System.Data.DataColumn> kolekcję obiektów, do których odwołuje się Właściwość **kolumn** tabeli.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="c6c6a-104">Ta kolekcja kolumn, wraz z wszelkimi ograniczeniami, definiuje schemat, czyli strukturę tabeli.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="c6c6a-105">Tworzysz obiekty **DataColumn** w tabeli przy użyciu konstruktora DataColumn lub wywołując metodę **Add** właściwości Columns tabeli, która jest. <xref:System.Data.DataColumnCollection></span><span class="sxs-lookup"><span data-stu-id="c6c6a-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="c6c6a-106">Metoda **Add** akceptuje opcjonalne argumenty **ColumnName**, **DataType**i **Expression** i tworzy nową **kolumnę DataColumn** jako element członkowski kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="c6c6a-107">Akceptuje również istniejący obiekt **DataColumn** i dodaje go do kolekcji i zwraca odwołanie do dodanej **kolumny** , jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="c6c6a-108">Ponieważ obiekty **DataTable** nie są specyficzne dla żadnego źródła danych, typy .NET Framework są używane podczas określania typu danych w **kolumnie DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="c6c6a-109">Poniższy przykład dodaje cztery kolumny do **elementu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-109">The following example adds four columns to a **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="c6c6a-110">W przykładzie należy zauważyć, że właściwości kolumny **CustId** są ustawione tak, aby nie zezwalały na wartości **DBNull** i ograniczać wartości jako unikatowe.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="c6c6a-111">Jednak w przypadku zdefiniowania kolumny **CustId** jako kolumny klucza podstawowego tabeli Właściwość **AllowDBNull** zostanie automatycznie ustawiona na **wartość false** , a właściwość **Unique** zostanie automatycznie ustawiona na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="c6c6a-112">Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="c6c6a-112">For more information, see [Defining Primary Keys](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="c6c6a-113">Jeśli nie podano nazwy kolumny dla kolumny, kolumna otrzymuje przyrostową domyślną nazwę kolumny*N,* rozpoczynając od "Kolumna1", gdy zostanie dodana do elementu DataColumnCollection.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="c6c6a-114">Zalecamy uniknięcie konwencji nazewnictwa "Column*N*" w przypadku podania nazwy kolumny, ponieważ dostarczona nazwa może powodować konflikt z istniejącą domyślną nazwą kolumny w elemencie DataColumnCollection.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="c6c6a-115">Jeśli podana nazwa już istnieje, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="c6c6a-116">Jeśli używasz <xref:System.Xml.Linq.XElement> programu <xref:System.Data.DataColumn.DataType%2A> jako <xref:System.Data.DataColumn> elementu w<xref:System.Data.DataTable>, serializacja XML nie będzie działała podczas odczytywania danych.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="c6c6a-117">Na przykład jeśli piszesz a <xref:System.Xml.XmlDocument> przy `DataTable.WriteXml` użyciu metody, po serializacji do kodu XML istnieje <xref:System.Xml.Linq.XElement>dodatkowy węzeł nadrzędny w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="c6c6a-118">Aby obejść ten problem, użyj <xref:System.Data.SqlTypes.SqlXml> typu <xref:System.Xml.Linq.XElement>zamiast.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="c6c6a-119">`ReadXml`i `WriteXml` działają poprawnie z <xref:System.Data.SqlTypes.SqlXml>.</span><span class="sxs-lookup"><span data-stu-id="c6c6a-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6c6a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6c6a-120">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="c6c6a-121">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="c6c6a-121">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="c6c6a-122">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="c6c6a-122">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="c6c6a-123">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="c6c6a-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
