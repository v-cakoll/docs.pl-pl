---
title: "Porady: usuwanie nieprawidłowych znaków z ciągów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f676ca9121498da7c88cdec8b49586bde91b181
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="4a45d-102">Porady: usuwanie nieprawidłowych znaków z ciągów</span><span class="sxs-lookup"><span data-stu-id="4a45d-102">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="4a45d-103">W poniższym przykładzie użyto statycznych <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodę usuwanie nieprawidłowych znaków z ciągu.</span><span class="sxs-lookup"><span data-stu-id="4a45d-103">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a45d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a45d-104">Example</span></span>  
 <span data-ttu-id="4a45d-105">Można użyć `CleanInput` metody zdefiniowanej w tym przykładzie do usuwanie potencjalnie szkodliwe znaków, które zostały wprowadzone do pola tekstowego, który akceptuje dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4a45d-105">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="4a45d-106">W takim przypadku `CleanInput` usuwa wszystkie znaków innych niż alfanumeryczne, z wyjątkiem kropki (.) na symbole (@), łączniki (-) i zwraca wynikowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="4a45d-106">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="4a45d-107">Jednak można zmodyfikować wzorzec wyrażenia regularnego, aby go usuwa wszystkie znaki, które nie powinny znajdować się w ciągu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="4a45d-107">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="4a45d-108">Wzorzec wyrażenia regularnego `[^\w\.@-]` dopasowuje dowolny znak, który nie jest znak słowa okres, symbol @ lub łącznika.</span><span class="sxs-lookup"><span data-stu-id="4a45d-108">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="4a45d-109">Znak słowa jest dowolną literę, cyfrę lub łącznika znaki interpunkcyjne, takie jak podkreślenie.</span><span class="sxs-lookup"><span data-stu-id="4a45d-109">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="4a45d-110">Zastępuje dowolny znak, który pasuje do tego wzorca <xref:System.String.Empty?displayProperty=nameWithType>, który jest zdefiniowany przez zastąpienie wzorca.</span><span class="sxs-lookup"><span data-stu-id="4a45d-110">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="4a45d-111">Aby zezwalać na dodatkowe znaki w danych wejściowych użytkownika, należy dodać te znaki do klasy znaków w wzorzec wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="4a45d-111">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="4a45d-112">Na przykład wzorzec wyrażenia regularnego `[^\w\.@-\\%]` umożliwia również symbol procentu i ukośnik odwrotny w parametrach wejściowych.</span><span class="sxs-lookup"><span data-stu-id="4a45d-112">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a45d-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a45d-113">See Also</span></span>  
 [<span data-ttu-id="4a45d-114">Wyrażeń regularnych programu .NET</span><span class="sxs-lookup"><span data-stu-id="4a45d-114">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
