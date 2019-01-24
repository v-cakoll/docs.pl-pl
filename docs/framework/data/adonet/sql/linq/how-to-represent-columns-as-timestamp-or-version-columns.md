---
title: 'Instrukcje: Reprezentuje kolumn jako sygnatura czasowa lub kolumny wersji'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: fa9ffe01c45df3ce0342b62e12007ddf88ee412d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674573"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="7c85c-102">Instrukcje: Reprezentuje kolumn jako sygnatura czasowa lub kolumny wersji</span><span class="sxs-lookup"><span data-stu-id="7c85c-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="7c85c-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby wyznaczyć reprezentująca kolumnę w bazie danych, który zawiera numery wersji lub sygnatur czasowych bazy danych do pola lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="7c85c-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="7c85c-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c85c-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="7c85c-105">Aby wyznaczyć reprezentujący kolumnę sygnatur czasowych lub wersji pola lub właściwości</span><span class="sxs-lookup"><span data-stu-id="7c85c-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1.  <span data-ttu-id="7c85c-106">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7c85c-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="7c85c-107">Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> wartość właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="7c85c-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c85c-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c85c-108">See also</span></span>
- [<span data-ttu-id="7c85c-109">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7c85c-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="7c85c-110">Instrukcje: Określ, której członkami są sprawdzane pod kątem konfliktów współbieżności</span><span class="sxs-lookup"><span data-stu-id="7c85c-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="7c85c-111">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="7c85c-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
