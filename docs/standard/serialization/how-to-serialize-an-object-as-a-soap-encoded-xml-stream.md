---
title: "Porady: szeregowania obiektu jako strumień SOAP zakodowane w formacie XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 863c79b36cd51b2e1e747169fd15a2358a1e6fee
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Porady: szeregowania obiektu jako strumień SOAP zakodowane w formacie XML
  
 Ponieważ wiadomości SOAP jest utworzony przy użyciu pliku XML <xref:System.Xml.Serialization.XmlSerializer> klasa może być używana do serializacji klasy oraz do generowania zakodowanego protokołu SOAP wiadomości. Wynikowy kod XML odpowiada [sekcji 5 dokumentu sieci World Wide Web konsorcjum "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512). Podczas tworzenia usługi XML sieci Web, który komunikuje się za pośrednictwem protokołu SOAP wiadomości, można dostosować w strumieniu XML stosując zestaw atrybutów SOAP specjalne do klas i członków klasy. Aby uzyskać listę atrybutów, zobacz [atrybuty że formant zakodowane SOAP serializacji](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Do serializacji obiektu jako strumień XML kodowany w formacie protokołu SOAP  
  
1.  Tworzenie przy użyciu klasy [narzędzie definicji schematu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).  
  
2.  Stosowanie jednej lub więcej atrybutów specjalne w `System.Xml.Serialization`. Zapoznaj się z listą w "Serializacji protokołu SOAP zakodowane tego formantu atrybuty".  
  
3.  Utwórz `XmlTypeMapping` przez utworzenie nowego `SoapReflectionImporter`i wywoływanie `ImportTypeMapping` metody z typem klasy serializacji.  
  
     Poniższy kod przykładowy wywołania `ImportTypeMapping` metody `SoapReflectionImporter` klasy w celu utworzenia `XmlTypeMapping`.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [Atrybuty kontrolujące zakodowaną serializację SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 [Serializacja XML z usługami internetowymi XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 [Instrukcje: Serializacja obiektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Instrukcje: Deserializacja obiektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [Instrukcje: Przesłanianie zakodowanej serializacji XML protokołu SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)
