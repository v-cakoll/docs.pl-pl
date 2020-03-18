---
title: Sprawdzanie, czy format poczty e-mail ciągów jest prawidłowy
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
ms.openlocfilehash: c02fc215fa66951ae3333175191ab96a226a2afe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73197583"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Sprawdzanie, czy format poczty e-mail ciągów jest prawidłowy

W poniższym przykładzie użyto wyrażenia regularnego, aby sprawdzić, czy ciąg jest w prawidłowym formacie wiadomości e-mail.

## <a name="example"></a>Przykład

W przykładzie definiuje `IsValidEmail` metodę, `true` która zwraca, jeśli ciąg `false` zawiera prawidłowy adres e-mail, a jeśli nie, ale nie podejmuje żadnej innej akcji.

Aby sprawdzić, czy adres e-mail jest prawidłowy, `IsValidEmail` metoda wywołuje <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> metodę z wzorcem `(@)(.+)$` wyrażenia regularnego, aby oddzielić nazwę domeny od adresu e-mail. Trzeci parametr jest <xref:System.Text.RegularExpressions.MatchEvaluator> pełnomocnikiem, który reprezentuje metodę, która przetwarza i zastępuje dopasowany tekst. Wzorzec wyrażenia regularnego jest interpretowany w następujący sposób.

|Wzorce|Opis|
|-------------|-----------------|
|`(@)`|Dopasuj znak @. Jest to pierwsza grupa przechwytywania.|
|`(.+)`|Dopasuj jedno lub więcej wystąpień dowolnego znaku. Jest to druga grupa przechwytywania.|
|`$`|Zakończ dopasowanie na końcu ciągu.|

Nazwa domeny wraz ze znakiem `DomainMapper` @ jest przekazywana do metody, która używa <xref:System.Globalization.IdnMapping> klasy do tłumaczenia znaków Unicode, które znajdują się poza zakresem znaków US-ASCII na Punycode. Metoda ustawia również `invalid` flagę, `True` <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> jeśli metoda wykryje nieprawidłowe znaki w nazwie domeny. Metoda zwraca nazwę domeny Punycode poprzedzoną symbolem @ do `IsValidEmail` metody.

Metoda `IsValidEmail` następnie wywołuje <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> metodę, aby sprawdzić, czy adres jest zgodny z wzorcem wyrażenia regularnego.

Należy zauważyć, że `IsValidEmail` metoda nie wykonuje uwierzytelniania w celu zweryfikowania adresu e-mail. Określa jedynie, czy jego format jest ważny dla adresu e-mail. Ponadto `IsValidEmail` metoda nie sprawdza, czy nazwa domeny najwyższego poziomu jest prawidłową nazwą domeny wymienioną w [bazie danych strefy głównej IANA](https://www.iana.org/domains/root/db), co wymagałoby operacji wyszukiwania. Zamiast tego wyrażenie regularne jedynie sprawdza, czy nazwa domeny najwyższego poziomu składa się z dwóch do dwudziestu czterech znaków ASCII, z alfanumerycznymi pierwszymi i ostatnimi znakami, a pozostałe znaki są alfanumeryczne lub łącznik (-).

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

W tym przykładzie wzorzec ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej legendzie. Wyrażenie regularne jest kompilowane <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> przy użyciu flagi.

Wzór `^`: Rozpocznij dopasowanie na początku ciągu.

Wzorzec `(?(")`: Określ, czy pierwszy znak jest cudzysłowem. `(?(")`to początek konstrukcji naprzemiennej.

Wzorzec `(?(")(".+?(?<!\\)"@)`: Jeśli pierwszy znak jest cudzysłowem, dopasuj początkowy cudzysłów, po którym następuje co najmniej jedno wystąpienie dowolnego znaku, po którym następuje końcowy cudzysłów. Końcowy cudzysłów nie może być poprzedzony znakiem ukośnika odwrotnego (\\). `(?<!`jest początkiem ujemnego potwierdzenia lookbehind o zerowej szerokości. Ciąg powinien zakończyć się znakiem at (@).

Wzorzec: `|(([0-9a-z]`Jeśli pierwszy znak nie jest cudzysłowem, dopasuj dowolny znak alfabetyczny od a do z lub Od A do Z (porównanie jest bez uwzględniania wielkości liter) lub dowolny znak liczbowy od 0 do 9.

Wzór `(\.(?!\.))`: Jeśli następny znak jest kropką, dopasuj go. Jeśli nie jest to kropka, spójrz w przyszłość na następny znak i kontynuuj dopasowanie. `(?!\.)`jest potwierdzeniem ujemnym wyglądem o zerowej szerokości, które uniemożliwia pojawienie się dwóch kolejnych okresów w lokalnej części adresu e-mail.

``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``Wzorzec : Jeśli następny znak nie jest kropką, dopasuj dowolny\*znak wyrazu\`{}lub jeden z następujących znaków: -!#$%&' +/=?^ |~

Wzorzec ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``: Dopasuj wzorzec naprzemienny (kropka, po której następuje okres nieokresowy lub jeden z wielu znaków) zero lub więcej razy.

Wzorzec `@`: Dopasuj znak @.

Wzorzec `(?<=[0-9a-z])`: Kontynuuj dopasowanie, jeśli znak, który poprzedza znak @ to Od A do Z, od a do z lub od 0 do 9. Ten wzorzec definiuje potwierdzenie patrzące z dodatnim wynikiem o zerowej szerokości.

Wzorzec `(?(\[)`: Sprawdź, czy poznawanym znakiem @ jest nawias otwierający.

Wzór `(\[(\d{1,3}\.){3}\d{1,3}\])`: Jeśli jest to nawias otwierający, dopasuj nawias otwierający, po którym następuje adres IP (cztery zestawy od jednej do trzech cyfr, z każdym zestawem oddzielonym kropką) i nawiaszamykający.

Wzorzec `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`: Jeśli poznawasię znak @ nie jest nawiasem otwierającym, dopasuj jeden znak alfanumeryczny do wartości A-Z, a-z lub 0-9, po którym następuje zero lub więcej wystąpień łącznika, po którym następuje zero lub jeden znak alfanumeryczny o wartości A-Z, a-z lub 0-9, po którym następuje kropka. Ten wzorzec można powtórzyć jeden lub więcej razy i musi następuje po nazwie domeny najwyższego poziomu.

Wzorzec: `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`Nazwa domeny najwyższego poziomu musi zaczynać się i kończyć znakiem alfanumerycznym (a-z, A-Z i 0-9). Może również zawierać od zera do 22 znaków ASCII, które są alfanumeryczne lub łączniki.

Wzorzec `$`: Zakończenie dopasowania na końcu ciągu.

## <a name="compile-the-code"></a>Skompiluj kod

Metody `IsValidEmail` `DomainMapper` i mogą być zawarte w bibliotece metod narzędzia wyrażeń regularnych lub mogą być zawarte jako prywatne metody statyczne lub wystąpienia w klasie aplikacji.

Można również użyć <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> tej metody, aby uwzględnić to wyrażenie regularne w bibliotece wyrażeń regularnych.

Jeśli są one używane w bibliotece wyrażeń regularnych, można wywołać je przy użyciu kodu, takiego jak:

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a>Zobacz też

- [.NET Framework — Wyrażenia regularne](../../../docs/standard/base-types/regular-expressions.md)
