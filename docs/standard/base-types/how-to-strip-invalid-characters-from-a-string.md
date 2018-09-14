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
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516334"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Porady: usuwanie nieprawidłowych znaków z ciągów
W poniższym przykładzie użyto statycznego <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody usuwanie nieprawidłowych znaków z ciągu.  
  
## <a name="example"></a>Przykład  
 Możesz użyć `CleanInput` metody zdefiniowanej w tym przykładzie w celu wyodrębnienia danych potencjalnie niebezpiecznych znaków, które zostały wprowadzone do pola tekstowego, który akceptuje dane wejściowe użytkownika. W tym przypadku `CleanInput` usuwa wszystkie znaki inne niż alfanumeryczne, z wyjątkiem kropki (.), u symbole (@), łączniki (-) i zwraca wynikowy ciąg. Można jednak zmodyfikować wzorzec wyrażenia regularnego, tak, aby go usuwa wszystkie znaki, które nie powinny być uwzględnione w ciągu wejściowym.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Definicję wzorca wyrażenia regularnego `[^\w\.@-]` dopasowuje dowolny znak, który nie jest znakiem słowa okres, symbol @ lub łącznik. Znak słowa jest żadnych litery, cyfry dziesiętnej lub łącznik znaki interpunkcyjne, takie jak podkreślenie. Zastępuje dowolny znak, który pasuje do tego wzorca <xref:System.String.Empty?displayProperty=nameWithType>, który jest zdefiniowany przez wzorzec zamieniania. Aby umożliwić dodatkowe znaki w danych wejściowych użytkownika, należy dodać te znaki, klasy znaku we wzorcu wyrażenia regularnego. Na przykład wzorzec wyrażenia regularnego `[^\w\.@-\\%]` umożliwia także symbol procentu i ukośnik odwrotny w ciągu wejściowym.  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md)
