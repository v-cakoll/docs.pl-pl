---
title: Wczytywanie deklaracji jednostek i odwołań do jednostek do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
ms.openlocfilehash: fa650e75d7661eeafea74146f5cbb61878978575
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710404"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>Wczytywanie deklaracji jednostek i odwołań do jednostek do modelu DOM
Jednostka jest deklaracją, która określa nazwę, która ma być używana w kodzie XML zamiast zawartości lub znaczników. Istnieją dwie części do jednostek. Najpierw należy powiązać nazwę z zastępowaniem zawartości za pomocą deklaracji jednostki. Deklaracja jednostki jest tworzona przy użyciu składni `<!ENTITY name "value">` w definicji typu dokumentu (DTD) lub schematu XML. Po drugie, Nazwa zdefiniowana w deklaracji jednostki jest następnie używana w kodzie XML. Gdy jest używana w kodzie XML, jest nazywana odwołaniem do jednostki. Na przykład następująca deklaracja jednostki deklaruje jednostkę nazwy, `publisher` jest skojarzona z zawartością "Microsoft Press".  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 W poniższym przykładzie pokazano sposób użycia tej deklaracji jednostki w kodzie XML jako odwołanie do jednostki.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Niektóre analizatory automatycznie rozszerzają jednostki, gdy dokument jest ładowany do pamięci. W związku z tym, gdy plik XML jest odczytywany do pamięci, deklaracje jednostek są zapamiętywane i zapisywane. Gdy analizator napotka następnie `&;` znaków, które identyfikują ogólne odwołanie do jednostki, Analizator wyszukuje tę nazwę w tabeli deklaracji jednostki. Odwołanie `&publisher;` jest zastępowane przez zawartość, którą reprezentuje. Przy użyciu następującego kodu XML  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 rozwijanie odwołania do jednostki i zastępowanie `&publisher;` przy użyciu zawartości Microsoft Press zapewnia następujący rozwinięty kod XML.  
  
 **Output**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Istnieje wiele rodzajów jednostek. Na poniższym diagramie przedstawiono podział typów jednostek i terminologii.  
  
 ![Wykres przepływu hierarchii typu jednostki](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")  
  
 Domyślnym implementacją Microsoft .NET Framework w Document Object Model XML (DOM) jest zachowywanie odwołań do jednostek i nie rozszerzanie jednostek podczas ładowania kodu XML. Implikacją tego jest to, że w przypadku załadowania dokumentu w modelu DOM zostanie utworzony węzeł **XmlEntityReference** zawierający zmienną referencyjną `&publisher;` z węzłami podrzędnymi reprezentującymi zawartość w jednostce zadeklarowanej w DTD.  
  
 Korzystając z deklaracji jednostki `<!ENTITY publisher "Microsoft Press">`, na poniższym diagramie przedstawiono węzły **XmlEntity** i **XmlText** utworzone na podstawie tej deklaracji.  
  
 ![węzły utworzone na podstawie deklaracji jednostki](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 Różnice w przypadku, gdy odwołania do jednostek są rozwinięte i gdy nie są one różnicą w jakie węzły są generowane w drzewie DOM, w pamięci. Różnica w węzłach, które zostały wygenerowane, została omówiona w [odwołaniach do jednostek](../../../../docs/standard/data/xml/entity-references-are-preserved.md) tematów, a [odwołania do jednostek są rozwinięte i nie są zachowywane](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
