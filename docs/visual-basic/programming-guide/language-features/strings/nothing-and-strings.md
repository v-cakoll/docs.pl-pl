---
title: Nothing i ciągi w Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d7693e712884a500495e4573900e7d9a049c2879
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="47fae-102">Nothing i ciągi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47fae-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="47fae-103">Środowisko uruchomieniowe Visual Basic i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] oceny `Nothing` inaczej po przejściu do ciągów.</span><span class="sxs-lookup"><span data-stu-id="47fae-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="47fae-104">Środowisko uruchomieniowe Visual Basic i .NET Framework</span><span class="sxs-lookup"><span data-stu-id="47fae-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="47fae-105">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="47fae-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 <span data-ttu-id="47fae-106">Środowisko uruchomieniowe Visual Basic zazwyczaj ocenia `Nothing` jako ciąg pusty ("").</span><span class="sxs-lookup"><span data-stu-id="47fae-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="47fae-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Nie zawiera i zgłasza wyjątek, gdy jest podejmowana próba wykonania operacji ciągu na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="47fae-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47fae-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47fae-108">See Also</span></span>  
 [<span data-ttu-id="47fae-109">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47fae-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
