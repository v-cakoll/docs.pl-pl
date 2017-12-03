---
title: "Atrybuty, które sterowania serializacją użyciu zakodowanego protokołu SOAP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 358b635ee74699d9d427e8fac23fabd70c6cfa98
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="attributes-that-control-encoded-soap-serialization"></a><span data-ttu-id="07026-102">Atrybuty, które sterowania serializacją użyciu zakodowanego protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="07026-102">Attributes That Control Encoded SOAP Serialization</span></span> 
<span data-ttu-id="07026-103">Dokument konsorcjum World Wide Web (www.w3.org) o nazwie "Simple Object Access Protocol (SOAP) 1.1" zawiera sekcja opcjonalna (sekcja 5), opisujące, jak mogą być kodowane parametry protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="07026-103">The World Wide Web Consortium (www.w3.org) document named "Simple Object Access Protocol (SOAP) 1.1" contains an optional section (section 5) that describes how SOAP parameters can be encoded.</span></span> <span data-ttu-id="07026-104">Aby jest zgodny z sekcji 5 specyfikacji, należy użyć specjalnego zestawu atrybutów w <xref:System.Xml.Serialization> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="07026-104">To conform to section 5 of the specification, you must use a special set of attributes found in the <xref:System.Xml.Serialization> namespace.</span></span> <span data-ttu-id="07026-105">Zastosuj te atrybuty odpowiednio do klas i członków klas, a następnie użyj <xref:System.Xml.Serialization.XmlSerializer> do serializacji wystąpienia klasy lub klas.</span><span class="sxs-lookup"><span data-stu-id="07026-105">Apply those attributes as appropriate to classes and members of classes, and then use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of the class or classes.</span></span>  
  
 <span data-ttu-id="07026-106">W poniższej tabeli przedstawiono atrybuty, których może być stosowana, a ich działania.</span><span class="sxs-lookup"><span data-stu-id="07026-106">The following table shows the attributes, where they can be applied, and what they do.</span></span> <span data-ttu-id="07026-107">Aby uzyskać więcej informacji o korzystaniu z tych atrybutów do formantu serializacji XML, zobacz [jak: szeregowania obiektu jako SOAP-Encoded strumień XML](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) i [jak: zastąpienie zakodowane serializacji XML protokołu SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="07026-107">For more information about using these attributes to control XML serialization, see [How to: Serialize an Object as a SOAP-Encoded XML Stream](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) and [How to: Override Encoded SOAP XML Serialization](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).</span></span>  
  
 <span data-ttu-id="07026-108">Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybutów](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="07026-108">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span>  
  
|<span data-ttu-id="07026-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="07026-109">Attribute</span></span>|<span data-ttu-id="07026-110">Informacje zawarte w tym artykule dotyczą</span><span class="sxs-lookup"><span data-stu-id="07026-110">Applies to</span></span>|<span data-ttu-id="07026-111">Określa</span><span class="sxs-lookup"><span data-stu-id="07026-111">Specifies</span></span>|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|<span data-ttu-id="07026-112">Pole publiczne, właściwość, parametru lub wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="07026-112">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="07026-113">Składowa klasy będzie serializowana jako atrybut XML.</span><span class="sxs-lookup"><span data-stu-id="07026-113">The class member will be serialized as an XML attribute.</span></span>|  
|<xref:System.Xml.Serialization.SoapElementAttribute>|<span data-ttu-id="07026-114">Pole publiczne, właściwość, parametru lub wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="07026-114">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="07026-115">Klasa będzie serializowana jako XML element.</span><span class="sxs-lookup"><span data-stu-id="07026-115">The class will be serialized as an XML element.</span></span>|  
|<xref:System.Xml.Serialization.SoapEnumAttribute>|<span data-ttu-id="07026-116">Pole publicznej jest identyfikatorem wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="07026-116">Public field that is an enumeration identifier.</span></span>|<span data-ttu-id="07026-117">Nazwa elementu element członkowski wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="07026-117">The element name of an enumeration member.</span></span>|  
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|<span data-ttu-id="07026-118">Właściwości publiczne i pola.</span><span class="sxs-lookup"><span data-stu-id="07026-118">Public properties and fields.</span></span>|<span data-ttu-id="07026-119">Właściwości lub pól mają być ignorowane, gdy klasa zawierająca jest serializowana.</span><span class="sxs-lookup"><span data-stu-id="07026-119">The property or field should be ignored when the containing class is serialized.</span></span>|  
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|<span data-ttu-id="07026-120">Klasa pochodna publicznego deklaracje i metod publicznych w dokumentach sieci Web Services Description Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="07026-120">Public-derived class declarations and public methods for Web Services Description Language (WSDL) documents.</span></span>|<span data-ttu-id="07026-121">Typ mają zostać uwzględnione podczas generowania schematów (do rozpoznany po serializacji).</span><span class="sxs-lookup"><span data-stu-id="07026-121">The type should be included when generating schemas (to be recognized when serialized).</span></span>|  
|<xref:System.Xml.Serialization.SoapTypeAttribute>|<span data-ttu-id="07026-122">Klasa publiczna deklaracji.</span><span class="sxs-lookup"><span data-stu-id="07026-122">Public class declarations.</span></span>|<span data-ttu-id="07026-123">Klasa powinien zostać Zserializowany jako typ XML.</span><span class="sxs-lookup"><span data-stu-id="07026-123">The class should be serialized as an XML type.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07026-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07026-124">See Also</span></span>  
 [<span data-ttu-id="07026-125">XML i serializacji SOAP</span><span class="sxs-lookup"><span data-stu-id="07026-125">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [<span data-ttu-id="07026-126">Porady: szeregowania obiektu jako strumień SOAP zakodowane w formacie XML</span><span class="sxs-lookup"><span data-stu-id="07026-126">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [<span data-ttu-id="07026-127">Porady: Zastąp serializacji XML użyciu zakodowanego protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="07026-127">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [<span data-ttu-id="07026-128">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="07026-128">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="07026-129">Porady: szeregowania obiektu</span><span class="sxs-lookup"><span data-stu-id="07026-129">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="07026-130">Porady: deserializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="07026-130">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
