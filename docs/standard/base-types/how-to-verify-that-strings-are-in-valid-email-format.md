---
title: 'Instrukcje: Sprawdzanie, czy format poczty e-mail ciągów jest prawidłowy'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6381747bc998f73b374442fcb15e025ca15795d
ms.sourcegitcommit: 46c68557bf6395f0ab9915f7558f2faae0097695
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2019
ms.locfileid: "65589524"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Instrukcje: Sprawdzanie, czy format poczty e-mail ciągów jest prawidłowy
Poniższy przykład używa wyrażenia regularnego, aby sprawdzić, czy ciąg jest w prawidłowym formacie poczty e-mail.  

## <a name="example"></a>Przykład  
 W przykładzie zdefiniowano `IsValidEmail` metodę, która zwraca `true` wartość, jeśli ciąg zawiera prawidłowy adres e-mail, `false` a jeśli nie, ale nie przyjmuje żadnych innych akcji.  
  
 Aby sprawdzić, czy adres e-mail jest prawidłowy, `IsValidEmail` Metoda <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> wywołuje metodę ze `(@)(.+)$` wzorcem wyrażenia regularnego w celu oddzielenia nazwy domeny od adresu e-mail. Trzeci parametr jest <xref:System.Text.RegularExpressions.MatchEvaluator> delegatem, który reprezentuje metodę, która przetwarza i zastępuje dopasowany tekst. Wzorzec wyrażenia regularnego jest interpretowany w następujący sposób.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(@)`|Dopasowuje znak @. Jest to pierwsza grupa przechwytywania.|  
|`(.+)`|Dopasowuje jedno lub więcej wystąpień dowolnego znaku. Jest to druga grupa przechwytywania.|  
|`$`|Zakończ dopasowanie na końcu ciągu.|  
  
 Nazwa domeny wraz ze znakiem @ jest przenoszona do `DomainMapper` metody, która <xref:System.Globalization.IdnMapping> używa klasy do translacji znaków Unicode, które są spoza zakresu znaków US-ASCII do formacie Punycode. Metoda ustawia `invalid` również flagę na `True` , jeśli <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> metoda wykryje nieprawidłowe znaki w nazwie domeny. Metoda zwraca nazwę domeny formacie Punycode poprzedzoną symbolem @ do `IsValidEmail` metody.  
  
 `IsValidEmail` Metoda następnie<xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> wywołuje metodę, aby sprawdzić, czy adres jest zgodny ze wzorcem wyrażenia regularnego.  
  
 Należy pamiętać, `IsValidEmail` że metoda nie przeprowadza uwierzytelniania w celu zweryfikowania adresu e-mail. Określa on tylko, czy jego format jest prawidłowy dla adresu e-mail. Ponadto `IsValidEmail` Metoda nie sprawdza, czy nazwa domeny najwyższego poziomu jest prawidłową nazwą domeny wymienioną w [bazie danych strefy głównej programu Iana](https://www.iana.org/domains/root/db), co wymagałoby operacji wyszukiwania. Zamiast tego wyrażenie regularne sprawdza tylko, czy nazwa domeny najwyższego poziomu składa się z dwóch i dwudziestu czterech znaków ASCII, z znakami alfanumerycznymi i ostatnimi, a pozostałe znaki są alfanumeryczne lub łącznika (-).  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 W tym przykładzie wzorzec ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli. Należy zauważyć, że wyrażenie regularne jest kompilowane przy <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> użyciu flagi.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij dopasowanie na początku ciągu.|  
|`(?(")`|Określ, czy pierwszy znak jest znakiem cudzysłowu. `(?(")`jest początkiem konstrukcji warunkowej.|  
|`(?("")("".+?(?<!\\)""@)`|Jeśli pierwszy znak jest znakiem cudzysłowu, dopasowuje początkowy znak cudzysłowu, po którym następuje co najmniej jedno wystąpienie dowolnego znaku, po którym następuje znak cudzysłowu końcowego. Znak cudzysłowu końcowego nie może być poprzedzony znakiem ukośnika odwrotnego\\(). `(?<!`to początek asercja wsteczna negatywnej zerowej szerokości. Ciąg powinien zawierać znak (@).|  
|<code>&#124;(([0-9a-z]</code>|Jeśli pierwszy znak nie jest znakiem cudzysłowu, dopasowuje dowolny znak alfabetyczny od a do z lub od A do Z (w porównaniu z rozróżnianiem wielkości liter) lub dowolny znak numeryczny od 0 do 9.|  
|`(\.(?!\.))`|Jeśli następny znak jest kropką, Dopasuj go. Jeśli nie jest to okres, spójrz na następny znak i Kontynuuj dopasowanie. `(?!\.)`to nieujemne potwierdzenie o zerowej szerokości, które uniemożliwia wyświetlanie dwóch kolejnych okresów w lokalnej części adresu e-mail.|  
|<code>&#124;[-!#\$%&'\*\+/=\?\^\`{}&#124;~\w]</code>|Jeśli następny znak nie jest kropką, Dopasuj dowolny znak wyrazu lub jeden z następujących znaków:-! # $% ' * + =? ^\`{}&#124;~.|  
|<code>((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^\`{}&#124;~\w])*</code>|Dopasowuje wzorzec alternatywny (kropka, po którym następuje nieokreślony lub jeden z kilku znaków) zero lub więcej razy.|  
|`@`|Dopasowuje znak @.|  
|`(?<=[0-9a-z])`|Kontynuuj dopasowanie, jeśli znak, który poprzedza znak @, jest od A do z, od a do z, lub od 0 do 9. `(?<=[0-9a-z])` Konstrukcja definiuje pozytywną asercja wstecznaą o zerowej szerokości.|  
|`(?(\[)`|Sprawdź, czy znak, który następuje po @, jest otwierającym nawiasem klamrowym.|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|Jeśli jest to nawias otwierający, dopasowuje nawias otwierający, po którym następuje adres IP (cztery zestawy od jednej do trzech cyfr, z każdym zestawem oddzielony kropką) i nawias zamykający.|  
|<code>&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+</code>|Jeśli znak, który następuje po @ nie jest nawiasem otwierającym, dopasowuje jeden znak alfanumeryczny o wartości A-Z, a-z, lub 0-9, po którym następuje zero lub więcej wystąpień łącznika, po którym następuje zero lub jeden znak alfanumeryczny o wartości A-Z, a-z, lub 0-9 , po którym następuje kropka. Ten wzorzec może być powtarzany jeden lub więcej razy i musi następować po nazwie domeny najwyższego poziomu.|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|Nazwa domeny najwyższego poziomu musi rozpoczynać się i kończyć znakiem alfanumerycznym (a-z, A-Z i 0-9). Może również zawierać od zera do 22 znaków ASCII, które są alfanumeryczne lub łączniki.|  
|`$`|Zakończ dopasowanie na końcu ciągu.|  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Metody `IsValidEmail` i`DomainMapper` można dołączać do biblioteki metod narzędzia wyrażenia regularnego lub mogą być dołączane jako prywatne metody statyczne lub wystąpienia w klasie aplikacji.  
  
 Można również użyć <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metody do dołączenia tego wyrażenia regularnego do biblioteki wyrażeń regularnych.  
  
 Jeśli są używane w bibliotece wyrażeń regularnych, można je wywoływać przy użyciu kodu, takiego jak:  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
## <a name="see-also"></a>Zobacz także

- [.NET Framework wyrażeń regularnych](../../../docs/standard/base-types/regular-expressions.md)
