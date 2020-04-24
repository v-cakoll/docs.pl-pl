---
title: Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 709ad98bbac6c8a1b97f884b09e7e91da0566fda
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135883"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="ff911-102">Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="ff911-102">XML Schema (XSD) Validation with XmlSchemaSet</span></span>
<span data-ttu-id="ff911-103">Dokumenty XML można sprawdzić pod kątem schematu języka definicji schematu XML (XSD) w <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ff911-103">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="ff911-104">Sprawdzanie poprawności dokumentów XML</span><span class="sxs-lookup"><span data-stu-id="ff911-104">Validating XML Documents</span></span>  
 <span data-ttu-id="ff911-105">Dokumenty XML są sprawdzane za <xref:System.Xml.XmlReader.Create%2A> pomocą metody <xref:System.Xml.XmlReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="ff911-105">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="ff911-106">Aby sprawdzić poprawność dokumentu XML, <xref:System.Xml.XmlReaderSettings> Utwórz obiekt, który zawiera schemat języka definicji schematu XML (XSD), za pomocą którego można sprawdzić poprawność dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ff911-106">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff911-107">Przestrzeń nazw zawiera metody rozszerzające, które ułatwiają Weryfikowanie drzewa XML względem pliku XSD przy użyciu [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [LINQ to XML (Visual Basic).](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) <xref:System.Xml.Schema></span><span class="sxs-lookup"><span data-stu-id="ff911-107">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="ff911-108">Aby uzyskać więcej informacji na temat walidacji dokumentów XML za pomocą LINQ to XML, zobacz [How to Validate using XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) i [How to: Validate using XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ff911-108">For more information on validating XML documents with LINQ to XML, see [How to validate using XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and [How to: Validate Using XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span></span>
  
 <span data-ttu-id="ff911-109">Pojedynczy schemat <xref:System.Xml.Schema.XmlSchemaSet>lub zestaw schematów (jako) można dodać do obiektu <xref:System.Xml.Schema.XmlSchemaSet> , przekazując jeden jako parametr do <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody. <xref:System.Xml.Schema.XmlSchemaSet></span><span class="sxs-lookup"><span data-stu-id="ff911-109">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="ff911-110">Należy pamiętać, że podczas walidacji dokumentu docelowa przestrzeń nazw dokumentu musi być zgodna z docelową przestrzenią nazw schematu w zestawie schematów.</span><span class="sxs-lookup"><span data-stu-id="ff911-110">Note that when validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="ff911-111">Poniżej znajduje się przykładowy dokument XML.</span><span class="sxs-lookup"><span data-stu-id="ff911-111">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="ff911-112">Poniżej znajduje się schemat, który sprawdza poprawność przykładowego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ff911-112">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="ff911-113">W poniższym przykładzie kodu schemat został dodany do <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwości <xref:System.Xml.XmlReaderSettings> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ff911-113">In the code example that follows, the schema above is added to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="ff911-114"><xref:System.Xml.XmlReaderSettings> Obiekt jest przekazaniem jako parametr do <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> obiektu, który sprawdza powyższy dokument XML.</span><span class="sxs-lookup"><span data-stu-id="ff911-114">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="ff911-115"><xref:System.Xml.XmlReaderSettings.ValidationType%2A> Właściwość <xref:System.Xml.XmlReaderSettings> obiektu jest ustawiona na `Schema` tak, aby wymuszać walidację dokumentu XML przez <xref:System.Xml.XmlReader.Create%2A> metodę <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ff911-115">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="ff911-116">Element <xref:System.Xml.Schema.ValidationEventHandler> jest dodawany do <xref:System.Xml.XmlReaderSettings> obiektu, aby obsłużyć dowolne <xref:System.Xml.Schema.XmlSeverityType.Warning> lub <xref:System.Xml.Schema.XmlSeverityType.Error> zdarzenia zgłoszone przez błędy znalezione podczas procesu weryfikacji zarówno dokumentu XML, jak i schematu.</span><span class="sxs-lookup"><span data-stu-id="ff911-116">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ff911-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff911-117">See also</span></span>

- [<span data-ttu-id="ff911-118">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="ff911-118">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="ff911-119">Praca ze schematami XML</span><span class="sxs-lookup"><span data-stu-id="ff911-119">Working with XML Schemas</span></span>](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
