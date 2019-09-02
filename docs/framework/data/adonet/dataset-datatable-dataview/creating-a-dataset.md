---
title: Tworzenie elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 19badb009ebe95c52ab1dbbaef96f280c769553b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205155"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="7a148-102">Tworzenie elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="7a148-102">Creating a DataSet</span></span>
<span data-ttu-id="7a148-103">Można utworzyć wystąpienie <xref:System.Data.DataSet> obiektu przez <xref:System.Data.DataSet> wywołanie konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7a148-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="7a148-104">Opcjonalnie można określić argument nazwy.</span><span class="sxs-lookup"><span data-stu-id="7a148-104">Optionally specify a name argument.</span></span> <span data-ttu-id="7a148-105">Jeśli nie określisz nazwy dla <xref:System.Data.DataSet>, nazwa zostanie ustawiona na "NewDataSet".</span><span class="sxs-lookup"><span data-stu-id="7a148-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="7a148-106">Możesz również utworzyć nowy <xref:System.Data.DataSet> oparty na istniejącym. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="7a148-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7a148-107"><xref:System.Data.DataSet> Nowy może być dokładną kopią istniejącej <xref:System.Data.DataSet> <xref:System.Data.DataSet> ; klon, który kopiuje strukturę relacyjną lub schemat <xref:System.Data.DataSet>, ale nie zawiera żadnych danych z istniejącego <xref:System.Data.DataSet>lub podzestawu, zawierający tylko zmodyfikowane wiersze z istniejących <xref:System.Data.DataSet> <xref:System.Data.DataSet.GetChanges%2A> przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="7a148-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="7a148-108">Aby uzyskać więcej informacji, zobacz [kopiowanie zawartości zestawu danych](copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="7a148-108">For more information, see [Copying DataSet Contents](copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="7a148-109">Poniższy przykład kodu demonstruje sposób konstruowania wystąpienia <xref:System.Data.DataSet>obiektu.</span><span class="sxs-lookup"><span data-stu-id="7a148-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a148-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a148-110">See also</span></span>

- [<span data-ttu-id="7a148-111">Wypełnianie zestawu danych z elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="7a148-111">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="7a148-112">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="7a148-112">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="7a148-113">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="7a148-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
