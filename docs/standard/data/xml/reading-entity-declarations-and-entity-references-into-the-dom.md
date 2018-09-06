---
title: Wczytywanie deklaracji jednostek i odwołań do jednostek do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e30b52b8cdfb4d185687d58c80f4475730031c86
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44031756"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>Wczytywanie deklaracji jednostek i odwołań do jednostek do modelu DOM
Jednostka jest deklaracja, która stanowi nazwę do użycia w formacie XML, zamiast zawartości lub znaczników. Istnieją dwie części do jednostek. Najpierw należy powiązać nazwę, aby nowa zawartość przy użyciu deklaracji entity. Deklaracja jednostki jest tworzona przy użyciu `<!ENTITY name "value">` składni w definicji typu dokumentu (DTD) lub schematu XML. Po drugie z nazwą zdefiniowaną w deklaracji jednostki są następnie używane w pliku XML. W przypadku użycia w pliku XML, jest on nazywany odwołania do jednostki. Na przykład następująca deklaracja jednostki deklaruje jednostki o nazwie `publisher` skojarzona z zawartością "Microsoft Press".  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 Poniższy przykład pokazuje użycie tej deklaracji jednostki w formacie XML, jako odwołanie do jednostki.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Niektóre parsery rozwiń jednostek automatycznie, gdy dokument jest ładowany do pamięci. W związku z tym podczas odczytywania pliku XML do pamięci, deklaracje jednostki zostaną zapamiętane i zapisane. Gdy analizator składni napotka później `&;` znaków, które należy zidentyfikować ogólne odwołanie do jednostki, analizator odwołuje się do tej nazwy tabeli deklaracji entity. Odwołanie, `&publisher;` zastępuje zawartości, który reprezentuje. Za pomocą następujący kod XML  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 rozwijanie odwołania do jednostki i zastępując `&publisher;` Microsoft Press zawartości zapewnia następujący kod XML rozwinięty.  
  
 **Output**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Istnieje wiele rodzajów jednostek. Na poniższym diagramie przedstawiono podział typów jednostek i terminologia.  
  
 ![Schemat blokowy hierarchii typów jednostek](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")  
  
 Wartość domyślna dla implementacji Microsoft .NET Framework XML Document Object Model (DOM) jest zachowanie odwołania jednostki i Rozwijaj jednostki po załadowaniu pliku XML. Domniemanie tego jest to, że ponieważ dokument został załadowany w modelu DOM, **XmlEntityReference** węzła zawierającego zmienną odwołania `&publisher;` jest tworzone, z węzłami podrzędnymi reprezentujących zawartości jednostki zadeklarowanych w DTD.  
  
 Za pomocą `<!ENTITY publisher "Microsoft Press">` deklaracji jednostki na poniższym diagramie przedstawiono **XmlEntity** i **XmlText** węzłów przygotowane na podstawie tej deklaracji.  
  
 ![węzłów przygotowane na podstawie jednostki deklaracji](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 Różnice podczas odwołań do jednostek zostaną rozwinięte i nie są one sprawia, że różnica w jakie węzły są generowane w drzewie DOM w pamięci. Różnica w węzły, które są generowane zostało wyjaśnione w tematach [odwołań do jednostek są zachowywane](../../../../docs/standard/data/xml/entity-references-are-preserved.md) i [odwołań do jednostek są rozwinięte i nie jest zachowywana](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
