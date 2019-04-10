---
title: 'Instrukcje: Reprezentacja kolumn jako kolumn znacznika czasu lub wersji'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: 60486223489f5f51478cdaec788f81f7be167114
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215095"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="a7ab0-102">Instrukcje: Reprezentacja kolumn jako kolumn znacznika czasu lub wersji</span><span class="sxs-lookup"><span data-stu-id="a7ab0-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="a7ab0-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby wyznaczyć reprezentująca kolumnę w bazie danych, który zawiera numery wersji lub sygnatur czasowych bazy danych do pola lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="a7ab0-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="a7ab0-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7ab0-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="a7ab0-105">Aby wyznaczyć reprezentujący kolumnę sygnatur czasowych lub wersji pola lub właściwości</span><span class="sxs-lookup"><span data-stu-id="a7ab0-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1.  <span data-ttu-id="a7ab0-106">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a7ab0-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="a7ab0-107">Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> wartość właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="a7ab0-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ab0-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7ab0-108">See also</span></span>

- [<span data-ttu-id="a7ab0-109">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a7ab0-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="a7ab0-110">Instrukcje: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności</span><span class="sxs-lookup"><span data-stu-id="a7ab0-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="a7ab0-111">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="a7ab0-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
