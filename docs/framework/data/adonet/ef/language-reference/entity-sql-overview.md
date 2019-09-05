---
title: Przegląd języka Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 4d7db9c6a7aaeef900132663a5b0aa7420afe668
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251070"
---
# <a name="entity-sql-overview"></a>Przegląd języka Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]to język przypominający SQL, który umożliwia tworzenie zapytań o modele koncepcyjne w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]programie. Modele koncepcyjne reprezentują dane jako jednostki i relacje, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a także umożliwiają wykonywanie zapytań o te jednostki i relacje w formacie, który jest znany dla osób, które używały języka SQL.  
  
 Współpracuje z dostawcami danych specyficznymi dla magazynu w celu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przetłumaczenia ogólnego na zapytania specyficzne dla magazynu. [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] Dostawca EntityClient umożliwia wykonywanie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] polecenia względem modelu jednostki i zwracanie bogatych typów danych, takich jak wyniki skalarne, zestawy wyników i wykresy obiektów. Podczas konstruowania <xref:System.Data.EntityClient.EntityCommand> obiektów można określić nazwę procedury składowanej lub tekst zapytania, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przypisując ciąg zapytania do jego <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> właściwości. <xref:System.Data.EntityClient.EntityDataReader> Prezentuje wyniki<xref:System.Data.EntityClient.EntityCommand> wykonywania względem modelu EDM. Aby wykonać polecenie <xref:System.Data.EntityClient.EntityDataReader>, które zwraca wywołanie <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.  
  
 Oprócz dostawcy [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] EntityClient umożliwia [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wykonywanie zapytań względem modelu koncepcyjnego i zwracanie danych jako obiektów CLR z silną typem, które są wystąpieniami typów jednostek. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../working-with-objects.md).  
  
 Ta sekcja zawiera informacje o pojęciach dotyczących [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Jak jednostka SQL różni się od języka Transact-SQL](how-entity-sql-differs-from-transact-sql.md)  
  
 [Szybkie odwołanie do jednostki SQL](entity-sql-quick-reference.md)  
  
 [System typów](type-system-entity-sql.md)  
  
 [Definicje typu](type-definitions-entity-sql.md)  
  
 [Konstruowanie typów](constructing-types-entity-sql.md)  
  
 [Buforowanie planu zapytania](query-plan-caching-entity-sql.md)  
  
 [Przestrzenie nazw](namespaces-entity-sql.md)  
  
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
  
 [Tworzenie zagnieżdżonych zapytań jednostki SQL](composing-nested-entity-sql-queries.md)  
  
 [Typy strukturalne dopuszczające wartości Null](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Jednostki języka SQL](entity-sql-language.md)
- [Specyfikacje CSDL, SSDL i MSL](csdl-ssdl-and-msl-specifications.md)
