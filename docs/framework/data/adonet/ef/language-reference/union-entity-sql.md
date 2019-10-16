---
title: Unia (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: a5a20beb0ab55dcbaf2dbbb75801b50ab9ef6722
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319216"
---
# <a name="union-entity-sql"></a><span data-ttu-id="777c6-102">Unia (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="777c6-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="777c6-103">Łączy wyniki dwóch lub więcej zapytań w jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="777c6-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="777c6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="777c6-104">Syntax</span></span>  
  
```sql  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="777c6-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="777c6-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="777c6-106">Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję do połączenia z kolekcją, wszystkie wyrażenia muszą być tego samego typu lub typu wspólnego lub pochodnego jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="777c6-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="777c6-107">UNION</span><span class="sxs-lookup"><span data-stu-id="777c6-107">UNION</span></span>  
 <span data-ttu-id="777c6-108">Określa, że wiele kolekcji ma być łączonych i zwracane jako pojedyncza kolekcja.</span><span class="sxs-lookup"><span data-stu-id="777c6-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="777c6-109">CAŁĄ</span><span class="sxs-lookup"><span data-stu-id="777c6-109">ALL</span></span>  
 <span data-ttu-id="777c6-110">Określa, że wielokrotne kolekcje mają być połączone i zwracane jako pojedyncze kolekcje, w tym duplikaty.</span><span class="sxs-lookup"><span data-stu-id="777c6-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="777c6-111">Jeśli nie zostanie określony, duplikaty są usuwane z kolekcji wyników.</span><span class="sxs-lookup"><span data-stu-id="777c6-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="777c6-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="777c6-112">Return Value</span></span>  
 <span data-ttu-id="777c6-113">Kolekcja tego samego typu lub typowego typu podstawowego lub pochodnego jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="777c6-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="777c6-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="777c6-114">Remarks</span></span>  
 <span data-ttu-id="777c6-115">Unia jest jednym z operatorów zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="777c6-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="777c6-116">Wszystkie operatory zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="777c6-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="777c6-117">Aby uzyskać informacje o pierwszeństwie dla operatorów zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zobacz [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="777c6-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="777c6-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="777c6-118">Example</span></span>  
 <span data-ttu-id="777c6-119">Poniższe zapytanie Entity SQL używa operatora UNION ALL do łączenia wyników dwóch zapytań w jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="777c6-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="777c6-120">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="777c6-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="777c6-121">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="777c6-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="777c6-122">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="777c6-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="777c6-123">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="777c6-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#UNION](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#union)]  
  
## <a name="see-also"></a><span data-ttu-id="777c6-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="777c6-124">See also</span></span>

- [<span data-ttu-id="777c6-125">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="777c6-125">Entity SQL Reference</span></span>](entity-sql-reference.md)
