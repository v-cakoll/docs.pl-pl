---
title: 'Instrukcje: serializowanie obiektu jako strumienia XML kodowanego w formacie protokołu SOAP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: bfbdda0861a6f2867a2e7003dd7054129fd343b8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334526"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="2023f-102">Instrukcje: serializowanie obiektu jako strumienia XML kodowanego w formacie protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="2023f-102">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="2023f-103">Ponieważ komunikatu protokołu SOAP jest skompilowane za pomocą języka XML, <xref:System.Xml.Serialization.XmlSerializer> klasy może służyć do serializacji klas i generowania zakodowany komunikaty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="2023f-103">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="2023f-104">Wynikowy kod XML jest zgodny z [sekcji 5 dokumentu World Wide Web Consortium "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span><span class="sxs-lookup"><span data-stu-id="2023f-104">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="2023f-105">Podczas tworzenia usługi XML sieci Web, która komunikuje się za pośrednictwem protokołu SOAP wiadomości stosując zestaw specjalnych protokołu SOAP atrybutów do klasy i składowych klas można dostosować strumień XML.</span><span class="sxs-lookup"><span data-stu-id="2023f-105">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="2023f-106">Aby uzyskać listę atrybutów, zobacz [atrybuty czy kontroli kodowany protokołu SOAP serializacji](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="2023f-106">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="2023f-107">Do serializacji obiektu jako strumień XML kodowany w formacie protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="2023f-107">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1. <span data-ttu-id="2023f-108">Tworzenie przy użyciu klasy [narzędzie definicji schematu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2023f-108">Create the class using the [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2. <span data-ttu-id="2023f-109">Zastosuj jeden lub więcej atrybutów specjalnych znaleziony w `System.Xml.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="2023f-109">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="2023f-110">Zapoznaj się z listą w "Serializacji protokołu SOAP zakodowane tego formantu atrybuty".</span><span class="sxs-lookup"><span data-stu-id="2023f-110">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3. <span data-ttu-id="2023f-111">Utwórz `XmlTypeMapping` przez utworzenie nowego `SoapReflectionImporter`i wywoływanie `ImportTypeMapping` metody z typem klasy serializacji.</span><span class="sxs-lookup"><span data-stu-id="2023f-111">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="2023f-112">Poniższy kod wywoła przykład `ImportTypeMapping` metody `SoapReflectionImporter` klasy w celu utworzenia `XmlTypeMapping`.</span><span class="sxs-lookup"><span data-stu-id="2023f-112">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
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
  
4. <span data-ttu-id="2023f-113">Utworzenie wystąpienia `XmlSerializer` klasy przez przekazanie `XmlTypeMapping` do <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2023f-113">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. <span data-ttu-id="2023f-114">Wywołanie `Serialize` lub `Deserialize` metody.</span><span class="sxs-lookup"><span data-stu-id="2023f-114">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2023f-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="2023f-115">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2023f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2023f-116">See also</span></span>

- [<span data-ttu-id="2023f-117">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="2023f-117">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- [<span data-ttu-id="2023f-118">Atrybuty kontrolujące zakodowaną serializację SOAP</span><span class="sxs-lookup"><span data-stu-id="2023f-118">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="2023f-119">Serializacja XML z usługami internetowymi XML</span><span class="sxs-lookup"><span data-stu-id="2023f-119">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)
- [<span data-ttu-id="2023f-120">Instrukcje: serializowanie obiektu</span><span class="sxs-lookup"><span data-stu-id="2023f-120">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="2023f-121">Instrukcje: deserializowanie obiektu</span><span class="sxs-lookup"><span data-stu-id="2023f-121">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="2023f-122">Instrukcje: zastępowanie zakodowanej serializacji XML protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="2023f-122">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)
