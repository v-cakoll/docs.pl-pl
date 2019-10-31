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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127651"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="e3821-102">Porady: usuwanie nieprawidłowych znaków z ciągów</span><span class="sxs-lookup"><span data-stu-id="e3821-102">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="e3821-103">W poniższym przykładzie zastosowano statyczną metodę <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType>, aby użyć nieprawidłowych znaków z ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3821-103">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3821-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3821-104">Example</span></span>  
 <span data-ttu-id="e3821-105">Można użyć metody `CleanInput` zdefiniowanej w tym przykładzie, aby podzielić potencjalnie szkodliwe znaki, które zostały wprowadzone do pola tekstowego akceptującego dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e3821-105">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="e3821-106">W takim przypadku `CleanInput` wszystkie znaki niealfanumeryczne oprócz kropek (.), w symbolach (@) i łączniki (-) i zwraca resztę ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3821-106">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="e3821-107">Można jednak zmodyfikować wzorzec wyrażenia regularnego tak, aby obejmował wszystkie znaki, które nie powinny być zawarte w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="e3821-107">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="e3821-108">Wzorzec wyrażenia regularnego `[^\w\.@-]` dopasowuje dowolny znak, który nie jest znakiem słowa, kropką, symbolem @ lub łącznikiem.</span><span class="sxs-lookup"><span data-stu-id="e3821-108">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="e3821-109">Znak wyrazu to jakakolwiek litera, cyfra dziesiętna lub łącznik interpunkcji, taki jak podkreślenie.</span><span class="sxs-lookup"><span data-stu-id="e3821-109">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="e3821-110">Dowolny znak, który jest zgodny z tym wzorcem, jest zastępowany przez <xref:System.String.Empty?displayProperty=nameWithType>, który jest ciągiem zdefiniowanym przez wzorzec zastępczy.</span><span class="sxs-lookup"><span data-stu-id="e3821-110">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="e3821-111">Aby zezwolić na dodatkowe znaki w danych wejściowych użytkownika, Dodaj te znaki do klasy znaków we wzorcu wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="e3821-111">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="e3821-112">Na przykład wzorzec wyrażenia regularnego `[^\w\.@-\\%]` również zezwala na symbol procentowy i ukośnik odwrotny w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="e3821-112">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3821-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3821-113">See also</span></span>

- [<span data-ttu-id="e3821-114">Wyrażenia regularne .NET</span><span class="sxs-lookup"><span data-stu-id="e3821-114">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
