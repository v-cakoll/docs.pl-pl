---
title: ISTNIEJE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 72d96c5f24fcedf870370de3792680831145a454
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311139"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="ec54e-102">ISTNIEJE (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="ec54e-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="ec54e-103">Określa, czy kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="ec54e-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec54e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec54e-104">Syntax</span></span>  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="ec54e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ec54e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ec54e-106">Dowolne prawidłowe wyrażenie, które zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="ec54e-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="ec54e-107">NIE</span><span class="sxs-lookup"><span data-stu-id="ec54e-107">NOT</span></span>  
 <span data-ttu-id="ec54e-108">Określa, że wynik EXISTS być ujemna.</span><span class="sxs-lookup"><span data-stu-id="ec54e-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec54e-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ec54e-109">Return Value</span></span>  
 <span data-ttu-id="ec54e-110">`true` Jeśli kolekcja nie jest pusta, w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ec54e-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec54e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec54e-111">Remarks</span></span>  
 <span data-ttu-id="ec54e-112">EXISTS jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="ec54e-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="ec54e-113">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są przetwarzane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="ec54e-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="ec54e-114">Pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zestaw operatorów, zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ec54e-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec54e-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec54e-115">Example</span></span>  
 <span data-ttu-id="ec54e-116">Następujące zapytanie SQL jednostki używa operatora EXISTS, aby ustalić, czy kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="ec54e-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="ec54e-117">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ec54e-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ec54e-118">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="ec54e-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ec54e-119">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ec54e-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ec54e-120">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="ec54e-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="ec54e-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec54e-121">See also</span></span>

- [<span data-ttu-id="ec54e-122">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="ec54e-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
