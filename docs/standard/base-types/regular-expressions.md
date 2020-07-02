---
title: Wyrażenia regularne .NET
description: Używaj wyrażeń regularnych do znajdowania określonych wzorców znaków, walidacji tekstu, pracy z podciągami tekstu, & dodawać wyodrębnione ciągi do kolekcji w programie .NET.
ms.date: 06/30/2020
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
ms.openlocfilehash: f57199c2ddf6569020554e74b6e70801844da641
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85802900"
---
# <a name="net-regular-expressions"></a>Wyrażenia regularne .NET

Wyrażenia regularne zapewniają zaawansowaną, elastyczną i wydajną metodę przetwarzania tekstu. Obszerna notacja zgodna z wzorcem wyrażeń regularnych umożliwia szybkie analizowanie dużych ilości tekstu w celu:

- Znajdź określone wzorce znakowe.
- Sprawdź poprawność tekstu, aby upewnić się, że jest zgodny ze wstępnie zdefiniowanym wzorcem (na przykład adres e-mail).
- Wyodrębnianie, edytowanie, zastępowanie lub usuwanie podciągów tekstu.
- Dodaj wyodrębnione ciągi do kolekcji w celu wygenerowania raportu.

W przypadku wielu aplikacji, które zajmują się ciągami lub analizują duże bloki tekstu, wyrażenia regularne są niezbędnym narzędziem.  
  
## <a name="how-regular-expressions-work"></a>Jak działają wyrażenia regularne

 Filarem przetwarzania tekstu z wyrażeniami regularnymi jest aparat wyrażeń regularnych, który jest reprezentowany przez <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> obiekt w .NET. Co najmniej przetwarzanie tekstu przy użyciu wyrażeń regularnych wymaga, aby aparat wyrażeń regularnych był dostarczany z następującymi dwoma elementami informacji:  
  
- Wzorzec wyrażenia regularnego do identyfikacji w tekście.  
  
     W programie .NET wzorce wyrażeń regularnych są definiowane przez specjalną składnię lub język, który jest zgodny z wyrażeniami regularnymi języka Perl 5 i dodaje niektóre dodatkowe funkcje, takie jak dopasowanie z prawej strony do lewej. Aby uzyskać więcej informacji, zobacz [Język wyrażeń regularnych — szybkie informacje](regular-expression-language-quick-reference.md).  
  
- Tekst do analizy wzorca wyrażenia regularnego.  
  
Metody <xref:System.Text.RegularExpressions.Regex> klasy umożliwiają wykonywanie następujących operacji:  
  
- Ustal, czy wzorzec wyrażenia regularnego występuje w tekście wejściowym przez wywołanie <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metody. Aby zapoznać się z przykładem korzystającym z <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metody sprawdzania poprawności tekstu, zobacz [How to: Verify, czy ciągi są w prawidłowym formacie poczty e-mail](how-to-verify-that-strings-are-in-valid-email-format.md).  
  
- Pobierz jedno lub wszystkie wystąpienia tekstu, które pasują do wzorca wyrażenia regularnego, wywołując <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metodę or. Poprzednia metoda zwraca <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> obiekt, który zawiera informacje na temat pasującego tekstu. Ostatni zwraca <xref:System.Text.RegularExpressions.MatchCollection> obiekt, który zawiera jeden <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> obiekt dla każdego dopasowania znaleziony w analizowanym tekście.  
  
- Zastąp tekst, który pasuje do wzorca wyrażenia regularnego, wywołując <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodę. Aby zapoznać się z przykładami korzystającymi z <xref:System.Text.RegularExpressions.Regex.Replace%2A> metody w celu zmiany formatów daty i usunięcia nieprawidłowych znaków z ciągu, zobacz [How to: Stripe nieprawidłowe znaki z ciągu](how-to-strip-invalid-characters-from-a-string.md) i [przykład: zmienianie formatów daty](regular-expression-example-changing-date-formats.md).  
  
Aby zapoznać się z omówieniem modelu obiektów wyrażeń regularnych, zobacz [model obiektów wyrażeń regularnych](the-regular-expression-object-model.md).  
  
