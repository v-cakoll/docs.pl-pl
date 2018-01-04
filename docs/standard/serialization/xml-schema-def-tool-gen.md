---
title: "Porady: Użyj narzędzia definicji schematu XML do generowania klasy i dokumentach schematów XML."
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0e390b808f9eaa5d6b305284e1abe28f45f4d104
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="815e5-102">Porady: Użyj narzędzia definicji schematu XML do generowania klasy i dokumentach schematów XML.</span><span class="sxs-lookup"><span data-stu-id="815e5-102">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="815e5-103">Narzędzie definicji schematu XML (Xsd.exe) służy do generowania schematu XML, która opisuje klasę lub do generowania klasy zdefiniowane przez schemat XML.</span><span class="sxs-lookup"><span data-stu-id="815e5-103">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="815e5-104">Poniższe procedury pokazują, jak wykonywać te operacje.</span><span class="sxs-lookup"><span data-stu-id="815e5-104">The following procedures show how to perform these operations.</span></span>  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="815e5-105">Do generowania klasy, które są zgodne z określonego schematu</span><span class="sxs-lookup"><span data-stu-id="815e5-105">To generate classes that conform to a specific schema</span></span>  
  
1.  <span data-ttu-id="815e5-106">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="815e5-106">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="815e5-107">Przekaż schematu XML jako argument do narzędzia do definicji schematu XML, który tworzy zestaw klas, które dokładnie dopasowane do schematu XML, na przykład:</span><span class="sxs-lookup"><span data-stu-id="815e5-107">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="815e5-108">To narzędzie może przetwarzać tylko schematy, które odwołują się do specyfikacji XML konsorcjum World Wide Web 16 marca 2001.</span><span class="sxs-lookup"><span data-stu-id="815e5-108">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="815e5-109">Innymi słowy przestrzeń nazw schematu XML musi być "http://www.w3.org/2001/XMLSchema", jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="815e5-109">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    ```  
  
3.  <span data-ttu-id="815e5-110">Modyfikuj klas, metod, właściwości lub pól, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="815e5-110">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="815e5-111">Aby uzyskać więcej informacji na temat modyfikowania klasy z atrybutami, zobacz [kontrolowanie atrybutów za pomocą serializacji XML](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) i [atrybuty że formant zakodowane SOAP serializacji](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="815e5-111">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="815e5-112">Często jest to przydatne, należy zapoznać się ze schematem strumień XML, który jest generowany, gdy są serializacji wystąpień klasy (lub klasy).</span><span class="sxs-lookup"><span data-stu-id="815e5-112">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="815e5-113">Na przykład może publikować schematu dla innych użytkowników lub może porównaj je z schematu, z którym próbujesz osiągnąć zgodności.</span><span class="sxs-lookup"><span data-stu-id="815e5-113">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="815e5-114">Do generowania dokumentu XML schematu z zestawu klas</span><span class="sxs-lookup"><span data-stu-id="815e5-114">To generate an XML Schema document from a set of classes</span></span>  
  
1.  <span data-ttu-id="815e5-115">Kompiluj klasy lub klas do biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="815e5-115">Compile the class or classes into a DLL.</span></span>  
  
2.  <span data-ttu-id="815e5-116">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="815e5-116">Open a command prompt.</span></span>  
  
3.  <span data-ttu-id="815e5-117">Przekaż plik DLL jako argument do Xsd.exe, na przykład:</span><span class="sxs-lookup"><span data-stu-id="815e5-117">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="815e5-118">Schemat (lub schematy) zostanie zapisany, rozpoczynając od nazwy "schema0.xsd".</span><span class="sxs-lookup"><span data-stu-id="815e5-118">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815e5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="815e5-119">See Also</span></span>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="815e5-120">Narzędzie definicji schematu XML i serializacja XML</span><span class="sxs-lookup"><span data-stu-id="815e5-120">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 [<span data-ttu-id="815e5-121">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="815e5-121">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="815e5-122">Narzędzie definicji schematu XML (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="815e5-122">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="815e5-123">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="815e5-123">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="815e5-124">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="815e5-124">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
