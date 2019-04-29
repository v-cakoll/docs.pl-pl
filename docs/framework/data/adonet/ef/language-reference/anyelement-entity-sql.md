---
title: ANYELEMENT (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: ff79417008b7807fbf206d4bcb65b4e5ea1cc576
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606039"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="0b11e-102">ANYELEMENT (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="0b11e-102">ANYELEMENT (Entity SQL)</span></span>
<span data-ttu-id="0b11e-103">Wyodrębnia element z kolekcji wielowartościowych.</span><span class="sxs-lookup"><span data-stu-id="0b11e-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b11e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b11e-104">Syntax</span></span>  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="0b11e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0b11e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0b11e-106">Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję można wyodrębnić elementu z.</span><span class="sxs-lookup"><span data-stu-id="0b11e-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b11e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0b11e-107">Return Value</span></span>  
 <span data-ttu-id="0b11e-108">Pojedynczy element w kolekcji lub dowolnego elementu, jeśli kolekcja zawiera więcej niż jedną; Jeśli kolekcja jest pusta, funkcja zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="0b11e-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="0b11e-109">Jeśli `collection` jest kolekcją typów `Collection<T>`, następnie `ANYELEMENT(collection)` jest prawidłowym wyrażeniem, które zwracają wystąpienia typu `T`.</span><span class="sxs-lookup"><span data-stu-id="0b11e-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b11e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b11e-110">Remarks</span></span>  
 <span data-ttu-id="0b11e-111">ANYELEMENT wyodrębnia dowolnego elementu z kolekcji wielowartościowych.</span><span class="sxs-lookup"><span data-stu-id="0b11e-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="0b11e-112">Na przykład, poniższy przykład próbuje wyodrębnić elementu pojedynczego wystąpienia z zestawu `Customers`.</span><span class="sxs-lookup"><span data-stu-id="0b11e-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="0b11e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b11e-113">Example</span></span>  
 <span data-ttu-id="0b11e-114">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora ANYELEMENT można wyodrębnić elementu z kolekcji wielowartościowych.</span><span class="sxs-lookup"><span data-stu-id="0b11e-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="0b11e-115">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0b11e-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0b11e-116">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="0b11e-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0b11e-117">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0b11e-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0b11e-118">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="0b11e-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="0b11e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b11e-119">See also</span></span>

- [<span data-ttu-id="0b11e-120">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="0b11e-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="0b11e-121">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="0b11e-121">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
