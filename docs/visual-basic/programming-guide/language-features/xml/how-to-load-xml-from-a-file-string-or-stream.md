---
title: 'Porady: ładowanie XML z pliku, ciągu lub strumienia'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7f2a961ebb7ecd4fc0512e141b4a437be87bec0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392291"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="9c980-102">Porady: ładowanie XML z pliku, ciągu lub strumienia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c980-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>

<span data-ttu-id="9c980-103">Można tworzyć [literały XML](../../../language-reference/xml-literals/index.md) i wypełniać je zawartością z zewnętrznego źródła, takiego jak plik, ciąg lub strumień, przy użyciu kilku metod.</span><span class="sxs-lookup"><span data-stu-id="9c980-103">You can create [XML Literals](../../../language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="9c980-104">Te metody przedstawiono w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="9c980-104">These methods are shown in the following examples.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a><span data-ttu-id="9c980-105">Aby załadować plik XML z pliku</span><span class="sxs-lookup"><span data-stu-id="9c980-105">To load XML from a file</span></span>

<span data-ttu-id="9c980-106">Aby wypełnić literał XML, taki jak <xref:System.Xml.Linq.XElement> obiekt lub <xref:System.Xml.Linq.XDocument> z pliku, należy użyć `Load` metody.</span><span class="sxs-lookup"><span data-stu-id="9c980-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="9c980-107">Ta metoda może przyjmować ścieżkę pliku, strumień tekstowy lub strumień XML jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="9c980-107">This method can take a file path, text stream, or XML stream as input.</span></span>

<span data-ttu-id="9c980-108">Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metody do wypełniania <xref:System.Xml.Linq.XDocument> obiektu atrybutem XML z pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="9c980-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a><span data-ttu-id="9c980-109">Aby załadować XML z ciągu</span><span class="sxs-lookup"><span data-stu-id="9c980-109">To load XML from a string</span></span>

<span data-ttu-id="9c980-110">Aby wypełnić literał XML, taki jak <xref:System.Xml.Linq.XElement> obiekt lub <xref:System.Xml.Linq.XDocument> z ciągu, można użyć `Parse` metody.</span><span class="sxs-lookup"><span data-stu-id="9c980-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>

<span data-ttu-id="9c980-111">Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metody do wypełniania <xref:System.Xml.Linq.XDocument> obiektu atrybutem XML z ciągu.</span><span class="sxs-lookup"><span data-stu-id="9c980-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="9c980-112">Aby załadować plik XML ze strumienia</span><span class="sxs-lookup"><span data-stu-id="9c980-112">To load XML from a stream</span></span>

<span data-ttu-id="9c980-113">Aby wypełnić literał XML, taki jak <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt ze strumienia, można użyć `Load` metody lub <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9c980-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="9c980-114">Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody do wypełnienia <xref:System.Xml.Linq.XDocument> obiektu z XML ze strumienia XML.</span><span class="sxs-lookup"><span data-stu-id="9c980-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a><span data-ttu-id="9c980-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c980-115">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9c980-116">Literały XML</span><span class="sxs-lookup"><span data-stu-id="9c980-116">XML Literals</span></span>](../../../language-reference/xml-literals/index.md)
- [<span data-ttu-id="9c980-117">XML</span><span class="sxs-lookup"><span data-stu-id="9c980-117">XML</span></span>](index.md)
- [<span data-ttu-id="9c980-118">Manipulowanie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c980-118">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
