---
title: 'Porady: sprawdzanie, czy format poczty e-mail ciągów jest prawidłowy'
ms.date: 03/30/2017
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
ms.openlocfilehash: 02c942dea3314581ce8f758bb9ed3ce88c2fe150
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Porady: sprawdzanie, czy format poczty e-mail ciągów jest prawidłowy
W poniższym przykładzie użyto wyrażenia regularnego, aby sprawdzić, czy ciąg w formacie prawidłowy adres e-mail.  

> [!NOTE]
>  Firma Microsoft zaleca używanie <xref:System.Net.Mail.MailAddress?displayProperty=nameWithType> klasy Sprawdź, czy ciąg w formacie adresu prawidłowy adres e-mail. Aby to zrobić, należy przekazać ciąg adresu e-mail do <xref:System.Net.Mail.MailAddress.%23ctor%28System.String%29?displayProperty=nameWithType> konstruktora klasy, która zgłasza <xref:System.FormatException> Jeśli ciąg ma nierozpoznany format.  
  
## <a name="example"></a>Przykład  
 W przykładzie zdefiniowano `IsValidEmail` metody, która zwraca `true` Jeśli ciąg zawiera prawidłowy adres e-mail i `false` Jeśli nie, ale nie podejmuje żadnych innych akcji.  
  
 Aby sprawdzić, czy adres e-mail jest prawidłowa, `IsValidEmail` wywołania metody <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> metody z `(@)(.+)$` wzorzec wyrażenia regularnego do Rozdziel nazwy domeny adresu e-mail. Trzeci parametr jest <xref:System.Text.RegularExpressions.MatchEvaluator> delegata, który reprezentuje metodę, która przetwarza i zastępuje dopasowanego tekstu. Wzorzec wyrażenia regularnego jest interpretowana w następujący sposób.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`(@)`|Dopasowanie znaku @. Jest to pierwsza grupa przechwytywania.|  
