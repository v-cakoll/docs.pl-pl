---
title: 'Instrukcje: Generowanie klas i dokumentów schematu XML przy użyciu narzędzia definicji schematu XML'
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 2bbdced0f984b653a58afba9685683e8c0891271
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389802"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a>Instrukcje: Generowanie klas i dokumentów schematu XML przy użyciu narzędzia definicji schematu XML
Narzędzie definicji schematu XML (Xsd.exe) służy do generowania schematu XML, która opisuje klasę lub do generowania klasy zdefiniowane przez schemat XML. Poniższe procedury pokazują, jak wykonywać te operacje.

Narzędzie XML Schema definition (Xsd.exe) zwykle można znaleźć w następującej ścieżce:\
_C:\\Pliki programów\\(x86)\\Zestaw\\Microsoft\\SDK Windows {version} bin\\NETFX {version} Narzędzia\\_

### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a>Do generowania klasy, które są zgodne z określonego schematu  
  
1. Otwórz wiersz polecenia.  
  
2. Przekaż schemat XML jako argument do narzędzia Definicja schematu XML, które tworzy zestaw klas, które są dokładnie dopasowane do schematu XML, na przykład:  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     To narzędzie może przetwarzać tylko schematy, które odwołują się do specyfikacji XML konsorcjum World Wide Web 16 marca 2001. Innymi słowy, obszar nazw schematu XMLhttp://www.w3.org/2001/XMLSchemamusi być " " jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. Modyfikuj klas, metod, właściwości lub pól, w razie potrzeby. Aby uzyskać więcej informacji na temat modyfikowania klasy z atrybutami, zobacz [Kontrolowanie serializacji XML przy użyciu atrybutów](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) i [atrybutów sterujących serializacją kodowanego protokołu SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
 Często jest to przydatne, należy zapoznać się ze schematem strumień XML, który jest generowany, gdy są serializacji wystąpień klasy (lub klasy). Na przykład można opublikować schemat dla innych do użycia lub można porównać go do schematu, z którym próbujesz osiągnąć zgodność.  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a>Do generowania dokumentu XML schematu z zestawu klas  
  
1. Kompiluj klasy lub klas do biblioteki DLL.  
  
2. Otwórz wiersz polecenia.  
  
3. Przekaż bibliotekę DLL jako argument do pliku Xsd.exe, na przykład:  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     Schemat (lub schematy) zostanie zapisany, rozpoczynając od nazwy "schema0.xsd".  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Data.DataSet>
- [Narzędzie definicji schematu XML i serializacja XML](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)
- [Wprowadzenie do serializacji XML](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [Narzędzie XML Do definicji schematu (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Instrukcje: Serializacja obiektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [Instrukcje: Deserializacja obiektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
