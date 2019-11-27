---
title: 'Porady: dostęp do znaków w ciągach'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 44a021ed3ce1d10613cf6ab7c959c62feec6046c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352461"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="2d174-102">Porady: dostęp do znaków w ciągach w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2d174-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="2d174-103">W tym przykładzie pokazano, jak użyć właściwości <xref:System.String.Chars%2A>, aby uzyskać dostęp do znaku w określonej lokalizacji w ciągu.</span><span class="sxs-lookup"><span data-stu-id="2d174-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d174-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d174-104">Example</span></span>  
 <span data-ttu-id="2d174-105">Czasami warto mieć dane dotyczące znaków w ciągu i położenia tych znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="2d174-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="2d174-106">Ciąg można traktować jako tablicę znaków (`Char` wystąpienia). można pobrać konkretny znak, odwołując się do indeksu tego znaku za pomocą właściwości <xref:System.String.Chars%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d174-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="2d174-107">`index` parametr właściwości <xref:System.String.Chars%2A> jest oparty na zero.</span><span class="sxs-lookup"><span data-stu-id="2d174-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2d174-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="2d174-108">Robust Programming</span></span>  
 <span data-ttu-id="2d174-109">Właściwość <xref:System.String.Chars%2A> zwraca znak w określonej pozycji.</span><span class="sxs-lookup"><span data-stu-id="2d174-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="2d174-110">Jednak niektóre znaki Unicode mogą być reprezentowane przez więcej niż jeden znak.</span><span class="sxs-lookup"><span data-stu-id="2d174-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="2d174-111">Aby uzyskać więcej informacji na temat sposobu pracy z znakami Unicode, zobacz [How to: Convert a String to array of characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="2d174-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="2d174-112">Właściwość <xref:System.String.Chars%2A> zgłasza wyjątek <xref:System.IndexOutOfRangeException>, jeśli parametr `index` jest większy lub równy długości ciągu lub jeśli wartość jest mniejsza od zera</span><span class="sxs-lookup"><span data-stu-id="2d174-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d174-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d174-113">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="2d174-114">Instrukcje: Konwertowanie ciągu na tablicę znaków</span><span class="sxs-lookup"><span data-stu-id="2d174-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="2d174-115">Konwertowanie między ciągami a innymi typami danych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2d174-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="2d174-116">Ciągi</span><span class="sxs-lookup"><span data-stu-id="2d174-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
