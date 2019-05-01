---
title: SPŁASZCZANIE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 4f9a6315fc9cc2f295c21cc5fb7e1007e47796b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879726"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="c7f7c-102">SPŁASZCZANIE (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="c7f7c-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="c7f7c-103">Konwertuje kolekcję spłaszczonych kolekcją kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c7f7c-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="c7f7c-104">Nowa kolekcja zawiera te same elementy co stary kolekcji, ale bez struktury zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="c7f7c-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7f7c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7f7c-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="c7f7c-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c7f7c-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="c7f7c-107">Dowolne prawidłowe wyrażenie, które zwraca kolekcję wartości kolekcji do spłaszczenia w jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="c7f7c-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7f7c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7f7c-108">Remarks</span></span>  
 <span data-ttu-id="c7f7c-109">`FLATTEN` Przykładem jest [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="c7f7c-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="c7f7c-110">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są przetwarzane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="c7f7c-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="c7f7c-111">Zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="c7f7c-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7f7c-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7f7c-112">Example</span></span>  
 <span data-ttu-id="c7f7c-113">Następujące zapytanie SQL jednostki używa `FLATTEN` operatora, aby przekonwertować kolekcję spłaszczonych kolekcją kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c7f7c-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="c7f7c-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="c7f7c-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c7f7c-115">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="c7f7c-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c7f7c-116">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="c7f7c-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="c7f7c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7f7c-117">See also</span></span>

- [<span data-ttu-id="c7f7c-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c7f7c-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
