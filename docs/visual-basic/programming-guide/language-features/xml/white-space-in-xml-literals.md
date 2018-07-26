---
title: Odstęp w literałach XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 60ee90c69aeda38f95107a6043801a4994972079
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245162"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="cd7c5-102">Odstęp w literałach XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd7c5-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="cd7c5-103">Kompilator Visual Basic zawiera znaki istotnych białych literał XML podczas tworzenia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu.</span><span class="sxs-lookup"><span data-stu-id="cd7c5-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="cd7c5-104">Znaki nieważny biały znak nie są włączone.</span><span class="sxs-lookup"><span data-stu-id="cd7c5-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="cd7c5-105">Znaczące i nieznaczne biały</span><span class="sxs-lookup"><span data-stu-id="cd7c5-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="cd7c5-106">Białych znaków w literałach XML są znaczące tylko dla trzech obszarach:</span><span class="sxs-lookup"><span data-stu-id="cd7c5-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="cd7c5-107">Gdy są one w wartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cd7c5-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="cd7c5-108">Gdy są one częścią zawartości tekstowej elementu i tekst zawiera również inne znaki.</span><span class="sxs-lookup"><span data-stu-id="cd7c5-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="cd7c5-109">Gdy są one osadzone wyrażenia dla zawartości tekstowej elementu.</span><span class="sxs-lookup"><span data-stu-id="cd7c5-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="cd7c5-110">W przeciwnym razie kompilator traktuje znaki odstępu jako nieważny i nie dołącza następnie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu dla literału.</span><span class="sxs-lookup"><span data-stu-id="cd7c5-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="cd7c5-111">Aby dołączyć literał XML nieważny biały znak, należy użyć wyrażenia osadzone zawierającej ciąg literału z białą przestrzenią.</span><span class="sxs-lookup"><span data-stu-id="cd7c5-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd7c5-112">Jeśli `xml:space` atrybutu jest wyświetlany w literał elementu XML, kompilator języka Visual Basic zawiera atrybut w <xref:System.Xml.Linq.XElement> obiekt, ale dodanie tego atrybutu nie zmienia się jak kompilator traktuje biały znak.</span><span class="sxs-lookup"><span data-stu-id="cd7c5-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cd7c5-113">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cd7c5-113">Examples</span></span>  
 <span data-ttu-id="cd7c5-114">Poniższy przykład zawiera dwa elementy XML, zewnętrznych i wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="cd7c5-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="cd7c5-115">Oba te elementy zawierają biały znak w ich zawartości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="cd7c5-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="cd7c5-116">Odstęp w elementu zewnętrznego będzie miała znaczenia, ponieważ zawiera ona tylko białych znaków i elementem XML.</span><span class="sxs-lookup"><span data-stu-id="cd7c5-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="cd7c5-117">Biały znak w elemencie wewnętrzny jest znacząca, ponieważ zawiera ona białych znaków i tekst.</span><span class="sxs-lookup"><span data-stu-id="cd7c5-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 <span data-ttu-id="cd7c5-118">Podczas uruchamiania, ten kod wyświetla następujący tekst.</span><span class="sxs-lookup"><span data-stu-id="cd7c5-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd7c5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd7c5-119">See Also</span></span>  
 [<span data-ttu-id="cd7c5-120">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cd7c5-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
