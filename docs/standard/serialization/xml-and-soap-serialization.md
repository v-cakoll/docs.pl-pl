---
title: Serializacja XML i SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: d9dc68d8e7eced031af404aaec20784573c9930a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028242"
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="70dfe-102">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="70dfe-102">XML and SOAP Serialization</span></span>

<span data-ttu-id="70dfe-103">Konwertuje serializacji XML (serializuje) pola publiczne i właściwości obiektu, lub parametry i wartości zwracane metod do strumień XML, który odpowiada określony dokument języka (XSD) definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="70dfe-103">XML serialization converts (serializes) the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="70dfe-104">Powoduje serializacji XML w silnie typizowanej klasy z właściwości publiczne i pola, które są konwertowane na format seryjny (w tym przypadku XML) do przechowywania lub transportu.</span><span class="sxs-lookup"><span data-stu-id="70dfe-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="70dfe-105">Ponieważ kod XML jest otwarty standard, strumień XML mogą być przetwarzane przez dowolną aplikację, zgodnie z potrzebami, niezależnie od platformy.</span><span class="sxs-lookup"><span data-stu-id="70dfe-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="70dfe-106">Na przykład usług sieci Web XML utworzone za pomocą programu ASP.NET, użyj <xref:System.Xml.Serialization.XmlSerializer> klasy w celu utworzenia strumieni XML, które przekazują dane między aplikacjami usług XML sieci Web w Internecie lub intranecie.</span><span class="sxs-lookup"><span data-stu-id="70dfe-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="70dfe-107">Z kolei deserializacji pobiera strumień XML i rekonstruuje obiektu.</span><span class="sxs-lookup"><span data-stu-id="70dfe-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="70dfe-108">Umożliwia także serializacji XML można serializować obiektów do strumieni XML, które są zgodne ze specyfikacją protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="70dfe-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="70dfe-109">Protokołu SOAP to protokół oparte na języku XML, zaprojektowany specjalnie w celu transportu wywołań procedur za pomocą języka XML.</span><span class="sxs-lookup"><span data-stu-id="70dfe-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="70dfe-110">Do serializacji lub deserializacji obiekty, użyj <xref:System.Xml.Serialization.XmlSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="70dfe-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="70dfe-111">Aby utworzyć klasy serializacji, należy użyć narzędzia definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="70dfe-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="70dfe-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="70dfe-112">In This Section</span></span>

[<span data-ttu-id="70dfe-113">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="70dfe-113">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)  
<span data-ttu-id="70dfe-114">Udostępnia ogólne definicji serializacji, zwłaszcza serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="70dfe-114">Provides a general definition of serialization, particularly XML serialization.</span></span>

[<span data-ttu-id="70dfe-115">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="70dfe-115">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)  
<span data-ttu-id="70dfe-116">Instrukcje krok po kroku dotyczący dla serializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="70dfe-116">Provides step-by-step instructions for serializing an object.</span></span>

[<span data-ttu-id="70dfe-117">Instrukcje: Deserializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="70dfe-117">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)  
<span data-ttu-id="70dfe-118">Instrukcje krok po kroku deserializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="70dfe-118">Provides step-by-step instructions for deserializing an object.</span></span>

[<span data-ttu-id="70dfe-119">Przykłady serializacji XML</span><span class="sxs-lookup"><span data-stu-id="70dfe-119">Examples of XML Serialization</span></span>](examples-of-xml-serialization.md)  
<span data-ttu-id="70dfe-120">Zawiera przykłady demonstrujące podstawy serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="70dfe-120">Provides examples that demonstrate the basics of XML serialization.</span></span>

[<span data-ttu-id="70dfe-121">Narzędzie definicji schematu XML i serializacja XML</span><span class="sxs-lookup"><span data-stu-id="70dfe-121">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)  
<span data-ttu-id="70dfe-122">Opisuje sposób można utworzyć klasy, które będą zgodne z określonym schematem języka (XSD) definicji schematu XML lub do generowania schematu XML z PLiku dll za pomocą narzędzia definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="70dfe-122">Describes how to use the XML Schema Definition tool to create classes that adhere to a particular XML Schema definition language (XSD) schema, or to generate an XML Schema from a .dll file.</span></span>

[<span data-ttu-id="70dfe-123">Kontrolowanie serializacji XML przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="70dfe-123">Controlling XML Serialization Using Attributes</span></span>](controlling-xml-serialization-using-attributes.md)  
<span data-ttu-id="70dfe-124">Opisuje sposób kontroluje serializacji przy użyciu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="70dfe-124">Describes how to control serialization by using attributes.</span></span>

[<span data-ttu-id="70dfe-125">Atrybuty kontrolujące serializację XML</span><span class="sxs-lookup"><span data-stu-id="70dfe-125">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)  
<span data-ttu-id="70dfe-126">Wyświetla listę atrybutów, które są używane do kontrolowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="70dfe-126">Lists the attributes that are used to control XML serialization.</span></span>

