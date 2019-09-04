---
title: System typów (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: 7f9b41181d9a7a7f23123f2e1b71893000b34d4a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248938"
---
# <a name="type-system-entity-sql"></a>System typów (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje wiele typów:  
  
- Typy pierwotne (proste), `Int32` takie jak i`String.`  
  
- Typy nominalne, które są zdefiniowane w schemacie, <xref:System.Data.Metadata.Edm.EntityType>takie <xref:System.Data.Metadata.Edm.ComplexType>jak, <xref:System.Data.Metadata.Edm.RelationshipType>, i.  
  
- Typy anonimowe, które nie są zdefiniowane w schemacie <xref:System.Data.Metadata.Edm.CollectionType>jawnie <xref:System.Data.Metadata.Edm.RowType>:, <xref:System.Data.Metadata.Edm.RefType>, i.  
  
 W tej sekcji omówiono typy anonimowe, które nie są zdefiniowane w schemacie jawnie, ale są obsługiwane przez Entity SQL. Aby uzyskać informacje na temat typów pierwotnych i nominalnych, zobacz [koncepcyjne typy modeli (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).  
  
## <a name="rows"></a>Wierszy  
 Struktura wiersza zależy od sekwencji wpisanych i nazwanych elementów członkowskich, z których składa się wiersz. Typ wiersza nie ma tożsamości i nie można go dziedziczyć. Wystąpienia tego samego typu wiersza są równoważne, jeśli elementy członkowskie są odpowiednio równoważne. Wiersze nie mają zachowania wykraczające poza ich równoważność strukturalną i nie mają odpowiednika w środowisku uruchomieniowym języka wspólnego. Zapytania mogą prowadzić do struktur, które zawierają wiersze lub kolekcje wierszy. Powiązanie interfejsu API między [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytaniami i językiem hosta definiuje sposób zrealizowania wierszy w zapytaniu, które wygenerowało wynik. Aby uzyskać informacje na temat sposobu konstruowania wystąpienia wiersza, zobacz [konstruowanie typów](constructing-types-entity-sql.md).  
  
## <a name="collections"></a>Kolekcje  
 Typy kolekcji reprezentują zero lub więcej wystąpień innych obiektów. Aby uzyskać informacje na temat tworzenia kolekcji, zobacz [konstruowanie typów](constructing-types-entity-sql.md).  
  
## <a name="references"></a>Odwołania  
 Odwołanie jest logicznym wskaźnikiem do określonej jednostki w określonym zestawie jednostek.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Program obsługuje następujące operatory do konstruowania, dekonstrukcji i nawigowania po odwołaniach:  
  
- [REF](ref-entity-sql.md)  
  
- [CREATEREF](createref-entity-sql.md)  
  
- [KEY](key-entity-sql.md)  
  
- [DEREF](deref-entity-sql.md)  
  
 Możesz nawigować przez odwołanie za pomocą operatora`.`dostępu do elementu członkowskiego (). Poniższy fragment kodu wyodrębnia Właściwość identyfikatora (Order), przechodząc przez właściwość r (Reference).  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 Jeśli wartość odwołania jest równa null lub jeśli obiekt docelowy odwołania nie istnieje, wynik ma wartość null.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [CAST](cast-entity-sql.md)
- [Specyfikacje CSDL, SSDL i MSL](csdl-ssdl-and-msl-specifications.md)
