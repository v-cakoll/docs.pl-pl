---
title: Definicje typów (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 471964266c290d5eba95804dbe1c2bc5225e3f83
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248950"
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="ce2b2-102">Definicje typów (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ce2b2-102">Type Definitions (Entity SQL)</span></span>
<span data-ttu-id="ce2b2-103">Definicja typu jest używana w instrukcji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] deklaracji funkcji wbudowanej.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce2b2-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce2b2-104">Remarks</span></span>  
 <span data-ttu-id="ce2b2-105">Instrukcja deklaracji dla wbudowanej funkcji składa się ze słowa kluczowego [Function](function-entity-sql.md) , po którym następuje identyfikator reprezentujący nazwę funkcji (na przykład "myavg"), po której następuje lista definicji parametrów w nawiasie (na przykład "Kolekcja opłat ( Decimal) ").</span><span class="sxs-lookup"><span data-stu-id="ce2b2-105">The declaration statement for an inline function consists of the [FUNCTION](function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="ce2b2-106">Lista definicji parametrów składa się z zero lub więcej definicji parametrów.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="ce2b2-107">Każda definicja parametru składa się z identyfikatora (nazwa parametru do funkcji, na przykład "należności"), po której następuje definicja typu (na przykład "Kolekcja (liczba dziesiętna)").</span><span class="sxs-lookup"><span data-stu-id="ce2b2-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="ce2b2-108">Definicje typów mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="ce2b2-108">The type definitions can be either:</span></span>  
  
- <span data-ttu-id="ce2b2-109">Typ identyfikatora (na przykład "Int32" lub "AdventureWorks. Order").</span><span class="sxs-lookup"><span data-stu-id="ce2b2-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
- <span data-ttu-id="ce2b2-110">Słowo kluczowe `COLLECTION` , po którym następuje inna definicja typu w nawiasie (na przykład "Kolekcja (AdventureWorks. Order)").</span><span class="sxs-lookup"><span data-stu-id="ce2b2-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
- <span data-ttu-id="ce2b2-111">WIERSZ słowa kluczowego, po którym następuje lista definicji właściwości w nawiasie (na przykład "wiersz (x AdventureWorks. Order)").</span><span class="sxs-lookup"><span data-stu-id="ce2b2-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="ce2b2-112">Definicje właściwości mają format, taki jak "`identifier type_definition`, `identifier type_definition`,...".</span><span class="sxs-lookup"><span data-stu-id="ce2b2-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
- <span data-ttu-id="ce2b2-113">Słowo kluczowe REF, po którym następuje Typ identyfikatora w nawiasie (na przykład "ref (AdventureWorks. Order)").</span><span class="sxs-lookup"><span data-stu-id="ce2b2-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="ce2b2-114">Operator definicji typu REF wymaga jako argumentu typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="ce2b2-115">Nie można określić typu pierwotnego jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="ce2b2-116">Można również zagnieżdżać definicje typów (na przykład "Kolekcja (wiersz (x ref (AdventureWorks. Order))").</span><span class="sxs-lookup"><span data-stu-id="ce2b2-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="ce2b2-117">Opcje definicji typu są następujące:</span><span class="sxs-lookup"><span data-stu-id="ce2b2-117">The type definition options are:</span></span>  
  
- <span data-ttu-id="ce2b2-118">`IdentifierName supported_type`lub</span><span class="sxs-lookup"><span data-stu-id="ce2b2-118">`IdentifierName supported_type`, or</span></span>  
  
- <span data-ttu-id="ce2b2-119">`IdentifierName`Kolekcja (`type_definition`) lub</span><span class="sxs-lookup"><span data-stu-id="ce2b2-119">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
- <span data-ttu-id="ce2b2-120">`IdentifierName`Wiersz (`property_definition`) lub</span><span class="sxs-lookup"><span data-stu-id="ce2b2-120">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
- <span data-ttu-id="ce2b2-121">`IdentifierName` REF(`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="ce2b2-121">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="ce2b2-122">Opcja definicji właściwości to `IdentifierName type_definition`.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="ce2b2-123">Obsługiwane typy to wszystkie typy w bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="ce2b2-124">Obejmują one zarówno pierwotne, jak i typy jednostek.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="ce2b2-125">Obsługiwane typy jednostek odwołują się tylko do typów jednostek w bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="ce2b2-126">Nie obejmują one typów pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ce2b2-127">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ce2b2-127">Examples</span></span>  
 <span data-ttu-id="ce2b2-128">Poniżej znajduje się przykład definicji typu prostego.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-128">The following is an example of a simple type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="ce2b2-129">Poniżej znajduje się przykład definicji typu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="ce2b2-130">Poniżej znajduje się przykład definicji typu wiersza.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-130">The following is an example of a ROW type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="ce2b2-131">Poniżej znajduje się przykład definicji typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-131">The following is an example of a REF type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce2b2-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce2b2-132">See also</span></span>

- [<span data-ttu-id="ce2b2-133">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="ce2b2-133">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="ce2b2-134">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="ce2b2-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
