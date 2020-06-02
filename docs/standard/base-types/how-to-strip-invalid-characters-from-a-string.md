---
title: 'Instrukcje: Usuwanie nieprawidłowych znaków z ciągu'
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
ms.openlocfilehash: 5f2a1e7a3202b14d32ed02c6808fe2411465d9b5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290438"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Instrukcje: Usuwanie nieprawidłowych znaków z ciągu
W poniższym przykładzie zastosowano statyczną <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodę, aby użyć nieprawidłowych znaków z ciągu.  
  
## <a name="example"></a>Przykład  
 Można użyć `CleanInput` metody zdefiniowanej w tym przykładzie, aby podzielić potencjalnie szkodliwe znaki, które zostały wprowadzone do pola tekstowego akceptującego dane wejściowe użytkownika. W takim przypadku należy wyłączać `CleanInput` wszystkie znaki niealfanumeryczne z wyjątkiem kropek (.), symboli (@) i łączników (-), a następnie zwracać pozostałe ciągi. Można jednak zmodyfikować wzorzec wyrażenia regularnego tak, aby obejmował wszystkie znaki, które nie powinny być zawarte w ciągu wejściowym.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Wzorzec wyrażenia regularnego `[^\w\.@-]` dopasowuje dowolny znak, który nie jest znakiem słowa, kropką, symbolem @ lub łącznikiem. Znak wyrazu to jakakolwiek litera, cyfra dziesiętna lub łącznik interpunkcji, taki jak podkreślenie. Dowolny znak, który jest zgodny z tym wzorcem, jest zastępowany przez <xref:System.String.Empty?displayProperty=nameWithType> , który jest ciągiem zdefiniowanym przez wzorzec zastępczy. Aby zezwolić na dodatkowe znaki w danych wejściowych użytkownika, Dodaj te znaki do klasy znaków we wzorcu wyrażenia regularnego. Na przykład wzorzec wyrażenia regularnego `[^\w\.@-\\%]` pozwala także na symbol procentowy i ukośnik odwrotny w ciągu wejściowym.  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia regularne .NET](regular-expressions.md)
