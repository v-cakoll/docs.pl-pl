---
title: 'Porady: dostęp do znaków w ciągach w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 48507cade639660e6ce36697975d09fb29206c20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="38bf3-102">Porady: dostęp do znaków w ciągach w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38bf3-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="38bf3-103">W tym przykładzie przedstawiono sposób użycia <xref:System.String.Chars%2A> dostęp do znaków w określonej lokalizacji w ciągu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="38bf3-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38bf3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="38bf3-104">Example</span></span>  
 <span data-ttu-id="38bf3-105">Czasami jest przydatne do danych o znaki w ciągu i położenia tych znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="38bf3-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="38bf3-106">Można traktować jako tablicę znaków z ciągu (`Char` wystąpień); można pobrać określonego znaku odwołujące się do indeksu za pomocą znaku <xref:System.String.Chars%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="38bf3-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 <span data-ttu-id="38bf3-107">`index` Parametr <xref:System.String.Chars%2A> właściwość jest liczony od zera.</span><span class="sxs-lookup"><span data-stu-id="38bf3-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="38bf3-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="38bf3-108">Robust Programming</span></span>  
 <span data-ttu-id="38bf3-109"><xref:System.String.Chars%2A> Właściwość zwraca znak na określonej pozycji.</span><span class="sxs-lookup"><span data-stu-id="38bf3-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="38bf3-110">Jednak niektóre znaki Unicode może być reprezentowany przez więcej niż jednego znaku.</span><span class="sxs-lookup"><span data-stu-id="38bf3-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="38bf3-111">Aby uzyskać więcej informacji na temat pracy z znaków Unicode, zobacz [porady: konwertowanie ciągu do tablicy znaków](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="38bf3-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="38bf3-112"><xref:System.String.Chars%2A> Zgłasza właściwości <xref:System.IndexOutOfRangeException> wyjątek Jeśli `index` parametr jest większa lub równa długości ciągu, lub jeśli jest ona mniejsza od zera</span><span class="sxs-lookup"><span data-stu-id="38bf3-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38bf3-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38bf3-113">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 [<span data-ttu-id="38bf3-114">Instrukcje: Konwertowanie ciągu na tablicę znaków</span><span class="sxs-lookup"><span data-stu-id="38bf3-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [<span data-ttu-id="38bf3-115">Konwertowanie pomiędzy ciągami a innymi typami danych w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38bf3-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="38bf3-116">Ciągi</span><span class="sxs-lookup"><span data-stu-id="38bf3-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
