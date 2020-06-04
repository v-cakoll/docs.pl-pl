---
title: Nothing i ciągi
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 392de45b0ee1688224f3e8170b0144f1acdb0912
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360569"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="fb414-102">Nothing i ciągi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb414-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="fb414-103">Środowisko uruchomieniowe Visual Basic i .NET Framework są oceniane w `Nothing` różny sposób, gdy przejdzie do ciągów.</span><span class="sxs-lookup"><span data-stu-id="fb414-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="fb414-104">Visual Basic środowisko uruchomieniowe i .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fb414-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="fb414-105">Rozpatrzmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="fb414-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="fb414-106">Środowisko uruchomieniowe Visual Basic zwykle jest obliczane `Nothing` jako ciąg pusty ("").</span><span class="sxs-lookup"><span data-stu-id="fb414-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="fb414-107">.NET Framework nie jest jednak ani zgłasza wyjątek, gdy podejmowana jest próba wykonania operacji na ciągach `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="fb414-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb414-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb414-108">See also</span></span>

- [<span data-ttu-id="fb414-109">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb414-109">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
