---
title: Nothing i ciągi w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 873c4e40a0b12dd657d3294785e04dd9efc23956
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967990"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="124e3-102">Nothing i ciągi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="124e3-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="124e3-103">Środowisko uruchomieniowe języka Visual Basic i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] oceny `Nothing` inaczej kiedy chodzi o ciągów.</span><span class="sxs-lookup"><span data-stu-id="124e3-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="124e3-104">Środowisko uruchomieniowe języka Visual Basic i .NET Framework</span><span class="sxs-lookup"><span data-stu-id="124e3-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="124e3-105">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="124e3-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="124e3-106">Środowisko uruchomieniowe języka Visual Basic zazwyczaj ocenia `Nothing` jako ciąg pusty ("").</span><span class="sxs-lookup"><span data-stu-id="124e3-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="124e3-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Nie zawiera i zgłasza wyjątek, zawsze wtedy, gdy podejmowana jest próba wykonania operacji ciągu na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="124e3-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="124e3-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="124e3-108">See also</span></span>
- [<span data-ttu-id="124e3-109">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="124e3-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
