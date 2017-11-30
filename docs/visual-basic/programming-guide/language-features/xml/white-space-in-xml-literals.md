---
title: "Odstęp w literałach XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d8587abb98fe33ab2c5a0cef6cea76049a00909e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="cd5d8-102">Odstęp w literałach XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd5d8-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="cd5d8-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora zawiera znaki znaczące białe literał XML podczas tworzenia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu.</span><span class="sxs-lookup"><span data-stu-id="cd5d8-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="cd5d8-104">Nie są włączane znaków nieznaczne biały znak.</span><span class="sxs-lookup"><span data-stu-id="cd5d8-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="cd5d8-105">Znaczące i nieznaczne biały znak</span><span class="sxs-lookup"><span data-stu-id="cd5d8-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="cd5d8-106">Białe znaki w literałach XML są znaczące tylko trzech obszarach:</span><span class="sxs-lookup"><span data-stu-id="cd5d8-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="cd5d8-107">Gdy są one w wartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cd5d8-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="cd5d8-108">Gdy są one częścią zawartości tekstowej elementu i tekst zawiera również inne znaki.</span><span class="sxs-lookup"><span data-stu-id="cd5d8-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="cd5d8-109">Gdy są one osadzone wyrażenia dla zawartości tekstowej elementu.</span><span class="sxs-lookup"><span data-stu-id="cd5d8-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="cd5d8-110">W przeciwnym razie kompilator traktuje jako nieważny białych znaków i nie obejmuje następnie w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu dla literału.</span><span class="sxs-lookup"><span data-stu-id="cd5d8-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="cd5d8-111">Aby uwzględnić nieważny biały znak w literał XML, użyj wyrażenia osadzonego, który zawiera ciąg literału z białą przestrzenią.</span><span class="sxs-lookup"><span data-stu-id="cd5d8-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd5d8-112">Jeśli `xml:space` atrybut występuje w elemencie XML literału, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora zawiera atrybut w <xref:System.Xml.Linq.XElement> obiekt, ale dodanie tego atrybutu nie zmienia sposób kompilator traktuje biały znak.</span><span class="sxs-lookup"><span data-stu-id="cd5d8-112">If the `xml:space` attribute appears in an XML element literal, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cd5d8-113">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cd5d8-113">Examples</span></span>  
 <span data-ttu-id="cd5d8-114">Poniższy przykład zawiera dwa elementy XML zewnętrznych i wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="cd5d8-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="cd5d8-115">Oba elementy zawierają biały znak w ich zawartości tekstowej.</span><span class="sxs-lookup"><span data-stu-id="cd5d8-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="cd5d8-116">Biały znak w elemencie zewnętrzne jest nieważny, ponieważ zawiera tylko biały znak i jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="cd5d8-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="cd5d8-117">Biały znak w elemencie wewnętrzny jest ważna, ponieważ zawiera białe i tekst.</span><span class="sxs-lookup"><span data-stu-id="cd5d8-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 <span data-ttu-id="cd5d8-118">Podczas uruchamiania, ten kod wyświetla następujący tekst.</span><span class="sxs-lookup"><span data-stu-id="cd5d8-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd5d8-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd5d8-119">See Also</span></span>  
 [<span data-ttu-id="cd5d8-120">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cd5d8-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
