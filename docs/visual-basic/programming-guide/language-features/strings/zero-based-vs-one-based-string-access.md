---
title: "Vs liczony od zera. Dostęp na podstawie jednego ciągu w języku Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 911f063d6ca9a3f5d88a1f50d9df7f908a488f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="0a0d2-102">Vs liczony od zera. Dostęp na podstawie jednego ciągu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a0d2-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="0a0d2-103">W tym temacie porównuje jak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zapewniają dostęp do znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-103">This topic compares how [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="0a0d2-104">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Zawsze zapewnia liczony od zera dostęp do znaków w ciągu, podczas gdy [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zapewnia dostęp liczony od zera i jedynki, w zależności od funkcji.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-104">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] always provides zero-based access to the characters in a string, whereas [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="0a0d2-105">Na podstawie jednej</span><span class="sxs-lookup"><span data-stu-id="0a0d2-105">One-Based</span></span>  
 <span data-ttu-id="0a0d2-106">Na przykład na podstawie jednej [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] działać, należy wziąć pod uwagę `Mid` funkcji.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-106">For an example of a one-based [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function, consider the `Mid` function.</span></span> <span data-ttu-id="0a0d2-107">Trwa argument, który wskazuje pozycję znaków, jaką rozpocznie podciąg, zaczynając od pozycji 1.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="0a0d2-108">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Metoda przyjmuje indeksu znaku w ciągu, w którym ma rozpocząć, podciąg zaczynając od pozycji 0.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-108">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="0a0d2-109">W związku z tym, jeśli masz ciąg "ABCDE" poszczególnych znaków są numerowane 1,2,3,4,5 do użytku z `Mid` funkcji, ale 0,1,2,3,4 do użytku z <xref:System.String.Substring%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="0a0d2-110">Liczony od zera</span><span class="sxs-lookup"><span data-stu-id="0a0d2-110">Zero-Based</span></span>  
 <span data-ttu-id="0a0d2-111">Przykład liczony od zera [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] działać, należy wziąć pod uwagę `Split` funkcji.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-111">For an example of a zero-based [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function, consider the `Split` function.</span></span> <span data-ttu-id="0a0d2-112">Dzieli się ciągiem, a zwraca tablicę zawierającą podciągów.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="0a0d2-113">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Metoda również dzieli się ciągiem i zwraca tablicę zawierającą podciągów.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-113">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="0a0d2-114">Ponieważ `Split` funkcji i <xref:System.String.Split%2A> metody zwracany [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tablic, muszą być liczony od zera.</span><span class="sxs-lookup"><span data-stu-id="0a0d2-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a0d2-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a0d2-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [<span data-ttu-id="0a0d2-116">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a0d2-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
