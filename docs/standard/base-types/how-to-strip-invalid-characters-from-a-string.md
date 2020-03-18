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
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Porady: usuwanie nieprawidłowych znaków z ciągów
W poniższym przykładzie <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> użyto metody statycznej do usuwania nieprawidłowych znaków z ciągu.  
  
## <a name="example"></a>Przykład  
 Można użyć `CleanInput` metody zdefiniowanej w tym przykładzie, aby usunąć potencjalnie szkodliwe znaki, które zostały wprowadzone do pola tekstowego, które akceptuje dane wejściowe użytkownika. W takim `CleanInput` przypadku usuwa wszystkie znaki niealfanumeryczne z wyjątkiem okresów (.), na symbolach (@) i łącznikach (-) i zwraca pozostały ciąg. Można jednak zmodyfikować wzorzec wyrażenia regularnego, tak aby usuwał wszystkie znaki, które nie powinny być uwzględniane w ciągu wejściowym.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Wzorzec `[^\w\.@-]` wyrażenia regularnego pasuje do każdego znaku, który nie jest znakiem wyrazu, kropką, symbolem @ ani łącznikiem. Znak wyrazu to dowolna litera, cyfra dziesiętna lub łącznik znaków interpunkcyjnych, takie jak znak podkreślenia. Każdy znak, który pasuje <xref:System.String.Empty?displayProperty=nameWithType>do tego wzorca, jest zastępowany przez ciąg zdefiniowany przez wzorzec zastępczy. Aby zezwolić na dodatkowe znaki w danych wejściowych użytkownika, dodaj te znaki do klasy znaków we wzorcu wyrażenia regularnego. Na przykład wzorzec `[^\w\.@-\\%]` wyrażenia regularnego umożliwia również symbol procentowy i ukośnik odwrotny w ciągu wejściowym.  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)
