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
ms.openlocfilehash: ac034ff37b0b39f41d6f58381286706f9a9ac602
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121705"
---
# <a name="net-regular-expressions"></a>Wyrażenia regularne .NET
Wyrażenia regularne zapewniają zaawansowaną, elastyczną i wydajną metodę przetwarzania tekstu. Obszerna notacja dopasowywania wzorców wyrażeń regularnych umożliwia szybkie analizowanie dużych ilości tekstu w celu znalezienia określonych wzorców znaków; aby sprawdzić poprawność tekstu, aby upewnić się, że pasuje on do wstępnie zdefiniowanego wzorca (takiego jak adres e-mail); wyodrębnianie, edytowanie, zamienianie lub usuwanie podciągów tekstowych; i dodać wyodrębnione ciągi do kolekcji w celu wygenerowania raportu. Dla wielu aplikacji, które zajmują się ciągami lub które analizują duże bloki tekstu, wyrażenia regularne są niezbędnym narzędziem.  
  
## <a name="how-regular-expressions-work"></a>Sposób, a jaki działają wyrażenia regularne  
 Centralnym elementem przetwarzania tekstu z wyrażeniami regularnymi jest aparat <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> wyrażeń regularnych, który jest reprezentowany przez obiekt w .NET. Przetwarzanie tekstu przy użyciu wyrażeń regularnych wymaga, aby aparat wyrażeń regularnych był dostarczany z następującymi dwoma elementami informacji:  
  
- Wzorzec wyrażenia regularnego do zidentyfikowania w tekście.  
  
     W .NET wzorce wyrażeń regularnych są definiowane przez specjalną składnię lub język, który jest zgodny z wyrażeniami regularnymi Perl 5 i dodaje kilka dodatkowych funkcji, takich jak dopasowanie od prawej do lewej. Aby uzyskać więcej informacji, zobacz [Język wyrażenia regularnego — podręczny numer referencyjny](regular-expression-language-quick-reference.md).  
  
- Tekst do przeanalizowania wzorca wyrażenia regularnego.  
  
 Metody <xref:System.Text.RegularExpressions.Regex> klasy umożliwiają wykonywanie następujących operacji:  
  
- Określ, czy wzorzec wyrażenia regularnego <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> występuje w tekście wejściowym, wywołując metodę. Na przykład, który <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> używa metody sprawdzania poprawności tekstu, zobacz [Jak: Sprawdź, czy ciągi są w prawidłowym formacie wiadomości e-mail](how-to-verify-that-strings-are-in-valid-email-format.md).  
  
- Pobierz jedno lub wszystkie wystąpienia tekstu, który pasuje <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> do <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> wzorca wyrażenia regularnego, wywołując lub metody. Poprzednia metoda <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> zwraca obiekt, który zawiera informacje o pasującego tekstu. Ten ostatni <xref:System.Text.RegularExpressions.MatchCollection> zwraca obiekt, <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> który zawiera jeden obiekt dla każdego dopasowania znalezione w przeanalizowanym tekście.  
  
