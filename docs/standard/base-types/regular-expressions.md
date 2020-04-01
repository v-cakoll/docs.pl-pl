---
title: .NET Framework — Wyrażenia regularne
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pattern-matching with regular expressions, about pattern-matching
- substrings
- searching with regular expressions, about regular expressions
- pattern-matching with regular expressions
- searching with regular expressions
- parsing text with regular expressions
- regular expressions [.NET Framework], about regular expressions
- regular expressions [.NET Framework]
- .NET Framework regular expressions, about
- characters [.NET Framework], regular expressions
- parsing text with regular expressions, overview
- .NET Framework regular expressions
- strings [.NET Framework], regular expressions
ms.assetid: 521b3f6d-f869-42e1-93e5-158c54a6895d
ms.openlocfilehash: 99a70fa1b56a45087ee380d063c66326976f5b41
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523794"
---
# <a name="net-regular-expressions"></a>Wyrażenia regularne platformy .NET

Wyrażenia regularne zapewniają wydajną, elastyczną i wydajną metodę przetwarzania tekstu. Obszerny notacja dopasowania wzorców wyrażeń regularnych umożliwia szybkie analizowanie dużych ilości tekstu w celu:

- Znajdź konkretne wzorce znaków.
- Sprawdź poprawność tekstu, aby upewnić się, że pasuje do wstępnie zdefiniowanego wzorca (takiego jak adres e-mail).
- Wyodrębnianie, edytowanie, zamienianie lub usuwanie podciągów tekstowych.
- Dodaj wyodrębnione ciągi do kolekcji w celu wygenerowania raportu.

W przypadku wielu aplikacji, które zajmują się ciągami lub analizują duże bloki tekstu, wyrażenia regularne są niezbędnym narzędziem.  
  
## <a name="how-regular-expressions-work"></a>Jak działają wyrażenia regularne

 Centralnym elementem przetwarzania tekstu za pomocą wyrażeń regularnych jest aparat <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> wyrażeń regularnych, który jest reprezentowany przez obiekt w .NET. Co najmniej przetwarzanie tekstu przy użyciu wyrażeń regularnych wymaga, aby aparat wyrażeń regularnych był wyposażony w następujące dwa elementy informacji:  
  
- Wzorzec wyrażenia regularnego do zidentyfikowania w tekście.  
  
     W .NET wzorce wyrażeń regularnych są definiowane przez specjalną składnię lub język, który jest zgodny z wyrażeniami regularnymi Perla 5 i dodaje kilka dodatkowych funkcji, takich jak dopasowywanie od prawej do lewej. Aby uzyskać więcej informacji, zobacz [Język wyrażenia regularnego — podręczna dokumentacja](regular-expression-language-quick-reference.md).  
  
- Tekst do przeanalizowania wzorca wyrażenia regularnego.  
  
Metody <xref:System.Text.RegularExpressions.Regex> klasy umożliwiają wykonywanie następujących operacji:  
  
- Określ, czy wzorzec wyrażenia regularnego <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> występuje w tekście wejściowym, wywołując metodę. Na przykład, który <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> używa metody sprawdzania poprawności tekstu, zobacz [Jak: Sprawdź, czy ciągi są w prawidłowym formacie wiadomości e-mail](how-to-verify-that-strings-are-in-valid-email-format.md).  
  
- Pobierz jedno lub wszystkie wystąpienia tekstu, który pasuje do <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> wzorca wyrażenia regularnego, wywołując lub metody. Pierwsza metoda zwraca <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> obiekt, który zawiera informacje o pasującym tekście. Ten ostatni <xref:System.Text.RegularExpressions.MatchCollection> zwraca obiekt, <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> który zawiera jeden obiekt dla każdego dopasowania znalezionego w analizowanym tekście.  
  
- Zamień tekst, który pasuje <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> do wzorca wyrażenia regularnego, wywołując metodę. Przykłady, które <xref:System.Text.RegularExpressions.Regex.Replace%2A> używają metody do zmiany formatów daty i usunięcia nieprawidłowych znaków z ciągu, zobacz [Jak: Paski nieprawidłowe znaki z ciągu](how-to-strip-invalid-characters-from-a-string.md) i [Przykład: Zmiana formatów daty](regular-expression-example-changing-date-formats.md).  
  
