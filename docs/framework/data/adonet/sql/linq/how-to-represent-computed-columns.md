---
title: 'Instrukcje: Reprezentacja kolumn obliczanych'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: 01c3442448285893ebb476ed11889e073065d4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943545"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="02e92-102">Instrukcje: Reprezentacja kolumn obliczanych</span><span class="sxs-lookup"><span data-stu-id="02e92-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="02e92-103">Użyj właściwości dla<xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby reprezentować kolumnę, której zawartość jest wynikiem obliczania. <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02e92-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="02e92-104">Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="02e92-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="02e92-105">Program nie obsługuje kolumn obliczanych jako kluczy podstawowych.</span><span class="sxs-lookup"><span data-stu-id="02e92-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="02e92-106">Aby przedstawić kolumnę obliczaną</span><span class="sxs-lookup"><span data-stu-id="02e92-106">To represent a computed column</span></span>  
  
1. <span data-ttu-id="02e92-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="02e92-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="02e92-108">Przypisz ciąg reprezentujący formułę do <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="02e92-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02e92-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02e92-109">See also</span></span>

- [<span data-ttu-id="02e92-110">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="02e92-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="02e92-111">Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu</span><span class="sxs-lookup"><span data-stu-id="02e92-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
