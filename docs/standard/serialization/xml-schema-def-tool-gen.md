---
title: 'Instrukcje: korzystanie z narzędzia definicji schematu XML do generowania klas i dokumentów schematu XML'
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 9b2cd67a1c4f30e6fe246124be5b8f7081c539a6
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392862"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="aad34-102">Instrukcje: korzystanie z narzędzia definicji schematu XML do generowania klas i dokumentów schematu XML</span><span class="sxs-lookup"><span data-stu-id="aad34-102">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="aad34-103">Narzędzie definicji schematu XML (Xsd.exe) służy do generowania schematu XML, która opisuje klasę lub do generowania klasy zdefiniowane przez schemat XML.</span><span class="sxs-lookup"><span data-stu-id="aad34-103">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="aad34-104">Poniższe procedury pokazują, jak wykonywać te operacje.</span><span class="sxs-lookup"><span data-stu-id="aad34-104">The following procedures show how to perform these operations.</span></span>  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="aad34-105">Do generowania klasy, które są zgodne z określonego schematu</span><span class="sxs-lookup"><span data-stu-id="aad34-105">To generate classes that conform to a specific schema</span></span>  
  
1. <span data-ttu-id="aad34-106">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="aad34-106">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="aad34-107">Przekaż schemat XML jako argument do narzędzia definicji schematu XML, które tworzy zestaw klas, które są dokładnie dopasowane do schematu XML, na przykład:</span><span class="sxs-lookup"><span data-stu-id="aad34-107">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="aad34-108">To narzędzie może przetwarzać tylko schematy, które odwołują się do specyfikacji XML konsorcjum World Wide Web 16 marca 2001.</span><span class="sxs-lookup"><span data-stu-id="aad34-108">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="aad34-109">Innymi słowy, przestrzeń nazw schematu XML musi mieć wartość "http://www.w3.org/2001/XMLSchema", jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="aad34-109">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    ```  
  
3. <span data-ttu-id="aad34-110">Modyfikuj klas, metod, właściwości lub pól, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="aad34-110">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="aad34-111">Aby uzyskać więcej informacji na temat modyfikowania klasy z atrybutami, zobacz [Kontrolowanie serializacji XML przy użyciu atrybutów](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) i atrybutów kontrolujących [ZAKODOWANĄ serializację protokołu SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="aad34-111">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="aad34-112">Często jest to przydatne, należy zapoznać się ze schematem strumień XML, który jest generowany, gdy są serializacji wystąpień klasy (lub klasy).</span><span class="sxs-lookup"><span data-stu-id="aad34-112">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="aad34-113">Na przykład można opublikować schemat do użytku przez inne osoby lub można go porównać ze schematem, z którym próbujesz osiągnąć zgodność.</span><span class="sxs-lookup"><span data-stu-id="aad34-113">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="aad34-114">Do generowania dokumentu XML schematu z zestawu klas</span><span class="sxs-lookup"><span data-stu-id="aad34-114">To generate an XML Schema document from a set of classes</span></span>  
  
1. <span data-ttu-id="aad34-115">Kompiluj klasy lub klas do biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="aad34-115">Compile the class or classes into a DLL.</span></span>  
  
2. <span data-ttu-id="aad34-116">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="aad34-116">Open a command prompt.</span></span>  
  
3. <span data-ttu-id="aad34-117">Przekaż plik DLL jako argument do pliku XSD. exe, na przykład:</span><span class="sxs-lookup"><span data-stu-id="aad34-117">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="aad34-118">Schemat (lub schematy) zostanie zapisany, rozpoczynając od nazwy "schema0.xsd".</span><span class="sxs-lookup"><span data-stu-id="aad34-118">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad34-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aad34-119">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="aad34-120">Narzędzie definicji schematu XML i serializacja XML</span><span class="sxs-lookup"><span data-stu-id="aad34-120">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="aad34-121">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="aad34-121">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="aad34-122">Narzędzie definicji schematu XML (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="aad34-122">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="aad34-123">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="aad34-123">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="aad34-124">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="aad34-124">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
