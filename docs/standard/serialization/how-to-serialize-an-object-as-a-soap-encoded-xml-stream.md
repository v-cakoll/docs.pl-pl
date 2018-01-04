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
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="af4b1-102">Porady: szeregowania obiektu jako strumień SOAP zakodowane w formacie XML</span><span class="sxs-lookup"><span data-stu-id="af4b1-102">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="af4b1-103">Ponieważ wiadomości SOAP jest utworzony przy użyciu pliku XML <xref:System.Xml.Serialization.XmlSerializer> klasa może być używana do serializacji klasy oraz do generowania zakodowanego protokołu SOAP wiadomości.</span><span class="sxs-lookup"><span data-stu-id="af4b1-103">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="af4b1-104">Wynikowy kod XML odpowiada [sekcji 5 dokumentu sieci World Wide Web konsorcjum "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span><span class="sxs-lookup"><span data-stu-id="af4b1-104">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="af4b1-105">Podczas tworzenia usługi XML sieci Web, który komunikuje się za pośrednictwem protokołu SOAP wiadomości, można dostosować w strumieniu XML stosując zestaw atrybutów SOAP specjalne do klas i członków klasy.</span><span class="sxs-lookup"><span data-stu-id="af4b1-105">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="af4b1-106">Aby uzyskać listę atrybutów, zobacz [atrybuty że formant zakodowane SOAP serializacji](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="af4b1-106">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="af4b1-107">Do serializacji obiektu jako strumień XML kodowany w formacie protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="af4b1-107">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1.  <span data-ttu-id="af4b1-108">Tworzenie przy użyciu klasy [narzędzie definicji schematu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="af4b1-108">Create the class using the [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2.  <span data-ttu-id="af4b1-109">Stosowanie jednej lub więcej atrybutów specjalne w `System.Xml.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="af4b1-109">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="af4b1-110">Zapoznaj się z listą w "Serializacji protokołu SOAP zakodowane tego formantu atrybuty".</span><span class="sxs-lookup"><span data-stu-id="af4b1-110">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3.  <span data-ttu-id="af4b1-111">Utwórz `XmlTypeMapping` przez utworzenie nowego `SoapReflectionImporter`i wywoływanie `ImportTypeMapping` metody z typem klasy serializacji.</span><span class="sxs-lookup"><span data-stu-id="af4b1-111">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="af4b1-112">Poniższy kod przykładowy wywołania `ImportTypeMapping` metody `SoapReflectionImporter` klasy w celu utworzenia `XmlTypeMapping`.</span><span class="sxs-lookup"><span data-stu-id="af4b1-112">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
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
  
4.  <span data-ttu-id="af4b1-113">Utworzenie wystąpienia `XmlSerializer` klasy przez przekazanie `XmlTypeMapping` do <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="af4b1-113">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  <span data-ttu-id="af4b1-114">Wywołanie `Serialize` lub `Deserialize` metody.</span><span class="sxs-lookup"><span data-stu-id="af4b1-114">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af4b1-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="af4b1-115">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="af4b1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af4b1-116">See Also</span></span>  
 [<span data-ttu-id="af4b1-117">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="af4b1-117">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [<span data-ttu-id="af4b1-118">Atrybuty kontrolujące zakodowaną serializację SOAP</span><span class="sxs-lookup"><span data-stu-id="af4b1-118">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 [<span data-ttu-id="af4b1-119">Serializacja XML z usługami internetowymi XML</span><span class="sxs-lookup"><span data-stu-id="af4b1-119">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 [<span data-ttu-id="af4b1-120">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="af4b1-120">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="af4b1-121">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="af4b1-121">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="af4b1-122">Instrukcje: Przesłanianie zakodowanej serializacji XML protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="af4b1-122">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)
