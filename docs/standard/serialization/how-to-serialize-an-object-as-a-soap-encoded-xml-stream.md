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
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291568"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="52d14-104">Instrukcje: Serializacja obiektu jako kodowanego strumienia XML protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="52d14-104">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="52d14-105">Ponieważ komunikat protokołu SOAP jest kompilowany przy użyciu kodu XML, <xref:System.Xml.Serialization.XmlSerializer> Klasa może służyć do serializacji klas i generowania zakodowanych komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="52d14-105">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="52d14-106">Wyniki XML są zgodne z [sekcją 5 dokumentu organizacja World Wide Web Consortium "Simple Object Access Protocol (SOAP) 1,1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span><span class="sxs-lookup"><span data-stu-id="52d14-106">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="52d14-107">Podczas tworzenia usługi sieci Web XML, która komunikuje się za pomocą komunikatów protokołu SOAP, można dostosować strumień XML, stosując zestaw specjalnych atrybutów protokołu SOAP do klas i składowych klas.</span><span class="sxs-lookup"><span data-stu-id="52d14-107">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="52d14-108">Aby zapoznać się z listą atrybutów, zobacz atrybuty kontrolujące [zakodowaną serializację protokołu SOAP](attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="52d14-108">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="52d14-109">Do serializacji obiektu jako strumień XML kodowany w formacie protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="52d14-109">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1. <span data-ttu-id="52d14-110">Utwórz klasę przy użyciu [Narzędzia definicji schematu XML (XSD. exe)](xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="52d14-110">Create the class using the [XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2. <span data-ttu-id="52d14-111">Zastosuj jeden lub więcej atrybutów specjalnych znalezionych w `System.Xml.Serialization` .</span><span class="sxs-lookup"><span data-stu-id="52d14-111">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="52d14-112">Zapoznaj się z listą w "Serializacji protokołu SOAP zakodowane tego formantu atrybuty".</span><span class="sxs-lookup"><span data-stu-id="52d14-112">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3. <span data-ttu-id="52d14-113">Utwórz `XmlTypeMapping` przez utworzenie nowego `SoapReflectionImporter`i wywoływanie `ImportTypeMapping` metody z typem klasy serializacji.</span><span class="sxs-lookup"><span data-stu-id="52d14-113">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="52d14-114">Poniższy przykład kodu wywołuje `ImportTypeMapping` metodę `SoapReflectionImporter` klasy w celu utworzenia `XmlTypeMapping` .</span><span class="sxs-lookup"><span data-stu-id="52d14-114">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
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
  
4. <span data-ttu-id="52d14-115">Utworzenie wystąpienia `XmlSerializer` klasy przez przekazanie `XmlTypeMapping` do <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="52d14-115">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. <span data-ttu-id="52d14-116">Wywołanie `Serialize` lub `Deserialize` metody.</span><span class="sxs-lookup"><span data-stu-id="52d14-116">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52d14-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="52d14-117">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="52d14-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52d14-118">See also</span></span>

- [<span data-ttu-id="52d14-119">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="52d14-119">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="52d14-120">Atrybuty kontrolujące zakodowaną serializację protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="52d14-120">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="52d14-121">Serializacji XML za pomocą usług sieci Web XML</span><span class="sxs-lookup"><span data-stu-id="52d14-121">XML Serialization with XML Web Services</span></span>](xml-serialization-with-xml-web-services.md)
- [<span data-ttu-id="52d14-122">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="52d14-122">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="52d14-123">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="52d14-123">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
- [<span data-ttu-id="52d14-124">Instrukcje: Przesłanianie zakodowanej serializacji XML protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="52d14-124">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)
