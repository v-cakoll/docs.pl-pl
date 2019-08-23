---
title: Odstęp w literałach XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: f72dcc25b158d793850069e5cc32c3a3c02fad17
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939211"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="a1397-102">Odstęp w literałach XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1397-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="a1397-103">Kompilator Visual Basic obejmuje tylko znaczące białe znaki ze literału XML podczas tworzenia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu.</span><span class="sxs-lookup"><span data-stu-id="a1397-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="a1397-104">Nieznaczące białe znaki nie są dołączone.</span><span class="sxs-lookup"><span data-stu-id="a1397-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="a1397-105">Znaczący i nieznaczący biały znak</span><span class="sxs-lookup"><span data-stu-id="a1397-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="a1397-106">Znaki białych znaków w literałach XML są znaczące tylko w trzech obszarach:</span><span class="sxs-lookup"><span data-stu-id="a1397-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
- <span data-ttu-id="a1397-107">Gdy znajdują się w wartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a1397-107">When they are in an attribute value.</span></span>  
  
- <span data-ttu-id="a1397-108">Gdy są częścią zawartości tekstowej elementu, a tekst zawiera również inne znaki.</span><span class="sxs-lookup"><span data-stu-id="a1397-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
- <span data-ttu-id="a1397-109">Gdy znajdują się w osadzonym wyrażeniu dla zawartości tekstowej elementu.</span><span class="sxs-lookup"><span data-stu-id="a1397-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="a1397-110">W przeciwnym razie kompilator traktuje znaki odstępu jako nieważne i nie uwzględnia następnie w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiekcie dla literału.</span><span class="sxs-lookup"><span data-stu-id="a1397-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="a1397-111">Aby uwzględnić nieznaczny biały znak w literale XML, należy użyć osadzonego wyrażenia zawierającego literał ciągu z białym znakiem.</span><span class="sxs-lookup"><span data-stu-id="a1397-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1397-112">Jeśli atrybut pojawia się w literale elementu XML, kompilator Visual Basic zawiera atrybut <xref:System.Xml.Linq.XElement> w obiekcie, ale dodanie tego atrybutu nie zmienia, jak kompilator traktuje biały znak. `xml:space`</span><span class="sxs-lookup"><span data-stu-id="a1397-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a1397-113">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a1397-113">Examples</span></span>  
 <span data-ttu-id="a1397-114">Poniższy przykład zawiera dwa elementy XML, zewnętrzne i wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="a1397-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="a1397-115">Oba elementy zawierają biały znak w zawartości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="a1397-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="a1397-116">Biały znak w elemencie zewnętrznym jest nieistotny, ponieważ zawiera tylko białe znaki i element XML.</span><span class="sxs-lookup"><span data-stu-id="a1397-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="a1397-117">Biały znak w elemencie wewnętrznym jest znaczący, ponieważ zawiera biały znak i tekst.</span><span class="sxs-lookup"><span data-stu-id="a1397-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 <span data-ttu-id="a1397-118">Po uruchomieniu ten kod wyświetla następujący tekst.</span><span class="sxs-lookup"><span data-stu-id="a1397-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1397-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1397-119">See also</span></span>

- [<span data-ttu-id="a1397-120">Tworzenie kodu XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1397-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
