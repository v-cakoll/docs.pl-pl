---
title: Typ systemu (entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: b8b721aff5b7886fdb897ecaa3dcc163ec94ae79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149834"
---
# <a name="type-system-entity-sql"></a>Typ systemu (entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje wiele typów:  
  
- Prymitywne (proste) `Int32` typy, takie jak i`String.`  
  
- Typy nominalne zdefiniowane w schemacie, takie jak <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>i <xref:System.Data.Metadata.Edm.RelationshipType>.  
  
- Typy anonimowe, które nie są <xref:System.Data.Metadata.Edm.CollectionType>zdefiniowane w schemacie jawnie: , <xref:System.Data.Metadata.Edm.RowType>, i <xref:System.Data.Metadata.Edm.RefType>.  
  
 W tej sekcji omówiono typy anonimowe, które nie są zdefiniowane w schemacie jawnie, ale są obsługiwane przez encji SQL. Aby uzyskać informacje na temat typów pierwotnych i nominalnych, zobacz [Typy modeli koncepcyjnych (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).  
  
## <a name="rows"></a>Rows (Wiersze)  
 Struktura wiersza zależy od sekwencji wpisanych i nazwanych elementów członkowskich, z których składa się wiersz. Typ wiersza nie ma tożsamości i nie można go dziedziczyć. Wystąpienia tego samego typu wiersza są równoważne, jeśli elementy członkowskie są odpowiednio równoważne. Wiersze nie mają zachowania poza ich równoważności strukturalnej i nie mają odpowiednika w czasie wykonywania języka wspólnego. Kwerendy mogą spowodować struktur, które zawierają wiersze lub kolekcje wierszy. Powiązanie interfejsu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] API między zapytaniami a językiem hosta definiuje sposób wykonywania wierszy w kwerendzie, która wywołała wynik. Aby uzyskać informacje na temat konstruowania wystąpienia wiersza, zobacz [Konstruowanie typów](constructing-types-entity-sql.md).  
  
## <a name="collections"></a>Kolekcje  
 Typy kolekcji reprezentują zero lub więcej wystąpień innych obiektów. Aby uzyskać informacje na temat konstruowania kolekcji, zobacz [Konstruowanie typów](constructing-types-entity-sql.md).  
  
## <a name="references"></a>Dokumentacja  
 Odwołanie jest logicznym wskaźnikiem do określonej jednostki w określonym zestawie jednostek.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje następujące operatory do konstruowania, dekonstrukcji i poruszania się po odwołaniach:  
  
- [Ref](ref-entity-sql.md)  
  
- [CREATEREF](createref-entity-sql.md)  
  
- [Klucz](key-entity-sql.md)  
  
- [DEREF](deref-entity-sql.md)  
  
 Można poruszać się po odwołaniu za pomocą operatora`.`dostępu elementu członkowskiego (kropka). Poniższy fragment kodu wyodrębnia Id właściwości (of Order) przez poruszanie się za pośrednictwem r (odwołanie) właściwości.  
  
```sql  
select o2.r.Id
from (select ref(o) as r from LOB.Orders as o) as o2
```  
  
 Jeśli wartość referencyjna jest null lub jeśli obiekt docelowy odwołania nie istnieje, wynik jest null.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie jednostki SQL](entity-sql-overview.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [CAST](cast-entity-sql.md)
- [Specyfikacje CSDL, SSDL i MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
