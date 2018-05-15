---
title: KOLEKCJA (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 2b13d373e6c54221249b17de4fa91347cbc0f9e6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="collection-entity-sql"></a><span data-ttu-id="0d8b7-102">KOLEKCJA (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="0d8b7-102">COLLECTION (Entity SQL)</span></span>
<span data-ttu-id="0d8b7-103">KOLEKCJA — słowo kluczowe jest używana tylko w definicji wbudowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="0d8b7-104">Funkcje kolekcji są funkcje, które działają na kolekcję wartości i wygenerować skalarne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d8b7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d8b7-105">Syntax</span></span>  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a><span data-ttu-id="0d8b7-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0d8b7-106">Arguments</span></span>  
 `type_definition`  
 <span data-ttu-id="0d8b7-107">Wyrażenie, które zwraca kolekcję obsługiwanych typów, wierszy i odwołań.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d8b7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d8b7-108">Remarks</span></span>  
 <span data-ttu-id="0d8b7-109">Aby uzyskać więcej informacji na temat — słowo kluczowe KOLEKCJI, zobacz [definicje typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0d8b7-109">For more information about the COLLECTION keyword, see [Type Definitions](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d8b7-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d8b7-110">Example</span></span>  
 <span data-ttu-id="0d8b7-111">Poniższy przykład przedstawia sposób użycia słowa kluczowego KOLEKCJI można deklarować kolekcji miejsc dziesiętnych jako argumentu dla funkcji wbudowanej zapytania.</span><span class="sxs-lookup"><span data-stu-id="0d8b7-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="0d8b7-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d8b7-112">See Also</span></span>  
 [<span data-ttu-id="0d8b7-113">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="0d8b7-113">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
