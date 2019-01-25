---
title: Przestrzenie nazw (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: eb4b956fa2ac9c0bb68c31d94e15b951807f8108
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724138"
---
# <a name="namespaces-entity-sql"></a>Przestrzenie nazw (jednostka SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] wprowadza przestrzenie nazw, aby uniknąć konfliktów nazw identyfikatorów globalnych, takich jak nazwy typów, zestawów encji, funkcje i tak dalej. Obsługa przestrzeni nazw w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest podobny do obsługi przestrzeni nazw w [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oferuje dwa rodzaje klauzuli USING: kwalifikowanych przestrzeni nazw (w miejscu podania krótszy alias dla przestrzeni nazw), a przestrzenie nazw niekwalifikowanych, jak pokazano w poniższym przykładzie:  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Zasad rozpoznawania nazw  
 Jeśli nie można rozpoznać identyfikatora w lokalnym zakresy [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje zlokalizować nazwy w zakresach globalnych (przestrzeni nazw). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] najpierw próbuje dopasować identyfikatora (prefiks) przy użyciu jednej z kwalifikowaną przestrzeni nazw. Jeśli istnieje dopasowanie, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje rozpoznać pozostałą część identyfikatora w określonej przestrzeni nazw. Jeśli nie zostanie znalezione dopasowanie, zwracany jest wyjątek.  
  
 Następnie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wyszukiwanie wszystkich niekwalifikowanej przestrzeni nazw (określony w prologu) dla identyfikatora. Jeśli identyfikator może znajdować się w dokładnie jedną przestrzeń nazw, zwracany jest tej lokalizacji. Jeśli więcej niż jednej przestrzeni nazw ma dopasowania dla tego identyfikatora, jest zgłaszany wyjątek. Jeśli można zidentyfikować żadnej przestrzeni nazw dla identyfikatora, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przekazuje nazwę na następny zakres na zewnątrz ( <xref:System.Data.Common.DbCommand> lub <xref:System.Data.Common.DbConnection> obiektu), jak pokazano w poniższym przykładzie:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>Różnice w stosunku do programu .NET Framework  
 W [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], można użyć częściowo kwalifikowane przestrzeni nazw. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie zezwala na to.  
  
## <a name="adonet-usage"></a>Użycie ADO.NET  
 Zapytania są wyrażone za pośrednictwem środowiska ADO.NET <xref:System.Data.Common.DbCommand> obiektów. <xref:System.Data.Common.DbCommand> obiekty mogą być wbudowane w <xref:System.Data.Common.DbConnection> obiektów. Przestrzenie nazw można również określić w ramach <xref:System.Data.Common.DbCommand> i <xref:System.Data.Common.DbConnection> obiektów. Jeśli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie można rozpoznać identyfikatora w ramach samo zapytanie zewnętrzne przestrzenie nazw są sondowany (na podstawie reguły podobne).  
  
## <a name="see-also"></a>Zobacz także
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
