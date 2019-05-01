---
title: System typów (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: 0afeffd3ad180d6cc6175010140754e279988b38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034115"
---
# <a name="type-system-entity-sql"></a>System typów (jednostka SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje wiele typów:  
  
- Typy pierwotne (proste), takich jak `Int32` i `String.`  
  
- Nominalna typy, które są zdefiniowane w schemacie, takie jak <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, i <xref:System.Data.Metadata.Edm.RelationshipType>.  
  
- Typy anonimowe, które nie są zdefiniowane w schemacie na jawnie: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, i <xref:System.Data.Metadata.Edm.RefType>.  
  
 W tej sekcji omówiono typy anonimowe, które nie są zdefiniowane w schemacie na jawnie, ale są obsługiwane przez jednostki SQL. Informacje o typach pierwotnych i nominalną, zobacz [koncepcyjny modelu typy (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).  
  
## <a name="rows"></a>Wiersze  
 Struktura wiersz zależy od sekwencji nazwane i wpisane elementów członkowskich, które składają się wiersz. Typ wiersza jest Brak tożsamości i nie może być dziedziczona z. Wystąpienia tego samego typu wiersza są równoważne, jeżeli elementy członkowskie są odpowiednio równoważne. Wiersze nie zachowanie poza ich równoważność strukturalnych i nie mają odpowiednika w środowisko uruchomieniowe języka wspólnego. Zapytania może spowodować struktur, które zawierają wiersze lub kolekcji wierszy. Interfejs API powiązania między [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania i języka hosta definiuje, jak wiersze są realizowane w zapytaniu, wytworzonego wynik. Aby uzyskać informacji na temat sposobu tworzenia wystąpienia wiersza, zobacz [konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="collections"></a>Kolekcje  
 Typy kolekcji reprezentują zero lub więcej wystąpień innych obiektów. Aby uzyskać informacje na temat sposobu tworzenia kolekcji, zobacz [konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="references"></a>Odwołania  
 Odwołanie jest logiczną wskaźnik do określonej jednostki w zestawie określonej jednostki.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje następujące operatory do konstruowania, dekonstruować i nawigowanie po odwołania:  
  
- [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
- [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
- [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 Możesz przejść przez odwołanie za pomocą operatora dostępu (kropka) elementu członkowskiego (`.`). Poniższy fragment kodu wyodrębnia Właściwość Id (zamówienia), przechodząc za pomocą właściwości r (odwołania).  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 Jeśli ma wartość odniesienia null, lub jeśli celem odwołania nie istnieje, wynikiem jest wartość null.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)
- [Specyfikacje CSDL, SSDL i MSL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
