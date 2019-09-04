---
title: SPŁASZCZ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 327a20bbc53566846e7d828f511bcd1d25cc5504
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250969"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="9353a-102">SPŁASZCZ (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9353a-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="9353a-103">Konwertuje kolekcję kolekcji na spłaszczoną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="9353a-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="9353a-104">Nowa kolekcja zawiera wszystkie te same elementy co stara kolekcja, ale bez zagnieżdżonej struktury.</span><span class="sxs-lookup"><span data-stu-id="9353a-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9353a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9353a-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="9353a-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9353a-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="9353a-107">Dowolne prawidłowe wyrażenie zwracające kolekcję kolekcji wartości do spłaszczenia do pojedynczej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9353a-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9353a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9353a-108">Remarks</span></span>  
 <span data-ttu-id="9353a-109">`FLATTEN`jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu.</span><span class="sxs-lookup"><span data-stu-id="9353a-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="9353a-110">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="9353a-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="9353a-111">Zobacz [z wyjątkiem](except-entity-sql.md) informacji o priorytecie dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu.</span><span class="sxs-lookup"><span data-stu-id="9353a-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9353a-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="9353a-112">Example</span></span>  
 <span data-ttu-id="9353a-113">Poniższe zapytanie Entity SQL używa `FLATTEN` operatora do konwertowania kolekcji kolekcji na spłaszczoną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="9353a-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="9353a-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="9353a-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9353a-115">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="9353a-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9353a-116">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="9353a-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="9353a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9353a-117">See also</span></span>

- [<span data-ttu-id="9353a-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="9353a-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
