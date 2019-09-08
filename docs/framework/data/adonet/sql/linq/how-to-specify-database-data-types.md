---
title: 'Instrukcje: Określanie typów danych bazy danych'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 09ca8dc6fa440138523bcd2905335a04517dd806
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793272"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="9c8c7-102">Instrukcje: Określanie typów danych bazy danych</span><span class="sxs-lookup"><span data-stu-id="9c8c7-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="9c8c7-103">Użyj właściwości dla<xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić dokładny tekst, który definiuje kolumnę w deklaracji tabeli T-SQL. <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c8c7-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="9c8c7-104"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> Właściwość należy określić tylko wtedy, gdy planujesz użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A> , aby utworzyć wystąpienie bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9c8c7-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="9c8c7-105">Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c8c7-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="9c8c7-106">Aby określić tekst definiujący typ danych w tabeli T-SQL</span><span class="sxs-lookup"><span data-stu-id="9c8c7-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1. <span data-ttu-id="9c8c7-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9c8c7-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="9c8c7-108">Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwości na dokładny tekst, który jest używany przez język T-SQL.</span><span class="sxs-lookup"><span data-stu-id="9c8c7-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c8c7-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c8c7-109">See also</span></span>

- [<span data-ttu-id="9c8c7-110">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9c8c7-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="9c8c7-111">Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu</span><span class="sxs-lookup"><span data-stu-id="9c8c7-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
