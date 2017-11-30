---
title: "Zasady wnioskowanie schematu węzła typy i struktury"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c28c0f21b03fe7db014f118251363230a6ffc591
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a>Zasady wnioskowanie schematu węzła typy i struktury
W tym temacie opisano, jak proces wnioskowania schematu tłumaczy typy węzłów w dokumencie XML do struktury języka (XSD) definicja schematu XML.  
  
## <a name="element-inference-rules"></a>Zasady wnioskowania — element  
 W tej sekcji opisano reguły wnioskowania dla deklaracji elementu. Brak struktur osiem deklaracji elementu, które będzie można wywnioskować:  
  
1.  Element typu prostego  
  
2.  Pusty element  
  
3.  Pusty element z atrybutami  
  
4.  Element z atrybutami i prostej zawartości  
  
5.  Element o sekwencję elementów podrzędnych  
  
6.  Element z sekwencją atrybutów i elementów podrzędnych  
  
7.  Element z sekwencją opcji elementów podrzędnych  
  
8.  Element z sekwencją opcji atrybutów i elementów podrzędnych  
  
> [!NOTE]
>  Wszystkie `complexType` deklaracje są wywnioskować jako typy anonimowe. Element tylko globalny wywnioskować jest elementem głównym; wszystkie inne elementy są lokalne.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów z dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
### <a name="simple-typed-element"></a>Element typu prostego  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> — metoda i schemat XML wygenerowany. Element pogrubiony zawiera schemat wywnioskowane dla elementu typu prostego.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów z dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a>Pusty Element  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> — metoda i schemat XML wygenerowany. Element pogrubiony zawiera schemat wywnioskowane dla pustego elementu.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów z dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a>Pusty Element z atrybutami  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> — metoda i schemat XML wygenerowany. Elementy pogrubione Pokaż schematu wywnioskowane dla pustego elementu z atrybutami.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów z dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a>Element z atrybutami i prostej zawartości  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> — metoda i schemat XML wygenerowany. Elementy pogrubione Pokaż schematu wywnioskowane dla elementu z atrybutami i prostej zawartości.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów z dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a>Element o sekwencję elementów podrzędnych  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> — metoda i schemat XML wygenerowany. Elementy pogrubione Pokaż schematu wywnioskowane dla elementu o sekwencję elementów podrzędnych.  
  
> [!NOTE]
>  Nawet wtedy, gdy element ma tylko jeden element podrzędny, nadal jest traktowany jako sekwencję.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów z dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a>Element z sekwencją atrybutów i elementów podrzędnych  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> — metoda i schemat XML wygenerowany. Elementy pogrubione Pokaż schematu wywnioskowane dla elementu z sekwencją atrybutów i elementów podrzędnych.  
  
> [!NOTE]
>  Nawet wtedy, gdy element ma tylko jeden element podrzędny, nadal jest traktowany jako sekwencję.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów z dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a>Element o sekwencję i wybór elementów podrzędnych  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> — metoda i schemat XML wygenerowany. Elementy pogrubione Pokaż schematu wywnioskowane dla elementu sekwencji i wybór elementów podrzędnych.  
  
> [!NOTE]
>  `maxOccurs` Atrybutu `xs:choice` element jest ustawiony na wartość `"unbounded"` wywnioskowany schemat.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów z dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a>Element o sekwencji i wybór elementów podrzędnych i atrybuty  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> — metoda i schemat XML wygenerowany. Elementy pogrubione Pokaż wywnioskowane dla elementu sekwencji i wybór elementów podrzędnych i atrybutów schematu.  
  
> [!NOTE]
>  `maxOccurs` Atrybutu `xs:choice` element jest ustawiony na wartość `"unbounded"` wywnioskowany schemat.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów z dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a>Przetwarzanie atrybutu  
 Napotkaniu nowy atrybut w węźle, jest ona dodawana do wykrywany definicję węzła o `use="required"`. Przy następnym tego samego węzła został znaleziony w wystąpieniu, proces wnioskowania porównuje atrybuty bieżącego wystąpienia z tymi już wywnioskować. Jeśli brakuje niektórych już wykrywany widocznych w wystąpieniu `use="optional"` jest dodane do definicji atrybutu. Nowe atrybuty są dodawane do istniejącej deklaracji z `use="optional"`.  
  
### <a name="occurrence-constraints"></a>Ograniczeń występowania  
 Podczas wnioskowania schematu `minOccurs` i `maxOccurs` atrybuty są generowane wnioskowany składników schematu, wartościami `"0"` lub `"1"` i `"1"` lub `"unbounded"`. Wartości `"1"` i `"unbounded"` są używane tylko wtedy, gdy wartości `"0"` i `"1"` nie można sprawdzić poprawności dokumentu XML (na przykład, jeśli `MinOccurs="0"` nie opisuje dokładnie element `minOccurs="1"` jest używany).  
  
### <a name="mixed-content"></a>Zawartość mieszaną  
 Jeśli element zawiera zawartość mieszana (na przykład tekst oraz elementy), `mixed="true"` atrybutu jest generowany dla definicji wnioskowany typ złożony.  
  
## <a name="other-node-type-inference-rules"></a>Inne zasady wnioskowania typu węzła  
 W poniższej tabeli opisano zasady wnioskowania przetwarzania instrukcji, komentarza, odwołania do jednostki, CDATA, typu dokumentu i przestrzeni nazw węzłów.  
  
|Typ węzła|Translacja|  
|---------------|-----------------|  
|Instrukcja przetwarzania|Ignorowane.|  
|Komentarz|Ignorowane.|  
|Odwołanie do jednostki|<xref:System.Xml.Schema.XmlSchemaInference> Klasa nie obsługuje odwołań do jednostek. Jeśli dokument XML zawiera odwołania do jednostki, należy użyć czytnika, który umożliwia rozwijanie jednostek. Na przykład można przekazać <xref:System.Xml.XmlTextReader> z <xref:System.Xml.XmlTextReader.EntityHandling%2A> ustawioną właściwość <xref:System.Xml.EntityHandling.ExpandEntities> jako parametr. Jeśli występują odwołania do jednostek i czytnik nie zwiększa jednostek, wyjątek jest throw.|  
|CDATA|Wszelkie `<![CDATA[ … ]]` sekcje w dokumencie XML będzie można wywnioskować jako `xs:string`.|  
|Typ dokumentu|Ignorowane.|  
|Namespaces|Ignorowane.|  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów z dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Schema.XmlSchemaInference>  
 [Model obiektu schematu XML (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [Wnioskowanie schematu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 [Wnioskowanie schematów z dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)  
 [Wnioskowanie typów prostych reguł](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
