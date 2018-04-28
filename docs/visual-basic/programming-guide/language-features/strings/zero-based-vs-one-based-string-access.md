---
title: Vs liczony od zera. Dostęp na podstawie jednego ciągu w języku Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bbc418147a83b93f94449beb607d7f6bc3eff7a2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="b7b4a-102">Vs liczony od zera. Dostęp na podstawie jednego ciągu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7b4a-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="b7b4a-103">W tym temacie porównuje jak Visual Basic i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zapewniają dostęp do znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="b7b4a-103">This topic compares how Visual Basic and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="b7b4a-104">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Zawsze zapewnia liczony od zera dostęp do znaków w ciągu, Visual Basic stanowi liczony od zera i jedynki dostęp, w zależności od funkcji.</span><span class="sxs-lookup"><span data-stu-id="b7b4a-104">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="b7b4a-105">Na podstawie jednej</span><span class="sxs-lookup"><span data-stu-id="b7b4a-105">One-Based</span></span>  
 <span data-ttu-id="b7b4a-106">Na przykład funkcję języka Visual Basic na podstawie co należy wziąć pod uwagę `Mid` funkcji.</span><span class="sxs-lookup"><span data-stu-id="b7b4a-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="b7b4a-107">Trwa argument, który wskazuje pozycję znaków, jaką rozpocznie podciąg, zaczynając od pozycji 1.</span><span class="sxs-lookup"><span data-stu-id="b7b4a-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="b7b4a-108">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Metoda przyjmuje indeksu znaku w ciągu, w którym ma rozpocząć, podciąg zaczynając od pozycji 0.</span><span class="sxs-lookup"><span data-stu-id="b7b4a-108">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="b7b4a-109">W związku z tym, jeśli masz ciąg "ABCDE" poszczególnych znaków są numerowane 1,2,3,4,5 do użytku z `Mid` funkcji, ale 0,1,2,3,4 do użytku z <xref:System.String.Substring%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b7b4a-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="b7b4a-110">Liczony od zera</span><span class="sxs-lookup"><span data-stu-id="b7b4a-110">Zero-Based</span></span>  
 <span data-ttu-id="b7b4a-111">Na przykład liczony od zera funkcja języka Visual Basic, należy wziąć pod uwagę `Split` funkcji.</span><span class="sxs-lookup"><span data-stu-id="b7b4a-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="b7b4a-112">Dzieli się ciągiem, a zwraca tablicę zawierającą podciągów.</span><span class="sxs-lookup"><span data-stu-id="b7b4a-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="b7b4a-113">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Metoda również dzieli się ciągiem i zwraca tablicę zawierającą podciągów.</span><span class="sxs-lookup"><span data-stu-id="b7b4a-113">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="b7b4a-114">Ponieważ `Split` funkcji i <xref:System.String.Split%2A> metody zwracany [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tablic, muszą być liczony od zera.</span><span class="sxs-lookup"><span data-stu-id="b7b4a-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b4a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7b4a-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [<span data-ttu-id="b7b4a-116">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7b4a-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
