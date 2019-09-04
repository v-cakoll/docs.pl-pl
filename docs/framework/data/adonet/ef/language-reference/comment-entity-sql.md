---
title: --(Komentarz) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 1ea1929b0e6f965f71fbb015ee6795affb3bce7c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251205"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="d7ade-102">--(Komentarz) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d7ade-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d7ade-103">zapytania mogą zawierać komentarze.</span><span class="sxs-lookup"><span data-stu-id="d7ade-103">queries can contain comments.</span></span> <span data-ttu-id="d7ade-104">Dwie kreski (`--`) — Zacznij od wiersza komentarza.</span><span class="sxs-lookup"><span data-stu-id="d7ade-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7ade-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7ade-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="d7ade-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d7ade-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="d7ade-107">Jest ciągiem znaków, który zawiera tekst komentarza.</span><span class="sxs-lookup"><span data-stu-id="d7ade-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7ade-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7ade-108">Example</span></span>  
 <span data-ttu-id="d7ade-109">W poniższym zapytaniu Entity SQL pokazano, jak używać komentarzy.</span><span class="sxs-lookup"><span data-stu-id="d7ade-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="d7ade-110">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d7ade-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d7ade-111">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="d7ade-111">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d7ade-112">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="d7ade-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="d7ade-113">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="d7ade-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="d7ade-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7ade-114">See also</span></span>

- [<span data-ttu-id="d7ade-115">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="d7ade-115">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="d7ade-116">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="d7ade-116">Entity SQL Reference</span></span>](entity-sql-reference.md)
