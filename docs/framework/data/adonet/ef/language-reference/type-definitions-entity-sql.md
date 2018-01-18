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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3a1321ae85b1f4952334672e7333e80094ad2e31
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="type-definitions-entity-sql"></a>Definicje typów (jednostka SQL)
Definicja typu jest używana w instrukcji deklaracji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wbudowanej funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja deklaracji dla funkcji wbudowanej składa się z [funkcja](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) następuje identyfikator reprezentujący nazwę funkcji (na przykład "MyAvg"), a następnie listy definicji parametrów w nawiasy okrągłe (dla — słowo kluczowe przykład "opłat Collection(Decimal)").  
  
 Lista definicji parametru składa się z definicjami parametrów zero lub więcej. Każda definicja parametru składa się z identyfikatorem (nazwa parametru funkcji, na przykład "należności") następuje definicji typu "(na przykład Collection(Decimal)").  
  
 Definicje typów mogą być:  
  
-   Typ identyfikatora (na przykład "Int32" lub "AdventureWorks.Order").  
  
-   Słowo kluczowe `COLLECTION` następuje innej definicji typu w nawiasach "(na przykład Collection(AdventureWorks.Order)").  
  
-   Słowo kluczowe wiersza następuje lista definicji właściwości w nawiasy okrągłe (na przykład "Row(x AdventureWorks.Order)"). Definicje właściwości mają format, takie jak "`identifier type_definition`, `identifier type_definition`,...".  
  
-   Słowo kluczowe REF oraz typ identyfikatora w nawiasy okrągłe "(na przykład Ref(AdventureWorks.Order)"). Operator definicji typu REF wymaga typu jednostki jako argument. Nie można określić typu pierwotnego jako argument.  
  
 Można zagnieżdżać w definicji typu (na przykład "kolekcji (Row(x Ref(AdventureWorks.Order)))").  
  
 Dostępne są opcje definicji typu:  
  
-   `IdentifierName supported_type`, lub  
  
-   `IdentifierName`KOLEKCJA (`type_definition`), lub  
  
-   `IdentifierName`WIERSZ (`property_definition`), lub  
  
-   `IdentifierName` REF(`supported_entity_type`)  
  
 Opcja definicji właściwości jest `IdentifierName type_definition`.  
  
 Obsługiwane typy to wszystkie typy w bieżącej przestrzeni nazw. Dotyczy to zarówno podstawowego, jak i jednostek, typy.  
  
 Obsługiwany obiekt, do którego będzie dotyczyć tylko typy jednostek w bieżącej przestrzeni nazw. Obejmują one typów pierwotnych.  
  
## <a name="examples"></a>Przykłady  
 Oto przykład definicją typu prostego.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 Oto przykład definicji typu KOLEKCJI.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 Oto przykład definicji typu wiersz.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
