---
title: Sprawdzanie, czy format poczty e-mail ciągów jest prawidłowy
description: Zapoznaj się z przykładem, jak wyrażenie regularne sprawdza, czy ciągi są w prawidłowym formacie poczty e-mail w programie .NET.
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
ms.openlocfilehash: 47ef4dedd20a2b885abaabf72c26de5f3312c66f
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768966"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Sprawdzanie, czy format poczty e-mail ciągów jest prawidłowy

Poniższy przykład używa wyrażenia regularnego, aby sprawdzić, czy ciąg jest w prawidłowym formacie poczty e-mail.

## <a name="example"></a>Przykład

W przykładzie zdefiniowano `IsValidEmail` metodę, która zwraca wartość, `true` Jeśli ciąg zawiera prawidłowy adres e-mail `false` , a jeśli nie, ale nie przyjmuje żadnych innych akcji.

Aby sprawdzić, czy adres e-mail jest prawidłowy, `IsValidEmail` Metoda wywołuje <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> metodę ze `(@)(.+)$` wzorcem wyrażenia regularnego w celu oddzielenia nazwy domeny od adresu e-mail. Trzeci parametr jest <xref:System.Text.RegularExpressions.MatchEvaluator> delegatem, który reprezentuje metodę, która przetwarza i zastępuje dopasowany tekst. Wzorzec wyrażenia regularnego jest interpretowany w następujący sposób.

|Wzorce|Opis|
|-------------|-----------------|
|`(@)`|Dopasowuje znak @. Jest to pierwsza grupa przechwytywania.|
|`(.+)`|Dopasowuje jedno lub więcej wystąpień dowolnego znaku. Jest to druga grupa przechwytywania.|
|`$`|Zakończ dopasowanie na końcu ciągu.|

Nazwa domeny wraz ze znakiem @ jest przenoszona do `DomainMapper` metody, która używa <xref:System.Globalization.IdnMapping> klasy do translacji znaków Unicode, które są spoza zakresu znaków US-ASCII do formacie Punycode. Metoda ustawia również `invalid` flagę na, `True` Jeśli <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> Metoda wykryje nieprawidłowe znaki w nazwie domeny. Metoda zwraca nazwę domeny formacie Punycode poprzedzoną symbolem @ do `IsValidEmail` metody.

`IsValidEmail`Metoda następnie wywołuje metodę, <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> Aby sprawdzić, czy adres jest zgodny ze wzorcem wyrażenia regularnego.

Należy pamiętać, że `IsValidEmail` Metoda nie przeprowadza uwierzytelniania w celu zweryfikowania adresu e-mail. Określa on tylko, czy jego format jest prawidłowy dla adresu e-mail. Ponadto `IsValidEmail` Metoda nie sprawdza, czy nazwa domeny najwyższego poziomu jest prawidłową nazwą domeny wymienioną w [bazie danych strefy głównej programu Iana](https://www.iana.org/domains/root/db), co wymagałoby operacji wyszukiwania. Zamiast tego wyrażenie regularne sprawdza tylko, czy nazwa domeny najwyższego poziomu składa się z dwóch i dwudziestu czterech znaków ASCII, z znakami alfanumerycznymi i ostatnimi, a pozostałe znaki są alfanumeryczne lub łącznika (-).

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

W tym przykładzie wzorzec wyrażenia regularnego ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` jest interpretowany jak pokazano w poniższej legendzie. Wyrażenie regularne jest kompilowane przy użyciu <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flagi.

Wzorzec `^` : Rozpocznij dopasowanie na początku ciągu.

Wzorzec `(?(")` : określa, czy pierwszy znak jest znakiem cudzysłowu. `(?(")`jest początkiem konstrukcji warunkowej.

Wzorzec `(?(")(".+?(?<!\\)"@)` : Jeśli pierwszy znak jest znakiem cudzysłowu, dopasowuje początkowy znak cudzysłowu, po którym następuje co najmniej jedno wystąpienie dowolnego znaku, po którym następuje znak cudzysłowu końcowego. Znak cudzysłowu końcowego nie może być poprzedzony znakiem ukośnika odwrotnego ( \\ ). `(?<!`to początek asercja wsteczna negatywnej zerowej szerokości. Ciąg powinien zawierać znak (@).

Wzorzec `|(([0-9a-z]` : Jeśli pierwszy znak nie jest znakiem cudzysłowu, dopasowuje dowolny znak alfabetyczny od a do z lub od a do z (w porównaniu z rozróżnianiem wielkości liter) lub dowolny znak numeryczny od 0 do 9.

Wzorzec `(\.(?!\.))` : Jeśli następny znak jest kropką, Dopasuj go. Jeśli nie jest to okres, spójrz na następny znak i Kontynuuj dopasowanie. `(?!\.)`to nieujemne potwierdzenie o zerowej szerokości, które uniemożliwia wyświetlanie dwóch kolejnych okresów w lokalnej części adresu e-mail.

Wzorzec ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]`` : Jeśli następny znak nie jest kropką, dopasowuje dowolny znak słowa lub jeden z następujących znaków:-! # $% & ' \* +/=? ^ \` {} | ~

Wzorzec ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*`` : dopasowuje wzorzec alternatywny (kropka, po którym następuje nieokreślony lub jeden z kilku znaków) zero lub więcej razy.

Wzorzec `@` : dopasowanie znaku @.

Wzorzec `(?<=[0-9a-z])` : Kontynuuj dopasowanie, jeśli znak poprzedzający znak @ ma wartość od a do z, od a do z, lub od 0 do 9. Ten wzorzec definiuje pozytywną asercja wstecznaą o zerowej szerokości.

Wzorzec `(?(\[)` : Sprawdź, czy znak, który następuje po @ jest nawiasem otwierającym.

Wzorzec `(\[(\d{1,3}\.){3}\d{1,3}\])` : Jeśli jest to nawias otwierający, dopasowuje nawias otwierający, po którym następuje adres IP (cztery zestawy od jednej do trzech cyfr, z każdym zestawem oddzielony kropką) i nawias zamykający.

Wzorzec `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+` : Jeśli znak, który następuje po @ nie jest nawiasem otwierającym, dopasowuje jeden znak alfanumeryczny o wartości a-Z, a-z, lub 0-9, po którym następuje zero lub więcej wystąpień łącznika, po którym następuje zero lub jeden znak alfanumeryczny o wartości a-z, a-z, i 0-9, po którym następuje kropka. Ten wzorzec może być powtarzany jeden lub więcej razy i musi następować po nazwie domeny najwyższego poziomu.

Wzorzec `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))` : nazwa domeny najwyższego poziomu musi rozpoczynać się i kończyć znakiem alfanumerycznym (a-z, a-z i 0-9). Może również zawierać od zera do 22 znaków ASCII, które są alfanumeryczne lub łączniki.

Wzorzec `$` : kończy dopasowanie na końcu ciągu.

## <a name="compile-the-code"></a>Kompiluj kod

`IsValidEmail`Metody i `DomainMapper` można dołączać do biblioteki metod narzędzia wyrażenia regularnego lub mogą być dołączane jako prywatne metody statyczne lub wystąpienia w klasie aplikacji.

Można również użyć <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metody do dołączenia tego wyrażenia regularnego do biblioteki wyrażeń regularnych.

Jeśli są używane w bibliotece wyrażeń regularnych, można je wywoływać przy użyciu kodu, takiego jak:

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a>Zobacz też

- [.NET Framework — Wyrażenia regularne](regular-expressions.md)
