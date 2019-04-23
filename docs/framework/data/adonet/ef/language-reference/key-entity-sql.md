---
title: KLUCZ (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 9cd3276583741f2b0261cb8a0e55f4185d20100e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319342"
---
# <a name="key-entity-sql"></a><span data-ttu-id="82d28-102">KLUCZ (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="82d28-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="82d28-103">Wyodrębnia klucz referencyjnego lub wyrażenie jednostki.</span><span class="sxs-lookup"><span data-stu-id="82d28-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82d28-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="82d28-104">Syntax</span></span>  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="82d28-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82d28-105">Remarks</span></span>  
 <span data-ttu-id="82d28-106">Klucz jednostki zawiera wartości klucza w odpowiedniej kolejności określonej jednostki lub odwołanie do jednostki.</span><span class="sxs-lookup"><span data-stu-id="82d28-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="82d28-107">Ponieważ wiele zestawów jednostki mogą być oparte na ten sam typ, ten sam klucz może pojawić się w każdym zestawie jednostek.</span><span class="sxs-lookup"><span data-stu-id="82d28-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="82d28-108">Aby odwołać unikatowy, należy użyć `REF`.</span><span class="sxs-lookup"><span data-stu-id="82d28-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="82d28-109">Zwracany typ operatora klucza jest typem wiersza, który zawiera jedno pole dla każdego klucza podmiotu, w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="82d28-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="82d28-110">W poniższym przykładzie operator kluczy odwołanie do jednostki BadOrder i zwraca część klucza tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="82d28-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="82d28-111">W tym przypadku rekordu typu przy użyciu dokładnie jedno pole odpowiadające `Id` właściwości.</span><span class="sxs-lookup"><span data-stu-id="82d28-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="82d28-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="82d28-112">Example</span></span>  
 <span data-ttu-id="82d28-113">Następujące zapytanie SQL jednostki używa operatora klucza do wyodrębnienia część klucza wyrażeniu zawierającym odwołania do typu.</span><span class="sxs-lookup"><span data-stu-id="82d28-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="82d28-114">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="82d28-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="82d28-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="82d28-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="82d28-116">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="82d28-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="82d28-117">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="82d28-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a><span data-ttu-id="82d28-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82d28-118">See also</span></span>

- [<span data-ttu-id="82d28-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="82d28-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="82d28-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="82d28-120">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [<span data-ttu-id="82d28-121">REF</span><span class="sxs-lookup"><span data-stu-id="82d28-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [<span data-ttu-id="82d28-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="82d28-122">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
