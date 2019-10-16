---
title: System typów (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: 0f7dae9e57132929737d752c67694cd369b79d9e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319238"
---
# <a name="type-system-entity-sql"></a>System typów (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje wiele typów:  
  
- Typy pierwotne (proste), takie jak `Int32` i `String.`  
  
- Typy nominalne, które są zdefiniowane w schemacie, takie jak <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType> i <xref:System.Data.Metadata.Edm.RelationshipType>.  
  
- Typy anonimowe, które nie są zdefiniowane w schemacie jawnie: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType> i <xref:System.Data.Metadata.Edm.RefType>.  
  
 W tej sekcji omówiono typy anonimowe, które nie są zdefiniowane w schemacie jawnie, ale są obsługiwane przez Entity SQL. Aby uzyskać informacje na temat typów pierwotnych i nominalnych, zobacz [koncepcyjne typy modeli (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).  
  
## <a name="rows"></a>Wierszy  
 Struktura wiersza zależy od sekwencji wpisanych i nazwanych elementów członkowskich, z których składa się wiersz. Typ wiersza nie ma tożsamości i nie można go dziedziczyć. Wystąpienia tego samego typu wiersza są równoważne, jeśli elementy członkowskie są odpowiednio równoważne. Wiersze nie mają zachowania wykraczające poza ich równoważność strukturalną i nie mają odpowiednika w środowisku uruchomieniowym języka wspólnego. Zapytania mogą prowadzić do struktur, które zawierają wiersze lub kolekcje wierszy. Powiązanie interfejsu API między zapytaniami [!INCLUDE[esql](../../../../../../includes/esql-md.md)] i językiem hosta definiują sposób zrealizowania wierszy w zapytaniu, które wygenerowało wynik. Aby uzyskać informacje na temat sposobu konstruowania wystąpienia wiersza, zobacz [konstruowanie typów](constructing-types-entity-sql.md).  
  
## <a name="collections"></a>Kolekcje  
 Typy kolekcji reprezentują zero lub więcej wystąpień innych obiektów. Aby uzyskać informacje na temat tworzenia kolekcji, zobacz [konstruowanie typów](constructing-types-entity-sql.md).  
  
## <a name="references"></a>Odwołania  
 Odwołanie jest logicznym wskaźnikiem do określonej jednostki w określonym zestawie jednostek.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje następujące operatory do konstruowania, dekonstrukcji i nawigowania po odwołaniach:  
  
- [REF](ref-entity-sql.md)  
  
- [CREATEREF](createref-entity-sql.md)  
  
- [KEY](key-entity-sql.md)  
  
- [DEREF](deref-entity-sql.md)  
  
 Możesz nawigować przez odwołanie za pomocą operatora dostęp do elementu członkowskiego (kropka) (`.`). Poniższy fragment kodu wyodrębnia Właściwość identyfikatora (Order), przechodząc przez właściwość r (Reference).  
  
```sql  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 Jeśli wartość odwołania jest równa null lub jeśli obiekt docelowy odwołania nie istnieje, wynik ma wartość null.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [CAST](cast-entity-sql.md)
- [Specyfikacje CSDL, SSDL i MSL](csdl-ssdl-and-msl-specifications.md)
