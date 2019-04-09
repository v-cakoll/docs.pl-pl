---
title: SPŁASZCZANIE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 76fba91f27479df19bbc4ac6e120d615a16f1d42
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115118"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="4f0b7-102">SPŁASZCZANIE (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="4f0b7-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="4f0b7-103">Konwertuje kolekcję spłaszczonych kolekcją kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4f0b7-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="4f0b7-104">Nowa kolekcja zawiera te same elementy co stary kolekcji, ale bez struktury zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="4f0b7-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f0b7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f0b7-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="4f0b7-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4f0b7-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="4f0b7-107">Dowolne prawidłowe wyrażenie, które zwraca kolekcję wartości kolekcji do spłaszczenia w jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="4f0b7-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f0b7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f0b7-108">Remarks</span></span>  
 `FLATTEN` <span data-ttu-id="4f0b7-109">Przykładem jest [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="4f0b7-109">is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="4f0b7-110">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są przetwarzane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="4f0b7-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="4f0b7-111">Zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="4f0b7-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f0b7-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f0b7-112">Example</span></span>  
 <span data-ttu-id="4f0b7-113">Następujące zapytanie SQL jednostki używa `FLATTEN` operatora, aby przekonwertować kolekcję spłaszczonych kolekcją kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4f0b7-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="4f0b7-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="4f0b7-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4f0b7-115">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4f0b7-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="4f0b7-116">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="4f0b7-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="4f0b7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f0b7-117">See also</span></span>

- [<span data-ttu-id="4f0b7-118">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4f0b7-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
