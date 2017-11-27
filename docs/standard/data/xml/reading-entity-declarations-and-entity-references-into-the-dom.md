---
title: "Odczytywanie deklaracje jednostki i odwołań do jednostek w modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6370db06cbe7ff8d46258b0315059f5c37587fea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>Odczytywanie deklaracje jednostki i odwołań do jednostek w modelu DOM
Jednostka jest deklaracją informującą Nazwa do użycia w kodzie XML zamiast zawartości lub znaczników. Istnieją dwie części jednostek. Najpierw należy powiązanie nazwę, aby nowa zawartość za pomocą deklaracji entity. Deklaracja jednostki jest tworzona przy użyciu `<!ENTITY name "value">` składni w definicji typu dokumentu (DTD) lub schematu XML. Po drugie z nazwą zdefiniowaną w deklaracji jednostki są następnie używane w kodzie XML. Używane w pliku XML, jest nazywany odwołania do jednostki. Na przykład następujące oświadczenie jednostka deklaruje jednostki nazwy `publisher` skojarzona z zawartością "Microsoft Press".  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 Poniższy przykład przedstawia użycie tej deklaracji jednostki w formacie XML jako odwołanie do jednostki.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Niektóre analizatory składni rozwinąć jednostek automatycznie, gdy dokument jest ładowany do pamięci. W związku z tym podczas odczytywania pliku XML do pamięci, deklaracje jednostki są zapamiętywane i zapisywane. Gdy analizator następnie napotka `&;` znaków, które identyfikują ogólne odwołanie do jednostki, Analizator wyszukuje tę nazwę tabeli deklaracji entity. Odwołanie, `&publisher;` zastępuje zawartość, która reprezentuje. Przy użyciu następującego pliku XML  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Rozszerzanie odwołanie do jednostki i zastępowanie `&publisher;` z Microsoft Press zawartości zapewnia następujące rozwinięte XML.  
  
 **Dane wyjściowe**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Istnieje wiele typów jednostek. Poniższy diagram przedstawia podział typów jednostek i terminologię.  
  
 ![Schemat blokowy hierarchii typów jednostek](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")  
  
 Wartość domyślna dla implementacji programu Microsoft .NET Framework z XML modelu DOM (Document Object) to zachowanie odwołań do jednostek i zwiększa jednostek po załadowaniu pliku XML. Wpływ na tego jest to, że zgodnie z dokumentem jest ładowany w modelu DOM, **XmlEntityReference** węzła odniesienia zmiennej zawierającego `&publisher;` jest utworzony, z węzłami podrzędnymi reprezentujący zawartości w jednostce zadeklarowany w definicji DTD.  
  
 Przy użyciu `<!ENTITY publisher "Microsoft Press">` deklaracji jednostki na poniższym diagramie przedstawiono **XmlEntity** i **XmlText** węzły utworzone na podstawie tej deklaracji.  
  
 ![węzły utworzone na podstawie deklaracji jednostki](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 Różnice po rozwinięciu są odwołań do jednostek i jeśli nie są one sprawia, że różnica w węzłach, które są generowane w drzewie DOM w pamięci. Różnica w węzłach, na których są generowane, znajduje się w tematach [odwołań do jednostek są zachowywane](../../../../docs/standard/data/xml/entity-references-are-preserved.md) i [odwołań do jednostek są rozwinięte i nie jest zachowywana](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