- Zamień tekst, który pasuje <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> do wzorca wyrażenia regularnego, wywołując metodę. Przykłady, które używają <xref:System.Text.RegularExpressions.Regex.Replace%2A> metody do zmiany formatów dat i usunięcia nieprawidłowych znaków z ciągu, zobacz [Jak: Paskinie nieprawidłowych znaków z ciągu](how-to-strip-invalid-characters-from-a-string.md) i [przykład: Zmiana formatów daty](regular-expression-example-changing-date-formats.md).  
  
 Aby zapoznać się z omówieniem modelu obiektów wyrażenia regularnego, zobacz [Model obiektu wyrażenia regularnego](the-regular-expression-object-model.md).  
  
 Aby uzyskać więcej informacji na temat języka wyrażenia regularnego, zobacz [Język wyrażenia regularnego — szybkie odwołanie](regular-expression-language-quick-reference.md) lub pobierz i wydrukuj jedną z tych broszur:  
  
 [Podręczny numer w formacie programu Word (docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Podręczny numer w formacie PDF (pdf)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a>Przykłady wyrażeń regularnych  
 Klasa <xref:System.String> zawiera szereg metod wyszukiwania ciągów i zastępowania, które można użyć, gdy chcesz zlokalizować ciągi literału w większym ciągu. Wyrażenia regularne są najbardziej przydatne, gdy chcesz zlokalizować jeden z kilku podciągów w większym ciągu lub gdy chcesz zidentyfikować wzorce w ciągu, jak ilustrują poniższe przykłady.  
  
### <a name="example-1-replacing-substrings"></a>Przykład 1: Zamienianie podciągów  
 Załóżmy, że lista dyskusyjna zawiera nazwy, które czasami zawierają tytuł (Pan, Pani, Miss, lub Pani)wraz z imieniem i nazwiskiem. Jeśli nie chcesz uwzględniać tytułów podczas generowania etykiet kopert y z listy, możesz użyć wyrażenia regularnego, aby usunąć tytuły, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Regex#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 Wzór `(Mr\.? |Mrs\.? |Miss |Ms\.? )` wyrażenia regularnego pasuje do każdego wystąpienia "Pan ", "Pan", "Pani ", "Pani", "Miss", "Pani lub "Pani ". Wywołanie <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody zastępuje dopasowany ciąg <xref:System.String.Empty?displayProperty=nameWithType>z ; innymi słowy, usuwa go z oryginalnego ciągu.  
  
### <a name="example-2-identifying-duplicated-words"></a>Przykład 2: Identyfikowanie zduplikowanych słów  
 Przypadkowo powielanie słów jest częstym błędem, który robią autorzy. Wyrażenie regularne może służyć do identyfikowania zduplikowanych wyrazów, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Regex#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 Wzorzec `\b(\w+?)\s\1\b` wyrażenia regularnego można interpretować w następujący sposób:  
  
|||  
|-|-|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|(\w+?)|Dopasuj jeden lub więcej znaków wyrazu, ale jak najmniej znaków. Razem tworzą grupę, którą można określać jako `\1`.|  
|`\s`|Dopasowuje znak odstępu.|  
|`\1`|Dopasuj podciąg równy grupie `\1`o nazwie .|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
 Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> jest wywoływana z opcjami wyrażenia regularnego ustawionymi na <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>. W związku z tym operacja dopasowania jest bez uwzględniania wielkości liter, a w przykładzie identyfikuje podciąg "To to" jako duplikacje.  
  
 Należy zauważyć, że ciąg wejściowy zawiera podciąg "this? To". Jednak ze względu na interweniujący znak interpunkcyjny nie jest on identyfikowany jako duplikacja.  
  
### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a>Przykład 3: Dynamicznie tworzenie wyrażenia regularnego z uwzględnieniem wrażliwość na ustawienia kulturowe  
 Poniższy przykład ilustruje moc wyrażeń regularnych w połączeniu z elastycznością oferowaną przez . funkcje globalizacji NET. Używa obiektu <xref:System.Globalization.NumberFormatInfo> do określenia formatu wartości waluty w bieżącej kulturze systemu. Następnie używa tych informacji do dynamicznego konstruowania wyrażenia regularnego, które wyodrębnia wartości waluty z tekstu. Dla każdego dopasowania wyodrębnia podgrupę, która zawiera tylko ciąg liczbowy, konwertuje go na <xref:System.Decimal> wartość i oblicza sumę bieżącą.  
  
 [!code-csharp[Conceptual.Regex#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 Na komputerze, którego bieżącą kulturą jest Angielski — Stany Zjednoczone (en-US), przykład dynamicznie tworzy wyrażenie `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`regularne . Ten wzorzec wyrażenia regularnego można interpretować w następujący sposób:  
  
|||  
|-|-|  
|`\$`|Poszukaj pojedynczego wystąpienia symbolu dolara (`$`) w ciągu wejściowym. Ciąg wzorca wyrażenia regularnego zawiera ukośnik odwrotny wskazujący, że symbol dolara ma być interpretowany dosłownie, a nie jako kotwica wyrażenia regularnego. (Sam `$` symbol wskazuje, że aparat wyrażeń regularnych powinien próbować rozpocząć jego dopasowanie na końcu ciągu.) Aby upewnić się, że symbol waluty bieżącej kultury nie jest błędnie interpretowany jako symbol wyrażenia regularnego, przykład wywołuje <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> metodę ucieczki znaku.|  
|`\s*`|Poszukaj zero lub więcej wystąpień znaku odstępu.|  
|`[-+]?`|Poszukaj zera lub jednego wystąpienia znaku dodatniego lub negatywnego.|  
|`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|Nawiasy zewnętrzne wokół tego wyrażenia definiują je jako grupę przechwytywania lub wyrażenie podrzędne. Jeśli zostanie znalezione dopasowanie, informacje o tej części pasującego ciągu <xref:System.Text.RegularExpressions.Group> można <xref:System.Text.RegularExpressions.GroupCollection> pobrać z drugiego <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> obiektu w obiekcie zwróconym przez właściwość. (Pierwszy element w kolekcji reprezentuje całe dopasowanie.)|  
|`[0-9]{0,3}`|Poszukaj od zera do trzech wystąpień cyfr dziesiętnych od 0 do 9.|  
|`(,[0-9]{3})*`|Poszukaj zero lub więcej wystąpień separatora grup, po których następują trzy cyfry dziesiętne.|  
|`\.`|Poszukaj pojedynczego wystąpienia separatora dziesiętnego.|  
|`[0-9]+`|Poszukaj co najmniej jednej cyfry dziesiętne.|  
|`(\.[0-9]+)?`|Poszukaj zera lub jednego wystąpienia separatora dziesiętnego, po którym następuje co najmniej jedna cyfra dziesiętna.|  
  
 Jeśli każdy z tych wzorców podrzędnych zostanie znaleziony w <xref:System.Text.RegularExpressions.Match> ciągu wejściowym, dopasowanie powiedzie <xref:System.Text.RegularExpressions.MatchCollection> się, a obiekt zawierający informacje o dopasowaniu jest dodawany do obiektu.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Język wyrażeń regularnych — podręczny wykaz](regular-expression-language-quick-reference.md)|Zawiera informacje o zestawie znaków, operatorów i konstrukcji, których można użyć do definiowania wyrażeń regularnych.|  
|[Model obiektów wyrażeń regularnych](the-regular-expression-object-model.md)|Zawiera informacje i przykłady kodu, które ilustrują sposób używania klas wyrażeń regularnych.|  
|[Szczegóły dotyczące zachowania wyrażeń regularnych](details-of-regular-expression-behavior.md)|Zawiera informacje o możliwościach i zachowaniu wyrażeń regularnych .NET.|  
|[Przykłady wyrażeń regularnych](regular-expression-examples.md)|Zawiera przykłady kodu, które ilustrują typowe zastosowania wyrażeń regularnych.|  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [Wyrażenia regularne — podręczny numer eksploatacja (pobieranie w formacie Worda)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Wyrażenia regularne — podręczna dokumentacja (pobieranie w formacie PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
