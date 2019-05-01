---
title: 'Instrukcje: Reprezentacja kluczy podstawowych'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: dcb8929c9cd9a7b88f19d760b70117a1092760f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877204"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="09c94-102">Instrukcje: Reprezentacja kluczy podstawowych</span><span class="sxs-lookup"><span data-stu-id="09c94-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="09c94-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić właściwość lub pole do reprezentowania klucza podstawowego dla kolumny bazy danych.</span><span class="sxs-lookup"><span data-stu-id="09c94-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="09c94-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="09c94-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="09c94-105">nie obsługuje kolumn obliczanych jako klucze podstawowe.</span><span class="sxs-lookup"><span data-stu-id="09c94-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="09c94-106">Aby wyznaczyć właściwość lub pole jako klucz podstawowy</span><span class="sxs-lookup"><span data-stu-id="09c94-106">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="09c94-107">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="09c94-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="09c94-108">Określ wartość jako `true`.</span><span class="sxs-lookup"><span data-stu-id="09c94-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09c94-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09c94-109">See also</span></span>

- [<span data-ttu-id="09c94-110">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="09c94-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="09c94-111">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="09c94-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
