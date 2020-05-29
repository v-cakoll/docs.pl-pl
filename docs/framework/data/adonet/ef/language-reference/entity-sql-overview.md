---
title: Przegląd języka Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: b4fe852847d8b1b4bc0b80e3ba8e1f5b4aae9ff7
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202251"
---
# <a name="entity-sql-overview"></a>Przegląd języka Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]to język przypominający SQL, który umożliwia wykonywanie zapytań względem modeli koncepcyjnych w Entity Framework. Modele koncepcyjne reprezentują dane jako jednostki i relacje, a także umożliwiają [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wykonywanie zapytań o te jednostki i relacje w formacie, który jest znany dla osób, które używały języka SQL.  

 Entity Framework współpracuje z dostawcami danych specyficznymi dla magazynu w celu tłumaczenia ogólnego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] na zapytania specyficzne dla magazynu. Dostawca EntityClient umożliwia wykonywanie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] polecenia względem modelu jednostki i zwracanie bogatych typów danych, takich jak wyniki skalarne, zestawy wyników i wykresy obiektów. Podczas konstruowania <xref:System.Data.EntityClient.EntityCommand> obiektów można określić nazwę procedury składowanej lub tekst zapytania, przypisując [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ciąg zapytania do jego <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> właściwości. <xref:System.Data.EntityClient.EntityDataReader>Prezentuje wyniki wykonywania <xref:System.Data.EntityClient.EntityCommand> względem modelu EDM. Aby wykonać polecenie, które zwraca <xref:System.Data.EntityClient.EntityDataReader> wywołanie <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A> .  
  
 Oprócz dostawcy EntityClient, Entity Framework umożliwia [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wykonywanie zapytań względem modelu koncepcyjnego i zwracanie danych jako obiektów CLR o jednoznacznie określonym typie, które są wystąpieniami typów jednostek. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../working-with-objects.md).  
  
 Ta sekcja zawiera informacje o pojęciach dotyczących [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Czym język Entity SQL różni się od języka Transact-SQL](how-entity-sql-differs-from-transact-sql.md)  
  
 [Szybkie odwołanie do języka Entity SQL](entity-sql-quick-reference.md)  
  
 [System typów](type-system-entity-sql.md)  
  
 [Definicje typu](type-definitions-entity-sql.md)  
  
 [Konstruowanie typów](constructing-types-entity-sql.md)  
  
 [Buforowanie planu zapytania](query-plan-caching-entity-sql.md)  
  
 [Namespaces](namespaces-entity-sql.md)  
  
 [Identyfikatory](identifiers-entity-sql.md)  
  
 [Parametry](parameters-entity-sql.md)  
  
 [Zmienne](variables-entity-sql.md)  
  
 [Nieobsługiwane wyrażenia](unsupported-expressions-entity-sql.md)  
  
 [Literały](literals-entity-sql.md)  
  
 [Literały null i wnioskowanie o typie](null-literals-and-type-inference-entity-sql.md)  
  
 [Wejściowy zestaw znaków](input-character-set-entity-sql.md)  
  
 [Wyrażenia zapytania](query-expressions-entity-sql.md)  
  
 [Funkcje](functions-entity-sql.md)  
  
 [Pierwszeństwo operatorów](operator-precedence-entity-sql.md)  
  
 [Stronicowanie](paging-entity-sql.md)  
  
 [Semantyka porównania](comparison-semantics-entity-sql.md)  
  
 [Tworzenie zagnieżdżonych zapytań w języku Entity SQL](composing-nested-entity-sql-queries.md)  
  
 [Typy strukturalne dopuszczające wartości Null](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Jednostki języka SQL](entity-sql-language.md)
- [Specyfikacje CSDL, SSDL i MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
