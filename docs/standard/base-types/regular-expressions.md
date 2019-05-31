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
ms.openlocfilehash: cb70b0ef4c6e619418f8464b543795a59c2ddff5
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423782"
---
# <a name="net-regular-expressions"></a>Wyrażeń regularnych programu .NET
Wyrażenia regularne umożliwiają zaawansowane, elastyczne i wydajne przetwarzanie tekstu. Rozbudowane notacji dopasowania do wzorca wyrażenia regularnego umożliwia do szybkiego analizowania dużych ilości tekstu, aby znaleźć wzory znaków specyficznych; Aby sprawdzić poprawność tekstu, aby upewnić się, czy jest on zgodny wstępnie zdefiniowanych wzorca (np. adres e-mail); Aby wyodrębnić, Edytuj, zastępowania lub usuwania podciągów tekstu; i dodawać wyodrębnione ciągi do kolekcji, aby wygenerować raport. Dla wielu aplikacji, które zajmują się ciągów lub że analizy dużych bloków tekstu, wyrażenia regularne są niezbędne narzędzia.  
  
## <a name="how-regular-expressions-work"></a>Sposób, a jaki działają wyrażenia regularne  
 Centralnym punktem tekstu przetwarzania za pomocą wyrażeń regularnych jest aparat wyrażeń regularnych, który jest reprezentowany przez <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> obiekt na platformie .NET. Co najmniej przetwarzanie tekstu przy użyciu wyrażeń regularnych wymaga podania aparat wyrażeń regularnych z następującymi elementami dwóch informacji:  
  
- Wzorzec wyrażenia regularnego, aby zidentyfikować w tekście.  
  
     Na platformie .NET wzorce wyrażeń regularnych są definiowane przez specjalnej składni lub języka, który jest zgodny z wyrażeniami regularnymi Perl 5 i dodaje niektóre dodatkowe funkcje, takie jak dopasowanie od prawej do lewej. Aby uzyskać więcej informacji, zobacz [język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md).  
  
- Tekst do analizy dla wzorca wyrażenia regularnego.  
  
 Metody <xref:System.Text.RegularExpressions.Regex> klasy umożliwiają wykonywanie następujących czynności:  
  
