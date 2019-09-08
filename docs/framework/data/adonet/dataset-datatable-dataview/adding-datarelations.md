---
title: Dodawanie elementów DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 8157d296636d0f8661a35af35de561f5cc49c30b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784810"
---
# <a name="adding-datarelations"></a><span data-ttu-id="b5854-102">Dodawanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="b5854-102">Adding DataRelations</span></span>
<span data-ttu-id="b5854-103">W przypadku <xref:System.Data.DataTable>zwieloma obiektami można użyć <xref:System.Data.DataRelation> obiektów, aby powiązać jedną tabelę z inną, aby nawigować przez tabele i zwracać elementy podrzędne lub nadrzędne z powiązanej tabeli. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="b5854-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="b5854-104">Argumenty wymagane do utworzenia **relacji** datarelationship są nazwami **tworzonego elementu** datarelationship i tablicą zawierającą <xref:System.Data.DataColumn> co najmniej jedno odwołanie do kolumn, które pełnią rolę kolumn nadrzędnych i podrzędnych w relacji.</span><span class="sxs-lookup"><span data-stu-id="b5854-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="b5854-105">Po utworzeniu **relacji**można jej używać do nawigowania między tabelami i pobierania wartości.</span><span class="sxs-lookup"><span data-stu-id="b5854-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="b5854-106">Dodawanie **relacji** do <xref:System.Data.DataSet> dodawania, domyślnie, <xref:System.Data.UniqueConstraint> do tabeli nadrzędnej i <xref:System.Data.ForeignKeyConstraint> do tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="b5854-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="b5854-107">Aby uzyskać więcej informacji o tych domyślnych ograniczeniach, zobacz temat [ograniczenia DataTable](datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="b5854-107">For more information about these default constraints, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="b5854-108">Poniższy przykład kodu tworzy **relację** danych przy użyciu dwóch <xref:System.Data.DataTable> obiektów w. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="b5854-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b5854-109">Każda <xref:System.Data.DataTable> z nich zawiera kolumnę o nazwie **CustId**, która służy jako link między dwoma <xref:System.Data.DataTable> obiektami.</span><span class="sxs-lookup"><span data-stu-id="b5854-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="b5854-110">Przykład dodaje pojedyncze **powiązanie** do <xref:System.Data.DataSet>kolekcji **relacji** .</span><span class="sxs-lookup"><span data-stu-id="b5854-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b5854-111">Pierwszy argument w przykładzie określa nazwę tworzonego **powiązania** .</span><span class="sxs-lookup"><span data-stu-id="b5854-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="b5854-112">Drugi argument ustawia nadrzędną **kolumnę** danych, a trzeci argument ustawia podrzędną **kolumnę**danych.</span><span class="sxs-lookup"><span data-stu-id="b5854-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
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
  
 <span data-ttu-id="b5854-113">**Relacja** danych ma również **zagnieżdżoną** właściwość, która po ustawieniu na **wartość true**powoduje, że wiersze z tabeli podrzędnej będą zagnieżdżone w skojarzonym wierszu z tabeli nadrzędnej, gdy są zapisywane jako elementy <xref:System.Data.DataSet.WriteXml%2A> XML przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="b5854-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="b5854-114">Aby uzyskać więcej informacji, zobacz [Używanie języka XML w zestawie danych](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="b5854-114">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5854-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5854-115">See also</span></span>

- [<span data-ttu-id="b5854-116">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="b5854-116">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="b5854-117">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b5854-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
