---
title: 'Porady: reprezentuje kolumny obliczane'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 42afded36f6006f369dfddb7ed3a51598b3fc33a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="402a9-102">Porady: reprezentuje kolumny obliczane</span><span class="sxs-lookup"><span data-stu-id="402a9-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="402a9-103">Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu do reprezentowania kolumny, których zawartość jest wynikiem obliczania.</span><span class="sxs-lookup"><span data-stu-id="402a9-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="402a9-104">Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="402a9-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="402a9-105">nie obsługuje kolumn obliczanych jako klucze podstawowe.</span><span class="sxs-lookup"><span data-stu-id="402a9-105"> does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="402a9-106">Do reprezentowania kolumny obliczanej</span><span class="sxs-lookup"><span data-stu-id="402a9-106">To represent a computed column</span></span>  
  
1.  <span data-ttu-id="402a9-107">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="402a9-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="402a9-108">Reprezentacja ciągu formuły, aby przypisać <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="402a9-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="402a9-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="402a9-109">See Also</span></span>  
 [<span data-ttu-id="402a9-110">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="402a9-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="402a9-111">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="402a9-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
