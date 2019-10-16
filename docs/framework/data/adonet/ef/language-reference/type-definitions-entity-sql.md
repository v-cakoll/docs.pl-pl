---
title: Definicje typów (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 35f660a66fd706b37187056830af5e06ac586caa
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319249"
---
# <a name="type-definitions-entity-sql"></a>Definicje typów (Entity SQL)
Definicja typu jest używana w instrukcji deklaracji funkcji wbudowanej [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja deklaracji dla wbudowanej funkcji składa się ze słowa kluczowego [Function](function-entity-sql.md) , po którym następuje identyfikator reprezentujący nazwę funkcji (na przykład "myavg"), po której następuje lista definicji parametrów w nawiasie (na przykład "Kolekcja opłat ( Decimal) ").  
  
 Lista definicji parametrów składa się z zero lub więcej definicji parametrów. Każda definicja parametru składa się z identyfikatora (nazwa parametru do funkcji, na przykład "należności"), po której następuje definicja typu (na przykład "Kolekcja (liczba dziesiętna)").  
  
 Definicje typów mogą być następujące:  
  
- Typ identyfikatora (na przykład "Int32" lub "AdventureWorks. Order").  
  
- Słowo kluczowe `COLLECTION` następuje przez inną definicję typu w nawiasie (na przykład "Kolekcja (AdventureWorks. Order)").  
  
- WIERSZ słowa kluczowego, po którym następuje lista definicji właściwości w nawiasie (na przykład "wiersz (x AdventureWorks. Order)"). Definicje właściwości mają format, taki jak "`identifier type_definition`, `identifier type_definition`,...".  
  
- Słowo kluczowe REF, po którym następuje Typ identyfikatora w nawiasie (na przykład "ref (AdventureWorks. Order)"). Operator definicji typu REF wymaga jako argumentu typu jednostki. Nie można określić typu pierwotnego jako argumentu.  
  
 Można również zagnieżdżać definicje typów (na przykład "Kolekcja (wiersz (x ref (AdventureWorks. Order))").  
  
 Opcje definicji typu są następujące:  
  
- `IdentifierName supported_type` lub  
  
- Kolekcja `IdentifierName` (`type_definition`) lub  
  
- `IdentifierName` wiersz (`property_definition`) lub  
  
- `IdentifierName` REF (`supported_entity_type`)  
  
 Opcja definicji właściwości jest `IdentifierName type_definition`.  
  
 Obsługiwane typy to wszystkie typy w bieżącej przestrzeni nazw. Obejmują one zarówno pierwotne, jak i typy jednostek.  
  
 Obsługiwane typy jednostek odwołują się tylko do typów jednostek w bieżącej przestrzeni nazw. Nie obejmują one typów pierwotnych.  
  
## <a name="examples"></a>Przykłady  
 Poniżej znajduje się przykład definicji typu prostego.  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 Poniżej znajduje się przykład definicji typu kolekcji.  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 Poniżej znajduje się przykład definicji typu wiersza.  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 Poniżej znajduje się przykład definicji typu odwołania.  
  
```sql  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
