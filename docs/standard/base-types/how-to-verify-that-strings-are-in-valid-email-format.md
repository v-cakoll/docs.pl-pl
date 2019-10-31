---
title: 'Porady: sprawdzanie, czy format poczty e-mail ciągów jest prawidłowy'
ms.date: 12/10/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET Framework], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET Framework], examples [Visual Basic]
- email [.NET Framework], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
ms.openlocfilehash: 1812235da6e6d02a97fe994568c5c26a3c7cde33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126415"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Instrukcje: Weryfikowanie, czy ciągi są w prawidłowym formacie poczty e-mail

Poniższy przykład używa wyrażenia regularnego, aby sprawdzić, czy ciąg jest w prawidłowym formacie poczty e-mail.

## <a name="example"></a>Przykład

W przykładzie zdefiniowano metodę `IsValidEmail`, która zwraca `true`, jeśli ciąg zawiera prawidłowy adres e-mail i `false` Jeśli nie, ale nie przyjmuje żadnych innych akcji.

Aby sprawdzić, czy adres e-mail jest prawidłowy, Metoda `IsValidEmail` wywołuje metodę <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> z wzorcem wyrażenia regularnego `(@)(.+)$`, aby oddzielić nazwę domeny od adresu e-mail. Trzeci parametr jest delegatem <xref:System.Text.RegularExpressions.MatchEvaluator>, który reprezentuje metodę, która przetwarza i zastępuje dopasowany tekst. Wzorzec wyrażenia regularnego jest interpretowany w następujący sposób.

|Wzorzec|Opis|
|-------------|-----------------|
|`(@)`|Dopasowuje znak @. Jest to pierwsza grupa przechwytywania.|
|`(.+)`|Dopasowuje jedno lub więcej wystąpień dowolnego znaku. Jest to druga grupa przechwytywania.|
|`$`|Zakończ dopasowanie na końcu ciągu.|

Nazwa domeny wraz ze znakiem @ jest przenoszona do metody `DomainMapper`, która używa klasy <xref:System.Globalization.IdnMapping> do translacji znaków Unicode, które są spoza zakresu znaków US-ASCII do formacie Punycode. Metoda ustawia również flagę `invalid`, aby `True`, jeśli metoda <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> wykryje nieprawidłowe znaki w nazwie domeny. Metoda zwraca nazwę domeny formacie Punycode poprzedzoną symbolem @ do metody `IsValidEmail`.

Metoda `IsValidEmail` następnie wywołuje metodę <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType>, aby sprawdzić, czy adres jest zgodny ze wzorcem wyrażenia regularnego.

Należy pamiętać, że metoda `IsValidEmail` nie przeprowadza uwierzytelniania w celu zweryfikowania adresu e-mail. Określa on tylko, czy jego format jest prawidłowy dla adresu e-mail. Ponadto Metoda `IsValidEmail` nie sprawdza, czy nazwa domeny najwyższego poziomu jest prawidłową nazwą domeny wymienioną w [bazie danych strefy głównej Iana](https://www.iana.org/domains/root/db), co wymagałoby operacji wyszukiwania. Zamiast tego wyrażenie regularne sprawdza tylko, czy nazwa domeny najwyższego poziomu składa się z dwóch i dwudziestu czterech znaków ASCII, z znakami alfanumerycznymi i ostatnimi, a pozostałe znaki są alfanumeryczne lub łącznika (-).

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

W tym przykładzie wzorzec wyrażenia regularnego ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` jest interpretowany jak pokazano w poniższym legendzie. Wyrażenie regularne jest kompilowane przy użyciu flagi <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.

`^`wzorca: Rozpocznij dopasowanie na początku ciągu.

`(?(")`wzorca: Określ, czy pierwszy znak jest znakiem cudzysłowu. `(?(")` jest początkiem konstrukcji warunkowej.

`(?(")(".+?(?<!\\)"@)`wzorca: Jeśli pierwszy znak jest znakiem cudzysłowu, dopasowuje początkowy znak cudzysłowu, po którym następuje co najmniej jedno wystąpienie dowolnego znaku, po którym następuje znak cudzysłowu końcowego. Znak cudzysłowu końcowego nie może być poprzedzony znakiem ukośnika odwrotnego (\\). `(?<!` to początek asercja wsteczna negatywnej zerowej szerokości. Ciąg powinien zawierać znak (@).

`|(([0-9a-z]`wzorca: Jeśli pierwszy znak nie jest znakiem cudzysłowu, dopasowuje dowolny znak alfabetyczny od a do z lub od A do Z (w porównaniu z rozróżnianiem wielkości liter) lub dowolny znak numeryczny od 0 do 9.

`(\.(?!\.))`wzorca: Jeśli następny znak jest kropką, Dopasuj go. Jeśli nie jest to okres, spójrz na następny znak i Kontynuuj dopasowanie. `(?!\.)` to nieujemne potwierdzenie o zerowej szerokości, które uniemożliwia wyświetlanie dwóch kolejnych okresów w lokalnej części adresu e-mail.

``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``wzorca: Jeśli następny znak nie jest kropką, dopasowuje dowolny znak słowa lub jeden z następujących znaków:-! # $% & ' * +/=? ^ '{}| ~

``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``wzorca: pasuje do wzorca warunkowego (kropka, po którym następuje nie kropka lub jedna z kilku znaków) zero lub więcej razy.

`@`wzorca: dopasowanie znaku @.

`(?<=[0-9a-z])`wzorca: Kontynuuj dopasowanie, jeśli znak, który poprzedza znak @, od A do Z, od a do z, lub od 0 do 9. Ten wzorzec definiuje pozytywną asercja wstecznaą o zerowej szerokości.

`(?(\[)`wzorca: Sprawdź, czy znak, który następuje po @ jest nawiasem otwierającym.

`(\[(\d{1,3}\.){3}\d{1,3}\])`wzorca: Jeśli jest to nawias otwierający, dopasowuje nawias otwierający, po którym następuje adres IP (cztery zestawy od jednej do trzech cyfr, z każdym zestawem oddzielonym kropką) i zamykającym nawiasem klamrowym.

`|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`wzorca: Jeśli znak, który następuje po @ nie jest nawiasem otwierającym, dopasowuje jeden znak alfanumeryczny o wartości A-Z, a-z, i 0-9, po którym następuje zero lub więcej wystąpień łącznika, po którym następuje zero lub jeden znak alfanumeryczny o wartości A-Z , a – z, lub 0-9, po którym następuje kropka. Ten wzorzec może być powtarzany jeden lub więcej razy i musi następować po nazwie domeny najwyższego poziomu.

`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`wzorca: nazwa domeny najwyższego poziomu musi rozpoczynać się i kończyć znakiem alfanumerycznym (a-z, A-Z i 0-9). Może również zawierać od zera do 22 znaków ASCII, które są alfanumeryczne lub łączniki.

`$`wzorca: kończy dopasowanie na końcu ciągu.

## <a name="compile-the-code"></a>Kompiluj kod

Metody `IsValidEmail` i `DomainMapper` mogą być zawarte w bibliotece metod narzędzia wyrażenia regularnego lub mogą być dołączane jako prywatne metody statyczne lub wystąpienia w klasie aplikacji.

Można również użyć metody <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType>, aby uwzględnić to wyrażenie regularne w bibliotece wyrażeń regularnych.

Jeśli są używane w bibliotece wyrażeń regularnych, można je wywoływać przy użyciu kodu, takiego jak:

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a>Zobacz także

- [.NET Framework wyrażeń regularnych](../../../docs/standard/base-types/regular-expressions.md)
