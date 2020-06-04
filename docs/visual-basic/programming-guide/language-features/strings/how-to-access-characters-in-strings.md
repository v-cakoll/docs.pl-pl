---
title: 'Porady: dostęp do znaków w ciągach'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: fa5920cfd25f61f6e6c7d5438ef7c0e38a48fa1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401956"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="ba331-102">Porady: dostęp do znaków w ciągach w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba331-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="ba331-103">W tym przykładzie pokazano, jak użyć <xref:System.String.Chars%2A> właściwości w celu uzyskania dostępu do znaku w określonej lokalizacji w ciągu.</span><span class="sxs-lookup"><span data-stu-id="ba331-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba331-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba331-104">Example</span></span>  
 <span data-ttu-id="ba331-105">Czasami warto mieć dane dotyczące znaków w ciągu i położenia tych znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="ba331-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="ba331-106">Można traktować ciąg jako tablicę znaków ( `Char` Instances); można pobrać konkretny znak, odwołując się do indeksu tego znaku za pomocą <xref:System.String.Chars%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ba331-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="ba331-107">`index`Parametr <xref:System.String.Chars%2A> właściwości jest oparty na zero.</span><span class="sxs-lookup"><span data-stu-id="ba331-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ba331-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="ba331-108">Robust Programming</span></span>  
 <span data-ttu-id="ba331-109"><xref:System.String.Chars%2A>Właściwość zwraca znak na określonej pozycji.</span><span class="sxs-lookup"><span data-stu-id="ba331-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="ba331-110">Jednak niektóre znaki Unicode mogą być reprezentowane przez więcej niż jeden znak.</span><span class="sxs-lookup"><span data-stu-id="ba331-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="ba331-111">Aby uzyskać więcej informacji na temat sposobu pracy z znakami Unicode, zobacz [How to: Convert a String to array of characters](how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="ba331-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="ba331-112"><xref:System.String.Chars%2A>Właściwość zgłasza <xref:System.IndexOutOfRangeException> wyjątek `index` , jeśli parametr jest większy niż lub równy długości ciągu lub jeśli wartość jest mniejsza od zera</span><span class="sxs-lookup"><span data-stu-id="ba331-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba331-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba331-113">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="ba331-114">Porady: konwertowanie ciągu do tablicy znaków</span><span class="sxs-lookup"><span data-stu-id="ba331-114">How to: Convert a String to an Array of Characters</span></span>](how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="ba331-115">Konwertowanie pomiędzy ciągami a innymi typami danych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba331-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="ba331-116">Ciągi</span><span class="sxs-lookup"><span data-stu-id="ba331-116">Strings</span></span>](index.md)
