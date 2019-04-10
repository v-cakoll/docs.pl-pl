---
title: 'Instrukcje: Określanie typów danych bazy danych'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: bf53463be8c715fd1c599efac1b19d838be19f86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218046"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="21e7a-102">Instrukcje: Określanie typów danych bazy danych</span><span class="sxs-lookup"><span data-stu-id="21e7a-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="21e7a-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić dokładną tekst, który definiuje kolumnę w deklaracji tabeli języka T-SQL.</span><span class="sxs-lookup"><span data-stu-id="21e7a-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="21e7a-104">Należy określić <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwości tylko wtedy, gdy planujesz używać <xref:System.Data.Linq.DataContext.CreateDatabase%2A> do utworzenia wystąpienia bazy danych.</span><span class="sxs-lookup"><span data-stu-id="21e7a-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="21e7a-105">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="21e7a-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="21e7a-106">Aby określić tekst, aby zdefiniować typ danych w tabeli języka T-SQL</span><span class="sxs-lookup"><span data-stu-id="21e7a-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1.  <span data-ttu-id="21e7a-107">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="21e7a-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="21e7a-108">Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwości tekstu do dokładnego dopasowania, który jest używany przez język T-SQL.</span><span class="sxs-lookup"><span data-stu-id="21e7a-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e7a-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21e7a-109">See also</span></span>

- [<span data-ttu-id="21e7a-110">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="21e7a-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="21e7a-111">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="21e7a-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