- Określić, czy wzorzec wyrażenia regularnego występuje w tekście wejściowym, wywołując <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metody. Aby uzyskać przykład, który używa <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metody sprawdzania poprawności tekstu, zobacz [jak: Verify that Strings Are w prawidłowym formacie adresu E-mail](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
- Pobierz jeden lub wszystkie wystąpienia tekstu, który pasuje do wzorca wyrażenia regularnego, wywołując <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody. Zwraca pierwszej metody <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> obiektu, który dostarcza informacji na temat dopasowania tekstu. Zwraca ostatnie <xref:System.Text.RegularExpressions.MatchCollection> obiektu, który zawiera jeden <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> obiekt dla każdego dopasowania w tekście przeanalizowany.  
  
- Zastąp tekst, który pasuje do wzorca wyrażenia regularnego, wywołując <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody. Aby uzyskać przykłady, które używają <xref:System.Text.RegularExpressions.Regex.Replace%2A> metodę, aby zmienić formaty daty i usuwanie nieprawidłowych znaków z ciągu, zobacz [jak: Usuwanie nieprawidłowych znaków z ciągu](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md) i [przykładu: Zmienianie formatów daty](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md).  
  
 Aby zapoznać się z omówieniem model obiektów wyrażeń regularnych, zobacz [Model obiektów wyrażeń regularnych](../../../docs/standard/base-types/the-regular-expression-object-model.md).  
  
 Aby uzyskać więcej informacji na temat języka wyrażeń regularnych, zobacz [język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md) lub pobrać i wydrukować jedną z tych broszury:  
  
 [Krótki przewodnik w formacie programu Word (.docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Krótki przewodnik w formacie PDF (PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a>Przykłady wyrażeń regularnych  
 <xref:System.String> Klasy istnieje kilka metod znajdowania i zamieniania ciągów, których można użyć, gdy chcesz zlokalizować ciągi literałów w dłuższym ciągu. Wyrażenia regularne są najbardziej przydatne, gdy chcesz zlokalizować jednego z kilku podciągów w dłuższym ciągu lub gdy chcesz zidentyfikować wzorce w ciągu, jak w poniższych przykładach pokazano.  
  
### <a name="example-1-replacing-substrings"></a>Przykład 1: Zamienianie podciągów  
 Przyjęto założenie, że listy adresowej zawiera nazwy, które czasami dołączyć tytuł (Pan, trafienia lub Pani Ms.) oraz imię i nazwisko. Jeśli nie chcesz zawierają tytuły, podczas generowania schematu envelope etykiety na liście, umożliwia wyrażenie regularne. usuwanie tytułów, tak jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Regex#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 Definicję wzorca wyrażenia regularnego`(Mr\.? |Mrs\.? |Miss |Ms\.? )` pasuje do dowolnego wystąpienia "Mr", "Pan", "Pani", "Pani", "Trafienia", "Ms lub"Ms.". Wywołanie <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metoda zamienia dopasowany ciąg z <xref:System.String.Empty?displayProperty=nameWithType>; innymi słowy, spowoduje usunięcie go z oryginalnego ciągu.  
  
### <a name="example-2-identifying-duplicated-words"></a>Przykład 2: Identyfikowanie zduplikowanych słów  
 Przypadkowo duplikowanie wyrazów jest typowym błędem wchodzące modułów zapisujących. Wyrażenie regularne może służyć do identyfikowania zduplikowanych słów, co ilustruje poniższy przykład.  
  
 [!code-csharp[Conceptual.Regex#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 Definicję wzorca wyrażenia regularnego `\b(\w+?)\s\1\b` może być interpretowany w następujący sposób:  
  
|||  
|-|-|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|(\w+?)|Dopasowuje co najmniej jeden znak słowa, ale liczbę znaków, jak to możliwe. Razem tworzą one grupy, które mogą być określane jako `\1`.|  
|`\s`|Dopasowuje znak odstępu.|  
|`\1`|Dopasuj podciąg, który jest równy grupę o nazwie `\1`.|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Metoda jest wywoływana z opcji wyrażenia regularnego zestawu <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>. W związku z tym, operacja jest rozróżniana wielkość liter, a przykład identyfikuje podciągu "To this" jako dublowania.  
  
 Należy pamiętać, że ciąg wejściowy zawiera podciąg "to jest? To". Jednak ze względu na pośredniczące znak interpunkcyjny, go nie zostanie zidentyfikowany jako dublowania.  
  
### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a>Przykład 3: Dynamicznie Tworzenie wyrażenia regularnego z uwzględnieniem kultury  
 Poniższy przykład ilustruje możliwości w połączeniu z elastyczności oferowanej przez wyrażenia regularne. Funkcje globalizacji firmy NET. Używa ona <xref:System.Globalization.NumberFormatInfo> obiekt, aby określić format wartości waluty w bieżącej kultury systemu. Następnie używa tych informacji do dynamicznego utworzenia wyrażenia regularnego, który wyodrębnia wartości waluty w tekście. Dla każdego dopasowania wyodrębnia podgrupę, która zawiera tylko ciągu numerycznego, konwertuje ją na <xref:System.Decimal> wartości, a następnie oblicza sumę bieżącą.  
  
 [!code-csharp[Conceptual.Regex#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 Na komputerze, którego bieżącą kulturą jest angielski - Stany Zjednoczone (en US) przykład dynamicznie tworzy wyrażenie regularne `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`. Ten wzorzec wyrażenia regularnego może być interpretowany w następujący sposób:  
  
|||  
|-|-|  
|`\$`|Wyszukaj pojedynczego wystąpienia znaku dolara (`$`) w ciągu wejściowym. Ciąg wzorca wyrażenia regularnego zawiera ukośnik odwrotny, aby wskazać, czy symbol Dolar ma być interpretowany dosłownie, a nie jako zakotwiczenia wyrażenia regularnego. ( `$` Symbol samodzielnie wskazują, że aparat wyrażeń regularnych starać się rozpocząć jego dopasowanie na końcu ciągu.) Aby upewnić się, że symbol waluty bieżącej kultury jest nieprawidłowo interpretowane jako symbol separatora wyrażeń regularnych, przykład wywołuje <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> metodę, aby uniknąć użycia znaku.|  
|`\s*`|Zwróć uwagę na zero lub więcej wystąpień znaku odstępu.|  
|`[-+]?`|Zwróć uwagę na wystąpienie zero lub jeden znak wartości dodatnich lub znaku minus.|  
|`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|Zewnętrzne nawiasów wokół tego wyrażenia definiowania go jako grupa przechwytywania lub podwyrażenia. Jeśli zostanie znalezione dopasowanie, można pobrać informacji na temat tej części pasującego ciągu drugiego <xref:System.Text.RegularExpressions.Group> obiektu <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości. (Całe dopasowanie reprezentuje pierwszy element w kolekcji.)|  
|`[0-9]{0,3}`|Zwróć uwagę na zero, wystąpień trzech cyfr dziesiętnych od 0 do 9.|  
|`(,[0-9]{3})*`|Zwróć uwagę na zero lub więcej wystąpień separatora grupy następują trzy cyfry dziesiętne.|  
|`\.`|Zwróć uwagę na pojedyncze wystąpienie separatora dziesiętnego.|  
|`[0-9]+`|Zwróć uwagę na jeden lub więcej cyfr dziesiętnych.|  
|`(\.[0-9]+)?`|Zwróć uwagę na zera lub jednego wystąpienia separatora dziesiętnego, następuje co najmniej jedną cyfrę dziesiętną.|  
  
 W przypadku każdego z tych subpatterns znalezione w ciągu wejściowym, dopasowanie się powiedzie, a <xref:System.Text.RegularExpressions.Match> obiekt, który zawiera informacje o zgodności zostanie dodany do <xref:System.Text.RegularExpressions.MatchCollection> obiektu.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Zawiera informacje dotyczące zestawu znaków, operatorów i konstrukcji, które służą do definiowania wyrażeń regularnych.|  
|[Model obiektów wyrażeń regularnych](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Zawiera informacje i przykłady kodu, które ilustrują sposób korzystania z klasy wyrażeń regularnych.|  
|[Szczegóły dotyczące zachowania wyrażeń regularnych](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|Zawiera informacje dotyczące funkcji i zachowania wyrażeń regularnych programu .NET.|  
|[Przykłady wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-examples.md)|Zawiera przykłady kodu, które ilustrują typowe używa wyrażeń regularnych.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [Wyrażeń regularnych — podręczny wykaz (do pobrania w formacie programu Word)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Wyrażeń regularnych — podręczny wykaz (do pobrania w formacie PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
