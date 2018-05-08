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
ms.openlocfilehash: 66fe5dd1da148e8afd07ae69cec960438b53536a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Porady: usuwanie nieprawidłowych znaków z ciągów
W poniższym przykładzie użyto statycznych <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodę usuwanie nieprawidłowych znaków z ciągu.  
  
## <a name="example"></a>Przykład  
 Można użyć `CleanInput` metody zdefiniowanej w tym przykładzie do usuwanie potencjalnie szkodliwe znaków, które zostały wprowadzone do pola tekstowego, który akceptuje dane wejściowe użytkownika. W takim przypadku `CleanInput` usuwa wszystkie znaków innych niż alfanumeryczne, z wyjątkiem kropki (.) na symbole (@), łączniki (-) i zwraca wynikowy ciąg. Jednak można zmodyfikować wzorzec wyrażenia regularnego, aby go usuwa wszystkie znaki, które nie powinny znajdować się w ciągu wejściowego.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Wzorzec wyrażenia regularnego `[^\w\.@-]` dopasowuje dowolny znak, który nie jest znak słowa okres, symbol @ lub łącznika. Znak słowa jest dowolną literę, cyfrę lub łącznika znaki interpunkcyjne, takie jak podkreślenie. Zastępuje dowolny znak, który pasuje do tego wzorca <xref:System.String.Empty?displayProperty=nameWithType>, który jest zdefiniowany przez zastąpienie wzorca. Aby zezwalać na dodatkowe znaki w danych wejściowych użytkownika, należy dodać te znaki do klasy znaków w wzorzec wyrażenia regularnego. Na przykład wzorzec wyrażenia regularnego `[^\w\.@-\\%]` umożliwia również symbol procentu i ukośnik odwrotny w parametrach wejściowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md)