[<span data-ttu-id="70dfe-127">Instrukcje: Określ nazwę elementu alternatywny Stream XML</span><span class="sxs-lookup"><span data-stu-id="70dfe-127">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
<span data-ttu-id="70dfe-128">Przedstawia informacje o zaawansowanym scenariuszu prezentujący do generowania wielu strumieni XML przez zastąpienie serializacji.</span><span class="sxs-lookup"><span data-stu-id="70dfe-128">Presents an advanced scenario showing how to generate multiple XML streams by overriding the serialization.</span></span>

[<span data-ttu-id="70dfe-129">Instrukcje: Kontrola serializacji w klasach pochodnych</span><span class="sxs-lookup"><span data-stu-id="70dfe-129">How to: Control Serialization of Derived Classes</span></span>](how-to-control-serialization-of-derived-classes.md)  
<span data-ttu-id="70dfe-130">Zawiera przykładowy sposób kontroluje serializacji w klasach pochodnych.</span><span class="sxs-lookup"><span data-stu-id="70dfe-130">Provides an example of how to control the serialization of derived classes.</span></span>

[<span data-ttu-id="70dfe-131">Instrukcje: Kwalifikowanie elementu XML i nazw atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="70dfe-131">How to: Qualify XML Element and XML Attribute Names</span></span>](how-to-qualify-xml-element-and-xml-attribute-names.md)  
<span data-ttu-id="70dfe-132">Opisuje sposób definiowania i kontrolować sposób, w których XML obszary nazw są używane w strumieniu XML.</span><span class="sxs-lookup"><span data-stu-id="70dfe-132">Describes how to define and control the way in which XML namespaces are used in the XML stream.</span></span>

[<span data-ttu-id="70dfe-133">Serializacja XML z usługami internetowymi XML</span><span class="sxs-lookup"><span data-stu-id="70dfe-133">XML Serialization with XML Web Services</span></span>](xml-serialization-with-xml-web-services.md)  
<span data-ttu-id="70dfe-134">W tym artykule wyjaśniono, jak serializacji XML jest używany w usługach sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="70dfe-134">Explains how XML serialization is used in XML Web services.</span></span>

[<span data-ttu-id="70dfe-135">Instrukcje: Serializacja obiektu jako Stream XML kodowany w formacie protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="70dfe-135">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
<span data-ttu-id="70dfe-136">Opisuje sposób używania <xref:System.Xml.Serialization.XmlSerializer> klasy w celu utworzenia zakodowany strumieni XML protokołu SOAP, które są zgodne z części 5 dokumentu World Wide Web Consortium (W3C) [proste obiektu dostępu protokołu (protokołu SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).</span><span class="sxs-lookup"><span data-stu-id="70dfe-136">Describes how to use the <xref:System.Xml.Serialization.XmlSerializer> class to create encoded SOAP XML streams that conform to section 5 of the World Wide Web Consortium (W3C) document titled [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).</span></span>

[<span data-ttu-id="70dfe-137">Instrukcje: Zastąp zakodowanego protokołu SOAP serializacji XML</span><span class="sxs-lookup"><span data-stu-id="70dfe-137">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)  
<span data-ttu-id="70dfe-138">Opisuje proces zastępowanie serializacji obiektów XML jako komunikaty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="70dfe-138">Describes the process for overriding XML serialization of objects as SOAP messages.</span></span>

[<span data-ttu-id="70dfe-139">Atrybuty kontrolujące zakodowaną serializację SOAP</span><span class="sxs-lookup"><span data-stu-id="70dfe-139">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)  
<span data-ttu-id="70dfe-140">Wyświetla listę atrybutów, które są używane do kontrolowania serializacji kodowany w formacie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="70dfe-140">Lists the attributes that are used to control SOAP-encoded serialization.</span></span>

[<span data-ttu-id="70dfe-141">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="70dfe-141">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)  
<span data-ttu-id="70dfe-142">Element konfiguracji najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="70dfe-142">The top-level configuration element for controlling XML serialization.</span></span>

[<span data-ttu-id="70dfe-143">\<dateTimeSerialization> Element</span><span class="sxs-lookup"><span data-stu-id="70dfe-143">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)  
<span data-ttu-id="70dfe-144">Określa tryb serializacji <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="70dfe-144">Controls the serialization mode of <xref:System.DateTime> objects.</span></span>

[<span data-ttu-id="70dfe-145">\<schemaImporterExtensions> Element</span><span class="sxs-lookup"><span data-stu-id="70dfe-145">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)  
<span data-ttu-id="70dfe-146">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.</span><span class="sxs-lookup"><span data-stu-id="70dfe-146">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>

[<span data-ttu-id="70dfe-147">\<add> Element for \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="70dfe-147">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)  
<span data-ttu-id="70dfe-148">Dodaje typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.</span><span class="sxs-lookup"><span data-stu-id="70dfe-148">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>

## <a name="related-sections"></a><span data-ttu-id="70dfe-149">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="70dfe-149">Related Sections</span></span>

<span data-ttu-id="70dfe-150">[Usługi sieci Web XML utworzone za pomocą platformy ASP.NET i klientów usługi sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="70dfe-150">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>  
<span data-ttu-id="70dfe-151">Zawiera tematy, które opisują, a wyjaśniają, jak program usług XML sieci Web za pomocą programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="70dfe-151">Provides topics that describe and explain how to program XML Web services using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="70dfe-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70dfe-152">See also</span></span>

- [<span data-ttu-id="70dfe-153">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="70dfe-153">Binary Serialization</span></span>](binary-serialization.md)
