---
title: --(Komentarz) (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 40a0ee8f6bc2cf8fae5779ecb3d103c77dde161b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137179"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="74872-102">--(Komentarz) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="74872-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="74872-103">zapytania mogą zawierać komentarzy.</span><span class="sxs-lookup"><span data-stu-id="74872-103">queries can contain comments.</span></span> <span data-ttu-id="74872-104">Dwa łączniki (`--`) uruchom wiersz komentarza.</span><span class="sxs-lookup"><span data-stu-id="74872-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74872-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="74872-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="74872-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="74872-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="74872-107">Jest ciąg znaków, który zawiera tekst komentarza.</span><span class="sxs-lookup"><span data-stu-id="74872-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74872-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="74872-108">Example</span></span>  
 <span data-ttu-id="74872-109">Następujące zapytanie SQL jednostki pokazuje, jak używać komentarzy.</span><span class="sxs-lookup"><span data-stu-id="74872-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="74872-110">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="74872-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="74872-111">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="74872-111">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="74872-112">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="74872-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="74872-113">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="74872-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="74872-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74872-114">See also</span></span>

- [<span data-ttu-id="74872-115">Przegląd języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="74872-115">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="74872-116">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="74872-116">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
