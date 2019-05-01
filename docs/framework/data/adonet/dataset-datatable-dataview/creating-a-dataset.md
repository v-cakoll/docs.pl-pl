---
title: Tworzenie elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: d2d17056e6dcd29ef9b5c5e8c3024a32fce32bd5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879882"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="13ca5-102">Tworzenie elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="13ca5-102">Creating a DataSet</span></span>
<span data-ttu-id="13ca5-103">Utwórz wystąpienie <xref:System.Data.DataSet> przez wywołanie metody <xref:System.Data.DataSet> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="13ca5-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="13ca5-104">Opcjonalnie można określić argument nazwy.</span><span class="sxs-lookup"><span data-stu-id="13ca5-104">Optionally specify a name argument.</span></span> <span data-ttu-id="13ca5-105">Jeśli nie określisz nazwę <xref:System.Data.DataSet>, nazwa jest równa "NewDataSet".</span><span class="sxs-lookup"><span data-stu-id="13ca5-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="13ca5-106">Można również utworzyć nową <xref:System.Data.DataSet> oparty na istniejącym <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="13ca5-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="13ca5-107">Nowy <xref:System.Data.DataSet> może być dokładną kopię istniejącego <xref:System.Data.DataSet>; klonu <xref:System.Data.DataSet> , kopiuje relacyjnej struktury lub schematu, ale która nie zawiera żadnych danych z istniejącego <xref:System.Data.DataSet>; lub być podzbiorem wartości <xref:System.Data.DataSet>, zawierająca tylko zmodyfikowane wiersze z istniejącego <xref:System.Data.DataSet> przy użyciu <xref:System.Data.DataSet.GetChanges%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="13ca5-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="13ca5-108">Aby uzyskać więcej informacji, zobacz [kopiowanie zawartości elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="13ca5-108">For more information, see [Copying DataSet Contents](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="13ca5-109">Poniższy przykład kodu pokazuje, jak skonstruować wystąpienia <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="13ca5-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="13ca5-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13ca5-110">See also</span></span>

- [<span data-ttu-id="13ca5-111">Wypełnianie zestawu danych z elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="13ca5-111">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="13ca5-112">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="13ca5-112">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="13ca5-113">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="13ca5-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
