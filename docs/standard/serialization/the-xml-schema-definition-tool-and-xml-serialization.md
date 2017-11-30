---
title: "Narzędzie definicji schematu XML i serializacja XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b943251ff426d5557c4715a856ffdadd3013b9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="3ffd5-102">Narzędzie definicji schematu XML i serializacja XML</span><span class="sxs-lookup"><span data-stu-id="3ffd5-102">The XML Schema Definition Tool and XML Serialization</span></span>
<span data-ttu-id="3ffd5-103">Narzędzie definicji schematu XML ([narzędzie definicji schematu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) jest instalowany wraz z narzędzia .NET Framework jako część systemu Windows® Software Development Kit (SDK).</span><span class="sxs-lookup"><span data-stu-id="3ffd5-103">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows® Software Development Kit (SDK).</span></span> <span data-ttu-id="3ffd5-104">To narzędzie jest przeznaczony głównie do dwóch celów:</span><span class="sxs-lookup"><span data-stu-id="3ffd5-104">The tool is designed primarily for two purposes:</span></span>  
  
-   <span data-ttu-id="3ffd5-105">Aby wygenerować C# lub Visual Basic PLików klasy, które są zgodne z określonego schematu języka (XSD) definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="3ffd5-105">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="3ffd5-106">Narzędzie wykonuje schematu XML jako argument i generuje PLik, który zawiera wiele klas, gdy serializowany z <xref:System.Xml.Serialization.XmlSerializer>, zgodny ze schematem.</span><span class="sxs-lookup"><span data-stu-id="3ffd5-106">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="3ffd5-107">Aby uzyskać informacje o tym, jak korzystać z narzędzia do generowania klasy, które są zgodne z określonego schematu, zobacz [jak: Użyj narzędzia definicji schematu XML do generowania klasy i dokumentach schematów XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="3ffd5-107">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
-   <span data-ttu-id="3ffd5-108">Do generowania dokumentu XML schematu z PLiku .dll lub .exe.</span><span class="sxs-lookup"><span data-stu-id="3ffd5-108">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="3ffd5-109">Aby wyświetlić schemat zestaw PLiki, których zostanie utworzony lub, który został zmodyfikowany z atrybutów, należy przekazać wartość DLL lub EXE jako argument do narzędzia do generowania schematu XML.</span><span class="sxs-lookup"><span data-stu-id="3ffd5-109">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="3ffd5-110">Aby uzyskać informacje o tym, jak korzystać z narzędzia do generowania dokumentu schematu XML z zestaw klas, zobacz [jak: Użyj narzędzia definicji schematu XML do generowania klasy i dokumentach schematów XML](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="3ffd5-110">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
 <span data-ttu-id="3ffd5-111">Aby uzyskać więcej informacji na temat to narzędzie i innych użytkowników, zobacz [narzędzia](../../../docs/framework/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="3ffd5-111">For more information about this tool and others, see [Tools](../../../docs/framework/tools/index.md).</span></span> <span data-ttu-id="3ffd5-112">Informacje o opcjach narzędzia, zobacz [narzędzie definicji schematu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3ffd5-112">For information about the tool's options, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ffd5-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ffd5-113">See Also</span></span>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="3ffd5-114">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="3ffd5-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="3ffd5-115">Narzędzie definicji schematu XML (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="3ffd5-115">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="3ffd5-116">Porady: szeregowania obiektu</span><span class="sxs-lookup"><span data-stu-id="3ffd5-116">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="3ffd5-117">Porady: deserializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="3ffd5-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="3ffd5-118">Porady: Użyj narzędzia definicji schematu XML do generowania klasy i dokumentach schematów XML.</span><span class="sxs-lookup"><span data-stu-id="3ffd5-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)  
 [<span data-ttu-id="3ffd5-119">Schemat XML powiązania pomocy technicznej w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3ffd5-119">XML Schema Binding Support in the .NET Framework</span></span>](http://msdn.microsoft.com/en-us/8f0619dd-f1fc-4895-ae21-6d45d0382cc1)
