---
title: 'Porady: sprawdzanie, czy format poczty e-mail ciągów jest prawidłowy'
ms.date: 08/10/2018
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
ms.openlocfilehash: 1fe0ead93d1ff2b7867a52d80cf812e2850ea7b3
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44338431"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Porady: sprawdzanie, czy format poczty e-mail ciągów jest prawidłowy
W poniższym przykładzie użyto wyrażenia regularnego, aby sprawdzić, czy ciąg jest w prawidłowym formacie adresu e-mail.  

## <a name="example"></a>Przykład  
 W przykładzie zdefiniowano `IsValidEmail` metody, która zwraca `true` Jeśli ciąg zawiera prawidłowy adres e-mail i `false` Jeśli nie, ale bez podejmowania żadnych innych działań.  
  
 Aby sprawdzić, czy adres e-mail jest prawidłowy, `IsValidEmail` wywołania metody <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> metody z `(@)(.+)$` wzorzec wyrażenia regularnego, aby oddzielić nazwę domeny od adresu e-mail. Trzeci parametr jest <xref:System.Text.RegularExpressions.MatchEvaluator> delegata, który reprezentuje metodę, która przetwarza i zastępuje dopasowany tekst. Definicję wzorca wyrażenia regularnego jest interpretowany w następujący sposób.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(@)`|Dopasowania znaku @. Jest to pierwsza grupa przechwytywania.|  
|`(.+)`|Dopasowuje jedno lub więcej wystąpień dowolnego znaku. Jest to druga grupa przechwytywania.|  
|`$`|Dopasowywanie kończy się na końcu ciągu.|  
  
 Nazwa domeny wraz ze znakiem @ jest przekazywana do `DomainMapper` metodę, która używa <xref:System.Globalization.IdnMapping> klasy do translacji znaków Unicode, które są spoza zakresu znaków US-ASCII do Punycode. Metoda ustawia również `invalid` flaga `True` Jeśli <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> metoda wykrywa nieprawidłowe znaki w nazwie domeny. Metoda ta zwraca nazwę domeny Punycode poprzedzoną przez symbol @ do `IsValidEmail` metody.  
  
 `IsValidEmail` Następnie wywołuje metodę <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> metodę, aby sprawdzić, czy adres jest zgodny z wzorcem wyrażenia regularnego.  
  
 Należy pamiętać, że `IsValidEmail` metoda nie wykonuje uwierzytelniania, aby sprawdzić poprawność adresu e-mail. Określa jedynie, czy jego format jest prawidłowy dla adresu e-mail. Ponadto `IsValidEmail` metoda nie sprawdza, czy nazwa domeny najwyższego poziomu jest prawidłową nazwą domeny wymienioną w [bazie danych strefy głównej IANA](https://www.iana.org/domains/root/db), co wymagałoby operacji wyszukiwania. Zamiast tego wyrażenie regularne sprawdza jedynie, że nazwa domeny najwyższego poziomu składa się z od dwóch do dwudziestu czterech znaków ASCII, znaki alfanumeryczne imię i nazwisko i pozostałe znaki alfanumeryczne lub a łącznikiem (-).  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 W tym przykładzie wzorzec wyrażenia regularnego ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` jest interpretowane tak jak pokazano w poniższej tabeli. Należy pamiętać, że wyrażenie regularne jest kompilowane przy użyciu <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flagi.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpoczyna dopasowanie na początku ciągu.|  
