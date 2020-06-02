---
title: Dodawanie kolumn do elementu DataTable
description: Element DataTable zawiera obiekty DataColumn, do których odwołują się właściwości Columns tabeli. Użyj tego przykładowego kodu, aby dodać kolumny do tabeli w ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 9d6d21696acd7a6b63cfd6d2ea7e906ec2acd7c9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286950"
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="45c94-104">Dodawanie kolumn do elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="45c94-104">Adding Columns to a DataTable</span></span>
<span data-ttu-id="45c94-105">A <xref:System.Data.DataTable> zawiera kolekcję obiektów, <xref:System.Data.DataColumn> do których odwołuje się Właściwość **kolumn** tabeli.</span><span class="sxs-lookup"><span data-stu-id="45c94-105">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="45c94-106">Ta kolekcja kolumn, wraz z wszelkimi ograniczeniami, definiuje schemat, czyli strukturę tabeli.</span><span class="sxs-lookup"><span data-stu-id="45c94-106">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="45c94-107">Tworzysz obiekty **DataColumn** w tabeli przy użyciu konstruktora **DataColumn** lub wywołując metodę **Add** właściwości **Columns** tabeli, która jest <xref:System.Data.DataColumnCollection> .</span><span class="sxs-lookup"><span data-stu-id="45c94-107">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="45c94-108">Metoda **Add** akceptuje opcjonalne argumenty **ColumnName**, **DataType**i **Expression** i tworzy nową **kolumnę DataColumn** jako element członkowski kolekcji.</span><span class="sxs-lookup"><span data-stu-id="45c94-108">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="45c94-109">Akceptuje również istniejący obiekt **DataColumn** i dodaje go do kolekcji i zwraca odwołanie do dodanej **kolumny** , jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="45c94-109">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="45c94-110">Ponieważ obiekty **DataTable** nie są specyficzne dla żadnego źródła danych, typy .NET Framework są używane podczas określania typu danych w **kolumnie DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="45c94-110">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="45c94-111">Poniższy przykład dodaje cztery kolumny do **elementu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="45c94-111">The following example adds four columns to a **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="45c94-112">W przykładzie należy zauważyć, że właściwości kolumny **CustId** są ustawione tak, aby nie zezwalały na wartości **DBNull** i ograniczać wartości jako unikatowe.</span><span class="sxs-lookup"><span data-stu-id="45c94-112">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="45c94-113">Jednak w przypadku zdefiniowania kolumny **CustId** jako kolumny klucza podstawowego tabeli Właściwość **AllowDBNull** zostanie automatycznie ustawiona na **wartość false** , a właściwość **Unique** zostanie automatycznie ustawiona na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="45c94-113">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="45c94-114">Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="45c94-114">For more information, see [Defining Primary Keys](defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="45c94-115">Jeśli nie podano nazwy kolumny dla kolumny, kolumna otrzymuje przyrostową domyślną nazwę kolumny*N,* rozpoczynając od "Kolumna1", gdy zostanie dodana do elementu **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="45c94-115">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="45c94-116">Zalecamy uniknięcie konwencji nazewnictwa "Column*N*" w przypadku podania nazwy kolumny, ponieważ dostarczona nazwa może powodować konflikt z istniejącą domyślną nazwą kolumny w elemencie **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="45c94-116">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="45c94-117">Jeśli podana nazwa już istnieje, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="45c94-117">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="45c94-118">Jeśli używasz programu <xref:System.Xml.Linq.XElement> jako elementu <xref:System.Data.DataColumn.DataType%2A> <xref:System.Data.DataColumn> w <xref:System.Data.DataTable> , serializacja XML nie będzie działała podczas odczytywania danych.</span><span class="sxs-lookup"><span data-stu-id="45c94-118">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="45c94-119">Na przykład jeśli piszesz a przy <xref:System.Xml.XmlDocument> użyciu `DataTable.WriteXml` metody, po serializacji do kodu XML istnieje dodatkowy węzeł nadrzędny w obiekcie <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="45c94-119">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="45c94-120">Aby obejść ten problem, użyj <xref:System.Data.SqlTypes.SqlXml> typu zamiast <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="45c94-120">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="45c94-121">`ReadXml`i `WriteXml` działają poprawnie z <xref:System.Data.SqlTypes.SqlXml> .</span><span class="sxs-lookup"><span data-stu-id="45c94-121">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c94-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45c94-122">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="45c94-123">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="45c94-123">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="45c94-124">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="45c94-124">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="45c94-125">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="45c94-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
