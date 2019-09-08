---
title: 'Instrukcje: Reprezentacja kluczy podstawowych'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 5df82292f000d7f5e61cab699237b86de30bda70
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793434"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="a91e8-102">Instrukcje: Reprezentacja kluczy podstawowych</span><span class="sxs-lookup"><span data-stu-id="a91e8-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="a91e8-103">Użyj właściwości w atrybucie, <xref:System.Data.Linq.Mapping.ColumnAttribute> aby wyznaczyć właściwość lub pole reprezentujące klucz podstawowy dla kolumny bazy danych. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a91e8-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="a91e8-104">Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="a91e8-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a91e8-105">Program nie obsługuje kolumn obliczanych jako kluczy podstawowych.</span><span class="sxs-lookup"><span data-stu-id="a91e8-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="a91e8-106">Aby wyznaczyć właściwość lub pole jako klucz podstawowy</span><span class="sxs-lookup"><span data-stu-id="a91e8-106">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="a91e8-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a91e8-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="a91e8-108">Określ wartość jako `true`.</span><span class="sxs-lookup"><span data-stu-id="a91e8-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a91e8-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a91e8-109">See also</span></span>

- [<span data-ttu-id="a91e8-110">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a91e8-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="a91e8-111">Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu</span><span class="sxs-lookup"><span data-stu-id="a91e8-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
