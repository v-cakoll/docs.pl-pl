---
title: 'Instrukcje: Serializacja obiektu jako kodowanego strumienia XML protokołu SOAP'
description: Dowiedz się, jak serializować obiekt jako strumień XML kodowany przy użyciu protokołu SOAP. Klasa XmlSerializer może służyć do serializacji klas i generowania zakodowanych komunikatów SOAP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: 1d38c4e334439ef41b4d4429e52cff04c6463573
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84291568"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Instrukcje: Serializacja obiektu jako kodowanego strumienia XML protokołu SOAP
  
 Ponieważ komunikat protokołu SOAP jest kompilowany przy użyciu kodu XML, <xref:System.Xml.Serialization.XmlSerializer> Klasa może służyć do serializacji klas i generowania zakodowanych komunikatów protokołu SOAP. Wyniki XML są zgodne z [sekcją 5 dokumentu organizacja World Wide Web Consortium "Simple Object Access Protocol (SOAP) 1,1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512). Podczas tworzenia usługi sieci Web XML, która komunikuje się za pomocą komunikatów protokołu SOAP, można dostosować strumień XML, stosując zestaw specjalnych atrybutów protokołu SOAP do klas i składowych klas. Aby zapoznać się z listą atrybutów, zobacz atrybuty kontrolujące [zakodowaną serializację protokołu SOAP](attributes-that-control-encoded-soap-serialization.md).  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Do serializacji obiektu jako strumień XML kodowany w formacie protokołu SOAP  
  
1. Utwórz klasę przy użyciu [Narzędzia definicji schematu XML (XSD. exe)](xml-schema-definition-tool-xsd-exe.md).  
  
2. Zastosuj jeden lub więcej atrybutów specjalnych znalezionych w `System.Xml.Serialization` . Zapoznaj się z listą w "Serializacji protokołu SOAP zakodowane tego formantu atrybuty".  
  
3. Utwórz `XmlTypeMapping` przez utworzenie nowego `SoapReflectionImporter`i wywoływanie `ImportTypeMapping` metody z typem klasy serializacji.  
  
     Poniższy przykład kodu wywołuje `ImportTypeMapping` metodę `SoapReflectionImporter` klasy w celu utworzenia `XmlTypeMapping` .  
  
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
  
4. Utworzenie wystąpienia `XmlSerializer` klasy przez przekazanie `XmlTypeMapping` do <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> konstruktora.  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. Wywołanie `Serialize` lub `Deserialize` metody.  
  
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

- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
- [Atrybuty kontrolujące zakodowaną serializację protokołu SOAP](attributes-that-control-encoded-soap-serialization.md)
- [Serializacji XML za pomocą usług sieci Web XML](xml-serialization-with-xml-web-services.md)
- [Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)
- [Instrukcje: Deserializacja obiektu](how-to-deserialize-an-object.md)
- [Instrukcje: Przesłanianie zakodowanej serializacji XML protokołu SOAP](how-to-override-encoded-soap-xml-serialization.md)