Aby uzyskać więcej informacji na temat języka wyrażeń regularnych, zobacz temat [wyrażenie regularne — krótkie odwołanie](regular-expression-language-quick-reference.md) lub pobieranie i drukowanie jednej z następujących broszur:  
  
- [Krótki przewodnik w formacie Word (. docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [Krótki przewodnik w formacie PDF (PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a>Przykłady wyrażeń regularnych

<xref:System.String>Klasa zawiera szereg metod wyszukiwania i zamiany ciągów, których można użyć, gdy chcesz zlokalizować ciągi literału w większym ciągu. Wyrażenia regularne są najbardziej przydatne, gdy chcesz zlokalizować jeden z kilku podciągów w większym ciągu lub Kiedy chcesz identyfikować wzorce w ciągu, jak pokazano w poniższych przykładach.

[!INCLUDE [regex](../../../includes/regex.md)]

> [!TIP]
> <xref:System.Web.RegularExpressions>Przestrzeń nazw zawiera wiele obiektów wyrażeń regularnych, które implementują wstępnie zdefiniowane wzorce wyrażeń regularnych na potrzeby analizowania ciągów z dokumentów HTML, XML i ASP.NET. Na przykład <xref:System.Web.RegularExpressions.TagRegex> Klasa identyfikuje początkowe Tagi w ciągu, a <xref:System.Web.RegularExpressions.CommentRegex> Klasa identyfikuje Komentarze ASP.NET w ciągu.

### <a name="example-1-replace-substrings"></a>Przykład 1: Zastąp podciągi  

 Załóżmy, że lista adresowa zawiera nazwy, które czasami zawierają tytuł (Mr., Pani., chybień lub MS.) wraz z imię i nazwisko. Jeśli nie chcesz uwzględniać tytułów podczas generowania etykiet kopert z listy, możesz użyć wyrażenia regularnego, aby usunąć tytuły, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Regex#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 Wzorzec wyrażenia regularnego `(Mr\.? |Mrs\.? |Miss |Ms\.? )` pasuje do dowolnego wystąpienia "Mr", "Mr.", "Pani", "Pani", "chybień", "MS" lub "MS". Wywołanie <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody zastępuje dopasowany ciąg znakami <xref:System.String.Empty?displayProperty=nameWithType> ; innymi słowy, usuwa je z oryginalnego ciągu.  
  
### <a name="example-2-identify-duplicated-words"></a>Przykład 2: Identyfikowanie zduplikowanych wyrazów  

 Przypadkowe duplikowanie słów jest typowym błędem wprowadzanym przez autorów. Wyrażenie regularne może służyć do identyfikowania zduplikowanych wyrazów, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Regex#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 Wzorzec wyrażenia regularnego `\b(\w+?)\s\1\b` można interpretować w następujący sposób:  
  
> [!div class="mx-tdCol2BreakAll"]
> |Wzorce|Interpretacja|  
> |-|-|
> |`\b`|Rozpoczyna na granicy wyrazu.|  
> |`(\w+?)`|Dopasowuje co najmniej jeden znak słowa, ale jak najmniejsza liczba znaków. Razem tworzą one grupę, która może być określana jako `\1` .|  
> |`\s`|Dopasowuje znak odstępu.|  
> |`\1`|Dopasowuje podciąg, który jest równy grupie o nazwie `\1` .|  
> |`\b`|Dopasowuje granicę wyrazu.|  
  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>Metoda jest wywoływana z opcjami wyrażenia regularnego ustawionym na <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> . W związku z tym, Operacja dopasowania nie uwzględnia wielkości liter, a przykład określa podciąg "this this" jako duplikacji.  
  
 Ciąg wejściowy zawiera podciąg "this? To ". Jednak ze względu na pozostały znak interpunkcyjny nie jest on identyfikowany jako duplikowanie.  
  
### <a name="example-3-dynamically-build-a-culture-sensitive-regular-expression"></a>Przykład 3: dynamiczne tworzenie wyrażenia regularnego z uwzględnieniem kultury  

 Poniższy przykład ilustruje moc wyrażeń regularnych połączonych z elastyczną oferowaną przez. Funkcje globalizacji sieci. Używa <xref:System.Globalization.NumberFormatInfo> obiektu do określenia formatu wartości walutowych w bieżącej kulturze systemu. Następnie używa tych informacji do dynamicznego konstruowania wyrażenia regularnego, które wyodrębnia wartości walutowe z tekstu. Dla każdego dopasowania wyodrębnia podgrupę zawierającą tylko ciąg liczbowy, konwertuje ją na <xref:System.Decimal> wartość i oblicza sumę uruchomienia.  
  
 [!code-csharp[Conceptual.Regex#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 Na komputerze, którego bieżącą kulturą jest angielski — Stany Zjednoczone (EN-US), przykład dynamicznie kompiluje wyrażenie regularne `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)` . Ten wzorzec wyrażenia regularnego można interpretować w następujący sposób:  

> [!div class="mx-tdCol2BreakAll"]
> |Wzorce|Interpretacja|  
> |-|-|  
> |`\$`|Poszukaj pojedynczego wystąpienia symbolu dolara ( `$` ) w ciągu wejściowym. Ciąg wzorca wyrażenia regularnego zawiera ukośnik odwrotny wskazujący, że symbol dolara ma być interpretowany dosłownie, a nie jako zakotwiczenie wyrażenia regularnego. ( `$` Sam symbol wskazuje, że aparat wyrażeń regularnych powinien próbować rozpocząć jego dopasowanie na końcu ciągu znaków). Aby upewnić się, że symbol waluty bieżącej kultury nie jest interpretowany jako symbol wyrażenia regularnego, przykład wywołuje <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> metodę w celu ucieczki znaku.|  
> |`\s*`|Wyszukaj zero lub więcej wystąpień znaku odstępu.|  
> |`[-+]?`|Poszukaj zera lub jednego wystąpienia znaku dodatniego lub znaku minus.|  
> |`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|Nawiasy zewnętrzne wokół tego wyrażenia definiują je jako grupę przechwytywania lub Podwyrażenie. W przypadku znalezienia dopasowania informacje o tej części pasującego ciągu można pobrać z drugiego <xref:System.Text.RegularExpressions.Group> obiektu w <xref:System.Text.RegularExpressions.GroupCollection> obiekcie zwracanym przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Właściwość. (Pierwszy element w kolekcji reprezentuje całe dopasowanie).|  
> |`[0-9]{0,3}`|Wyszukaj zero do trzech wystąpień cyfr dziesiętnych od 0 do 9.|  
> |`(,[0-9]{3})*`|Wyszukaj zero lub więcej wystąpień separatora grupy, po których następuje trzy cyfry dziesiętne.|  
> |`\.`|Poszukaj pojedynczego wystąpienia separatora dziesiętnego.|  
> |`[0-9]+`|Wyszukaj co najmniej jedną cyfrę dziesiętną.|  
> |`(\.[0-9]+)?`|Poszukaj zera lub jednego wystąpienia separatora dziesiętnego, po którym następuje co najmniej jedna cyfra dziesiętna.|  
  
 Jeśli każdy z tych wzorców znajduje się w ciągu wejściowym, dopasowanie powiedzie się, a <xref:System.Text.RegularExpressions.Match> obiekt, który zawiera informacje o dopasowaniu, jest dodawany do <xref:System.Text.RegularExpressions.MatchCollection> obiektu.  
  
## <a name="related-topics"></a>Powiązane tematy  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Język wyrażeń regularnych — podręczny wykaz](regular-expression-language-quick-reference.md)|Zawiera informacje dotyczące zestawu znaków, operatorów i konstrukcji, których można użyć do definiowania wyrażeń regularnych.|  
|[Model obiektów wyrażeń regularnych](the-regular-expression-object-model.md)|Zawiera informacje i przykłady kodu, które ilustrują sposób korzystania z klas wyrażeń regularnych.|  
|[Szczegóły zachowania dotyczącego wyrażeń regularnych](details-of-regular-expression-behavior.md)|Zawiera informacje na temat możliwości i zachowania wyrażeń regularnych programu .NET.|
|[Używanie wyrażeń regularnych w programie Visual Studio](/visualstudio/ide/using-regular-expressions-in-visual-studio)||
  
## <a name="reference"></a>Dokumentacja  

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
- [Wyrażenia regularne — krótkie odwołanie (pobieranie w formacie programu Word)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [Wyrażenia regularne — krótkie odwołanie (pobieranie w formacie PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
