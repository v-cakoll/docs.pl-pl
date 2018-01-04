---
title: Odczytywanie i zapisywanie schematy XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 96f8cf924ffe510e1fea4d21fe86ca860fe8fab0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="9ffda-102">Odczytywanie i zapisywanie schematy XML</span><span class="sxs-lookup"><span data-stu-id="9ffda-102">Reading and Writing XML Schemas</span></span>
<span data-ttu-id="9ffda-103">Schematu obiektu modelu (SOM) interfejsu API może służyć do odczytu i zapisu definicji schematu XML schematy języka (XSD) z plików lub innych źródeł i tworzenie XML schematów w pamięci przy użyciu klas w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw, które są mapowane na struktury zdefiniowane w świecie Zalecenie szerokiej sieci Web konsorcjum W3C XML schematu.</span><span class="sxs-lookup"><span data-stu-id="9ffda-103">The Schema Object Model (SOM) API can be used to read and write XML Schema definition language (XSD) schemas from files or other sources and build XML schemas in-memory using the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation.</span></span>  
  
## <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="9ffda-104">Odczytywanie i zapisywanie schematy XML</span><span class="sxs-lookup"><span data-stu-id="9ffda-104">Reading and Writing XML Schemas</span></span>  
 <span data-ttu-id="9ffda-105"><xref:System.Xml.Schema.XmlSchema> Klasa udostępnia <xref:System.Xml.Schema.XmlSchema.Read%2A> i <xref:System.Xml.Schema.XmlSchema.Write%2A> metody do odczytu i zapisu schematów XML.</span><span class="sxs-lookup"><span data-stu-id="9ffda-105">The <xref:System.Xml.Schema.XmlSchema> class provides the <xref:System.Xml.Schema.XmlSchema.Read%2A> and <xref:System.Xml.Schema.XmlSchema.Write%2A> methods to read and write XML schemas.</span></span> <span data-ttu-id="9ffda-106"><xref:System.Xml.Schema.XmlSchema.Read%2A> Metoda zwraca <xref:System.Xml.Schema.XmlSchema> obiekt reprezentujący schematu XML i przyjmuje opcjonalny <xref:System.Xml.Schema.ValidationEventHandler> jako parametr do obsługi schemat sprawdzania poprawności ostrzeżeń i błędów napotkanych podczas odczytywania schematu XML.</span><span class="sxs-lookup"><span data-stu-id="9ffda-106">The <xref:System.Xml.Schema.XmlSchema.Read%2A> method returns an <xref:System.Xml.Schema.XmlSchema> object representing the XML schema and takes an optional <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to handle schema validation warnings and errors encountered while reading an XML schema.</span></span>  
  
 <span data-ttu-id="9ffda-107"><xref:System.Xml.Schema.XmlSchema.Write%2A> Metoda zapisuje schematów XML do <xref:System.IO.Stream>, <xref:System.IO.TextWriter> i <xref:System.Xml.XmlWriter> obiektów i może być opcjonalny <xref:System.Xml.XmlNamespaceManager> obiektu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="9ffda-107">The <xref:System.Xml.Schema.XmlSchema.Write%2A> method writes XML schemas to <xref:System.IO.Stream>, <xref:System.IO.TextWriter> and <xref:System.Xml.XmlWriter> objects and can take an optional <xref:System.Xml.XmlNamespaceManager> object as a parameter.</span></span> <span data-ttu-id="9ffda-108"><xref:System.Xml.XmlNamespaceManager> Służy do obsługi przestrzeni nazw w schematu XML.</span><span class="sxs-lookup"><span data-stu-id="9ffda-108">An <xref:System.Xml.XmlNamespaceManager> is used to handle namespaces encountered in an XML schema.</span></span> <span data-ttu-id="9ffda-109">Aby uzyskać więcej informacji na temat <xref:System.Xml.XmlNamespaceManager> , zobacz [Zarządzanie przestrzeni nazw w dokumencie XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="9ffda-109">For more information about the <xref:System.Xml.XmlNamespaceManager> class, see [Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).</span></span>  
  
 <span data-ttu-id="9ffda-110">W poniższym przykładzie kodu przedstawiono odczytywanie i zapisywanie schematów XML z i do pliku.</span><span class="sxs-lookup"><span data-stu-id="9ffda-110">The following code example illustrates reading and writing XML schemas from and to a file.</span></span> <span data-ttu-id="9ffda-111">Przykładowy kod ma `example.xsd` pliku odczytuje go do <xref:System.Xml.Schema.XmlSchema> przy użyciu `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metody, a następnie zapisuje plik do konsoli i nowy `new.xsd` pliku.</span><span class="sxs-lookup"><span data-stu-id="9ffda-111">The code example takes the `example.xsd` file, reads it into an <xref:System.Xml.Schema.XmlSchema> object using the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method, and then writes the file to the console and a new `new.xsd` file.</span></span> <span data-ttu-id="9ffda-112">Udostępnia również przykładowy kod <xref:System.Xml.Schema.ValidationEventHandler> jako parametr `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> można obsłużyć schemat sprawdzania poprawności ostrzeżeń i błędów napotkanych podczas odczytywania schematu XML.</span><span class="sxs-lookup"><span data-stu-id="9ffda-112">The code example also provides a <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method to handle any schema validation warnings or errors encountered while reading the XML schema.</span></span> <span data-ttu-id="9ffda-113">Jeśli <xref:System.Xml.Schema.ValidationEventHandler> nie określono (`null`), nie zostały zgłoszone nie ostrzeżenia i błędy.</span><span class="sxs-lookup"><span data-stu-id="9ffda-113">If the <xref:System.Xml.Schema.ValidationEventHandler> is not specified (`null`), no warnings or errors are reported.</span></span>  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 <span data-ttu-id="9ffda-114">Przykład przyjmuje `example.xsd` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="9ffda-114">The example takes the `example.xsd` as input.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ffda-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ffda-115">See Also</span></span>  
 [<span data-ttu-id="9ffda-116">Model SOM (XML Schema Object Model) ― omówienie</span><span class="sxs-lookup"><span data-stu-id="9ffda-116">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [<span data-ttu-id="9ffda-117">Tworzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="9ffda-117">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [<span data-ttu-id="9ffda-118">Przechodzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="9ffda-118">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="9ffda-119">Edytowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="9ffda-119">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [<span data-ttu-id="9ffda-120">Uwzględnianie lub importowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="9ffda-120">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [<span data-ttu-id="9ffda-121">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="9ffda-121">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="9ffda-122">Zestaw informacji po kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="9ffda-122">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)  
 [<span data-ttu-id="9ffda-123">Zarządzanie przestrzeniami nazw w dokumencie XML</span><span class="sxs-lookup"><span data-stu-id="9ffda-123">Managing Namespaces in an XML Document</span></span>](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)
