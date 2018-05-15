---
title: 'Porady: reprezentowały kolumny znaczników czasu lub kolumny wersji'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: 2fc8aaf260dc3657e33e539939fdf58ad8224c93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="b2470-102">Porady: reprezentowały kolumny znaczników czasu lub kolumny wersji</span><span class="sxs-lookup"><span data-stu-id="b2470-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="b2470-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu określone pole lub właściwość jako reprezentujący kolumny bazy danych, który zawiera numery sygnatury czasowe lub wersji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b2470-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="b2470-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2470-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="b2470-105">Aby wyznaczyć kolumny znaczników czasu lub wersja reprezentujący pola lub właściwości</span><span class="sxs-lookup"><span data-stu-id="b2470-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1.  <span data-ttu-id="b2470-106">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b2470-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="b2470-107">Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> wartości właściwości do `true`.</span><span class="sxs-lookup"><span data-stu-id="b2470-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2470-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2470-108">See Also</span></span>  
 [<span data-ttu-id="b2470-109">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b2470-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="b2470-110">Instrukcje: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności</span><span class="sxs-lookup"><span data-stu-id="b2470-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 [<span data-ttu-id="b2470-111">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="b2470-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
