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
ms.openlocfilehash: c109143601e304b1ec15a60c71d65fe6bd15aae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="9173a-102">Porady: konwertowanie ciągu do tablicy znaków w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9173a-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="9173a-103">Czasami jest przydatne do danych o znaki w ciągu i pozycje te znaki w ciągu, na przykład gdy są analizowania parametrów.</span><span class="sxs-lookup"><span data-stu-id="9173a-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="9173a-104">W tym przykładzie pokazano, jak wprowadzasz tablicy znaków w ciągu wywołując ciąg <xref:System.String.ToCharArray%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9173a-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9173a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="9173a-105">Example</span></span>  
 <span data-ttu-id="9173a-106">W tym przykładzie pokazano, jak podzielić ciąg do `Char` tablicy i dzielenia ciąg do `String` tablicy jego znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="9173a-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="9173a-107">Przyczyna tej różnicy to, że znaków Unicode może składać się z co najmniej dwóch `Char` znaków (np. para zastępcza lub łączenie sekwencja znaków).</span><span class="sxs-lookup"><span data-stu-id="9173a-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="9173a-108">Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.TextElementEnumerator> i "Unicode Standard" w http://www.unicode.org.</span><span class="sxs-lookup"><span data-stu-id="9173a-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and "The Unicode Standard" at http://www.unicode.org.</span></span>  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="9173a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="9173a-109">Example</span></span>  
 <span data-ttu-id="9173a-110">Trudniej podzielić ciąg na jego znaków Unicode, ale jest to konieczne, jeśli potrzebujesz informacji na temat wizualną reprezentację ciągu.</span><span class="sxs-lookup"><span data-stu-id="9173a-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="9173a-111">W tym przykładzie użyto <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodę, aby uzyskać informacje na temat wchodzące w skład ciąg znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="9173a-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9173a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9173a-112">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [<span data-ttu-id="9173a-113">Instrukcje: Dostęp do znaków w ciągach</span><span class="sxs-lookup"><span data-stu-id="9173a-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [<span data-ttu-id="9173a-114">Konwertowanie pomiędzy ciągami a innymi typami danych w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9173a-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="9173a-115">Ciągi</span><span class="sxs-lookup"><span data-stu-id="9173a-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
