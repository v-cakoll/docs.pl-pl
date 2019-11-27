---
title: Nothing i ciągi
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: dfc43748d0754f0a6a29763c42ab82d9937f89f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344295"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="b5dbf-102">Nothing i ciągi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5dbf-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="b5dbf-103">Środowisko uruchomieniowe Visual Basic i .NET Framework oceniane `Nothing` w różny sposób, gdy przejdzie do ciągów.</span><span class="sxs-lookup"><span data-stu-id="b5dbf-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="b5dbf-104">Visual Basic środowisko uruchomieniowe i .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b5dbf-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="b5dbf-105">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="b5dbf-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="b5dbf-106">Środowisko uruchomieniowe Visual Basic zwykle szacuje `Nothing` jako ciąg pusty ("").</span><span class="sxs-lookup"><span data-stu-id="b5dbf-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="b5dbf-107">.NET Framework nie jest jednak ani zgłasza wyjątek, gdy podejmowana jest próba wykonania operacji na ciągach na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="b5dbf-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5dbf-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5dbf-108">See also</span></span>

- [<span data-ttu-id="b5dbf-109">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5dbf-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
