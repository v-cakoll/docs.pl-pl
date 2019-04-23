---
title: WIERSZ (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: b83020601373ba93124dfb24308dd048bfa3c6dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319394"
---
# <a name="row-entity-sql"></a><span data-ttu-id="0ec9b-102">WIERSZ (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="0ec9b-102">ROW (Entity SQL)</span></span>
<span data-ttu-id="0ec9b-103">Tworzy rekordy anonimowe, strukturalnie wpisane z co najmniej jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-103">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ec9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ec9b-104">Syntax</span></span>  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="0ec9b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0ec9b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0ec9b-106">Dowolne wyrażenie prawidłową kwerendę, która zwraca wartość do konstruowania typu wiersza.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-106">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="0ec9b-107">Określa alias dla wartości określonej w typu wiersza.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-107">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="0ec9b-108">Jeśli nie zostanie podany alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] spróbuje wygenerować na podstawie alias [!INCLUDE[esql](../../../../../../includes/esql-md.md)] reguły generowania aliasu.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-108">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ec9b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0ec9b-109">Return Value</span></span>  
 <span data-ttu-id="0ec9b-110">Typ wiersza.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-110">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ec9b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ec9b-111">Remarks</span></span>  
 <span data-ttu-id="0ec9b-112">Użyj wiersza konstruktorów w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do konstruowania anonimowe, strukturalnie wpisane rekordy z co najmniej jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-112">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="0ec9b-113">Typ wyniku w Konstruktorze wierszy jest typu wiersza, w których typy pól odpowiadają typy wartości, które zostały użyte do konstruowania wiersza.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-113">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="0ec9b-114">Na przykład poniższe wyrażenie tworzy wartość typu `Record(a int, b string, c int)`.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-114">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="0ec9b-115">Jeśli nie podasz alias wyrażenia w Konstruktorze wierszy, platformy Entity Framework podejmie próbę go wygeneruje.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-115">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="0ec9b-116">Aby uzyskać więcej informacji, zobacz sekcję "Zasady aliasowania" [identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-116">For more information, see the "Aliasing Rules" section of the [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="0ec9b-117">Następujące reguły stosuje się do wyrażenia aliasów w Konstruktorze wierszy:</span><span class="sxs-lookup"><span data-stu-id="0ec9b-117">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
-   <span data-ttu-id="0ec9b-118">Wyrażenia w Konstruktorze row nie może odwoływać się do innych aliasów w tej samej konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-118">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
-   <span data-ttu-id="0ec9b-119">Dwóch wyrażeń w tym samym Konstruktor row nie może mieć takiego samego aliasu.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-119">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="0ec9b-120">Aby uzyskać więcej informacji o konstruktory zapytania, zobacz [konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0ec9b-120">For more information about query constructors, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ec9b-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ec9b-121">Example</span></span>  
 <span data-ttu-id="0ec9b-122">Następujące zapytanie SQL jednostki używa operatora wiersz do konstruowania anonimowe, strukturalnie kontrolą typów rekordów.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-122">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="0ec9b-123">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0ec9b-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0ec9b-124">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="0ec9b-124">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0ec9b-125">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0ec9b-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0ec9b-126">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="0ec9b-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a><span data-ttu-id="0ec9b-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ec9b-127">See also</span></span>

- [<span data-ttu-id="0ec9b-128">Konstruowanie typów</span><span class="sxs-lookup"><span data-stu-id="0ec9b-128">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="0ec9b-129">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="0ec9b-129">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="0ec9b-130">Definicje typu</span><span class="sxs-lookup"><span data-stu-id="0ec9b-130">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
