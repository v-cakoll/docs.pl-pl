---
title: Wartości typu „type1” nie można przekonwertować na „type2”.
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: f19f157bd4c76f481aa3232bc33c2a0c6ac21367
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400282"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="5c87a-102">Wartości typu „type1” nie można przekonwertować na „type2”.</span><span class="sxs-lookup"><span data-stu-id="5c87a-102">Value of type 'type1' cannot be converted to 'type2'</span></span>
<span data-ttu-id="5c87a-103">Nie można przekonwertować wartości typu "type1" na "type2".</span><span class="sxs-lookup"><span data-stu-id="5c87a-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="5c87a-104">Za pomocą właściwości "value" można uzyskać wartość ciągu pierwszego elementu " \<parentElement> ".</span><span class="sxs-lookup"><span data-stu-id="5c87a-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="5c87a-105">Podjęto próbę niejawnego rzutowania literału XML na konkretny typ.</span><span class="sxs-lookup"><span data-stu-id="5c87a-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="5c87a-106">Literału XML nie można rzutować niejawnie na określony typ.</span><span class="sxs-lookup"><span data-stu-id="5c87a-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="5c87a-107">**Identyfikator błędu:** BC31194</span><span class="sxs-lookup"><span data-stu-id="5c87a-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5c87a-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="5c87a-108">To correct this error</span></span>  
  
- <span data-ttu-id="5c87a-109">Użyj `Value` Właściwości literału XML, aby odwołać się do jej wartości jako `String` .</span><span class="sxs-lookup"><span data-stu-id="5c87a-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="5c87a-110">Użyj `CType` funkcji, innej funkcji konwersji typu lub <xref:System.Convert> klasy do rzutowania wartości jako określonego typu.</span><span class="sxs-lookup"><span data-stu-id="5c87a-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c87a-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c87a-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="5c87a-112">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="5c87a-112">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="5c87a-113">Literały XML</span><span class="sxs-lookup"><span data-stu-id="5c87a-113">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="5c87a-114">XML</span><span class="sxs-lookup"><span data-stu-id="5c87a-114">XML</span></span>](../../programming-guide/language-features/xml/index.md)
