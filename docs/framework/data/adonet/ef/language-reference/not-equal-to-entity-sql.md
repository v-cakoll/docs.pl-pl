---
title: '! = (Nie jest równa) (jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: 4ed09b0c5f10ef1ac77c4b374619508d714f1dc3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="65106-102">! = (Nie jest równa) (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="65106-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="65106-103">Porównuje dwa wyrażenia, aby określić, czy po lewej stronie wyrażenia nie jest równa prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="65106-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="65106-104">! = (Nie) operator równe jest funkcjonalnym odpowiednikiem < > — operator.</span><span class="sxs-lookup"><span data-stu-id="65106-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65106-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="65106-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="65106-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="65106-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="65106-107">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="65106-107">Any valid expression.</span></span> <span data-ttu-id="65106-108">Oba wyrażenia musi mieć typów danych umożliwiają niejawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="65106-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="65106-109">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="65106-109">Result Types</span></span>  
 <span data-ttu-id="65106-110">`true` Jeśli po lewej stronie wyrażenia nie jest równa prawe wyrażenie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="65106-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65106-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="65106-111">Example</span></span>  
 <span data-ttu-id="65106-112">Następujące zapytanie SQL jednostki używa! = — operator do porównania dwóch wyrażeń w celu ustalenia, czy po lewej stronie wyrażenia nie jest równa prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="65106-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="65106-113">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="65106-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="65106-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="65106-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="65106-115">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="65106-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="65106-116">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="65106-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="65106-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65106-117">See Also</span></span>  
 [<span data-ttu-id="65106-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="65106-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
