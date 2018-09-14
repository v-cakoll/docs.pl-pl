---
title: Dodawanie elementów DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: d0f481979ead7af775d462a2624ec43080e2c5a9
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45517492"
---
# <a name="adding-datarelations"></a><span data-ttu-id="500b4-102">Dodawanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="500b4-102">Adding DataRelations</span></span>
<span data-ttu-id="500b4-103">W <xref:System.Data.DataSet> z wieloma <xref:System.Data.DataTable> obiektów, można użyć <xref:System.Data.DataRelation> obiektów do powiązania z jednej tabeli do innej, aby poruszać się po w tabelach i zwracanie podrzędnej lub nadrzędnej wierszy z tabeli powiązanej.</span><span class="sxs-lookup"><span data-stu-id="500b4-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="500b4-104">Argumenty wymagane do utworzenia **DataRelation** są nazwę **DataRelation** tworzona i tablicę co najmniej jeden <xref:System.Data.DataColumn> odwołania do kolumn, które służą jako nadrzędne i podrzędne kolumny w relacji.</span><span class="sxs-lookup"><span data-stu-id="500b4-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="500b4-105">Po utworzeniu **DataRelation**, można użyć go do nawigacji między tabelami i pobierać wartości.</span><span class="sxs-lookup"><span data-stu-id="500b4-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="500b4-106">Dodawanie **DataRelation** do <xref:System.Data.DataSet> dodaje domyślnie <xref:System.Data.UniqueConstraint> tabeli nadrzędnej i <xref:System.Data.ForeignKeyConstraint> do tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="500b4-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="500b4-107">Aby uzyskać więcej informacji o tych ograniczeniach domyślnych, zobacz [ograniczenia elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="500b4-107">For more information about these default constraints, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="500b4-108">Poniższy przykład kodu tworzy **DataRelation** za pomocą dwóch <xref:System.Data.DataTable> obiekty w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="500b4-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="500b4-109">Każdy <xref:System.Data.DataTable> zawiera kolumnę o nazwie **CustID**, który służy jako łącza między tymi dwoma <xref:System.Data.DataTable> obiektów.</span><span class="sxs-lookup"><span data-stu-id="500b4-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="500b4-110">W przykładzie dodano pojedynczej **DataRelation** do **relacji** zbiór <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="500b4-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="500b4-111">Pierwszy argument w przykładzie określa nazwę **DataRelation** tworzona.</span><span class="sxs-lookup"><span data-stu-id="500b4-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="500b4-112">Drugi argument określa element nadrzędny **DataColumn** i trzeci argument ustawia element podrzędny **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="500b4-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 <span data-ttu-id="500b4-113">A **DataRelation** ma również **zagnieżdżone** właściwość, która po ustawieniu **true**, powoduje, że wiersze z tabeli podrzędnej na być zagnieżdżony w skojarzonych wiersz z tabeli nadrzędnej Podczas zapisywania jako elementów XML przy użyciu <xref:System.Data.DataSet.WriteXml%2A> .</span><span class="sxs-lookup"><span data-stu-id="500b4-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="500b4-114">Aby uzyskać więcej informacji, zobacz [za pomocą XML w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="500b4-114">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="500b4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="500b4-115">See Also</span></span>  
 [<span data-ttu-id="500b4-116">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="500b4-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="500b4-117">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="500b4-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
