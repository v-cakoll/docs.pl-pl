---
title: 'Instrukcje: Usuwanie nieprawidłowych znaków z ciągu'
description: Przeczytaj przykład pokazujący, jak rozdzielić potencjalnie szkodliwe znaki z ciągu przy użyciu statycznego wyrażenia regularnego. Replace.
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
ms.openlocfilehash: f9d671587d174a1eb2bb6a5dac24bdd0220be3dd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600831"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="40673-103">Instrukcje: Usuwanie nieprawidłowych znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="40673-103">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="40673-104">W poniższym przykładzie zastosowano statyczną <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodę, aby użyć nieprawidłowych znaków z ciągu.</span><span class="sxs-lookup"><span data-stu-id="40673-104">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40673-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="40673-105">Example</span></span>  
 <span data-ttu-id="40673-106">Można użyć `CleanInput` metody zdefiniowanej w tym przykładzie, aby podzielić potencjalnie szkodliwe znaki, które zostały wprowadzone do pola tekstowego akceptującego dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="40673-106">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="40673-107">W takim przypadku należy wyłączać `CleanInput` wszystkie znaki niealfanumeryczne z wyjątkiem kropek (.), symboli (@) i łączników (-), a następnie zwracać pozostałe ciągi.</span><span class="sxs-lookup"><span data-stu-id="40673-107">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="40673-108">Można jednak zmodyfikować wzorzec wyrażenia regularnego tak, aby obejmował wszystkie znaki, które nie powinny być zawarte w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="40673-108">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="40673-109">Wzorzec wyrażenia regularnego `[^\w\.@-]` dopasowuje dowolny znak, który nie jest znakiem słowa, kropką, symbolem @ lub łącznikiem.</span><span class="sxs-lookup"><span data-stu-id="40673-109">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="40673-110">Znak wyrazu to jakakolwiek litera, cyfra dziesiętna lub łącznik interpunkcji, taki jak podkreślenie.</span><span class="sxs-lookup"><span data-stu-id="40673-110">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="40673-111">Dowolny znak, który jest zgodny z tym wzorcem, jest zastępowany przez <xref:System.String.Empty?displayProperty=nameWithType> , który jest ciągiem zdefiniowanym przez wzorzec zastępczy.</span><span class="sxs-lookup"><span data-stu-id="40673-111">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="40673-112">Aby zezwolić na dodatkowe znaki w danych wejściowych użytkownika, Dodaj te znaki do klasy znaków we wzorcu wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="40673-112">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="40673-113">Na przykład wzorzec wyrażenia regularnego `[^\w\.@-\\%]` pozwala także na symbol procentowy i ukośnik odwrotny w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="40673-113">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40673-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40673-114">See also</span></span>

- [<span data-ttu-id="40673-115">Wyrażenia regularne .NET</span><span class="sxs-lookup"><span data-stu-id="40673-115">.NET Regular Expressions</span></span>](regular-expressions.md)
