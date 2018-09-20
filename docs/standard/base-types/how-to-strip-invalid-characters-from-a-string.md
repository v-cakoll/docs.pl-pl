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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3bbd25e40607bd316f1bbab974174fe5433770f
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46325433"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="c8c2d-102">Porady: usuwanie nieprawidłowych znaków z ciągów</span><span class="sxs-lookup"><span data-stu-id="c8c2d-102">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="c8c2d-103">W poniższym przykładzie użyto statycznego <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody usuwanie nieprawidłowych znaków z ciągu.</span><span class="sxs-lookup"><span data-stu-id="c8c2d-103">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8c2d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8c2d-104">Example</span></span>  
 <span data-ttu-id="c8c2d-105">Możesz użyć `CleanInput` metody zdefiniowanej w tym przykładzie w celu wyodrębnienia danych potencjalnie niebezpiecznych znaków, które zostały wprowadzone do pola tekstowego, który akceptuje dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c8c2d-105">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="c8c2d-106">W tym przypadku `CleanInput` usuwa wszystkie znaki inne niż alfanumeryczne, z wyjątkiem kropki (.), u symbole (@), łączniki (-) i zwraca wynikowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="c8c2d-106">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="c8c2d-107">Można jednak zmodyfikować wzorzec wyrażenia regularnego, tak, aby go usuwa wszystkie znaki, które nie powinny być uwzględnione w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="c8c2d-107">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="c8c2d-108">Definicję wzorca wyrażenia regularnego `[^\w\.@-]` dopasowuje dowolny znak, który nie jest znakiem słowa okres, symbol @ lub łącznik.</span><span class="sxs-lookup"><span data-stu-id="c8c2d-108">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="c8c2d-109">Znak słowa jest żadnych litery, cyfry dziesiętnej lub łącznik znaki interpunkcyjne, takie jak podkreślenie.</span><span class="sxs-lookup"><span data-stu-id="c8c2d-109">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="c8c2d-110">Zastępuje dowolny znak, który pasuje do tego wzorca <xref:System.String.Empty?displayProperty=nameWithType>, który jest zdefiniowany przez wzorzec zamieniania.</span><span class="sxs-lookup"><span data-stu-id="c8c2d-110">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="c8c2d-111">Aby umożliwić dodatkowe znaki w danych wejściowych użytkownika, należy dodać te znaki, klasy znaku we wzorcu wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="c8c2d-111">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="c8c2d-112">Na przykład wzorzec wyrażenia regularnego `[^\w\.@-\\%]` umożliwia także symbol procentu i ukośnik odwrotny w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="c8c2d-112">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8c2d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8c2d-113">See also</span></span>

- [<span data-ttu-id="c8c2d-114">Wyrażeń regularnych programu .NET</span><span class="sxs-lookup"><span data-stu-id="c8c2d-114">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
