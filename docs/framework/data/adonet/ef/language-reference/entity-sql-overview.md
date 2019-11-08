---
title: Przegląd języka Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: e0f154ab2d9db1a1fdbaba8c72bc7e43ad71ee0b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738487"
---
# <a name="entity-sql-overview"></a>Przegląd języka Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] to język przypominający SQL, który umożliwia wykonywanie zapytań względem modeli koncepcyjnych w Entity Framework. Modele koncepcyjne reprezentują dane jako jednostki i relacje, a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwiają wykonywanie zapytań dotyczących tych jednostek i relacji w formacie, który jest znany dla osób, które używały języka SQL.  
      
 Entity Framework współpracuje z dostawcami danych specyficznymi dla magazynu w celu tłumaczenia ogólnych [!INCLUDE[esql](../../../../../../includes/esql-md.md)] na zapytania specyficzne dla magazynu. Dostawca EntityClient umożliwia wykonywanie polecenia [!INCLUDE[esql](../../../../../../includes/esql-md.md)] względem modelu jednostki i zwracanie bogatych typów danych, takich jak wyniki skalarne, zestawy wyników i wykresy obiektów. Podczas konstruowania obiektów <xref:System.Data.EntityClient.EntityCommand> można określić nazwę procedury składowanej lub tekst zapytania, przypisując [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ciąg zapytania do jego właściwości <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>. <xref:System.Data.EntityClient.EntityDataReader> prezentuje wyniki wykonywania <xref:System.Data.EntityClient.EntityCommand> dla modelu EDM. Aby wykonać polecenie, które zwraca <xref:System.Data.EntityClient.EntityDataReader>, wywołaj <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.  
  
 Oprócz dostawcy EntityClient Entity Framework umożliwia korzystanie z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do wykonywania zapytań względem modelu koncepcyjnego i zwracania danych jako obiektów CLR z silną typem, które są wystąpieniami typów jednostek. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../working-with-objects.md).  
  
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
  
 [Kolejność wykonywania działań](operator-precedence-entity-sql.md)  
  
 [Stronicowanie](paging-entity-sql.md)  
  
 [Semantyka porównania](comparison-semantics-entity-sql.md)  
  
 [Tworzenie zagnieżdżonych zapytań jednostki SQL](composing-nested-entity-sql-queries.md)  
  
 [Typy strukturalne dopuszczające wartości Null](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Jednostki języka SQL](entity-sql-language.md)
- [Specyfikacje CSDL, SSDL i MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
