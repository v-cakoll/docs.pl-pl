---
title: KLUCZ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 44ab5352c3b2a94cb210c3de775d2347d2df7fe7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250484"
---
# <a name="key-entity-sql"></a><span data-ttu-id="c1974-102">KLUCZ (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c1974-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="c1974-103">Wyodrębnia klucz odwołania lub wyrażenia jednostki.</span><span class="sxs-lookup"><span data-stu-id="c1974-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1974-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1974-104">Syntax</span></span>  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="c1974-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1974-105">Remarks</span></span>  
 <span data-ttu-id="c1974-106">Klucz jednostki zawiera wartości klucza w prawidłowej kolejności określonej jednostki lub odwołania do jednostki.</span><span class="sxs-lookup"><span data-stu-id="c1974-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="c1974-107">Ponieważ wiele zestawów jednostek może opierać się na tym samym typie, ten sam klucz może pojawić się w każdym zestawie jednostek.</span><span class="sxs-lookup"><span data-stu-id="c1974-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="c1974-108">Aby uzyskać unikatowe odwołanie, użyj `REF`.</span><span class="sxs-lookup"><span data-stu-id="c1974-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="c1974-109">Zwracany typ operatora klucza jest typem wiersza, który zawiera jedno pole dla każdego klucza jednostki, w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="c1974-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="c1974-110">W poniższym przykładzie operator klucza jest przekazywać odwołanie do jednostki BadOrder i zwraca część klucza tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="c1974-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="c1974-111">W tym przypadku typ rekordu z dokładnie jednym polem odpowiadającym `Id` właściwości.</span><span class="sxs-lookup"><span data-stu-id="c1974-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="c1974-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1974-112">Example</span></span>  
 <span data-ttu-id="c1974-113">Poniższe zapytanie Entity SQL używa operatora KEY do wyodrębnienia części klucza wyrażenia z odwołaniem do typu.</span><span class="sxs-lookup"><span data-stu-id="c1974-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="c1974-114">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c1974-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c1974-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="c1974-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c1974-116">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="c1974-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c1974-117">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="c1974-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a><span data-ttu-id="c1974-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1974-118">See also</span></span>

- [<span data-ttu-id="c1974-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c1974-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c1974-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="c1974-120">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="c1974-121">REF</span><span class="sxs-lookup"><span data-stu-id="c1974-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="c1974-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="c1974-122">DEREF</span></span>](deref-entity-sql.md)
