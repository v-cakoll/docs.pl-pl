---
title: 'Porady: ładowanie XML z pliku, ciągu lub strumienia'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7a2a0513a066ae8ea8a70f7a5ae340ab29de7d25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330959"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="55557-102">Porady: ładowanie XML z pliku, ciągu lub strumienia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55557-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>

<span data-ttu-id="55557-103">Można tworzyć [literały XML](../../../../visual-basic/language-reference/xml-literals/index.md) i wypełniać je zawartością z zewnętrznego źródła, takiego jak plik, ciąg lub strumień, przy użyciu kilku metod.</span><span class="sxs-lookup"><span data-stu-id="55557-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="55557-104">Te metody przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="55557-104">These methods are shown in the following examples.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a><span data-ttu-id="55557-105">Aby załadować plik XML z pliku</span><span class="sxs-lookup"><span data-stu-id="55557-105">To load XML from a file</span></span>

<span data-ttu-id="55557-106">Aby wypełnić literał XML, taki jak obiekt <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> z pliku, należy użyć metody `Load`.</span><span class="sxs-lookup"><span data-stu-id="55557-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="55557-107">Ta metoda może przyjmować ścieżkę pliku, strumień tekstowy lub strumień XML jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="55557-107">This method can take a file path, text stream, or XML stream as input.</span></span>

<span data-ttu-id="55557-108">Poniższy przykład kodu pokazuje użycie metody <xref:System.Xml.Linq.XDocument.Load%28System.String%29> do wypełnienia obiektu <xref:System.Xml.Linq.XDocument> z XML z pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="55557-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a><span data-ttu-id="55557-109">Aby załadować XML z ciągu</span><span class="sxs-lookup"><span data-stu-id="55557-109">To load XML from a string</span></span>

<span data-ttu-id="55557-110">Aby wypełnić literał XML, taki jak obiekt <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> z ciągu, można użyć metody `Parse`.</span><span class="sxs-lookup"><span data-stu-id="55557-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>

<span data-ttu-id="55557-111">Poniższy przykład kodu pokazuje użycie metody <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType>, aby wypełnić obiekt <xref:System.Xml.Linq.XDocument> z XML z ciągu.</span><span class="sxs-lookup"><span data-stu-id="55557-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="55557-112">Aby załadować plik XML ze strumienia</span><span class="sxs-lookup"><span data-stu-id="55557-112">To load XML from a stream</span></span>

<span data-ttu-id="55557-113">Aby wypełnić literał XML, taki jak obiekt <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> ze strumienia, można użyć metody `Load` lub metody <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="55557-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="55557-114">Poniższy przykład kodu pokazuje użycie metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> do wypełnienia obiektu <xref:System.Xml.Linq.XDocument> z XML ze strumienia XML.</span><span class="sxs-lookup"><span data-stu-id="55557-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a><span data-ttu-id="55557-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55557-115">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="55557-116">Literały XML</span><span class="sxs-lookup"><span data-stu-id="55557-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="55557-117">XML</span><span class="sxs-lookup"><span data-stu-id="55557-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="55557-118">Manipulowanie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55557-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
