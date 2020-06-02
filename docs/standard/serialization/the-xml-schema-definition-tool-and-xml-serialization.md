---
title: Narzędzie definicji schematu XML i serializacja XML
description: Narzędzie definicji schematu XML generuje pliki klasy C# lub Visual Basic dla schematu XSD i generuje schemat XML z biblioteki lub pliku wykonywalnego.
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: c88770403d4c2abfb5ce99f44ea1bec1f8337545
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279779"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="3c71d-103">Narzędzie definicji schematu XML i serializacja XML</span><span class="sxs-lookup"><span data-stu-id="3c71d-103">The XML Schema Definition Tool and XML Serialization</span></span>

<span data-ttu-id="3c71d-104">Narzędzie definicji schematu XML ([narzędzie definicji schematu XML (XSD. exe)](xml-schema-definition-tool-xsd-exe.md)) jest instalowane wraz z narzędziami .NET Framework w ramach &reg; zestawu Software Development Kit (SDK) dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3c71d-104">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows&reg; Software Development Kit (SDK).</span></span> <span data-ttu-id="3c71d-105">To narzędzie jest przeznaczony głównie do dwóch celów:</span><span class="sxs-lookup"><span data-stu-id="3c71d-105">The tool is designed primarily for two purposes:</span></span>  
  
- <span data-ttu-id="3c71d-106">Aby wygenerować C# lub Visual Basic PLików klasy, które są zgodne z określonego schematu języka (XSD) definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="3c71d-106">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="3c71d-107">Narzędzie wykonuje schematu XML jako argument i generuje PLik, który zawiera wiele klas, gdy serializowany z <xref:System.Xml.Serialization.XmlSerializer>, zgodny ze schematem.</span><span class="sxs-lookup"><span data-stu-id="3c71d-107">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="3c71d-108">Aby uzyskać informacje na temat sposobu użycia narzędzia do generowania klas, które są zgodne z określonym schematem, zobacz [How to: use a XML Schema Definition Tool to Generating Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="3c71d-108">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span></span>  
  
- <span data-ttu-id="3c71d-109">Do generowania dokumentu XML schematu z PLiku .dll lub .exe.</span><span class="sxs-lookup"><span data-stu-id="3c71d-109">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="3c71d-110">Aby wyświetlić schemat zestaw PLiki, których zostanie utworzony lub, który został zmodyfikowany z atrybutów, należy przekazać wartość DLL lub EXE jako argument do narzędzia do generowania schematu XML.</span><span class="sxs-lookup"><span data-stu-id="3c71d-110">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="3c71d-111">Aby uzyskać informacje o sposobach generowania dokumentu schematu XML z zestawu klas przy użyciu narzędzia, zobacz [How to: use a XML Schema Definition Tool to Generating Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="3c71d-111">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span></span>  
  
<span data-ttu-id="3c71d-112">Aby uzyskać więcej informacji na temat korzystania z tego narzędzia, zobacz [narzędzie definicji schematu XML (XSD. exe)](xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3c71d-112">For more information about using the tool, see [XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c71d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c71d-113">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="3c71d-114">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="3c71d-114">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="3c71d-115">Narzędzie definicji schematu XML (XSD. exe)</span><span class="sxs-lookup"><span data-stu-id="3c71d-115">XML Schema Definition Tool (Xsd.exe)</span></span>](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="3c71d-116">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="3c71d-116">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="3c71d-117">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="3c71d-117">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
- [<span data-ttu-id="3c71d-118">Instrukcje: Generowanie klas i dokumentów schematu XML przy użyciu narzędzia definicji schematu XML</span><span class="sxs-lookup"><span data-stu-id="3c71d-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](xml-schema-def-tool-gen.md)
- <span data-ttu-id="3c71d-119">[Obsługa powiązań schematu XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3c71d-119">[XML Schema Binding Support](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>
