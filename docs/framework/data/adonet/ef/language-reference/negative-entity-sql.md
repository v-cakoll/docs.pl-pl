---
title: '- Poziomem (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 7716b9115587a873531be9c14b7da93c7a148ed8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319537"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="a98b4-102">-(Wartość ujemna) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a98b4-102">- (Negative) (Entity SQL)</span></span>
<span data-ttu-id="a98b4-103">Zwraca ujemną wartość wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="a98b4-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a98b4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a98b4-104">Syntax</span></span>  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a98b4-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a98b4-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a98b4-106">Dowolne prawidłowe wyrażenie jednego z typów danych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="a98b4-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a98b4-107">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="a98b4-107">Result Types</span></span>  
 <span data-ttu-id="a98b4-108">Typ danych `expression`.</span><span class="sxs-lookup"><span data-stu-id="a98b4-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a98b4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a98b4-109">Remarks</span></span>  
 <span data-ttu-id="a98b4-110">Jeśli `expression` jest typem bez znaku, typ wyniku będzie typem ze znakiem, który najlepiej odnosi się do typu `expression`.</span><span class="sxs-lookup"><span data-stu-id="a98b4-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="a98b4-111">Na przykład jeśli `expression` jest typu Byte, zostanie zwrócona wartość typu Int16.</span><span class="sxs-lookup"><span data-stu-id="a98b4-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a98b4-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="a98b4-112">Example</span></span>  
 <span data-ttu-id="a98b4-113">Poniższe zapytanie Entity SQL używa operatora-arytmetycznego, aby zwrócić ujemną wartość wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="a98b4-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="a98b4-114">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a98b4-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a98b4-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="a98b4-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a98b4-116">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a98b4-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a98b4-117">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="a98b4-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="a98b4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a98b4-118">See also</span></span>

- [<span data-ttu-id="a98b4-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="a98b4-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
