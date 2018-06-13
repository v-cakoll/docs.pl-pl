---
title: Wartości typu &#39;type1&#39; nie można przekonwertować na &#39;type2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 9e59d3bc5e2bfca3628248d08ffc475334d4da79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602765"
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a><span data-ttu-id="386cc-102">Wartości typu &#39;type1&#39; nie można przekonwertować na &#39;type2&#39;</span><span class="sxs-lookup"><span data-stu-id="386cc-102">Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39;</span></span>
<span data-ttu-id="386cc-103">Nie można przekonwertować wartości typu "type1" na "type2".</span><span class="sxs-lookup"><span data-stu-id="386cc-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="386cc-104">Można użyć właściwości 'Value' można uzyskać wartość ciągu pierwszego elementu obiektu "\<parentElement >".</span><span class="sxs-lookup"><span data-stu-id="386cc-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="386cc-105">Nastąpiła próba niejawnie rzutować literału dla określonego typu XML.</span><span class="sxs-lookup"><span data-stu-id="386cc-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="386cc-106">Literał XML nie można rzutować niejawnie do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="386cc-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="386cc-107">**Identyfikator błędu:** BC31194</span><span class="sxs-lookup"><span data-stu-id="386cc-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="386cc-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="386cc-108">To correct this error</span></span>  
  
-   <span data-ttu-id="386cc-109">Użyj `Value` właściwość literału XML odwoływać się do jego wartości jako `String`.</span><span class="sxs-lookup"><span data-stu-id="386cc-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="386cc-110">Użyj `CType` funkcji, funkcji konwersji innego typu, lub <xref:System.Convert> klasy można rzutować wartości jako określonego typu.</span><span class="sxs-lookup"><span data-stu-id="386cc-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="386cc-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="386cc-111">See Also</span></span>  
 <xref:System.Convert>  
 [<span data-ttu-id="386cc-112">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="386cc-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="386cc-113">Literały XML</span><span class="sxs-lookup"><span data-stu-id="386cc-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="386cc-114">XML</span><span class="sxs-lookup"><span data-stu-id="386cc-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
