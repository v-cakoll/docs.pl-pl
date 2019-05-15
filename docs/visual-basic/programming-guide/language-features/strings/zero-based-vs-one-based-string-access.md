---
title: Dostęp do ciągu liczonego od zera a Dostęp do ciągu liczonego od jednego w języku Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: cc8f286de41d7e44225e889e73ff3c7b1fdbd881
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591751"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="7ac3c-102">Dostęp do ciągu liczonego od zera a Dostęp do ciągu liczonego od jednego w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ac3c-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="7ac3c-103">W tym temacie przedstawiono porównanie, w jaki Visual Basic i .NET Framework zapewnia dostęp do znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="7ac3c-103">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="7ac3c-104">.NET Framework zawsze udostępnia liczony od zera znaków w ciągu, natomiast języka Visual Basic udostępnia liczony od zera i jednobazowa, w zależności od funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ac3c-104">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="7ac3c-105">Liczonego od jednego</span><span class="sxs-lookup"><span data-stu-id="7ac3c-105">One-Based</span></span>  
 <span data-ttu-id="7ac3c-106">Na przykład funkcję liczonego od jednego języka Visual Basic należy wziąć pod uwagę `Mid` funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ac3c-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="7ac3c-107">Trwa argument, który wskazuje pozycję znaku, w którym podciąg rozpocznie się, zaczynając od pozycji 1.</span><span class="sxs-lookup"><span data-stu-id="7ac3c-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="7ac3c-108">.NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda przyjmuje indeks znaku w ciągu, w którym podciąg jest uruchomienie, zaczynając od pozycji 0.</span><span class="sxs-lookup"><span data-stu-id="7ac3c-108">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="7ac3c-109">W związku z tym, jeśli ciąg "ABCDE", pojedyncze znaki są numerowane 1,2,3,4,5 do użytku z programem `Mid` funkcji, ale 0,1,2,3,4 do użytku z programem <xref:System.String.Substring%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="7ac3c-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="7ac3c-110">Liczony od zera</span><span class="sxs-lookup"><span data-stu-id="7ac3c-110">Zero-Based</span></span>  
 <span data-ttu-id="7ac3c-111">Na przykład liczony od zera funkcja języka Visual Basic należy wziąć pod uwagę `Split` funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ac3c-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="7ac3c-112">On dzieli ciąg i zwraca tablicę zawierającą podciągów.</span><span class="sxs-lookup"><span data-stu-id="7ac3c-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="7ac3c-113">.NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> metoda również dzieli ciąg i zwraca tablicę zawierającą podciągów.</span><span class="sxs-lookup"><span data-stu-id="7ac3c-113">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="7ac3c-114">Ponieważ `Split` funkcji i <xref:System.String.Split%2A> metody zwracają tablice platformy .NET Framework, muszą one być liczony od zera.</span><span class="sxs-lookup"><span data-stu-id="7ac3c-114">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ac3c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ac3c-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="7ac3c-116">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ac3c-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
