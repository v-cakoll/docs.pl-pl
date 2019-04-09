---
title: (Modulo) (Jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: b08689b6f5b17950738c557e02f995fa85aeb35e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160488"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="e9668-102">(Modulo) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="e9668-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="e9668-103">Zwraca resztę z dzielenia jednego wyrażenia podzielona przez inny.</span><span class="sxs-lookup"><span data-stu-id="e9668-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9668-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9668-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="e9668-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e9668-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="e9668-106">Wyrażenie liczbowe, aby podzielić.</span><span class="sxs-lookup"><span data-stu-id="e9668-106">The numeric expression to divide.</span></span> `dividend` <span data-ttu-id="e9668-107">jest dowolne prawidłowe wyrażenie jednego z typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="e9668-107">is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="e9668-108">Wyrażenie liczbowe do dzielenia dzielnej przez.</span><span class="sxs-lookup"><span data-stu-id="e9668-108">The numeric expression to divide the dividend by.</span></span> `divisor` <span data-ttu-id="e9668-109">jest dowolne prawidłowe wyrażenie jednego z typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="e9668-109">is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e9668-110">Typy wyników</span><span class="sxs-lookup"><span data-stu-id="e9668-110">Result Types</span></span>  
 <span data-ttu-id="e9668-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="e9668-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9668-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9668-112">Example</span></span>  
 <span data-ttu-id="e9668-113">Następujące zapytanie SQL jednostki używa operatora arytmetycznego % do zwracania końca jedno wyrażenie podzielona przez inny.</span><span class="sxs-lookup"><span data-stu-id="e9668-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="e9668-114">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e9668-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e9668-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="e9668-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e9668-116">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e9668-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="e9668-117">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="e9668-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="e9668-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9668-118">See also</span></span>

- [<span data-ttu-id="e9668-119">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e9668-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
