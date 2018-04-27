---
title: Sprawdzanie poprawności schematu (XSD) XML z XmlSchemaSet
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
caps.latest.revision: 3
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f18852411d733d12bcbbdba2b64bc2f134ea061c
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="c993b-102">Sprawdzanie poprawności schematu (XSD) XML z XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="c993b-102">XML Schema (XSD) Validation with XmlSchemaSet</span></span>
<span data-ttu-id="c993b-103">Dokumenty XML może zostać zweryfikowany względem schematu XML schema definition language (XSD) w <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="c993b-103">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="c993b-104">Sprawdzanie poprawności dokumentów XML</span><span class="sxs-lookup"><span data-stu-id="c993b-104">Validating XML Documents</span></span>  
 <span data-ttu-id="c993b-105">Dokumenty XML są weryfikowane przez <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="c993b-105">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="c993b-106">Aby sprawdzić poprawność dokument XML, utworzyć <xref:System.Xml.XmlReaderSettings> obiekt, który zawiera schemat XML schematu definition language (XSD) używanemu do walidacji dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c993b-106">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c993b-107"><xref:System.Xml.Schema> Przestrzeń nazw zawiera metody rozszerzenia, które ułatwiają sprawdzanie poprawności drzewo XML przed plik XSD, korzystając z [LINQ do XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span><span class="sxs-lookup"><span data-stu-id="c993b-107">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span> <span data-ttu-id="c993b-108">Aby uzyskać więcej informacji dotyczących sprawdzania poprawności dokumentów XML za pomocą LINQ do XML, zobacz [porady: Sprawdzanie poprawności za pomocą schematu XSD](https://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).</span><span class="sxs-lookup"><span data-stu-id="c993b-108">For more information on validating XML documents with LINQ to XML, see [How to: Validate Using XSD](https://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).</span></span>  
  
 <span data-ttu-id="c993b-109">Poszczególne schematu lub zestawu schematów (jako <xref:System.Xml.Schema.XmlSchemaSet>) mogą być dodawane do <xref:System.Xml.Schema.XmlSchemaSet> przez przekazanie dowolnego z nich jako parametr <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="c993b-109">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="c993b-110">Należy pamiętać, że podczas sprawdzania poprawności dokumentu docelowego obszaru nazw dokumentu musi odpowiadać docelowa przestrzeń nazw schematu w zestawie schematów.</span><span class="sxs-lookup"><span data-stu-id="c993b-110">Note that when validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="c993b-111">Poniżej przedstawiono przykładowy dokument XML.</span><span class="sxs-lookup"><span data-stu-id="c993b-111">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="c993b-112">Oto schemat sprawdzania przykładowy dokument XML.</span><span class="sxs-lookup"><span data-stu-id="c993b-112">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="c993b-113">W następującym przykładzie kodu powyższego schematu jest dodawany do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwość <xref:System.Xml.XmlReaderSettings> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c993b-113">In the code example that follows, the schema above is added to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="c993b-114"><xref:System.Xml.XmlReaderSettings> Obiekt został przekazany jako parametr <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> obiektu, który sprawdza poprawność powyżej dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c993b-114">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="c993b-115"><xref:System.Xml.XmlReaderSettings.ValidationType%2A> Właściwość <xref:System.Xml.XmlReaderSettings> obiektu ma ustawioną wartość `Schema` wymusić dokumentu XML przez <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c993b-115">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="c993b-116">A <xref:System.Xml.Schema.ValidationEventHandler> jest dodawany do <xref:System.Xml.XmlReaderSettings> obiektu do obsługi dowolnej <xref:System.Xml.Schema.XmlSeverityType.Warning> lub <xref:System.Xml.Schema.XmlSeverityType.Error> zdarzenia wywoływane przez błędy znalezione w procesie weryfikacji dokumentu XML i schematu.</span><span class="sxs-lookup"><span data-stu-id="c993b-116">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c993b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c993b-117">See Also</span></span>  
 [<span data-ttu-id="c993b-118">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="c993b-118">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="c993b-119">Praca ze schematami XML</span><span class="sxs-lookup"><span data-stu-id="c993b-119">Working with XML Schemas</span></span>](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
