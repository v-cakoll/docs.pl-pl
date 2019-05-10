---
title: 'Instrukcje: Ładowanie kodu XML z pliku, ciągu lub Stream (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 097c766fc9efbc810859ab693d3b26f5c1db57ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598334"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="8e163-102">Instrukcje: Ładowanie kodu XML z pliku, ciągu lub Stream (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e163-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>
<span data-ttu-id="8e163-103">Możesz utworzyć [literałów XML](../../../../visual-basic/language-reference/xml-literals/index.md) i wypełnić je przy użyciu zawartości ze źródła zewnętrznego pliku, ciągu lub strumienia za pomocą kilku metod.</span><span class="sxs-lookup"><span data-stu-id="8e163-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="8e163-104">W poniższych przykładach przedstawiono te metody.</span><span class="sxs-lookup"><span data-stu-id="8e163-104">These methods are shown in the following examples.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a><span data-ttu-id="8e163-105">Aby załadować XML z pliku</span><span class="sxs-lookup"><span data-stu-id="8e163-105">To load XML from a file</span></span>  
  
- <span data-ttu-id="8e163-106">Aby wypełnić literał, takich jak XML <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt z pliku, użyj `Load` metody.</span><span class="sxs-lookup"><span data-stu-id="8e163-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="8e163-107">Ta metoda może potrwać ścieżka do pliku, strumienia tekstu lub strumienia XML jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="8e163-107">This method can take a file path, text stream, or XML stream as input.</span></span>  
  
     <span data-ttu-id="8e163-108">Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metodę, aby wypełnić <xref:System.Xml.Linq.XDocument> obiektu z danymi XML z pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="8e163-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>  
  
     [!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]  
  
### <a name="to-load-xml-from-a-string"></a><span data-ttu-id="8e163-109">Aby załadować XML z ciągu</span><span class="sxs-lookup"><span data-stu-id="8e163-109">To load XML from a string</span></span>  
  
- <span data-ttu-id="8e163-110">Aby wypełnić literał, takich jak XML <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt z ciągu, można użyć `Parse` metody.</span><span class="sxs-lookup"><span data-stu-id="8e163-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>  
  
     <span data-ttu-id="8e163-111">Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metodę, aby wypełnić <xref:System.Xml.Linq.XDocument> obiektu z danymi XML z ciągu.</span><span class="sxs-lookup"><span data-stu-id="8e163-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>  
  
     [!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]  
  
### <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="8e163-112">Aby załadować XML ze strumienia</span><span class="sxs-lookup"><span data-stu-id="8e163-112">To load XML from a stream</span></span>  
  
- <span data-ttu-id="8e163-113">Do wypełniania literał, takich jak XML <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektów ze strumienia, możesz użyć `Load` metody lub <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8e163-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="8e163-114">Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XNode.ReadFrom%2A> metodę, aby wypełnić <xref:System.Xml.Linq.XDocument> obiektu z danymi XML ze strumienia XML.</span><span class="sxs-lookup"><span data-stu-id="8e163-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>  
  
 [!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="8e163-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e163-115">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8e163-116">Literały XML</span><span class="sxs-lookup"><span data-stu-id="8e163-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="8e163-117">XML</span><span class="sxs-lookup"><span data-stu-id="8e163-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="8e163-118">Manipulowanie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e163-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
