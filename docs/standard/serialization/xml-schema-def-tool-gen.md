---
title: 'Instrukcje: Generowanie klas i dokumentów schematu XML przy użyciu narzędzia definicji schematu XML'
description: Dowiedz się, w jaki sposób używać narzędzia definicji schematu XML do generowania schematu XML opisującego klasę lub generowania klasy zdefiniowanej przez schemat XML.
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 21ce4ad846e21a328ba199f6253bd259be9d932b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379525"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="6768a-103">Instrukcje: Generowanie klas i dokumentów schematu XML przy użyciu narzędzia definicji schematu XML</span><span class="sxs-lookup"><span data-stu-id="6768a-103">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="6768a-104">Narzędzie definicji schematu XML (Xsd.exe) służy do generowania schematu XML, która opisuje klasę lub do generowania klasy zdefiniowane przez schemat XML.</span><span class="sxs-lookup"><span data-stu-id="6768a-104">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="6768a-105">Poniższe procedury pokazują, jak wykonywać te operacje.</span><span class="sxs-lookup"><span data-stu-id="6768a-105">The following procedures show how to perform these operations.</span></span>

<span data-ttu-id="6768a-106">Narzędzie definicji schematu XML (XSD. exe) zwykle można znaleźć w następującej ścieżce: </span><span class="sxs-lookup"><span data-stu-id="6768a-106">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:</span></span>\
<span data-ttu-id="6768a-107">_C: \\ Program Files (x86) \\ Microsoft SDK \\ Windows \\ {Version} \\ bin \\ NETFX {Version} Tools\\_</span><span class="sxs-lookup"><span data-stu-id="6768a-107">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="6768a-108">Do generowania klasy, które są zgodne z określonego schematu</span><span class="sxs-lookup"><span data-stu-id="6768a-108">To generate classes that conform to a specific schema</span></span>  
  
1. <span data-ttu-id="6768a-109">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="6768a-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="6768a-110">Przekaż schemat XML jako argument do narzędzia definicji schematu XML, które tworzy zestaw klas, które są dokładnie dopasowane do schematu XML, na przykład:</span><span class="sxs-lookup"><span data-stu-id="6768a-110">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="6768a-111">To narzędzie może przetwarzać tylko schematy, które odwołują się do specyfikacji XML konsorcjum World Wide Web 16 marca 2001.</span><span class="sxs-lookup"><span data-stu-id="6768a-111">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="6768a-112">Innymi słowy, przestrzeń nazw schematu XML musi być " http://www.w3.org/2001/XMLSchema ", jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6768a-112">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. <span data-ttu-id="6768a-113">Modyfikuj klas, metod, właściwości lub pól, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="6768a-113">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="6768a-114">Aby uzyskać więcej informacji na temat modyfikowania klasy z atrybutami, zobacz [Kontrolowanie serializacji XML przy użyciu atrybutów](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) i atrybutów kontrolujących [ZAKODOWANĄ serializację protokołu SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="6768a-114">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="6768a-115">Często jest to przydatne, należy zapoznać się ze schematem strumień XML, który jest generowany, gdy są serializacji wystąpień klasy (lub klasy).</span><span class="sxs-lookup"><span data-stu-id="6768a-115">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="6768a-116">Na przykład można opublikować schemat do użytku przez inne osoby lub można go porównać ze schematem, z którym próbujesz osiągnąć zgodność.</span><span class="sxs-lookup"><span data-stu-id="6768a-116">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="6768a-117">Do generowania dokumentu XML schematu z zestawu klas</span><span class="sxs-lookup"><span data-stu-id="6768a-117">To generate an XML Schema document from a set of classes</span></span>  
  
1. <span data-ttu-id="6768a-118">Kompiluj klasy lub klas do biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="6768a-118">Compile the class or classes into a DLL.</span></span>  
  
2. <span data-ttu-id="6768a-119">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="6768a-119">Open a command prompt.</span></span>  
  
3. <span data-ttu-id="6768a-120">Przekaż plik DLL jako argument do pliku XSD. exe, na przykład:</span><span class="sxs-lookup"><span data-stu-id="6768a-120">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="6768a-121">Schemat (lub schematy) zostanie zapisany, rozpoczynając od nazwy "schema0.xsd".</span><span class="sxs-lookup"><span data-stu-id="6768a-121">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6768a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6768a-122">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="6768a-123">Narzędzie definicji schematu XML i serializacja XML</span><span class="sxs-lookup"><span data-stu-id="6768a-123">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="6768a-124">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="6768a-124">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="6768a-125">Narzędzie definicji schematu XML (XSD. exe)</span><span class="sxs-lookup"><span data-stu-id="6768a-125">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="6768a-126">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="6768a-126">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="6768a-127">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="6768a-127">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
