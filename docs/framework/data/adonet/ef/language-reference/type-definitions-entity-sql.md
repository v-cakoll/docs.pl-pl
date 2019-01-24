---
title: Definicje typów (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 7ac27c3dd43cb83272bff991dbd713e8269ccbb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743533"
---
# <a name="type-definitions-entity-sql"></a>Definicje typów (jednostka SQL)
Definicja typu jest używana w instrukcji deklaracji elementu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcja w tekście.  
  
## <a name="remarks"></a>Uwagi  
 Instrukcji deklaracji dla wbudowanej funkcji składa się z [funkcja](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) następuje identyfikator reprezentujący nazwę funkcji (na przykład "MyAvg"), a następnie listę definicji parametrów w nawiasie (słowo kluczowe przykład "opłat Collection(Decimal)").  
  
 Lista definicji parametru składa się z zero lub więcej definicji parametru. Każda definicja parametru składa się z identyfikatora (nazwa parametru funkcji, na przykład "opłat") następuje definicję typu "(na przykład Collection(Decimal)").  
  
 Definicje typów może być:  
  
-   Typ identyfikatora (na przykład "Int32" lub "AdventureWorks.Order").  
  
-   Słowo kluczowe `COLLECTION` następuje inną definicję typu w nawiasach "(na przykład Collection(AdventureWorks.Order)").  
  
-   Słowo kluczowe wiersza, a następnie listę definicji właściwości w nawiasie (na przykład "Row(x AdventureWorks.Order)"). Definicje właściwości mają format, takie jak "`identifier type_definition`, `identifier type_definition`,...".  
  
-   Słowo kluczowe REF, a następnie typ identyfikatora w nawiasie "(na przykład Ref(AdventureWorks.Order)"). Operator definicji typu REF wymaga typ jednostki jako argument. Typ pierwotny nie można określić jako argument.  
  
 Można także zagnieżdżać definicje typów (na przykład "kolekcji (Row(x Ref(AdventureWorks.Order)))").  
  
 Dostępne są opcje definicji typu:  
  
-   `IdentifierName supported_type`, lub  
  
-   `IdentifierName` KOLEKCJA (`type_definition`), lub  
  
-   `IdentifierName` WIERSZ (`property_definition`), lub  
  
-   `IdentifierName` REF(`supported_entity_type`)  
  
 Opcja definicji właściwości jest `IdentifierName type_definition`.  
  
 Obsługiwane typy to żadnych typów w bieżącej przestrzeni nazw. Obejmują one typy zarówno podstawowego, jak i jednostek.  
  
 Obsługiwane typy dotyczą tylko typy jednostek w bieżącym obszarze nazw jednostki. Obejmują one typy pierwotne.  
  
## <a name="examples"></a>Przykłady  
 Oto przykład definicją typu prostego.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 Oto przykład definicja typu KOLEKCJI.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 Oto przykład definicja typu wiersza.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 Oto przykład definicji typu REF.  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a>Zobacz także
- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
