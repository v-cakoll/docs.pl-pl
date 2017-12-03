---
title: XML i serializacji SOAP
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
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d5b89392801e7cf85fcda121a86d0bda4e7ac18
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="48e90-102">XML i serializacji SOAP</span><span class="sxs-lookup"><span data-stu-id="48e90-102">XML and SOAP Serialization</span></span>
<span data-ttu-id="48e90-103">Konwertuje serializacji XML (serializuje) pola publiczne i właściwości obiektu, lub parametry i wartości zwracane metod do strumień XML, który odpowiada określony dokument języka (XSD) definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="48e90-103">XML serialization converts (serializes) the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="48e90-104">Powoduje serializacji XML w silnie typizowanej klasy z właściwości publiczne i pola, które są konwertowane na format seryjny (w tym przypadku XML) do przechowywania lub transportu.</span><span class="sxs-lookup"><span data-stu-id="48e90-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>  
  
 <span data-ttu-id="48e90-105">Ponieważ XML jest standardem otwartym, strumień XML mogą być przetwarzane przez dowolną aplikację, zgodnie z potrzebami, niezależnie od platformy.</span><span class="sxs-lookup"><span data-stu-id="48e90-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="48e90-106">Na przykład usługi XML sieci Web utworzony przy użyciu platformy ASP.NET <xref:System.Xml.Serialization.XmlSerializer> klasa do tworzenia strumieni XML, które przekazywania danych między aplikacjami usług XML sieci Web w Internecie lub intranecie.</span><span class="sxs-lookup"><span data-stu-id="48e90-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="48e90-107">Z kolei deserializacji pobiera strumień XML i rekonstruuje obiektu.</span><span class="sxs-lookup"><span data-stu-id="48e90-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>  
  
 <span data-ttu-id="48e90-108">Umożliwia także serializacji XML można serializować obiektów do strumieni XML, które są zgodne ze specyfikacją protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="48e90-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="48e90-109">Protokołu SOAP to protokół oparte na języku XML, zaprojektowany specjalnie w celu transportu wywołań procedur za pomocą języka XML.</span><span class="sxs-lookup"><span data-stu-id="48e90-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>  
  
 <span data-ttu-id="48e90-110">Do serializacji lub deserializacji obiekty, użyj <xref:System.Xml.Serialization.XmlSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="48e90-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="48e90-111">Aby utworzyć klasy serializacji, należy użyć narzędzia definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="48e90-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="48e90-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="48e90-112">In This Section</span></span>  
 [<span data-ttu-id="48e90-113">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="48e90-113">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 <span data-ttu-id="48e90-114">Udostępnia ogólne definicji serializacji, zwłaszcza serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="48e90-114">Provides a general definition of serialization, particularly XML serialization.</span></span>  
  
 [<span data-ttu-id="48e90-115">Porady: szeregowania obiektu</span><span class="sxs-lookup"><span data-stu-id="48e90-115">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 <span data-ttu-id="48e90-116">Instrukcje krok po kroku dotyczący dla serializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="48e90-116">Provides step-by-step instructions for serializing an object.</span></span>  
  
 [<span data-ttu-id="48e90-117">Porady: deserializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="48e90-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 <span data-ttu-id="48e90-118">Instrukcje krok po kroku deserializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="48e90-118">Provides step-by-step instructions for deserializing an object.</span></span>  
  
 [<span data-ttu-id="48e90-119">Przykłady serializacji XML</span><span class="sxs-lookup"><span data-stu-id="48e90-119">Examples of XML Serialization</span></span>](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 <span data-ttu-id="48e90-120">Przykłady, które przedstawiają podstawy serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="48e90-120">Provides examples that demonstrate the basics of XML serialization.</span></span>  
  
 [<span data-ttu-id="48e90-121">Narzędzie definicji schematu XML i serializacja XML</span><span class="sxs-lookup"><span data-stu-id="48e90-121">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 <span data-ttu-id="48e90-122">Opisuje sposób można utworzyć klasy, które będą zgodne z określonym schematem języka (XSD) definicji schematu XML lub do generowania schematu XML z PLiku dll za pomocą narzędzia definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="48e90-122">Describes how to use the XML Schema Definition tool to create classes that adhere to a particular XML Schema definition language (XSD) schema, or to generate an XML Schema from a .dll file.</span></span>  
  
 [<span data-ttu-id="48e90-123">Kontrolowanie serializacji XML przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="48e90-123">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 <span data-ttu-id="48e90-124">Opisuje sposób kontroluje serializacji przy użyciu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="48e90-124">Describes how to control serialization by using attributes.</span></span>  
  
 [<span data-ttu-id="48e90-125">Atrybuty, które kontrolują serializacji XML</span><span class="sxs-lookup"><span data-stu-id="48e90-125">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 <span data-ttu-id="48e90-126">Wyświetla listę atrybutów, które są używane do kontrolowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="48e90-126">Lists the attributes that are used to control XML serialization.</span></span>  
  
 [<span data-ttu-id="48e90-127">Porady: Określ nazwę elementu alternatywnego strumienia XML</span><span class="sxs-lookup"><span data-stu-id="48e90-127">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 <span data-ttu-id="48e90-128">Przedstawia informacje o zaawansowanych scenariusz przedstawiający sposób generowania wielu strumieni XML przez zastąpienie serializacji.</span><span class="sxs-lookup"><span data-stu-id="48e90-128">Presents an advanced scenario showing how to generate multiple XML streams by overriding the serialization.</span></span>  
  
 [<span data-ttu-id="48e90-129">Porady: kontrolowanie serializacji klas pochodnych</span><span class="sxs-lookup"><span data-stu-id="48e90-129">How to: Control Serialization of Derived Classes</span></span>](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 <span data-ttu-id="48e90-130">Przykład sposobu sterowania serializacją klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="48e90-130">Provides an example of how to control the serialization of derived classes.</span></span>  
  
 [<span data-ttu-id="48e90-131">Porady: kwalifikują się do elementu XML i nazwach atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="48e90-131">How to: Qualify XML Element and XML Attribute Names</span></span>](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 <span data-ttu-id="48e90-132">Opisuje sposób definiowania i kontrolować sposób, w których XML obszary nazw są używane w strumieniu XML.</span><span class="sxs-lookup"><span data-stu-id="48e90-132">Describes how to define and control the way in which XML namespaces are used in the XML stream.</span></span>  
  
 [<span data-ttu-id="48e90-133">Serializacja XML z usługami sieci Web XML</span><span class="sxs-lookup"><span data-stu-id="48e90-133">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 <span data-ttu-id="48e90-134">Wyjaśniono, jak serializacji XML jest używany w usług XML sieci Web.</span><span class="sxs-lookup"><span data-stu-id="48e90-134">Explains how XML serialization is used in XML Web services.</span></span>  
  
 [<span data-ttu-id="48e90-135">Porady: szeregowania obiektu jako strumień SOAP zakodowane w formacie XML</span><span class="sxs-lookup"><span data-stu-id="48e90-135">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 <span data-ttu-id="48e90-136">Informacje dotyczące używania <xref:System.Xml.Serialization.XmlSerializer> klasy w celu utworzenia zakodowanego strumieni XML protokołu SOAP, które są zgodne z sekcji 5 konsorcjum World Wide Web (www.w3.org) dokumentu "Simple Object Access Protocol (SOAP) 1.1."</span><span class="sxs-lookup"><span data-stu-id="48e90-136">Describes how to use the <xref:System.Xml.Serialization.XmlSerializer> class to create encoded SOAP XML streams that conform to section 5 of the World Wide Web Consortium (www.w3.org) document titled "Simple Object Access Protocol (SOAP) 1.1."</span></span>  
  
 [<span data-ttu-id="48e90-137">Porady: Zastąp serializacji XML użyciu zakodowanego protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="48e90-137">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 <span data-ttu-id="48e90-138">Opisuje proces zastępowanie serializacji obiektów XML jako komunikaty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="48e90-138">Describes the process for overriding XML serialization of objects as SOAP messages.</span></span>  
  
 [<span data-ttu-id="48e90-139">Atrybuty, które sterowania serializacją użyciu zakodowanego protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="48e90-139">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 <span data-ttu-id="48e90-140">Wyświetla listę atrybutów, które są używane do kontrolowania serializacji kodowany w formacie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="48e90-140">Lists the attributes that are used to control SOAP-encoded serialization.</span></span>  
  
 [<span data-ttu-id="48e90-141">\<System.XML.serialization > — Element</span><span class="sxs-lookup"><span data-stu-id="48e90-141">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 <span data-ttu-id="48e90-142">Element konfiguracji najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="48e90-142">The top-level configuration element for controlling XML serialization.</span></span>  
  
 [<span data-ttu-id="48e90-143">\<dateTimeSerialization > — Element</span><span class="sxs-lookup"><span data-stu-id="48e90-143">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 <span data-ttu-id="48e90-144">Określa tryb serializacji <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="48e90-144">Controls the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 [<span data-ttu-id="48e90-145">\<schemaImporterExtensions > — Element</span><span class="sxs-lookup"><span data-stu-id="48e90-145">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 <span data-ttu-id="48e90-146">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.</span><span class="sxs-lookup"><span data-stu-id="48e90-146">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
 [<span data-ttu-id="48e90-147">\<Dodaj > elementu \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="48e90-147">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 <span data-ttu-id="48e90-148">Dodaje typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.</span><span class="sxs-lookup"><span data-stu-id="48e90-148">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="48e90-149">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="48e90-149">Related Sections</span></span>  
 [<span data-ttu-id="48e90-150">Programowanie zaawansowanych technologii</span><span class="sxs-lookup"><span data-stu-id="48e90-150">Advanced Development Technologies</span></span>](http://msdn.microsoft.com/en-us/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 <span data-ttu-id="48e90-151">Łącza do dodatkowych informacji zadań związanych z projektowaniem zaawansowane i techniki programistyczne w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48e90-151">Provides links to more information on sophisticated development tasks and techniques in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="48e90-152">Utworzone za pomocą programu ASP.NET i klientami usługi XML sieci Web usług XML sieci Web</span><span class="sxs-lookup"><span data-stu-id="48e90-152">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 <span data-ttu-id="48e90-153">Zawiera tematy, które opisują oraz wyjaśniono, jak do usług XML sieci Web za pomocą programu ASP.NET programu.</span><span class="sxs-lookup"><span data-stu-id="48e90-153">Provides topics that describe and explain how to program XML Web services using ASP.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e90-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48e90-154">See Also</span></span>  
 [<span data-ttu-id="48e90-155">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="48e90-155">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
