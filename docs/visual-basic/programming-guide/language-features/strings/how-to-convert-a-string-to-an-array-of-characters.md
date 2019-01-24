---
title: 'Instrukcje: Konwertowanie ciągu na tablicę znaków w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: 9d68e3d90c52d6a4312ccb7c0c9610968e7a4b55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603758"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="909a3-102">Instrukcje: Konwertowanie ciągu na tablicę znaków w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="909a3-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="909a3-103">Czasami przydatne jest zapewnienie dane dotyczące znaków w ciągu i położenie tych znaków w ciągu, na przykład gdy są analizowania parametrów.</span><span class="sxs-lookup"><span data-stu-id="909a3-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="909a3-104">W tym przykładzie pokazano, jak uzyskać tablicę znaków w ciągu, wywołując ciągu <xref:System.String.ToCharArray%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="909a3-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="909a3-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="909a3-105">Example</span></span>  
 <span data-ttu-id="909a3-106">W tym przykładzie pokazano, jak podzielić ciąg do `Char` tablicy i jak pozwala podzielić ciąg do `String` tablicy jej znaków Unicode, tekst.</span><span class="sxs-lookup"><span data-stu-id="909a3-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="909a3-107">Przyczyna wykonywania tego rozróżnienia to, że znaki tekstowe Unicode mogą się składać z co najmniej dwóch `Char` znaki (np. para zastępcza lub łączenie sekwencji znaków).</span><span class="sxs-lookup"><span data-stu-id="909a3-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="909a3-108">Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.TextElementEnumerator> i [Unicode Standard](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="909a3-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="909a3-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="909a3-109">Example</span></span>  
 <span data-ttu-id="909a3-110">Jest trudniejsze do podzielić ciąg na jego znaków Unicode, ale jest to konieczne, jeśli potrzebujesz informacji na temat wizualnej reprezentacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="909a3-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="909a3-111">W tym przykładzie użyto <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodę, aby uzyskać informacje, które tworzą ciąg znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="909a3-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="909a3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="909a3-112">See also</span></span>
- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [<span data-ttu-id="909a3-113">Instrukcje: Dostęp do znaków w ciągach</span><span class="sxs-lookup"><span data-stu-id="909a3-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [<span data-ttu-id="909a3-114">Konwertowanie pomiędzy ciągami a innymi typami danych w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="909a3-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="909a3-115">Ciągi</span><span class="sxs-lookup"><span data-stu-id="909a3-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
