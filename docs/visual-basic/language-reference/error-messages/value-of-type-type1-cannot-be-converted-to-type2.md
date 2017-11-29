---
title: "Wartość typu &#39; type1 &#39; Nie można przekonwertować na &#39; type2 &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords: BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: efa6fcd4d996fb3277cc4cac2af16a86a2d65977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a><span data-ttu-id="c406c-102">Wartość typu &#39; type1 &#39; Nie można przekonwertować na &#39; type2 &#39;</span><span class="sxs-lookup"><span data-stu-id="c406c-102">Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39;</span></span>
<span data-ttu-id="c406c-103">Nie można przekonwertować wartości typu "type1" na "type2".</span><span class="sxs-lookup"><span data-stu-id="c406c-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="c406c-104">Można użyć właściwości 'Value' można uzyskać wartość ciągu pierwszego elementu obiektu "\<parentElement >".</span><span class="sxs-lookup"><span data-stu-id="c406c-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="c406c-105">Nastąpiła próba niejawnie rzutować literału dla określonego typu XML.</span><span class="sxs-lookup"><span data-stu-id="c406c-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="c406c-106">Literał XML nie można rzutować niejawnie do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="c406c-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="c406c-107">**Identyfikator błędu:** BC31194</span><span class="sxs-lookup"><span data-stu-id="c406c-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c406c-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c406c-108">To correct this error</span></span>  
  
-   <span data-ttu-id="c406c-109">Użyj `Value` właściwość literału XML odwoływać się do jego wartości jako `String`.</span><span class="sxs-lookup"><span data-stu-id="c406c-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="c406c-110">Użyj `CType` funkcji, funkcji konwersji innego typu, lub <xref:System.Convert> klasy można rzutować wartości jako określonego typu.</span><span class="sxs-lookup"><span data-stu-id="c406c-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c406c-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c406c-111">See Also</span></span>  
 <xref:System.Convert>  
 [<span data-ttu-id="c406c-112">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="c406c-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="c406c-113">Literały XML</span><span class="sxs-lookup"><span data-stu-id="c406c-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="c406c-114">XML</span><span class="sxs-lookup"><span data-stu-id="c406c-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
