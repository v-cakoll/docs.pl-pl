---
title: Odstęp w literałach XML
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: b3caf7ac052f3fed3fe5427da0cc96bbdd955ea6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360478"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="784e2-102">Odstęp w literałach XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="784e2-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="784e2-103">Kompilator Visual Basic obejmuje tylko znaczące białe znaki ze literału XML podczas tworzenia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu.</span><span class="sxs-lookup"><span data-stu-id="784e2-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="784e2-104">Nieznaczące białe znaki nie są dołączone.</span><span class="sxs-lookup"><span data-stu-id="784e2-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="784e2-105">Znaczący i nieznaczący biały znak</span><span class="sxs-lookup"><span data-stu-id="784e2-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="784e2-106">Znaki białych znaków w literałach XML są znaczące tylko w trzech obszarach:</span><span class="sxs-lookup"><span data-stu-id="784e2-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
- <span data-ttu-id="784e2-107">Gdy znajdują się w wartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="784e2-107">When they are in an attribute value.</span></span>  
  
- <span data-ttu-id="784e2-108">Gdy są częścią zawartości tekstowej elementu, a tekst zawiera również inne znaki.</span><span class="sxs-lookup"><span data-stu-id="784e2-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
- <span data-ttu-id="784e2-109">Gdy znajdują się w osadzonym wyrażeniu dla zawartości tekstowej elementu.</span><span class="sxs-lookup"><span data-stu-id="784e2-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="784e2-110">W przeciwnym razie kompilator traktuje znaki odstępu jako nieważne i nie uwzględnia następnie w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiekcie dla literału.</span><span class="sxs-lookup"><span data-stu-id="784e2-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="784e2-111">Aby uwzględnić nieznaczny biały znak w literale XML, należy użyć osadzonego wyrażenia zawierającego literał ciągu z białym znakiem.</span><span class="sxs-lookup"><span data-stu-id="784e2-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="784e2-112">Jeśli `xml:space` atrybut pojawia się w literale elementu XML, kompilator Visual Basic zawiera atrybut w <xref:System.Xml.Linq.XElement> obiekcie, ale dodanie tego atrybutu nie zmienia, jak kompilator traktuje biały znak.</span><span class="sxs-lookup"><span data-stu-id="784e2-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="784e2-113">Przykłady</span><span class="sxs-lookup"><span data-stu-id="784e2-113">Examples</span></span>  
 <span data-ttu-id="784e2-114">Poniższy przykład zawiera dwa elementy XML, zewnętrzne i wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="784e2-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="784e2-115">Oba elementy zawierają biały znak w zawartości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="784e2-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="784e2-116">Biały znak w elemencie zewnętrznym jest nieistotny, ponieważ zawiera tylko białe znaki i element XML.</span><span class="sxs-lookup"><span data-stu-id="784e2-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="784e2-117">Biały znak w elemencie wewnętrznym jest znaczący, ponieważ zawiera biały znak i tekst.</span><span class="sxs-lookup"><span data-stu-id="784e2-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 <span data-ttu-id="784e2-118">Po uruchomieniu ten kod wyświetla następujący tekst.</span><span class="sxs-lookup"><span data-stu-id="784e2-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="784e2-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="784e2-119">See also</span></span>

- [<span data-ttu-id="784e2-120">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="784e2-120">Creating XML in Visual Basic</span></span>](creating-xml.md)
