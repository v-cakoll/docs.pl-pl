---
title: 'Instrukcje: Reprezentacja kolumn obliczanych'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: df72562b303e5b9a7c31334df06926f157b59b05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903880"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="07a57-102">Instrukcje: Reprezentacja kolumn obliczanych</span><span class="sxs-lookup"><span data-stu-id="07a57-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="07a57-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu do reprezentowania kolumny, w których zawartość jest wynik obliczenia.</span><span class="sxs-lookup"><span data-stu-id="07a57-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="07a57-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="07a57-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="07a57-105">nie obsługuje kolumn obliczanych jako klucze podstawowe.</span><span class="sxs-lookup"><span data-stu-id="07a57-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="07a57-106">Do reprezentowania kolumny obliczanej</span><span class="sxs-lookup"><span data-stu-id="07a57-106">To represent a computed column</span></span>  
  
1. <span data-ttu-id="07a57-107">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="07a57-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="07a57-108">Reprezentacja ciągu formułę, aby przypisać <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="07a57-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a57-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07a57-109">See also</span></span>

- [<span data-ttu-id="07a57-110">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="07a57-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="07a57-111">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="07a57-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
