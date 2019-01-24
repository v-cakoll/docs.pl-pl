---
title: 'Instrukcje: Serializacja obiektu jako Stream XML kodowany w formacie protokołu SOAP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: dc5c4a68c1fba303937ae126cd5b5d4f7f8107ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631389"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Instrukcje: Serializacja obiektu jako Stream XML kodowany w formacie protokołu SOAP
  
 Ponieważ komunikatu protokołu SOAP jest skompilowane za pomocą języka XML, <xref:System.Xml.Serialization.XmlSerializer> klasy może służyć do serializacji klas i generowania zakodowany komunikaty protokołu SOAP. Wynikowy kod XML jest zgodny z [sekcji 5 dokumentu World Wide Web Consortium "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512). Podczas tworzenia usługi XML sieci Web, która komunikuje się za pośrednictwem protokołu SOAP wiadomości stosując zestaw specjalnych protokołu SOAP atrybutów do klasy i składowych klas można dostosować strumień XML. Aby uzyskać listę atrybutów, zobacz [atrybuty czy kontroli kodowany protokołu SOAP serializacji](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Do serializacji obiektu jako strumień XML kodowany w formacie protokołu SOAP  
  
1.  Tworzenie przy użyciu klasy [narzędzie definicji schematu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).  
  
2.  Zastosuj jeden lub więcej atrybutów specjalnych znaleziony w `System.Xml.Serialization`. Zapoznaj się z listą w "Serializacji protokołu SOAP zakodowane tego formantu atrybuty".  
  
3.  Utwórz `XmlTypeMapping` przez utworzenie nowego `SoapReflectionImporter`i wywoływanie `ImportTypeMapping` metody z typem klasy serializacji.  
  
     Poniższy kod wywoła przykład `ImportTypeMapping` metody `SoapReflectionImporter` klasy w celu utworzenia `XmlTypeMapping`.  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping =
        New SoapReflectionImporter().ImportTypeMapping(GetType(Group))  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping =
        new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
    ```  
  
4.  Utworzenie wystąpienia `XmlSerializer` klasy przez przekazanie `XmlTypeMapping` do <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> konstruktora.  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  Wywołanie `Serialize` lub `Deserialize` metody.  
  
## <a name="example"></a>Przykład  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping =
    New SoapReflectionImporter().ImportTypeMapping(GetType(Group))
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping =
    new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## <a name="see-also"></a>Zobacz także

- [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- [Atrybuty kontrolujące zakodowaną serializację SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)
- [Serializacja XML z usługami internetowymi XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)
- [Instrukcje: Serializacja obiektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [Instrukcje: Deserializacji obiektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [Instrukcje: Zastąp zakodowanego protokołu SOAP serializacji XML](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)
