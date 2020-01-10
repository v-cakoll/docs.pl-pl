---
title: Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 6bd7525b77d4154193b57f8e6589cb865ace5fd6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709884"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="1fc2a-102">Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="1fc2a-102">XML Schema (XSD) Validation with XmlSchemaSet</span></span>
<span data-ttu-id="1fc2a-103">Dokumenty XML można sprawdzić w oparciu o schemat języka definicji schematu XML (XSD) w <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="1fc2a-103">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="1fc2a-104">Sprawdzanie poprawności dokumentów XML</span><span class="sxs-lookup"><span data-stu-id="1fc2a-104">Validating XML Documents</span></span>  
 <span data-ttu-id="1fc2a-105">Dokumenty XML są weryfikowane przez metodę <xref:System.Xml.XmlReader.Create%2A> klasy <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="1fc2a-105">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="1fc2a-106">Aby sprawdzić poprawność dokumentu XML, Utwórz obiekt <xref:System.Xml.XmlReaderSettings>, który zawiera schemat języka definicji schematu XML (XSD), za pomocą którego ma zostać zweryfikowany dokument XML.</span><span class="sxs-lookup"><span data-stu-id="1fc2a-106">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1fc2a-107">Przestrzeń nazw <xref:System.Xml.Schema> zawiera metody rozszerzające, które ułatwiają Weryfikowanie drzewa XML względem pliku XSD przy użyciu [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1fc2a-107">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="1fc2a-108">Aby uzyskać więcej informacji na temat sprawdzania poprawności dokumentów XML za pomocą LINQ to XML, zobacz [How to Validate using XSDC#(LINQ to XML) ()](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) i [How to: Validate using XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1fc2a-108">For more information on validating XML documents with LINQ to XML, see [How to validate using XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and [How to: Validate Using XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span></span>
  
 <span data-ttu-id="1fc2a-109">Pojedynczy schemat lub zestaw schematów (jako <xref:System.Xml.Schema.XmlSchemaSet>) można dodać do <xref:System.Xml.Schema.XmlSchemaSet>, przekazując jeden jako parametr do metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="1fc2a-109">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="1fc2a-110">Należy pamiętać, że podczas walidacji dokumentu docelowa przestrzeń nazw dokumentu musi być zgodna z docelową przestrzenią nazw schematu w zestawie schematów.</span><span class="sxs-lookup"><span data-stu-id="1fc2a-110">Note that when validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="1fc2a-111">Poniżej znajduje się przykładowy dokument XML.</span><span class="sxs-lookup"><span data-stu-id="1fc2a-111">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="1fc2a-112">Poniżej znajduje się schemat, który sprawdza poprawność przykładowego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="1fc2a-112">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="1fc2a-113">W poniższym przykładzie kodu schemat został dodany do właściwości <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> obiektu <xref:System.Xml.XmlReaderSettings>.</span><span class="sxs-lookup"><span data-stu-id="1fc2a-113">In the code example that follows, the schema above is added to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="1fc2a-114">Obiekt <xref:System.Xml.XmlReaderSettings> jest przenoszona jako parametr do metody <xref:System.Xml.XmlReader.Create%2A> obiektu <xref:System.Xml.XmlReader>, który sprawdza powyższy dokument XML.</span><span class="sxs-lookup"><span data-stu-id="1fc2a-114">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="1fc2a-115">Właściwość <xref:System.Xml.XmlReaderSettings.ValidationType%2A> obiektu <xref:System.Xml.XmlReaderSettings> jest ustawiona na `Schema` w celu wymuszenia walidacji dokumentu XML przez metodę <xref:System.Xml.XmlReader.Create%2A> obiektu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="1fc2a-115">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="1fc2a-116"><xref:System.Xml.Schema.ValidationEventHandler> jest dodawany do obiektu <xref:System.Xml.XmlReaderSettings>, aby obsłużyć wszystkie zdarzenia <xref:System.Xml.Schema.XmlSeverityType.Warning> lub <xref:System.Xml.Schema.XmlSeverityType.Error> zgłoszone przez błędy znalezione podczas procesu weryfikacji zarówno dokumentu XML, jak i schematu.</span><span class="sxs-lookup"><span data-stu-id="1fc2a-116">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1fc2a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fc2a-117">See also</span></span>

- [<span data-ttu-id="1fc2a-118">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="1fc2a-118">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="1fc2a-119">Praca ze schematami XML</span><span class="sxs-lookup"><span data-stu-id="1fc2a-119">Working with XML Schemas</span></span>](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
