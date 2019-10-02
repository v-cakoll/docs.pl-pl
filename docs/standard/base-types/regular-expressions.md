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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89b527d4febb677512b3cdcf7cd47344d182ae26
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736864"
---
# <a name="net-regular-expressions"></a>Wyrażenia regularne .NET
Wyrażenia regularne zapewniają zaawansowaną, elastyczną i wydajną metodę przetwarzania tekstu. Obszerna notacja zgodna z wzorcem wyrażeń regularnych umożliwia szybkie analizowanie dużych ilości tekstu w celu znalezienia określonych wzorców znaków; Aby sprawdzić poprawność tekstu w celu upewnienia się, że jest zgodny ze wstępnie zdefiniowanym wzorcem (na przykład adres e-mail); Aby wyodrębnić, edytować, zamienić lub usunąć podciągi tekstowe; i aby dodać wyodrębnione ciągi do kolekcji w celu wygenerowania raportu. W przypadku wielu aplikacji, które zajmują się ciągami lub analizują duże bloki tekstu, wyrażenia regularne są niezbędnym narzędziem.  
  
## <a name="how-regular-expressions-work"></a>Sposób, a jaki działają wyrażenia regularne  
 Filarem przetwarzania tekstu przy użyciu wyrażeń regularnych jest aparatem wyrażeń regularnych, który jest reprezentowany przez obiekt <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> w programie .NET. Co najmniej przetwarzanie tekstu przy użyciu wyrażeń regularnych wymaga, aby aparat wyrażeń regularnych był dostarczany z następującymi dwoma elementami informacji:  
  
- Wzorzec wyrażenia regularnego do identyfikacji w tekście.  
  
     W programie .NET wzorce wyrażeń regularnych są definiowane przez specjalną składnię lub język, który jest zgodny z wyrażeniami regularnymi języka Perl 5 i dodaje niektóre dodatkowe funkcje, takie jak dopasowanie z prawej strony do lewej. Aby uzyskać więcej informacji, zobacz [Język wyrażeń regularnych — szybkie informacje](regular-expression-language-quick-reference.md).  
  
- Tekst do analizy wzorca wyrażenia regularnego.  
  
 Metody klasy <xref:System.Text.RegularExpressions.Regex> umożliwiają wykonywanie następujących operacji:  
  
- Ustal, czy wzorzec wyrażenia regularnego występuje w tekście wejściowym przez wywołanie metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType>. Aby zapoznać się z przykładem, który używa metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> do walidacji tekstu, zobacz [How to: Verify, czy ciągi są w prawidłowym formacie poczty e-mail](how-to-verify-that-strings-are-in-valid-email-format.md).  
  
- Pobierz jedno lub wszystkie wystąpienia tekstu, które pasują do wzorca wyrażenia regularnego, wywołując metodę <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>. Dawna Metoda zwraca obiekt <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType>, który zawiera informacje na temat pasującego tekstu. Ostatni zwraca obiekt <xref:System.Text.RegularExpressions.MatchCollection>, który zawiera jeden obiekt <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> dla każdego dopasowania znalezionego w analizowanym tekście.  
  
