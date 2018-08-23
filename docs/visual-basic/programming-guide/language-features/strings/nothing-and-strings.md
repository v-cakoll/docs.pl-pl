---
title: Nothing i ciągi w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: d03781209f0f9b021d540bd251c6c6025ad21422
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42751944"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="c004d-102">Nothing i ciągi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c004d-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="c004d-103">Środowisko uruchomieniowe języka Visual Basic i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] oceny `Nothing` inaczej kiedy chodzi o ciągów.</span><span class="sxs-lookup"><span data-stu-id="c004d-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="c004d-104">Środowisko uruchomieniowe języka Visual Basic i .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c004d-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="c004d-105">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="c004d-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 <span data-ttu-id="c004d-106">Środowisko uruchomieniowe języka Visual Basic zazwyczaj ocenia `Nothing` jako ciąg pusty ("").</span><span class="sxs-lookup"><span data-stu-id="c004d-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="c004d-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Nie zawiera i zgłasza wyjątek, zawsze wtedy, gdy podejmowana jest próba wykonania operacji ciągu na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c004d-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c004d-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c004d-108">See Also</span></span>  
 [<span data-ttu-id="c004d-109">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c004d-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
