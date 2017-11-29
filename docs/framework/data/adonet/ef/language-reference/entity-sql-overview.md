---
title: "Omówienie SQL jednostki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 301a934cad59b14d1a65a1e98247490d578e6866
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="entity-sql-overview"></a>Omówienie SQL jednostki
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]jest języka przypominającego SQL umożliwia zapytania modeli koncepcyjnych w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Modele koncepcyjne zawierają dane jako jednostki i relacje, i [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwia kwerendy te jednostki i relacje w formacie, który jest znana do tych, którzy użyli SQL.  
  
 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] Współpracuje z dostawców magazynu danych do tłumaczenia ogólnego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do specyficznych dla magazynu zapytań. Dostawca EntityClient udostępnia sposób wykonywania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] polecenia w odniesieniu do modelu jednostki i zwracanych zaawansowanych typów danych w tym skalarne wyników, zestawów wyników i wykresów obiektów. Podczas konstruowania <xref:System.Data.EntityClient.EntityCommand> obiekty, można określić nazwę procedury składowanej lub tekst zapytania, przypisując [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ciągu do zapytania jego <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> właściwości. <xref:System.Data.EntityClient.EntityDataReader> Przedstawia wyniki wykonania <xref:System.Data.EntityClient.EntityCommand> przed EDM. Do wykonania polecenia, która zwraca <xref:System.Data.EntityClient.EntityDataReader>, wywołaj <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.  
  
 Oprócz dostawcy EntityClient [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] pozwala na użycie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wykonywanie zapytań względem modelu koncepcyjnego i zwraca dane jako silnie typizowanych obiektów CLR, które wystąpień typów jednostek. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Ta sekcja zawiera informacje o pojęciach dotyczących [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Jak jednostki SQL różni się od języka Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
  
 [Szybkie odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-quick-reference.md)  
  
 [System typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)  
  
 [Definicje typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)  
  
 [Konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
  
 [Buforowanie Plan zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-plan-caching-entity-sql.md)  
  
 [Przestrzenie nazw](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
  
 [Identyfikatory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 [Parametry](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
  
 [Zmienne](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)  
  
 [Nieobsługiwane wyrażenia](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)  
  
 [Literały](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)  
  
 [Literały null i wnioskowanie o typie](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)  
  
 [Zestaw znaków](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)  
  
 [Wyrażenia zapytań](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
  
 [Funkcje](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)  
  
 [Kolejność wykonywania działań](../../../../../../docs/framework/data/adonet/ef/language-reference/operator-precedence-entity-sql.md)  
  
 [Stronicowania](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
  
 [Semantykę porównania](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-semantics-entity-sql.md)  
  
 [Tworzenie zapytań SQL zagnieżdżonych jednostki](../../../../../../docs/framework/data/adonet/ef/language-reference/composing-nested-entity-sql-queries.md)  
  
 [Typy dopuszczające wartości zerowe strukturalnych](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Jednostki języka SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [CSDL, SSDL, MSL specyfikacji i](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