- Zastąp tekst, który pasuje do wzorca wyrażenia regularnego, wywołując metodę <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType>. Przykłady korzystające z metody <xref:System.Text.RegularExpressions.Regex.Replace%2A> w celu zmiany formatów daty i usunięcia nieprawidłowych znaków z ciągu można znaleźć w temacie [How to: Stripe nieprawidłowe znaki z ciągu](how-to-strip-invalid-characters-from-a-string.md) i [przykład: zmienianie formatów daty](regular-expression-example-changing-date-formats.md).  
  
 Aby zapoznać się z omówieniem modelu obiektów wyrażeń regularnych, zobacz [model obiektów wyrażeń regularnych](the-regular-expression-object-model.md).  
  
 Aby uzyskać więcej informacji na temat języka wyrażeń regularnych, zobacz temat [wyrażenie regularne — krótkie odwołanie](regular-expression-language-quick-reference.md) lub pobieranie i drukowanie jednej z następujących broszur:  
  
 [Krótki przewodnik w formacie Word (. docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Krótki przewodnik w formacie PDF (PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a>Przykłady wyrażeń regularnych  
 Klasa <xref:System.String> zawiera wiele metod wyszukiwania i zamiany ciągów, których można użyć, gdy chcesz zlokalizować ciągi literału w większym ciągu. Wyrażenia regularne są najbardziej przydatne, gdy chcesz zlokalizować jeden z kilku podciągów w większym ciągu lub Kiedy chcesz identyfikować wzorce w ciągu, jak pokazano w poniższych przykładach.  
  
### <a name="example-1-replacing-substrings"></a>Przykład 1: Zamienianie podciągów  
 Załóżmy, że lista adresowa zawiera nazwy, które czasami zawierają tytuł (Mr., Pani., chybień lub MS.) wraz z imię i nazwisko. Jeśli nie chcesz uwzględniać tytułów podczas generowania etykiet kopert z listy, możesz użyć wyrażenia regularnego, aby usunąć tytuły, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Regex#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 Wzorzec wyrażenia regularnego `(Mr\.? |Mrs\.? |Miss |Ms\.? )` dopasowuje dowolne wystąpienie "Mr", "Mr", "Pani", "Pani", "chybień", "MS" lub "MS". Wywołanie metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> zastępuje dopasowany ciąg <xref:System.String.Empty?displayProperty=nameWithType>; Innymi słowy usuwa je z oryginalnego ciągu.  
  
### <a name="example-2-identifying-duplicated-words"></a>Przykład 2: Identyfikowanie zduplikowanych słów  
 Przypadkowe duplikowanie słów jest typowym błędem wprowadzanym przez autorów. Wyrażenie regularne może służyć do identyfikowania zduplikowanych wyrazów, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Regex#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 Wzorzec wyrażenia regularnego `\b(\w+?)\s\1\b` może być interpretowany w następujący sposób:  
  
|||  
|-|-|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|(\w +?)|Dopasowuje co najmniej jeden znak słowa, ale jak najmniejsza liczba znaków. Razem tworzą one grupę, która może być określana jako `\1`.|  
|`\s`|Dopasowuje znak odstępu.|  
|`\1`|Dopasowuje podciąg, który jest równy grupie o nazwie `\1`.|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
 Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> jest wywoływana z opcją wyrażenia regularnego ustawioną na <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>. W związku z tym, Operacja dopasowania nie uwzględnia wielkości liter, a przykład określa podciąg "this this" jako duplikacji.  
  
 Należy zauważyć, że ciąg wejściowy zawiera podciąg "this? To ". Jednak ze względu na pozostały znak interpunkcyjny nie jest on identyfikowany jako duplikowanie.  
  
### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a>Przykład 3: Dynamicznie tworzenie wyrażenia regularnego z uwzględnieniem wrażliwość na ustawienia kulturowe  
 Poniższy przykład ilustruje moc wyrażeń regularnych połączonych z elastyczną oferowaną przez. Funkcje globalizacji sieci. Używa obiektu <xref:System.Globalization.NumberFormatInfo> do określenia formatu wartości walutowych w bieżącej kulturze systemu. Następnie używa tych informacji do dynamicznego konstruowania wyrażenia regularnego, które wyodrębnia wartości walutowe z tekstu. Dla każdego dopasowania wyodrębnia podgrupę zawierającą tylko ciąg liczbowy, konwertuje ją na wartość <xref:System.Decimal> i oblicza sumę działania.  
  
 [!code-csharp[Conceptual.Regex#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 Na komputerze, którego bieżącą kulturą jest angielski — Stany Zjednoczone (EN-US), przykład dynamicznie kompiluje wyrażenie regularne `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`. Ten wzorzec wyrażenia regularnego można interpretować w następujący sposób:  
  
|||  
|-|-|  
|`\$`|Poszukaj pojedynczego wystąpienia symbolu dolara (`$`) w ciągu wejściowym. Ciąg wzorca wyrażenia regularnego zawiera ukośnik odwrotny wskazujący, że symbol dolara ma być interpretowany dosłownie, a nie jako zakotwiczenie wyrażenia regularnego. (Symbol `$` wskazuje, że aparat wyrażeń regularnych powinien próbować rozpocząć jego dopasowanie na końcu ciągu znaków). Aby upewnić się, że symbol waluty bieżącej kultury nie jest interpretowany jako symbol wyrażenia regularnego, przykład wywołuje metodę <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType>, aby wypróbować znak.|  
|`\s*`|Wyszukaj zero lub więcej wystąpień znaku odstępu.|  
|`[-+]?`|Poszukaj zera lub jednego wystąpienia znaku dodatniego lub znaku minus.|  
|`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|Nawiasy zewnętrzne wokół tego wyrażenia definiują je jako grupę przechwytywania lub Podwyrażenie. W przypadku znalezienia dopasowania informacje o tej części pasującego ciągu można pobrać z drugiego obiektu <xref:System.Text.RegularExpressions.Group> w obiekcie <xref:System.Text.RegularExpressions.GroupCollection> zwróconym przez właściwość <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>. (Pierwszy element w kolekcji reprezentuje całe dopasowanie).|  
|`[0-9]{0,3}`|Wyszukaj zero do trzech wystąpień cyfr dziesiętnych od 0 do 9.|  
|`(,[0-9]{3})*`|Wyszukaj zero lub więcej wystąpień separatora grupy, po których następuje trzy cyfry dziesiętne.|  
|`\.`|Poszukaj pojedynczego wystąpienia separatora dziesiętnego.|  
|`[0-9]+`|Wyszukaj co najmniej jedną cyfrę dziesiętną.|  
|`(\.[0-9]+)?`|Poszukaj zera lub jednego wystąpienia separatora dziesiętnego, po którym następuje co najmniej jedna cyfra dziesiętna.|  
  
 Jeśli każdy z tych wzorców znajduje się w ciągu wejściowym, dopasowanie powiedzie się, a obiekt <xref:System.Text.RegularExpressions.Match> zawierający informacje o dopasowaniu zostanie dodany do obiektu <xref:System.Text.RegularExpressions.MatchCollection>.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Język wyrażeń regularnych — podręczny wykaz](regular-expression-language-quick-reference.md)|Zawiera informacje dotyczące zestawu znaków, operatorów i konstrukcji, których można użyć do definiowania wyrażeń regularnych.|  
|[Model obiektów wyrażeń regularnych](the-regular-expression-object-model.md)|Zawiera informacje i przykłady kodu, które ilustrują sposób korzystania z klas wyrażeń regularnych.|  
|[Szczegóły dotyczące zachowania wyrażeń regularnych](details-of-regular-expression-behavior.md)|Zawiera informacje na temat możliwości i zachowania wyrażeń regularnych programu .NET.|  
|[Przykłady wyrażeń regularnych](regular-expression-examples.md)|Zawiera przykłady kodu, które ilustrują typowe zastosowania wyrażeń regularnych.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [Wyrażenia regularne — krótkie odwołanie (pobieranie w formacie programu Word)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Wyrażenia regularne — krótkie odwołanie (pobieranie w formacie PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
