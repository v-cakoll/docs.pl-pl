---
title: Tworzenie elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: d496167b7bce31491402414c43ae0bcdee423b89
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786504"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="20d9e-102">Tworzenie elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="20d9e-102">Creating a DataSet</span></span>
<span data-ttu-id="20d9e-103">Można utworzyć wystąpienie <xref:System.Data.DataSet> obiektu przez <xref:System.Data.DataSet> wywołanie konstruktora.</span><span class="sxs-lookup"><span data-stu-id="20d9e-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="20d9e-104">Opcjonalnie można określić argument nazwy.</span><span class="sxs-lookup"><span data-stu-id="20d9e-104">Optionally specify a name argument.</span></span> <span data-ttu-id="20d9e-105">Jeśli nie określisz nazwy dla <xref:System.Data.DataSet>, nazwa zostanie ustawiona na "NewDataSet".</span><span class="sxs-lookup"><span data-stu-id="20d9e-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="20d9e-106">Możesz również utworzyć nowy <xref:System.Data.DataSet> oparty na istniejącym. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="20d9e-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="20d9e-107"><xref:System.Data.DataSet> Nowy może być dokładną kopią istniejącej <xref:System.Data.DataSet> <xref:System.Data.DataSet> ; klon, który kopiuje strukturę relacyjną lub schemat <xref:System.Data.DataSet>, ale nie zawiera żadnych danych z istniejącego <xref:System.Data.DataSet>lub podzestawu, zawierający tylko zmodyfikowane wiersze z istniejących <xref:System.Data.DataSet> <xref:System.Data.DataSet.GetChanges%2A> przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="20d9e-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="20d9e-108">Aby uzyskać więcej informacji, zobacz [kopiowanie zawartości zestawu danych](copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="20d9e-108">For more information, see [Copying DataSet Contents](copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="20d9e-109">Poniższy przykład kodu demonstruje sposób konstruowania wystąpienia <xref:System.Data.DataSet>obiektu.</span><span class="sxs-lookup"><span data-stu-id="20d9e-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="20d9e-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20d9e-110">See also</span></span>

- [<span data-ttu-id="20d9e-111">Wypełnianie zestawu danych z elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="20d9e-111">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="20d9e-112">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="20d9e-112">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="20d9e-113">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="20d9e-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
