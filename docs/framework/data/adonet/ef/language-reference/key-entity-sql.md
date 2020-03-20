---
title: KLUCZ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 894a9d41aa3a14ad66b537433aa315823a299f95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150172"
---
# <a name="key-entity-sql"></a><span data-ttu-id="32702-102">KLUCZ (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="32702-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="32702-103">Wyodrębnia klucz odwołania lub wyrażenia jednostki.</span><span class="sxs-lookup"><span data-stu-id="32702-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32702-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32702-104">Syntax</span></span>  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="32702-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32702-105">Remarks</span></span>  
 <span data-ttu-id="32702-106">Klucz jednostki zawiera wartości klucza w prawidłowej kolejności określonego odwołania do encji lub jednostki.</span><span class="sxs-lookup"><span data-stu-id="32702-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="32702-107">Ponieważ wiele zestawów jednostek może być opartych na tym samym typie, ten sam klucz może pojawić się w każdym zestawie jednostek.</span><span class="sxs-lookup"><span data-stu-id="32702-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="32702-108">Aby uzyskać unikatowe `REF`odwołanie, użyj programu .</span><span class="sxs-lookup"><span data-stu-id="32702-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="32702-109">Typ zwracany operatora KEY jest typem wiersza, który zawiera jedno pole dla każdego klucza encji w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="32702-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="32702-110">W poniższym przykładzie operator klucza jest przekazywana odwołanie do BadOrder jednostki i zwraca kluczową część tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="32702-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="32702-111">W takim przypadku typ rekordu z dokładnie jednym `Id` polem odpowiadającym właściwości.</span><span class="sxs-lookup"><span data-stu-id="32702-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="32702-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="32702-112">Example</span></span>  
 <span data-ttu-id="32702-113">Następująca kwerenda SQL jednostki używa key operatora wyodrębnić kluczową część wyrażenia z odwołania typu.</span><span class="sxs-lookup"><span data-stu-id="32702-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="32702-114">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="32702-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="32702-115">Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="32702-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="32702-116">Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="32702-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="32702-117">Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:</span><span class="sxs-lookup"><span data-stu-id="32702-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a><span data-ttu-id="32702-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32702-118">See also</span></span>

- [<span data-ttu-id="32702-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="32702-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="32702-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="32702-120">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="32702-121">Ref</span><span class="sxs-lookup"><span data-stu-id="32702-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="32702-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="32702-122">DEREF</span></span>](deref-entity-sql.md)
