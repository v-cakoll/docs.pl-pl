---
title: Wartości typu „type1” nie można przekonwertować na „type2”.
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: c8480c6fab2bff931950ebc21d0a8affe3c41c66
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827149"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="fae0a-102">Wartości typu „type1” nie można przekonwertować na „type2”.</span><span class="sxs-lookup"><span data-stu-id="fae0a-102">Value of type 'type1' cannot be converted to 'type2'</span></span>
<span data-ttu-id="fae0a-103">Nie można przekonwertować wartości typu 'type1' na 'Typ2'.</span><span class="sxs-lookup"><span data-stu-id="fae0a-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="fae0a-104">Właściwość "Value" umożliwia uzyskać wartość ciągu pierwszego elementu obiektu "\<parentElement >".</span><span class="sxs-lookup"><span data-stu-id="fae0a-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="fae0a-105">Podjęta próba niejawnie rzutowany literał dla określonego typu XML.</span><span class="sxs-lookup"><span data-stu-id="fae0a-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="fae0a-106">Literał XML nie może być niejawnie rzutowany na określonego typu.</span><span class="sxs-lookup"><span data-stu-id="fae0a-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="fae0a-107">**Identyfikator błędu:** BC31194</span><span class="sxs-lookup"><span data-stu-id="fae0a-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fae0a-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="fae0a-108">To correct this error</span></span>  
  
-   <span data-ttu-id="fae0a-109">Użyj `Value` właściwość literał XML, aby odwoływać się do jej wartość jako `String`.</span><span class="sxs-lookup"><span data-stu-id="fae0a-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="fae0a-110">Użyj `CType` funkcji, inny typ funkcji konwersji lub <xref:System.Convert> klasy, aby rzutować wartość jako określonego typu.</span><span class="sxs-lookup"><span data-stu-id="fae0a-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae0a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fae0a-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="fae0a-112">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="fae0a-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="fae0a-113">Literały XML</span><span class="sxs-lookup"><span data-stu-id="fae0a-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="fae0a-114">XML</span><span class="sxs-lookup"><span data-stu-id="fae0a-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
