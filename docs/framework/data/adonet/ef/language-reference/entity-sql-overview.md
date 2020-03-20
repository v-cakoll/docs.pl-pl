---
title: Przegląd języka Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 880b81f2b6d4c4b893d28c919490f88dfb2a42e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150379"
---
# <a name="entity-sql-overview"></a>Przegląd języka Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]jest językiem sql-like, który umożliwia wykonywanie zapytań o modele koncepcyjne w ramach encji. Modele koncepcyjne reprezentują dane jako jednostki i relacje i [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwia wykonywanie zapytań o te jednostki i relacje w formacie znanym osobom, które korzystały z języka SQL.  

 Entity Framework współpracuje z dostawcami danych [!INCLUDE[esql](../../../../../../includes/esql-md.md)] specyficznych dla magazynu, aby przetłumaczyć ogólne na zapytania specyficzne dla magazynu. Dostawca EntityClient dostarcza sposób wykonania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] polecenia względem modelu jednostki i zwraca bogate typy danych, w tym wyniki skalarne, zestawy wyników i wykresy obiektów. Podczas konstruowania <xref:System.Data.EntityClient.EntityCommand> obiektów można określić nazwę procedury składowanej lub [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tekst kwerendy, przypisując ciąg zapytania do jego <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> właściwości. Ujawnia <xref:System.Data.EntityClient.EntityDataReader> wyniki wykonywania <xref:System.Data.EntityClient.EntityCommand> przeciwko EDM. Aby wykonać polecenie, <xref:System.Data.EntityClient.EntityDataReader>które <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>zwraca polecenie , call .  
  
 Oprócz dostawcy EntityClient entity Framework umożliwia wykonywanie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytań względem modelu koncepcyjnego i zwracanie danych jako silnie typizowane obiekty CLR, które są wystąpieniami typów jednostek. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../working-with-objects.md).  
  
 Ta sekcja zawiera informacje [!INCLUDE[esql](../../../../../../includes/esql-md.md)]koncepcyjne na temat .  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Czym język Entity SQL różni się od języka Transact-SQL](how-entity-sql-differs-from-transact-sql.md)  
  
 [Szybkie odwołanie do języka Entity SQL](entity-sql-quick-reference.md)  
  
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
  
 [Kolejność wykonywania działań](operator-precedence-entity-sql.md)  
  
 [Stronicowanie](paging-entity-sql.md)  
  
 [Semantyka porównania](comparison-semantics-entity-sql.md)  
  
 [Tworzenie zagnieżdżonych zapytań w języku Entity SQL](composing-nested-entity-sql-queries.md)  
  
 [Typy strukturalne dopuszczające wartości Null](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Jednostki języka SQL](entity-sql-language.md)
- [Specyfikacje CSDL, SSDL i MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