Aby zapoznać się z omówieniem modelu obiektu wyrażenia regularnego, zobacz [Model obiektu wyrażenia regularnego](the-regular-expression-object-model.md).  
  
Aby uzyskać więcej informacji na temat języka wyrażeń regularnych, zobacz [Język wyrażenia regularnego — podręczna dokumentacja](regular-expression-language-quick-reference.md) lub pobierz i wydrukuj jedną z tych broszur:  
  
- [Podręczna dokumentacja w formacie programu Word (docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [Podręczna dokumentacja w formacie PDF (pdf)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a>Przykłady wyrażeń regularnych

Klasa <xref:System.String> zawiera szereg metod wyszukiwania ciągów i zastępowania, których można użyć, gdy chcesz zlokalizować ciągi literału w większym ciągu. Wyrażenia regularne są najbardziej przydatne, gdy chcesz zlokalizować jeden z kilku podciągów w większym ciągu lub gdy chcesz zidentyfikować wzorce w ciągu, jak pokazują poniższe przykłady.

> [!TIP]
> Obszar <xref:System.Web.RegularExpressions> nazw zawiera wiele obiektów wyrażeń regularnych, które implementują wstępnie zdefiniowane wzorce wyrażeń regularnych do analizowania ciągów z dokumentów HTML, XML i ASP.NET. Na przykład <xref:System.Web.RegularExpressions.TagRegex> klasa identyfikuje tagi początkowe w <xref:System.Web.RegularExpressions.CommentRegex> ciągu, a klasa identyfikuje komentarze ASP.NET w ciągu.

### <a name="example-1-replace-substrings"></a>Przykład 1: Zamień podciągi  

 Załóżmy, że lista adresowa zawiera nazwy, które czasami zawierają tytuł (Mr., Mrs., Miss lub Ms.) wraz z imieniem i nazwiskiem. Jeśli nie chcesz dołączać tytułów podczas generowania etykiet kopert z listy, możesz użyć wyrażenia regularnego, aby usunąć tytuły, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Regex#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 Wzorzec `(Mr\.? |Mrs\.? |Miss |Ms\.? )` wyrażenia regularnego pasuje do każdego wystąpienia "Mr", "Mr. ", "Mrs", "Mrs. ", "Miss ", "Ms or "Ms. ". Wywołanie <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody zastępuje dopasowany ciąg <xref:System.String.Empty?displayProperty=nameWithType>za pomocą ; innymi słowy, usuwa go z oryginalnego ciągu.  
  
### <a name="example-2-identify-duplicated-words"></a>Przykład 2: Identyfikowanie zduplikowanych słów  

 Przypadkowe powielanie słów jest częstym błędem popełnianym przez autorów. Wyrażenie regularne może służyć do identyfikowania zduplikowanych słów, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Regex#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 Wzorzec `\b(\w+?)\s\1\b` wyrażenia regularnego można interpretować w następujący sposób:  
  
> [!div class="mx-tdCol2BreakAll"]
> |Wzorce|Interpretacja|  
> |-|-|
> |`\b`|Rozpoczyna na granicy wyrazu.|  
> |`(\w+?)`|Dopasuj jeden lub więcej znaków słownych, ale jak najmniej znaków. Razem tworzą grupę, która może `\1`być określona jako .|  
> |`\s`|Dopasowuje znak odstępu.|  
> |`\1`|Dopasuj podciąg, który `\1`jest równy grupie o nazwie .|  
> |`\b`|Dopasowuje granicę wyrazu.|  
  
 Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> jest wywoływana z opcjami wyrażenia regularnego ustawionymi na <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>. W związku z tym operacja dopasowania jest bez uwzględniania wielkości liter, a przykład identyfikuje podciąg "To to" jako powielania.  
  
 Należy zauważyć, że ciąg wejściowy zawiera podciąg "to? To". Jednakże ze względu na interpunkcyjny znak interpunkcyjny nie jest on określany jako powielanie.  
  
### <a name="example-3-dynamically-build-a-culture-sensitive-regular-expression"></a>Przykład 3: Dynamicznie budujemy wyrażenie regularne uwzględniające kulturę  

 Poniższy przykład ilustruje moc wyrażeń regularnych w połączeniu z elastycznością oferowaną przez program . Funkcje globalizacji NET. Używa <xref:System.Globalization.NumberFormatInfo> obiektu do określenia formatu wartości walut w bieżącej kulturze systemu. Następnie używa tych informacji do dynamicznego konstruowania wyrażenia regularnego, które wyodrębnia wartości waluty z tekstu. Dla każdego dopasowania wyodrębnia podgrupę, która zawiera tylko ciąg numeryczny, konwertuje go na <xref:System.Decimal> wartość i oblicza sumę bieżącą.  
  
 [!code-csharp[Conceptual.Regex#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 Na komputerze, którego bieżącą kulturą jest angielski - Stany Zjednoczone (en-US), przykład dynamicznie tworzy wyrażenie `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`regularne . Ten wzorzec wyrażenia regularnego można interpretować w następujący sposób:  

> [!div class="mx-tdCol2BreakAll"]
> |Wzorce|Interpretacja|  
> |-|-|  
> |`\$`|Poszukaj pojedynczego wystąpienia`$`symbolu dolara ( ) w ciągu wejściowym. Ciąg wzorca wyrażenia regularnego zawiera ukośnik odwrotny wskazujący, że symbol dolara ma być interpretowany dosłownie, a nie jako kotwica wyrażenia regularnego. (Sam `$` symbol oznacza, że aparat wyrażeń regularnych powinien próbować rozpocząć dopasowanie na końcu ciągu). Aby upewnić się, że symbol waluty bieżącej kultury nie jest błędnie <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> interpretowany jako symbol wyrażenia regularnego, w przykładzie wywołuje metodę ucieczki od znaku.|  
> |`\s*`|Poszukaj zero lub więcej wystąpień znaku odstępu.|  
> |`[-+]?`|Poszukaj zera lub jednego wystąpienia znaku dodatniego lub ujemnego.|  
> |`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|Nawiasy zewnętrzne wokół tego wyrażenia definiują go jako grupę przechwytywania lub wyrażenie podrzędne. Jeśli zostanie znaleziony dopasowania, informacje o tej części pasującego ciągu <xref:System.Text.RegularExpressions.Group> mogą <xref:System.Text.RegularExpressions.GroupCollection> być pobierane <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> z drugiego obiektu w obiekcie zwróconym przez właściwość. (Pierwszy element w kolekcji reprezentuje całe dopasowanie.)|  
> |`[0-9]{0,3}`|Poszukaj od zera do trzech wystąpień cyfr dziesiętnych od 0 do 9.|  
> |`(,[0-9]{3})*`|Poszukaj zero lub więcej wystąpień separatora grupy, po których następują trzy cyfry dziesiętne.|  
> |`\.`|Poszukaj pojedynczego wystąpienia separatora dziesiętnego.|  
> |`[0-9]+`|Poszukaj co najmniej jednej cyfry dziesiętnej.|  
> |`(\.[0-9]+)?`|Poszukaj zera lub jednego wystąpienia separatora dziesiętnego, po którym następuje co najmniej jedna cyfra dziesiętna.|  
  
 Jeśli każdy z tych podwzorów zostanie znaleziony w ciągu wejściowym, dopasowanie powiedzie się, a <xref:System.Text.RegularExpressions.Match> obiekt, który zawiera informacje o dopasowaniu jest dodawany do <xref:System.Text.RegularExpressions.MatchCollection> obiektu.  
  
## <a name="related-topics"></a>Powiązane tematy  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Język wyrażeń regularnych — podręczny wykaz](regular-expression-language-quick-reference.md)|Zawiera informacje o zestawie znaków, operatorów i konstrukcji, których można użyć do definiowania wyrażeń regularnych.|  
|[Model obiektów wyrażeń regularnych](the-regular-expression-object-model.md)|Zawiera informacje i przykłady kodu, które ilustrują, jak używać klas wyrażeń regularnych.|  
|[Szczegóły zachowania dotyczącego wyrażeń regularnych](details-of-regular-expression-behavior.md)|Zawiera informacje o możliwościach i zachowaniu wyrażeń regularnych platformy .NET.|
|[Używanie wyrażeń regularnych w programie Visual Studio](/visualstudio/ide/using-regular-expressions-in-visual-studio)||
  
## <a name="reference"></a>Tematy pomocy  

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
- [Wyrażenia regularne — podręczna dokumentacja (pobieranie w formacie Word)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [Wyrażenia regularne — podręczna dokumentacja (pobieranie w formacie PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
