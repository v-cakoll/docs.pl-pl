---
title: WIERSZ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: dfd0031f49cbdf41797cecf21c149fafde4d7a8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249252"
---
# <a name="row-entity-sql"></a><span data-ttu-id="2eb22-102">WIERSZ (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2eb22-102">ROW (Entity SQL)</span></span>
<span data-ttu-id="2eb22-103">Konstruuje anonimowe, strukturalnie wpisane rekordy z co najmniej jednej wartości.</span><span class="sxs-lookup"><span data-stu-id="2eb22-103">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eb22-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2eb22-104">Syntax</span></span>  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="2eb22-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2eb22-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2eb22-106">Każde prawidłowe wyrażenie zapytania, które zwraca wartość do skonstruowania w typie wiersza.</span><span class="sxs-lookup"><span data-stu-id="2eb22-106">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="2eb22-107">Określa alias dla wartości określonej w typie wiersza.</span><span class="sxs-lookup"><span data-stu-id="2eb22-107">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="2eb22-108">Jeśli nie podano aliasu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] program podejmie próbę wygenerowania aliasu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] na podstawie reguł generowania aliasów.</span><span class="sxs-lookup"><span data-stu-id="2eb22-108">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2eb22-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2eb22-109">Return Value</span></span>  
 <span data-ttu-id="2eb22-110">Typ wiersza.</span><span class="sxs-lookup"><span data-stu-id="2eb22-110">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2eb22-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2eb22-111">Remarks</span></span>  
 <span data-ttu-id="2eb22-112">Konstruktory wierszy w programie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] służą do konstruowania anonimowych, strukturalnie wpisanych rekordów z co najmniej jednej wartości.</span><span class="sxs-lookup"><span data-stu-id="2eb22-112">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="2eb22-113">Typ wyniku konstruktora wierszy jest typem wiersza, którego typy pól odpowiadają typom wartości, które były używane do konstruowania wiersza.</span><span class="sxs-lookup"><span data-stu-id="2eb22-113">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="2eb22-114">Na przykład następujące wyrażenie konstruuje wartość typu `Record(a int, b string, c int)`.</span><span class="sxs-lookup"><span data-stu-id="2eb22-114">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="2eb22-115">Jeśli nie podasz aliasu dla wyrażenia w konstruktorze wierszy, Entity Framework podejmie próbę wygenerowania jednego.</span><span class="sxs-lookup"><span data-stu-id="2eb22-115">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="2eb22-116">Aby uzyskać więcej informacji, zobacz sekcję "reguły aliasów" tematu [identyfikatory](identifiers-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="2eb22-116">For more information, see the "Aliasing Rules" section of the [Identifiers](identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="2eb22-117">W konstruktorze wierszy są stosowane następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="2eb22-117">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="2eb22-118">Wyrażenia w konstruktorze wierszy nie mogą odwoływać się do innych aliasów w tym samym konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="2eb22-118">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="2eb22-119">Dwa wyrażenia w tym samym konstruktorze wierszy nie mogą mieć tego samego aliasu.</span><span class="sxs-lookup"><span data-stu-id="2eb22-119">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="2eb22-120">Aby uzyskać więcej informacji na temat konstruktorów zapytań, zobacz [konstruowanie typów](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2eb22-120">For more information about query constructors, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2eb22-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="2eb22-121">Example</span></span>  
 <span data-ttu-id="2eb22-122">Poniższe zapytanie Entity SQL używa operatora wiersza do konstruowania anonimowych, strukturalnych rekordów z określonym typem.</span><span class="sxs-lookup"><span data-stu-id="2eb22-122">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="2eb22-123">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2eb22-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2eb22-124">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="2eb22-124">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2eb22-125">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="2eb22-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2eb22-126">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="2eb22-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a><span data-ttu-id="2eb22-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2eb22-127">See also</span></span>

- [<span data-ttu-id="2eb22-128">Konstruowanie typów</span><span class="sxs-lookup"><span data-stu-id="2eb22-128">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="2eb22-129">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="2eb22-129">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="2eb22-130">Definicje typu</span><span class="sxs-lookup"><span data-stu-id="2eb22-130">Type Definitions</span></span>](type-definitions-entity-sql.md)
