---
title: Definicje typów (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 5a8a0cae4599057a627cce6abebf34c7f05e821f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641396"
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="3fcef-102">Definicje typów (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="3fcef-102">Type Definitions (Entity SQL)</span></span>
<span data-ttu-id="3fcef-103">Definicja typu jest używana w instrukcji deklaracji elementu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcja w tekście.</span><span class="sxs-lookup"><span data-stu-id="3fcef-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fcef-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3fcef-104">Remarks</span></span>  
 <span data-ttu-id="3fcef-105">Instrukcji deklaracji dla wbudowanej funkcji składa się z [funkcja](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) następuje identyfikator reprezentujący nazwę funkcji (na przykład "MyAvg"), a następnie listę definicji parametrów w nawiasie (słowo kluczowe przykład "opłat Collection(Decimal)").</span><span class="sxs-lookup"><span data-stu-id="3fcef-105">The declaration statement for an inline function consists of the [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="3fcef-106">Lista definicji parametru składa się z zero lub więcej definicji parametru.</span><span class="sxs-lookup"><span data-stu-id="3fcef-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="3fcef-107">Każda definicja parametru składa się z identyfikatora (nazwa parametru funkcji, na przykład "opłat") następuje definicję typu "(na przykład Collection(Decimal)").</span><span class="sxs-lookup"><span data-stu-id="3fcef-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="3fcef-108">Definicje typów może być:</span><span class="sxs-lookup"><span data-stu-id="3fcef-108">The type definitions can be either:</span></span>  
  
- <span data-ttu-id="3fcef-109">Typ identyfikatora (na przykład "Int32" lub "AdventureWorks.Order").</span><span class="sxs-lookup"><span data-stu-id="3fcef-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
- <span data-ttu-id="3fcef-110">Słowo kluczowe `COLLECTION` następuje inną definicję typu w nawiasach "(na przykład Collection(AdventureWorks.Order)").</span><span class="sxs-lookup"><span data-stu-id="3fcef-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
- <span data-ttu-id="3fcef-111">Słowo kluczowe wiersza, a następnie listę definicji właściwości w nawiasie (na przykład "Row(x AdventureWorks.Order)").</span><span class="sxs-lookup"><span data-stu-id="3fcef-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="3fcef-112">Definicje właściwości mają format, takie jak "`identifier type_definition`, `identifier type_definition`,...".</span><span class="sxs-lookup"><span data-stu-id="3fcef-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
- <span data-ttu-id="3fcef-113">Słowo kluczowe REF, a następnie typ identyfikatora w nawiasie "(na przykład Ref(AdventureWorks.Order)").</span><span class="sxs-lookup"><span data-stu-id="3fcef-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="3fcef-114">Operator definicji typu REF wymaga typ jednostki jako argument.</span><span class="sxs-lookup"><span data-stu-id="3fcef-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="3fcef-115">Typ pierwotny nie można określić jako argument.</span><span class="sxs-lookup"><span data-stu-id="3fcef-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="3fcef-116">Można także zagnieżdżać definicje typów (na przykład "kolekcji (Row(x Ref(AdventureWorks.Order)))").</span><span class="sxs-lookup"><span data-stu-id="3fcef-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="3fcef-117">Dostępne są opcje definicji typu:</span><span class="sxs-lookup"><span data-stu-id="3fcef-117">The type definition options are:</span></span>  
  
- <span data-ttu-id="3fcef-118">`IdentifierName supported_type`, lub</span><span class="sxs-lookup"><span data-stu-id="3fcef-118">`IdentifierName supported_type`, or</span></span>  
  
- <span data-ttu-id="3fcef-119">`IdentifierName` KOLEKCJA (`type_definition`), lub</span><span class="sxs-lookup"><span data-stu-id="3fcef-119">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
- <span data-ttu-id="3fcef-120">`IdentifierName` WIERSZ (`property_definition`), lub</span><span class="sxs-lookup"><span data-stu-id="3fcef-120">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
- <span data-ttu-id="3fcef-121">`IdentifierName` REF(`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="3fcef-121">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="3fcef-122">Opcja definicji właściwości jest `IdentifierName type_definition`.</span><span class="sxs-lookup"><span data-stu-id="3fcef-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="3fcef-123">Obsługiwane typy to żadnych typów w bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3fcef-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="3fcef-124">Obejmują one typy zarówno podstawowego, jak i jednostek.</span><span class="sxs-lookup"><span data-stu-id="3fcef-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="3fcef-125">Obsługiwane typy dotyczą tylko typy jednostek w bieżącym obszarze nazw jednostki.</span><span class="sxs-lookup"><span data-stu-id="3fcef-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="3fcef-126">Obejmują one typy pierwotne.</span><span class="sxs-lookup"><span data-stu-id="3fcef-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3fcef-127">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3fcef-127">Examples</span></span>  
 <span data-ttu-id="3fcef-128">Oto przykład definicją typu prostego.</span><span class="sxs-lookup"><span data-stu-id="3fcef-128">The following is an example of a simple type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="3fcef-129">Oto przykład definicja typu KOLEKCJI.</span><span class="sxs-lookup"><span data-stu-id="3fcef-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="3fcef-130">Oto przykład definicja typu wiersza.</span><span class="sxs-lookup"><span data-stu-id="3fcef-130">The following is an example of a ROW type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="3fcef-131">Oto przykład definicji typu REF.</span><span class="sxs-lookup"><span data-stu-id="3fcef-131">The following is an example of a REF type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="3fcef-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fcef-132">See also</span></span>

- [<span data-ttu-id="3fcef-133">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="3fcef-133">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="3fcef-134">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="3fcef-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
