---
title: 'Porady: konwertowanie ciągu do tablicy znaków w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: cc12b70cddcb93a72b4421a8ddd93542ef84f55b
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845193"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="b3d60-102">Porady: konwertowanie ciągu do tablicy znaków w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3d60-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="b3d60-103">Czasami przydatne jest zapewnienie dane dotyczące znaków w ciągu i położenie tych znaków w ciągu, na przykład gdy są analizowania parametrów.</span><span class="sxs-lookup"><span data-stu-id="b3d60-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="b3d60-104">W tym przykładzie pokazano, jak uzyskać tablicę znaków w ciągu, wywołując ciągu <xref:System.String.ToCharArray%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b3d60-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3d60-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3d60-105">Example</span></span>  
 <span data-ttu-id="b3d60-106">W tym przykładzie pokazano, jak podzielić ciąg do `Char` tablicy i jak pozwala podzielić ciąg do `String` tablicy jej znaków Unicode, tekst.</span><span class="sxs-lookup"><span data-stu-id="b3d60-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="b3d60-107">Przyczyna wykonywania tego rozróżnienia to, że znaki tekstowe Unicode mogą się składać z co najmniej dwóch `Char` znaki (np. para zastępcza lub łączenie sekwencji znaków).</span><span class="sxs-lookup"><span data-stu-id="b3d60-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="b3d60-108">Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.TextElementEnumerator> i [Unicode Standard](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="b3d60-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="b3d60-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3d60-109">Example</span></span>  
 <span data-ttu-id="b3d60-110">Jest trudniejsze do podzielić ciąg na jego znaków Unicode, ale jest to konieczne, jeśli potrzebujesz informacji na temat wizualnej reprezentacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="b3d60-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="b3d60-111">W tym przykładzie użyto <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodę, aby uzyskać informacje, które tworzą ciąg znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="b3d60-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b3d60-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3d60-112">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [<span data-ttu-id="b3d60-113">Instrukcje: Dostęp do znaków w ciągach</span><span class="sxs-lookup"><span data-stu-id="b3d60-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [<span data-ttu-id="b3d60-114">Konwertowanie pomiędzy ciągami a innymi typami danych w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3d60-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="b3d60-115">Ciągi</span><span class="sxs-lookup"><span data-stu-id="b3d60-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
