---
title: Zasady wnioskowania typów węzłów schematu i struktury
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c2f28490203bcc4853bc6736ce7089f308bc275
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338712"
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a>Zasady wnioskowania typów węzłów schematu i struktury
W tym temacie opisano, jak procesu wnioskowania schematu tłumaczy typy węzłów w dokumencie XML do struktury języka (XSD) definicji schematu XML.  
  
## <a name="element-inference-rules"></a>Zasady wnioskowania — element  
 W tej sekcji opisano reguły wnioskowania dla deklaracji elementu. Istnieją osiem struktury deklaracji elementu, które zostanie wywnioskowany:  
  
1. Element typu prostego  
  
2. Pusty element  
  
3. Pusty element za pomocą atrybutów  
  
4. Element z atrybutami i zawartość, proste  
  
5. Element z sekwencji elementów podrzędnych  
  
6. Element z sekwencji elementów podrzędnych i atrybutów  
  
7. Element z sekwencji wybór elementów podrzędnych  
  
8. Element z sekwencji liczbę elementów podrzędnych i atrybutów  
  
> [!NOTE]
>  Wszystkie `complexType` deklaracje są wnioskowane jako typów anonimowych. Element jedyna globalna wywnioskować jest głównym elementem; wszystkie inne elementy są lokalne.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
### <a name="simple-typed-element"></a>Prosty Element Typizowane  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda i schematu XML wygenerowany. Element pogrubiony zawiera schemat wywnioskowane dla elementów typu prostego.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a>Pusty Element  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda i schematu XML wygenerowany. Element pogrubiony zawiera schemat wywnioskowane dla pustego elementu.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a>Pusty Element za pomocą atrybutów  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda i schematu XML wygenerowany. Elementy pogrubione Pokaż schemat wywnioskowane dla pustego elementu z atrybutami.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a>Element z atrybutami i zawartość, proste  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda i schematu XML wygenerowany. Elementy pogrubione Pokaż schemat wywnioskowane dla elementu z atrybutami i prostej zawartości.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a>Element z sekwencji elementów podrzędnych  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda i schematu XML wygenerowany. Elementy pogrubione Pokaż schemat wywnioskowane dla elementu sekwencji elementów podrzędnych.  
  
> [!NOTE]
>  Nawet wtedy, gdy element ma tylko jeden element podrzędny, nadal jest traktowany jako sekwencja.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a>Element z sekwencji elementów podrzędnych i atrybutów  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda i schematu XML wygenerowany. Elementy pogrubione Pokaż schemat wywnioskowane dla elementu sekwencji elementów podrzędnych i atrybutów.  
  
> [!NOTE]
>  Nawet wtedy, gdy element ma tylko jeden element podrzędny, nadal jest traktowany jako sekwencja.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a>Element z sekwencji i wybór elementów podrzędnych  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda i schematu XML wygenerowany. Elementy pogrubione Pokaż schemat wywnioskowane dla elementu z sekwencji i wybór elementów podrzędnych.  
  
> [!NOTE]
>  `maxOccurs` Atrybutu `xs:choice` element jest ustawiony na wartość `"unbounded"` w schemacie wykrywany.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a>Element o kolejności i wybór elementów podrzędnych i atrybutów  
 W poniższej tabeli przedstawiono dane wejściowe XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda i schematu XML wygenerowany. Elementy pogrubione Pokaż schemat wywnioskowane dla elementu z sekwencji i wybór elementów podrzędnych i atrybutów.  
  
> [!NOTE]
>  `maxOccurs` Atrybutu `xs:choice` element jest ustawiony na wartość `"unbounded"` w schemacie wykrywany.  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schemat|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a>Przetwarzanie atrybutu  
 Napotkaniu nowy atrybut w węźle, jest ona dodawana do wywnioskowane definicji węzła o `use="required"`. Przy następnym tego samego węzła znajduje się w wystąpieniu procesu wnioskowania porównuje atrybuty bieżącego wystąpienia z nich, które już wywnioskować. Jeśli brakuje niektórych z nich już wykrywany w wystąpieniu `use="optional"` jest dodawany do definicji atrybutów. Nowe atrybuty zostaną dodane do istniejącej deklaracji z `use="optional"`.  
  
### <a name="occurrence-constraints"></a>Ograniczeń występowania  
 Podczas procesu wnioskowania schematu `minOccurs` i `maxOccurs` atrybuty są generowane, wywnioskowane składników schematu, przy użyciu wartości `"0"` lub `"1"` i `"1"` lub `"unbounded"`. Wartości `"1"` i `"unbounded"` są używane tylko wtedy, gdy wartości `"0"` i `"1"` nie można sprawdzić poprawności dokumentu XML (na przykład, jeśli `MinOccurs="0"` niedokładnie opisuje element `minOccurs="1"` jest używany).  
  
### <a name="mixed-content"></a>Zawartość mieszana  
 Jeśli element zawiera zawartość mieszana (na przykład tekst oraz elementy), `mixed="true"` atrybutu jest generowany dla definicji wywnioskowanego typu złożonego.  
  
## <a name="other-node-type-inference-rules"></a>Inne reguły wnioskowania typu węzła  
 W poniższej tabeli opisano reguły wnioskowania dla przetwarzania instrukcji, komentarza, odwołania do jednostki, CDATA, typ dokumentu i węzły przestrzeni nazw.  
  
|Typ węzła|{1&gt;Translacja&lt;1}|  
|---------------|-----------------|  
|Instrukcja przetwarzania|Ignorowane.|  
|Komentarz|Ignorowane.|  
|Odwołanie do jednostki|<xref:System.Xml.Schema.XmlSchemaInference> Klasa nie obsługuje odwołań do jednostek. Jeśli dokument XML zawiera odwołania do jednostki, należy użyć czytnika, który rozwija jednostki. Na przykład, można przekazać <xref:System.Xml.XmlTextReader> z <xref:System.Xml.XmlTextReader.EntityHandling%2A> właściwością <xref:System.Xml.EntityHandling.ExpandEntities> jako parametr. Jeśli zostaną napotkane odwołań do jednostek i czytnik nie rozwija jednostek, wyjątek jest throw.|  
|CDATA|Wszelkie `<![CDATA[ … ]]` sekcji w dokumencie XML zostanie wywnioskowany, jako `xs:string`.|  
|Typ dokumentu|Ignorowane.|  
|Namespaces|Ignorowane.|  
  
 Aby uzyskać więcej informacji na temat procesu wnioskowania schematu, zobacz [wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Schema.XmlSchemaInference>
- [Model SOM (XML Schema Object Model)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [Wnioskowanie schematu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)
- [Wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)
- [Zasady wnioskowania typów prostych](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
