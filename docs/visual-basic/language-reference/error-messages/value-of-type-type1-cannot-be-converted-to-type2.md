---
title: Wartości typu &#39;type1&#39; nie można przekonwertować na &#39;Typ2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 657e0feb675e15b9ece00d40c3d1ebe932a29099
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568296"
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a><span data-ttu-id="9d275-102">Wartości typu &#39;type1&#39; nie można przekonwertować na &#39;Typ2&#39;</span><span class="sxs-lookup"><span data-stu-id="9d275-102">Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39;</span></span>
<span data-ttu-id="9d275-103">Nie można przekonwertować wartości typu 'type1' na 'Typ2'.</span><span class="sxs-lookup"><span data-stu-id="9d275-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="9d275-104">Właściwość "Value" umożliwia uzyskać wartość ciągu pierwszego elementu obiektu "\<parentElement >".</span><span class="sxs-lookup"><span data-stu-id="9d275-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="9d275-105">Podjęta próba niejawnie rzutowany literał dla określonego typu XML.</span><span class="sxs-lookup"><span data-stu-id="9d275-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="9d275-106">Literał XML nie może być niejawnie rzutowany na określonego typu.</span><span class="sxs-lookup"><span data-stu-id="9d275-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="9d275-107">**Identyfikator błędu:** BC31194</span><span class="sxs-lookup"><span data-stu-id="9d275-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9d275-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9d275-108">To correct this error</span></span>  
  
-   <span data-ttu-id="9d275-109">Użyj `Value` właściwość literał XML, aby odwoływać się do jej wartość jako `String`.</span><span class="sxs-lookup"><span data-stu-id="9d275-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="9d275-110">Użyj `CType` funkcji, inny typ funkcji konwersji lub <xref:System.Convert> klasy, aby rzutować wartość jako określonego typu.</span><span class="sxs-lookup"><span data-stu-id="9d275-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d275-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d275-111">See also</span></span>
- <xref:System.Convert>
- [<span data-ttu-id="9d275-112">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="9d275-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="9d275-113">Literały XML</span><span class="sxs-lookup"><span data-stu-id="9d275-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="9d275-114">XML</span><span class="sxs-lookup"><span data-stu-id="9d275-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
