---
title: WIERSZ (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: eb5062399eec9d8453d8922e05698ca9124d94d7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765610"
---
# <a name="row-entity-sql"></a><span data-ttu-id="4b0e3-102">WIERSZ (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="4b0e3-102">ROW (Entity SQL)</span></span>
<span data-ttu-id="4b0e3-103">Tworzy rekordy anonimowe, strukturę typu z co najmniej jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-103">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b0e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b0e3-104">Syntax</span></span>  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b0e3-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4b0e3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4b0e3-106">Dowolne wyrażenie prawidłową kwerendę, która zwraca wartość do konstruowania typu wiersza.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-106">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="4b0e3-107">Określa aliasu dla wartości określonej w typu wiersza.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-107">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="4b0e3-108">Jeśli nie podano aliasu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować alias na podstawie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generowania reguł.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-108">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b0e3-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4b0e3-109">Return Value</span></span>  
 <span data-ttu-id="4b0e3-110">Typ wiersza.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-110">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b0e3-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b0e3-111">Remarks</span></span>  
 <span data-ttu-id="4b0e3-112">Użyj konstruktorów wiersza w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do skonstruowania anonimowe, strukturę maszynowy rekordy z co najmniej jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-112">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="4b0e3-113">Typ wyniku konstruktorze wierszy jest typu wiersza, których typy pól odpowiadają typy wartości, które zostały użyte do konstruowania wiersza.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-113">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="4b0e3-114">Na przykład poniższe wyrażenie tworzy wartość typu `Record(a int, b string, c int)`.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-114">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="4b0e3-115">Jeśli nie zostanie określona alias dla wyrażenia w Konstruktorze row, programu Entity Framework próbuje wygenerować.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-115">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="4b0e3-116">Aby uzyskać więcej informacji, zobacz sekcję "Zasady aliasowania" [identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-116">For more information, see the "Aliasing Rules" section of the [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="4b0e3-117">Wyrażenie aliasów w Konstruktorze row mają zastosowanie następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="4b0e3-117">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
-   <span data-ttu-id="4b0e3-118">Wyrażenia w Konstruktorze row nie może odwoływać się do innych aliasów w tej samej konstruktora.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-118">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
-   <span data-ttu-id="4b0e3-119">Dwóch wyrażeń w tym samym Konstruktor row nie może mieć takiego samego aliasu.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-119">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="4b0e3-120">Aby uzyskać więcej informacji o konstruktorów zapytania, zobacz [konstruowania typy](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4b0e3-120">For more information about query constructors, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b0e3-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b0e3-121">Example</span></span>  
 <span data-ttu-id="4b0e3-122">Następujące zapytanie SQL jednostki wykorzystuje operator wiersza do utworzenia anonimowe, strukturę typu rekordów.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-122">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="4b0e3-123">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4b0e3-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4b0e3-124">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="4b0e3-124">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4b0e3-125">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4b0e3-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="4b0e3-126">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="4b0e3-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a><span data-ttu-id="4b0e3-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b0e3-127">See Also</span></span>  
 [<span data-ttu-id="4b0e3-128">Konstruowanie typów</span><span class="sxs-lookup"><span data-stu-id="4b0e3-128">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="4b0e3-129">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="4b0e3-129">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="4b0e3-130">Definicje typu</span><span class="sxs-lookup"><span data-stu-id="4b0e3-130">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
