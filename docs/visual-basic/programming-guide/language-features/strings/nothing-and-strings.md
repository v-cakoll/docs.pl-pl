---
title: Nothing i ciągi w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 65a69861c2a74a3191a45eb782a97f289b0c0726
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574173"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="9a777-102">Nothing i ciągi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9a777-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="9a777-103">Środowisko uruchomieniowe języka Visual Basic i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] oceny `Nothing` inaczej kiedy chodzi o ciągów.</span><span class="sxs-lookup"><span data-stu-id="9a777-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="9a777-104">Środowisko uruchomieniowe języka Visual Basic i .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9a777-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="9a777-105">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="9a777-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 <span data-ttu-id="9a777-106">Środowisko uruchomieniowe języka Visual Basic zazwyczaj ocenia `Nothing` jako ciąg pusty ("").</span><span class="sxs-lookup"><span data-stu-id="9a777-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="9a777-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Nie zawiera i zgłasza wyjątek, zawsze wtedy, gdy podejmowana jest próba wykonania operacji ciągu na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9a777-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a777-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a777-108">See also</span></span>
- [<span data-ttu-id="9a777-109">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9a777-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
