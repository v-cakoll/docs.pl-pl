---
title: "System typów (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 333ae9a6b7d85298e02364f583903c2cd4b03d51
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="type-system-entity-sql"></a>System typów (jednostka SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje kilka typów:  
  
-   Typy pierwotne (proste), takich jak `Int32` i`String.`  
  
-   Nominalnego typy, które są zdefiniowane w schemacie, takich jak <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, i <xref:System.Data.Metadata.Edm.RelationshipType>.  
  
-   Typy anonimowe, które nie są zdefiniowane w schemacie na jawnie: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, i <xref:System.Data.Metadata.Edm.RefType>.  
  
 W tej sekcji omówiono typy anonimowe, które nie są w schemacie jawnie zdefiniowane, ale są obsługiwane przez [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Informacje o typach pierwotnych i nominalnego, zobacz [typu modelu koncepcyjnego (CSDL)](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4).  
  
## <a name="rows"></a>Wiersze  
 Struktura wiersza zależy sekwencja maszynowy i nazwanych elementów członkowskich, które wiersz składa się z. Typ wiersza ma nie tożsamość i nie może być dziedziczona z. Wystąpienia tego samego typu wiersza są równoważne, jeśli elementy członkowskie są odpowiednio równoważne. Wiersze nie zachowują się poza ich równoważność strukturalnych i nie mają odpowiednika w środowisko uruchomieniowe języka wspólnego. Struktury zawierające wierszy lub kolekcji wierszy może spowodować zapytania. Interfejs API powiązania między [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania i języka hosta definiuje sposób wierszy są realizowane w zapytaniu wytworzonego wynik. Aby uzyskać informacje na temat sposobu tworzenia wystąpienia wiersza, zobacz [konstruowania typy](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="collections"></a>Kolekcje  
 Typy kolekcji reprezentują zero lub więcej wystąpień innych obiektów. Aby uzyskać informacje o sposobie tworzenia kolekcji, zobacz [konstruowania typy](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
## <a name="references"></a>Odwołania  
 Odwołanie jest logiczną wskaźnika do określonej jednostki w zestawie określonej jednostki.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje następujące operatory utworzenia deconstruct i przejdź do odwołania:  
  
-   [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
-   [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
-   [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
-   [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 Odwołania można nawigować przy użyciu operatora dostępu (kropką) elementu członkowskiego (`.`). Poniższy fragment wyodrębnia właściwości identyfikatora (kolejność), przechodząc za pośrednictwem właściwości r (odwołanie).  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 Jeśli wartość odwołania ma wartość null, lub jeśli elementem docelowym odwołania nie istnieje, wynikiem jest null.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)  
 [Specyfikacje CSDL, SSDL i MSL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