|`(.+)`|Odpowiada jedno lub więcej wystąpień dowolnego znaku. Jest to druga grupa przechwytywania.|  
|`$`|Zakończenie dopasowuje koniec ciągu.|  
  
 Nazwa domeny wraz z programem znaku @ jest przekazywana do `DomainMapper` metodę, która używa <xref:System.Globalization.IdnMapping> klasy tłumaczenie znaków Unicode, które są poza zakresem znak US-ASCII na ciąg Punycode. Ustawia również metoda `invalid` flaga `True` Jeśli <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> metody wykrywa nieprawidłowych znaków w nazwie domeny. Metoda zwraca poprzedzona nazwą domeny Punycode @ symbol `IsValidEmail` metody.  
  
 `IsValidEmail` Metoda wywołuje <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> metodę, aby zweryfikować, że adres jest zgodny ze wzorcem wyrażenia regularnego.  
  
 Należy pamiętać, że `IsValidEmail` — metoda nie przeprowadza uwierzytelniania Sprawdź poprawność adresu e-mail. Określa jedynie, czy jego format jest nieprawidłowy dla adresu e-mail. Ponadto `IsValidEmail` — metoda sprawdza, czy nazwa domeny najwyższego poziomu nie jest prawidłową nazwę domeny wymienione na [bazy danych przez organizację IANA katalogu głównego strefy](https://www.iana.org/domains/root/db), które wymagałyby operacji wyszukiwania. Zamiast tego wyrażenia regularnego jedynie sprawdza, czy nazwa domeny najwyższego poziomu składa się z od dwóch do 24 znaków ASCII, znaki alfanumeryczne imię i nazwisko i pozostałe znaki alfanumeryczne lub a łącznikiem (-).  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 W tym przykładzie wzorzec wyrażenia regularnego ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` jest interpretowany, jak pokazano w poniższej tabeli. Należy pamiętać, że wyrażenie regularne jest skompilowana przy użyciu <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flagi.  
  
|Wzorzec|Opis|  
|-------------|-----------------|  
|`^`|Rozpocznij dopasowania na początku ciąg.|  
|`(?(")`|Ustal, czy pierwszy znak jest znak cudzysłowu. `(?(")` jest początek konstrukcji wyrażenia warunkowe.|  
|`(?("")("".+?(?<!\\)""@)`|Jeśli pierwszym znakiem jest znak cudzysłowu, zgodne cudzysłów początku następuje co najmniej jedno wystąpienie dowolny znak, następuje końcowy znak cudzysłowu. Końcowy znak cudzysłowu nie musi być poprzedzona znakiem ukośnika odwrotnego (\\). `(?<!` jest na początku potwierdzenia ujemne wybieganie wstecz zerowej szerokości. Ciąg powinien zawierać z znak @ (@).|  
|<code>&#124;(([0-9a-z]</code>|Jeśli pierwszy znak nie jest znak cudzysłowu, dopasowuje dowolny znak alfabetyczne, od do z i od A do Z (porównanie nie uwzględnia wielkości liter) lub dowolnego znaku numerycznego od 0 do 9.|  
|`(\.(?!\.))`|Jeśli następny znak jest okres, jest zgodny. Jeśli nie jest to okres, wyszukiwać na następny znak i kontynuować dopasowania. `(?!\.)` to potwierdzenie wyprzedzenia ujemna zerowej szerokości, uniemożliwiający dwóch następujących po sobie kropek znajdujących się w lokalnym części adresu e-mail.|  
|<code>&#124;[-!#\$%&'\*\+/=\?\^\`{}\&#124;~\w]</code>|Jeśli następny znak nie jest okres, zgodne dowolny znak słowa lub jeden z następujących znaków:-! #$% "* +=? ^\`{}&#124;~.|  
|<code>((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^\`{}\&#124;~\w])*</code>|Jest zgodna z wzorcem wyrażenia warunkowe (okres następuje z systemem innym niż okres lub jeden z wielu znaków) zero lub więcej razy.|  
|`@`|Dopasowanie znaku @.|  
|`(?<=[0-9a-z])`|Kontynuować dopasowania, jeśli znak poprzedza znaku @ jest od A do Z, do z i od 0 do 9. `(?<=[0-9a-z])` Konstrukcja definiuje potwierdzenia dodatnie wybieganie wstecz zerowej szerokości.|  
|`(?(\[)`|Sprawdź, czy znak znajdujący się @ nawiasem otwierającym.|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|Jeśli jest otwierający nawias kwadratowy, odpowiadać następuje adres IP (cztery zestawy jednej do trzech cyfr, z każdego zestawu oddzielona kropką) i zamykający nawias kwadratowy otwierający nawias kwadratowy.|  
|<code>&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+</code>|Jeśli znak znajdujący się @ nie jest otwierający nawias kwadratowy, jeden znak alfanumeryczny dopasowanie z wartością A-Z, a-z lub 0-9, a następnie zero lub więcej wystąpień łącznik, a następnie zero lub jeden znak alfanumeryczny o wartości A-Z, a-z lub 0-9 , a następnie kropki. Ten wzorzec można powtarzać jeden lub więcej razy, a musi następować nazwa domeny najwyższego poziomu.|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|Nazwa domeny najwyższego poziomu musi rozpoczynać i kończyć się znakiem alfanumerycznym (a – z, A-Z i 0 – 9). Mogą również obejmować od 0 do 22 znaki ASCII, które są alfanumeryczne i łączniki.|  
|`$`|Zakończenie dopasowuje koniec ciągu.|  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 `IsValidEmail` i `DomainMapper` metody mogą być zawarte w bibliotece metody narzędziowe wyrażenie regularne lub jako prywatny statyczny lub wystąpienie metody w klasie aplikacji mogą być uwzględnione.  
  
 Aby uwzględnić je w bibliotece wyrażenie regularne, albo i Wklej kod do projektu biblioteki klas w usłudze Visual Studio, lub skopiować i wkleić go do pliku tekstowego i skompiluj go z poziomu wiersza polecenia przy użyciu polecenia w następujący (przy założeniu, że nazwa kodu źródłowego  plik jest RegexUtilities.cs lub RegexUtilities.vb:  
  
```csharp  
csc /t:library RegexUtilities.cs  
```  
  
```vb  
vbc /t:library RegexUtilities.vb  
```  
  
 Można również użyć <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metodę w celu uwzględnienia tej wyrażenie regularne w bibliotece wyrażenia regularnego.  
  
 Jeśli są używane w bibliotece wyrażenie regularne, należy wywołać je przy użyciu kodu, takie jak następujące:  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
 Zakładając, że po utworzeniu biblioteki klas o nazwie RegexUtilities.dll zawierający wyrażenia regularnego sprawdzania poprawności poczty e-mail, będzie można kompilować w tym przykładzie w jednym z następujących sposobów:  
  
-   W programie Visual Studio, tworzenie aplikacji konsoli i dodać odwołanie do RegexUtilities.dll do projektu.  
  
-   W wierszu polecenia, kopiowanie i wklejanie kodu źródłowego w pliku tekstowym i kompilowania go za pomocą polecenia podobnie do następującej (przy założeniu, że nazwa pliku źródła kodu jest Example.cs lub Example.vb:  
  
    ```csharp  
    csc Example.cs /r:RegexUtilities.dll  
    ```  
  
    ```vb  
    vbc Example.vb /r:RegexUtilities.dll  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [.NET framework — nieprawidłowe wyrażenia](../../../docs/standard/base-types/regular-expressions.md)
