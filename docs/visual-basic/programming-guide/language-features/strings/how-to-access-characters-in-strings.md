---
title: 'Instrukcje: Dostęp do znaków w ciągach w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: f2831333008844c959c3625698fce6c485450683
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967558"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="879ae-102">Instrukcje: Dostęp do znaków w ciągach w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="879ae-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="879ae-103">W tym przykładzie przedstawiono sposób użycia <xref:System.String.Chars%2A> właściwość dostęp do znaków w określonej lokalizacji w ciągu.</span><span class="sxs-lookup"><span data-stu-id="879ae-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="879ae-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="879ae-104">Example</span></span>  
 <span data-ttu-id="879ae-105">Czasami przydatne jest zapewnienie dane dotyczące znaków w ciągu i położenie tych znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="879ae-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="879ae-106">Można traktować jako tablicę znaków ciągu (`Char` wystąpień); można pobrać określonego znaku, odwołując się do indeksu za pomocą znaku <xref:System.String.Chars%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="879ae-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="879ae-107">`index` Parametru <xref:System.String.Chars%2A> właściwość jest liczony od zera.</span><span class="sxs-lookup"><span data-stu-id="879ae-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="879ae-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="879ae-108">Robust Programming</span></span>  
 <span data-ttu-id="879ae-109"><xref:System.String.Chars%2A> Właściwość zwraca znak w określonej pozycji.</span><span class="sxs-lookup"><span data-stu-id="879ae-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="879ae-110">Jednak niektóre znaki Unicode mogą być reprezentowane za więcej niż jeden znak.</span><span class="sxs-lookup"><span data-stu-id="879ae-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="879ae-111">Aby uzyskać więcej informacji na temat sposobu pracy ze znakami Unicode, zobacz [jak: Konwertowanie ciągu na tablicę znaków](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="879ae-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="879ae-112"><xref:System.String.Chars%2A> Zgłasza właściwości <xref:System.IndexOutOfRangeException> wyjątek Jeśli `index` parametru jest większa lub równa długości ciągu, czy go jest mniejsza niż zero</span><span class="sxs-lookup"><span data-stu-id="879ae-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="879ae-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="879ae-113">See also</span></span>
- <xref:System.String.Chars%2A>
- [<span data-ttu-id="879ae-114">Instrukcje: Konwertowanie ciągu na tablicę znaków</span><span class="sxs-lookup"><span data-stu-id="879ae-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="879ae-115">Konwertowanie pomiędzy ciągami a innymi typami danych w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="879ae-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="879ae-116">Ciągi</span><span class="sxs-lookup"><span data-stu-id="879ae-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
