---
title: 'Porady: Użyj narzędzie definicji schematu XML można wygenerować klas i dokumentów schematu XML'
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 2edaf7ba540035fbf2f49ba78b41ab99f8889391
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44199313"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a>Porady: Użyj narzędzie definicji schematu XML można wygenerować klas i dokumentów schematu XML
Narzędzie definicji schematu XML (Xsd.exe) służy do generowania schematu XML, która opisuje klasę lub do generowania klasy zdefiniowane przez schemat XML. Poniższe procedury pokazują, jak wykonywać te operacje.  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a>Do generowania klasy, które są zgodne z określonego schematu  
  
1.  Otwórz wiersz polecenia.  
  
2.  Przekaż schematu XML jako argument do narzędzia definicji schematu XML, który tworzy zestaw klas dopasowane dokładnie do schematu XML, na przykład:  
  
    ```  
    xsd mySchema.xsd  
    ```  
  
     To narzędzie może przetwarzać tylko schematy, które odwołują się do specyfikacji XML konsorcjum World Wide Web 16 marca 2001. Innymi słowy, przestrzeń nazw schematu XML musi być "http://www.w3.org/2001/XMLSchema" jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    ```  
  
3.  Modyfikuj klas, metod, właściwości lub pól, w razie potrzeby. Aby uzyskać więcej informacji o modyfikowaniu klasę z atrybutów, zobacz [kontrolowanie atrybutów za pomocą serializacji XML](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) i [atrybuty czy kontroli kodowany protokołu SOAP serializacji](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
 Często jest to przydatne, należy zapoznać się ze schematem strumień XML, który jest generowany, gdy są serializacji wystąpień klasy (lub klasy). Na przykład może opublikować swojego schematu dla innych użytkowników lub może być porównywany ze schematem, z którą próbujesz osiągnąć zgodności.  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a>Do generowania dokumentu XML schematu z zestawu klas  
  
1.  Kompiluj klasy lub klas do biblioteki DLL.  
  
2.  Otwórz wiersz polecenia.  
  
3.  Przekazywania pliku DLL jako argument do Xsd.exe, na przykład:  
  
    ```  
    xsd MyFile.dll  
    ```  
  
     Schemat (lub schematy) zostanie zapisany, rozpoczynając od nazwy "schema0.xsd".  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataSet>  
- [Narzędzie definicji schematu XML i serializacja XML](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
- [Wprowadzenie do serializacji XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [Narzędzie definicji schematu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
- <xref:System.Xml.Serialization.XmlSerializer>  
- [Instrukcje: Serializacja obiektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [Instrukcje: Deserializacja obiektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
