---
title: Dostęp do ciągu liczonego od zera a Dostęp do ciągu liczonego od jednego w języku Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: a6ceb10d4a3cb9463551d8c85375ddbbb607ffdc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024459"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="d29d4-102">Dostęp do ciągu liczonego od zera a Dostęp do ciągu liczonego od jednego w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d29d4-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="d29d4-103">W tym temacie porównano jak Visual Basic i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zapewniają dostęp do znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="d29d4-103">This topic compares how Visual Basic and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="d29d4-104">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Zawsze udostępnia liczony od zera dla znaków w ciągu, Visual Basic przewiduje liczony od zera i oparte na jednym dostępu, w zależności od funkcji.</span><span class="sxs-lookup"><span data-stu-id="d29d4-104">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="d29d4-105">Liczonego od jednego</span><span class="sxs-lookup"><span data-stu-id="d29d4-105">One-Based</span></span>  
 <span data-ttu-id="d29d4-106">Na przykład funkcję liczonego od jednego języka Visual Basic należy wziąć pod uwagę `Mid` funkcji.</span><span class="sxs-lookup"><span data-stu-id="d29d4-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="d29d4-107">Trwa argument, który wskazuje pozycję znaku, w którym podciąg rozpocznie się, zaczynając od pozycji 1.</span><span class="sxs-lookup"><span data-stu-id="d29d4-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="d29d4-108">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Metoda przyjmuje indeks znaku w ciągu, w którym podciąg jest uruchomienie, zaczynając od pozycji 0.</span><span class="sxs-lookup"><span data-stu-id="d29d4-108">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="d29d4-109">W związku z tym, jeśli ciąg "ABCDE", pojedyncze znaki są numerowane 1,2,3,4,5 do użytku z programem `Mid` funkcji, ale 0,1,2,3,4 do użytku z programem <xref:System.String.Substring%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="d29d4-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="d29d4-110">Liczony od zera</span><span class="sxs-lookup"><span data-stu-id="d29d4-110">Zero-Based</span></span>  
 <span data-ttu-id="d29d4-111">Na przykład liczony od zera funkcja języka Visual Basic należy wziąć pod uwagę `Split` funkcji.</span><span class="sxs-lookup"><span data-stu-id="d29d4-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="d29d4-112">On dzieli ciąg i zwraca tablicę zawierającą podciągów.</span><span class="sxs-lookup"><span data-stu-id="d29d4-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="d29d4-113">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Metoda również dzieli ciąg i zwraca tablicę zawierającą podciągów.</span><span class="sxs-lookup"><span data-stu-id="d29d4-113">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="d29d4-114">Ponieważ `Split` funkcji i <xref:System.String.Split%2A> zwrotu metody [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tablic, muszą one być liczony od zera.</span><span class="sxs-lookup"><span data-stu-id="d29d4-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d29d4-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d29d4-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="d29d4-116">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d29d4-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
