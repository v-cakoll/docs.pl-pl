---
title: 'Porady: usuwanie nieprawidłowych znaków z ciągów'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
ms.openlocfilehash: cc90e6609f9335b7e2f08271e5540b182901e8c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127651"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="9c8dc-102">Porady: usuwanie nieprawidłowych znaków z ciągów</span><span class="sxs-lookup"><span data-stu-id="9c8dc-102">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="9c8dc-103">W poniższym przykładzie <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> użyto metody statycznej do usuwania nieprawidłowych znaków z ciągu.</span><span class="sxs-lookup"><span data-stu-id="9c8dc-103">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c8dc-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c8dc-104">Example</span></span>  
 <span data-ttu-id="9c8dc-105">Można użyć `CleanInput` metody zdefiniowanej w tym przykładzie, aby usunąć potencjalnie szkodliwe znaki, które zostały wprowadzone do pola tekstowego, które akceptuje dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9c8dc-105">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="9c8dc-106">W takim `CleanInput` przypadku usuwa wszystkie znaki niealfanumeryczne z wyjątkiem okresów (.), na symbolach (@) i łącznikach (-) i zwraca pozostały ciąg.</span><span class="sxs-lookup"><span data-stu-id="9c8dc-106">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="9c8dc-107">Można jednak zmodyfikować wzorzec wyrażenia regularnego, tak aby usuwał wszystkie znaki, które nie powinny być uwzględniane w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="9c8dc-107">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="9c8dc-108">Wzorzec `[^\w\.@-]` wyrażenia regularnego pasuje do każdego znaku, który nie jest znakiem wyrazu, kropką, symbolem @ ani łącznikiem.</span><span class="sxs-lookup"><span data-stu-id="9c8dc-108">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="9c8dc-109">Znak wyrazu to dowolna litera, cyfra dziesiętna lub łącznik znaków interpunkcyjnych, takie jak znak podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="9c8dc-109">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="9c8dc-110">Każdy znak, który pasuje <xref:System.String.Empty?displayProperty=nameWithType>do tego wzorca, jest zastępowany przez ciąg zdefiniowany przez wzorzec zastępczy.</span><span class="sxs-lookup"><span data-stu-id="9c8dc-110">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="9c8dc-111">Aby zezwolić na dodatkowe znaki w danych wejściowych użytkownika, dodaj te znaki do klasy znaków we wzorcu wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="9c8dc-111">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="9c8dc-112">Na przykład wzorzec `[^\w\.@-\\%]` wyrażenia regularnego umożliwia również symbol procentowy i ukośnik odwrotny w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="9c8dc-112">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c8dc-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c8dc-113">See also</span></span>

- [<span data-ttu-id="9c8dc-114">Wyrażenia regularne .NET</span><span class="sxs-lookup"><span data-stu-id="9c8dc-114">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
