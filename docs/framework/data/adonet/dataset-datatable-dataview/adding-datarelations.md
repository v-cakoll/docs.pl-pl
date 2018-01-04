---
title: Dodawanie DataRelations
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
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9741f44b68e1cac8c464338f556979d682d9e128
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="adding-datarelations"></a><span data-ttu-id="17b6b-102">Dodawanie DataRelations</span><span class="sxs-lookup"><span data-stu-id="17b6b-102">Adding DataRelations</span></span>
<span data-ttu-id="17b6b-103">W <xref:System.Data.DataSet> w wielu <xref:System.Data.DataTable> obiekty, można użyć <xref:System.Data.DataRelation> obiektów do powiązania z jednej tabeli do innego, przejdź do tabel i zwracanie wszystkich wierszy podrzędnej lub nadrzędnej z powiązanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="17b6b-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="17b6b-104">Argumenty wymagane do utworzenia **DataRelation** są nazwę **DataRelation** tworzona i tablicę co najmniej jeden <xref:System.Data.DataColumn> odwołania do kolumn, które służą jako nadrzędne i podrzędne kolumny w relacji.</span><span class="sxs-lookup"><span data-stu-id="17b6b-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="17b6b-105">Po utworzeniu **DataRelation**, go do przechodzenia między tabelami i służy do pobierania wartości.</span><span class="sxs-lookup"><span data-stu-id="17b6b-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="17b6b-106">Dodawanie **DataRelation** do <xref:System.Data.DataSet> dodaje domyślnie <xref:System.Data.UniqueConstraint> tabelą nadrzędną i <xref:System.Data.ForeignKeyConstraint> do tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="17b6b-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="17b6b-107">Aby uzyskać więcej informacji o tych ograniczeniach domyślnych, zobacz [ograniczenia DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="17b6b-107">For more information about these default constraints, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="17b6b-108">Poniższy przykład kodu tworzy **DataRelation** za pomocą dwóch <xref:System.Data.DataTable> obiekty w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="17b6b-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="17b6b-109">Każdy <xref:System.Data.DataTable> zawiera kolumny o nazwie **IDKlienta**, która służy jako łącza między dwoma <xref:System.Data.DataTable> obiektów.</span><span class="sxs-lookup"><span data-stu-id="17b6b-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="17b6b-110">W przykładzie dodano pojedynczy **DataRelation** do **relacji** kolekcji <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="17b6b-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="17b6b-111">Pierwszy argument w przykładzie nazwa **DataRelation** tworzona.</span><span class="sxs-lookup"><span data-stu-id="17b6b-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="17b6b-112">Drugi argument ustawia element nadrzędny **DataColumn** i trzeci argument zestawów dziecka **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="17b6b-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
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
  
 <span data-ttu-id="17b6b-113">A **DataRelation** ma również **zagnieżdżone** właściwości, gdy wartość **true**, powoduje, że wiersze z tabeli podrzędnej, aby być zagnieżdżone w obrębie skojarzone wiersza z tabeli nadrzędnej gdy zapisywane jako elementów XML za pomocą <xref:System.Data.DataSet.WriteXml%2A> .</span><span class="sxs-lookup"><span data-stu-id="17b6b-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="17b6b-114">Aby uzyskać więcej informacji, zobacz [za pomocą XML w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="17b6b-114">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b6b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17b6b-115">See Also</span></span>  
 [<span data-ttu-id="17b6b-116">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="17b6b-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="17b6b-117">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="17b6b-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