|`(?(")`|Ustal, czy pierwszym znakiem jest znak cudzysłowu. `(?(")` to początek początkiem konstrukcji.|  
|`(?("")("".+?(?<!\\)""@)`|Jeśli pierwszym znakiem jest znak cudzysłowu, Dopasuj do początkowego znaku cudzysłowu, a następnie co najmniej jedno wystąpienie dowolnego znaku, w którym następuje końcowy znak cudzysłowu. Końcowy znak cudzysłowu nie muszą być poprzedzone znakiem ukośnika odwrotnego (\\). `(?<!` to początek asercja negatywna asercja wsteczna o zerowej szerokości. Ciąg powinien być zakończony znakiem (@).|  
|<code>&#124;(([0-9a-z]</code>|Jeśli pierwszy znak nie jest znakiem cudzysłowu, Dopasuj dowolny znaku alfabetyczny od do z i od A do Z (wynik porównania jest uwzględniana wielkość liter) lub dowolną cyfrę z zakresu od 0 do 9.|  
|`(\.(?!\.))`|Jeśli następny znak jest kropką, Dopasuj do niego. Jeśli nie jest to okres, przód na następny znak i kontynuuje dopasowywanie. `(?!\.)` jest to asercja negatywna asercja wyprzedzająca o zerowej szerokości, która zapobiega wyświetlaniu w lokalnym składniku adresu e-mail dwóch następujących po sobie kropek.|  
|<code>&#124;[-!#\$%&'\*\+/=\?\^\`{}\&#124;~\w]</code>|Jeśli następny znak nie jest kropką, Dopasuj dowolny znak słowa lub jednego z następujących znaków:-! #$% ' * +=? ^\`{}&#124;~.|  
|<code>((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^\`{}\&#124;~\w])*</code>|Dopasowania wzorca naprzemiennego (kropki następuje znak inny niż kropka, lub jeden z wielu znaków) zero lub więcej razy.|  
|`@`|Dopasowania znaku @.|  
|`(?<=[0-9a-z])`|Kontynuuje dopasowywanie, jeśli znak, który poprzedza znak @, jest od A do Z, do z lub od 0 do 9. `(?<=[0-9a-z])` Konstrukcja definiuje potwierdzenia dodatnie asercje wsteczne o zerowej szerokości.|  
|`(?(\[)`|Sprawdź, czy znak, który następuje po @, jest nawiasem otwierającym.|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|Jeśli jest to nawias otwierający, Dopasuj do nawiasu otwierającego, w którym następuje adres IP (cztery zestawy od jednej do trzech cyfr, z każdym zestawem oddzielony kropką) i nawias zamykający.|  
|<code>&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+</code>|Jeśli znak, który następuje po @ nie jest otwierającym nawiasem, Dopasuj jeden znak alfanumeryczny o wartości A-Z, a-z lub 0-9, następuje zero lub więcej wystąpień łącznika, następuje zero lub jeden znak alfanumeryczny o wartości A-Z, a-z lub 0-9 , następuje kropka. Ten wzorzec można powtórzyć raz lub więcej razy, a musi następować nazwa domeny najwyższego poziomu.|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|Nazwa domeny najwyższego poziomu musi rozpoczynać się i kończyć się znakiem alfanumerycznym (a – z, A-Z i 0 – 9). Może również zawierać od 0 do 22 znaków ASCII, które są albo alfanumeryczne i łączniki.|  
|`$`|Dopasowywanie kończy się na końcu ciągu.|  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 `IsValidEmail` i `DomainMapper` metody mogą być zawarte w bibliotece metod narzędziowych wyrażenia regularnego lub one mogą być zawarte jako prywatna statyczna lub metoda instancji w klasie aplikacji.  
  
 Aby uwzględnić je w bibliotece wyrażeń regularnych, wartość i Wklej kod do projektu biblioteki klas w usłudze Visual Studio, lub skopiować i wkleić go do pliku tekstowego i skompiluj go z poziomu wiersza polecenia przy użyciu polecenia podobnego do poniższego (przy założeniu, że nazwa kodu źródłowego  plik jest RegexUtilities.cs lub RegexUtilities.vb:  
  
```csharp  
csc /t:library RegexUtilities.cs  
```  
  
```vb  
vbc /t:library RegexUtilities.vb  
```  
  
 Można również użyć <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metodę, aby uwzględnić tego wyrażenia regularnego w bibliotece wyrażeń regularnych.  
  
 Jeśli są one używane w bibliotece wyrażeń regularnych, możesz je wywołać przy użyciu kodu, takie jak następujące:  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
 Przy założeniu, że utworzono biblioteki klas o nazwie RegexUtilities.dll, który zawiera wyrażenie regularne sprawdzanie poprawności poczty e-mail, można kompilować ten przykład w jeden z następujących sposobów:  
  
-   W programie Visual Studio, tworząc aplikację Konsolową w języku i dodanie odwołania do RegexUtilities.dll do projektu.  
  
-   W wierszu polecenia przez kopiowanie i wklejanie kodu źródłowego do pliku tekstowego i kompilowania go za pomocą polecenia podobnego do poniższego (przy założeniu, że nazwa pliku źródła kodu jest Example.cs lub Example.vb:  
  
    ```csharp  
    csc Example.cs /r:RegexUtilities.dll  
    ```  
  
    ```vb  
    vbc Example.vb /r:RegexUtilities.dll  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażeń regularnych programu .NET framework](../../../docs/standard/base-types/regular-expressions.md)
