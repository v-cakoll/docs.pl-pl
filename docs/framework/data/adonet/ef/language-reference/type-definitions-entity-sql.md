---
title: "Definicje typów (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 269d0b7942a949b899a445af0fc15502e0ae3f7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="92dcd-102">Definicje typów (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="92dcd-102">Type Definitions (Entity SQL)</span></span>
<span data-ttu-id="92dcd-103">Definicja typu jest używana w instrukcji deklaracji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wbudowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="92dcd-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92dcd-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92dcd-104">Remarks</span></span>  
 <span data-ttu-id="92dcd-105">Instrukcja deklaracji dla funkcji wbudowanej składa się z [funkcja](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) następuje identyfikator reprezentujący nazwę funkcji (na przykład "MyAvg"), a następnie listy definicji parametrów w nawiasy okrągłe (dla — słowo kluczowe przykład "opłat Collection(Decimal)").</span><span class="sxs-lookup"><span data-stu-id="92dcd-105">The declaration statement for an inline function consists of the [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="92dcd-106">Lista definicji parametru składa się z definicjami parametrów zero lub więcej.</span><span class="sxs-lookup"><span data-stu-id="92dcd-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="92dcd-107">Każda definicja parametru składa się z identyfikatorem (nazwa parametru funkcji, na przykład "należności") następuje definicji typu "(na przykład Collection(Decimal)").</span><span class="sxs-lookup"><span data-stu-id="92dcd-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="92dcd-108">Definicje typów mogą być:</span><span class="sxs-lookup"><span data-stu-id="92dcd-108">The type definitions can be either:</span></span>  
  
-   <span data-ttu-id="92dcd-109">Typ identyfikatora (na przykład "Int32" lub "AdventureWorks.Order").</span><span class="sxs-lookup"><span data-stu-id="92dcd-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
-   <span data-ttu-id="92dcd-110">Słowo kluczowe `COLLECTION` następuje innej definicji typu w nawiasach "(na przykład Collection(AdventureWorks.Order)").</span><span class="sxs-lookup"><span data-stu-id="92dcd-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
-   <span data-ttu-id="92dcd-111">Słowo kluczowe wiersza następuje lista definicji właściwości w nawiasy okrągłe (na przykład "Row(x AdventureWorks.Order)").</span><span class="sxs-lookup"><span data-stu-id="92dcd-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="92dcd-112">Definicje właściwości mają format, takie jak "`identifier type_definition`, `identifier type_definition`,...".</span><span class="sxs-lookup"><span data-stu-id="92dcd-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
-   <span data-ttu-id="92dcd-113">Słowo kluczowe REF oraz typ identyfikatora w nawiasy okrągłe "(na przykład Ref(AdventureWorks.Order)").</span><span class="sxs-lookup"><span data-stu-id="92dcd-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="92dcd-114">Operator definicji typu REF wymaga typu jednostki jako argument.</span><span class="sxs-lookup"><span data-stu-id="92dcd-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="92dcd-115">Nie można określić typu pierwotnego jako argument.</span><span class="sxs-lookup"><span data-stu-id="92dcd-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="92dcd-116">Można zagnieżdżać w definicji typu (na przykład "kolekcji (Row(x Ref(AdventureWorks.Order)))").</span><span class="sxs-lookup"><span data-stu-id="92dcd-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="92dcd-117">Dostępne są opcje definicji typu:</span><span class="sxs-lookup"><span data-stu-id="92dcd-117">The type definition options are:</span></span>  
  
-   <span data-ttu-id="92dcd-118">`IdentifierName supported_type`, lub</span><span class="sxs-lookup"><span data-stu-id="92dcd-118">`IdentifierName supported_type`, or</span></span>  
  
-   <span data-ttu-id="92dcd-119">`IdentifierName`KOLEKCJA (`type_definition`), lub</span><span class="sxs-lookup"><span data-stu-id="92dcd-119">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
-   <span data-ttu-id="92dcd-120">`IdentifierName`WIERSZ (`property_definition`), lub</span><span class="sxs-lookup"><span data-stu-id="92dcd-120">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
-   <span data-ttu-id="92dcd-121">`IdentifierName`REF (`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="92dcd-121">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="92dcd-122">Opcja definicji właściwości jest `IdentifierName type_definition`.</span><span class="sxs-lookup"><span data-stu-id="92dcd-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="92dcd-123">Obsługiwane typy to wszystkie typy w bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="92dcd-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="92dcd-124">Dotyczy to zarówno podstawowego, jak i jednostek, typy.</span><span class="sxs-lookup"><span data-stu-id="92dcd-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="92dcd-125">Obsługiwany obiekt, do którego będzie dotyczyć tylko typy jednostek w bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="92dcd-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="92dcd-126">Obejmują one typów pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="92dcd-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="92dcd-127">Przykłady</span><span class="sxs-lookup"><span data-stu-id="92dcd-127">Examples</span></span>  
 <span data-ttu-id="92dcd-128">Oto przykład definicją typu prostego.</span><span class="sxs-lookup"><span data-stu-id="92dcd-128">The following is an example of a simple type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="92dcd-129">Oto przykład definicji typu KOLEKCJI.</span><span class="sxs-lookup"><span data-stu-id="92dcd-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="92dcd-130">Oto przykład definicji typu wiersz.</span><span class="sxs-lookup"><span data-stu-id="92dcd-130">The following is an example of a ROW type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="92dcd-131">Oto przykład definicji typu REF.</span><span class="sxs-lookup"><span data-stu-id="92dcd-131">The following is an example of a REF type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="92dcd-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92dcd-132">See Also</span></span>  
 [<span data-ttu-id="92dcd-133">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="92dcd-133">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="92dcd-134">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="92dcd-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
