---
title: < (Mniejsze niż) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: fb3f4a1c6bc0df6af3c27836f7b53b2701776366
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319694"
---
# <a name="-less-than-entity-sql"></a><span data-ttu-id="a26ff-102">\< (mniejsze niż) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a26ff-102">\< (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="a26ff-103">Porównuje dwa wyrażenia, aby określić, czy lewe wyrażenie ma wartość mniejszą niż prawo wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="a26ff-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a26ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a26ff-104">Syntax</span></span>  
  
```sql  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a26ff-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a26ff-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a26ff-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="a26ff-106">Any valid expression.</span></span> <span data-ttu-id="a26ff-107">Oba wyrażenia muszą mieć niejawnie wymienialne typy danych.</span><span class="sxs-lookup"><span data-stu-id="a26ff-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a26ff-108">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="a26ff-108">Result Types</span></span>  
 <span data-ttu-id="a26ff-109">`true`, jeśli lewe wyrażenie ma wartość mniejszą niż prawe wyrażenie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="a26ff-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a26ff-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="a26ff-110">Example</span></span>  
 <span data-ttu-id="a26ff-111">Poniższe zapytanie Entity SQL używa operatora porównania < do porównywania dwóch wyrażeń, aby określić, czy lewe wyrażenie ma wartość mniejszą niż prawe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="a26ff-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="a26ff-112">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a26ff-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a26ff-113">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="a26ff-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a26ff-114">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a26ff-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a26ff-115">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="a26ff-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="a26ff-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a26ff-116">See also</span></span>

- [<span data-ttu-id="a26ff-117">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="a26ff-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
