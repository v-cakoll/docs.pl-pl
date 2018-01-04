---
title: ".NET Framework — Wyrażenia regularne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b9922576e4ef942e896f365c44cebec717abe3b4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="net-regular-expressions"></a>Wyrażeń regularnych programu .NET
Wyrażenia regularne umożliwiają wydajne, elastyczne i wydajne przetwarzanie tekstu. Rozbudowana notacji dopasowywanie do wzorca wyrażeń regularnych umożliwia szybkie analizy dużych ilości tekst do znalezienia wzorce określonego znaku; Aby sprawdzić poprawność tekstu, aby upewnić się, że ze wzorcem wstępnie zdefiniowane (takie jak adres e-mail); do wyodrębnienia, Edycja, Zamień lub usuń tekst podciągów; i dodać wyodrębnione ciągi do kolekcji w celu wygenerowania raportu. Dla wielu aplikacji, które zajmują się ciągów lub który analizy dużych bloków tekstu i wyrażenia regularne są niezbędne narzędzia.  
  
## <a name="how-regular-expressions-work"></a>Sposób, a jaki działają wyrażenia regularne  
 Aparat wyrażeń regularnych, która jest reprezentowana przez jest bezpośrednio tekstu przetwarzania za pomocą wyrażeń regularnych <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> obiektu .NET. Co najmniej przetwarzania tekstu za pomocą wyrażeń regularnych wymaga podania aparat wyrażeń regularnych z poniższych dwóch elementów informacji:  
  
-   Wzorzec wyrażenia regularnego, aby zidentyfikować w tekście.  
  
     W środowisku .NET wyrażenie regularne wzorce są definiowane przez specjalne składni lub język, który jest zgodny z wyrażeniami regularnymi Perl 5 i dodaje niektóre dodatkowe funkcje, takie jak Dopasowywanie od prawej do lewej. Aby uzyskać więcej informacji, zobacz [język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md).  
  
-   Tekst, który można przeanalizować elementu wzorzec wyrażenia regularnego.  
  
 Metody <xref:System.Text.RegularExpressions.Regex> klasy umożliwiają wykonywanie następujących czynności:  
  
-   Określić, czy wzorzec wyrażenia regularnego występuje wejściowego tekstu przez wywołanie metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metody. Na przykład, który używa <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metody sprawdzania poprawności tekstu, zobacz [porady: Sprawdź, czy ciągów jest prawidłowy Format wiadomości E-mail](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
-   Pobrać jednego lub wszystkich wystąpień tekstu, który jest zgodny ze wzorcem wyrażenia regularnego wywołując <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody. Zwraca pierwszej metody <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> obiektu, który zawiera informacje o szukanego tekstu. Zwraca ostatni <xref:System.Text.RegularExpressions.MatchCollection> obiekt, który zawiera jeden <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> obiekt dla każdego dopasowania w tekście przeanalizowany.  
  
-   Zastąp tekst, który jest zgodny ze wzorcem wyrażenia regularnego przez wywołanie metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metody. Aby uzyskać przykłady pokazujące, które używają <xref:System.Text.RegularExpressions.Regex.Replace%2A> metodę Zmienianie formatów daty i usuwanie nieprawidłowych znaków z ciągu, zobacz [jak: paska nieprawidłowych znaków z ciągu](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md) i [przykład: Zmienianie formatów daty](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md).  
  
 Omówienie model obiektów wyrażeń regularnych, zobacz [Model obiektów wyrażeń regularnych](../../../docs/standard/base-types/the-regular-expression-object-model.md).  
  
 Aby uzyskać więcej informacji na temat języka wyrażeń regularnych, zobacz [język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md) lub pobrać i wydrukować jeden z tych broszury:  
  
 [Krótki przewodnik w formacie programu Word (.docx)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Krótki przewodnik w formacie PDF (PDF)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a>Przykłady wyrażeń regularnych  
 <xref:System.String> Klasa zawiera wiele metod wyszukiwania i zamiany ciągów, których można użyć, aby zlokalizować ciągi literału ciągu większy. Wyrażenia regularne są najbardziej przydatne, aby zlokalizować jednego z kilku podciągów w ciągu większy lub gdy chcesz zidentyfikować wzorce w ciągu, jak poniższe przykłady przedstawiają.  
  
### <a name="example-1-replacing-substrings"></a>Przykład 1: Zamienianie podciągów  
 Założono, że listy adresowej zawiera nazwy zawierające czasami tytuł (p., chybienie lub Pani Ms.) wraz z imię i nazwisko. Jeśli nie chcesz zawierają tytuły podczas generowania schematu envelope etykiety z listy, możesz użycie wyrażenia regularnego do usunięcia tytuły, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Regex#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 Wzorzec wyrażenia regularnego`(Mr\.? |Mrs\.? |Miss |Ms\.? )` dopasowuje wszystkie wystąpienia "Mr", "P.", "Pani", "Pani", "Chybienie", "Ms lub"Ms.". Wywołanie <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metoda zastępuje dopasowany ciąg z <xref:System.String.Empty?displayProperty=nameWithType>; innymi słowy, usuwa ją z oryginalnego ciągu.  
  
### <a name="example-2-identifying-duplicated-words"></a>Przykład 2: Identyfikowanie zduplikowanych słów  
 Przypadkowo duplikowanie słowa jest typowym błędem że autorów. Wyrażenie regularne można zidentyfikować zduplikowane wyrazy, jak przedstawiono na poniższym przykładzie.  
  
 [!code-csharp[Conceptual.Regex#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 Wzorzec wyrażenia regularnego `\b(\w+?)\s\1\b` może zostać zinterpretowany w następujący sposób:  
  
|||  
|-|-|  
|`\b`|Rozpoczyna na granicy wyrazu.|  
|(\w+?)|Zgodne z co najmniej jeden znak słowa, ale liczbę znaków, jak to możliwe. Razem tworzą grupy, które mogą być określone jako `\1`.|  
|`\s`|Dopasowuje znak odstępu.|  
|`\1`|Pasuje do podciągu, który jest taki sam, jak grupę o nazwie `\1`.|  
|`\b`|Dopasowuje granicę wyrazu.|  
  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Metoda jest wywoływana z ustawioną opcje wyrażeń regularnych <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>. W związku z tym operacja dopasowania jest rozróżniana wielkość liter, a przykład identyfikuje podciąg "To to" jako dublowania.  
  
 Należy pamiętać, że ciąg wejściowy zawiera podciąg "to? To". Jednak ze względu na pośredniczące znak interpunkcyjny, jest nie identyfikowane jako dublowania.  
  
### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a>Przykład 3: Dynamicznie tworzenie wyrażenia regularnego z uwzględnieniem wrażliwość na ustawienia kulturowe  
 Poniższy przykład przedstawia możliwości wyrażeń regularnych w połączeniu z elastycznością oferowane przez. Funkcje globalizacji w sieci. Używa <xref:System.Globalization.NumberFormatInfo> obiektem, aby określić format wartości waluty w systemie bieżącej kultury. Następnie używa tych informacji do dynamicznie utworzyć wyrażenie regularne, która wyodrębnia wartości waluty w tekście. Dla każdego dopasowania wyodrębniane podgrupę, która zawiera tylko ciągi numeryczne, konwertuje go do <xref:System.Decimal> wartość, a następnie oblicza sumę bieżącą.  
  
 [!code-csharp[Conceptual.Regex#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 Na komputerze, na których bieżącej kultury jest angielski — Stany Zjednoczone (en US) przykładzie dynamicznie tworzy wyrażenie regularne `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`. Ten wzorzec wyrażenia regularnego może zostać zinterpretowany w następujący sposób:  
  
|||  
|-|-|  
|`\$`|Poszukaj pojedyncze wystąpienie symbol dolara ($) w ciągu wejściowym. Ciąg wzorzec wyrażenia regularnego obejmuje odwrotny ukośnik, aby wskazać, że symbol dolara ($) jest interpretowane jako literału, a nie jako zakotwiczenia wyrażenia regularnego. (Symbol $ wyłącznie wskazuje czy aparat wyrażeń regularnych powinno się rozpocząć jego dopasowuje koniec ciągu.) Aby upewnić się, że symbol waluty bieżącej kultury jest nieprawidłowo interpretowane jako wyrażenie regularne symbol przykład wywołuje <xref:System.Text.RegularExpressions.Regex.Escape%2A> metody, aby anulować znak.|  
|`\s*`|Poszukaj zero lub więcej wystąpień biały znak.|  
|`[-+]?`|Poszukaj wystąpień zero lub jeden dodatnią znaku lub symbolu wartości ujemnej.|  
|`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|Zewnętrzne nawiasy, w tym wyrażeniu zdefiniować jako grupę przechwytywania lub Podwyrażenie. Jeśli zostanie znaleziony dopasowanie, można pobrać informacji o tej części dopasowania ciągu w od drugiego <xref:System.Text.RegularExpressions.Group> obiektu w <xref:System.Text.RegularExpressions.GroupCollection> obiektu zwróconego przez <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> właściwości. (Cały dopasowania reprezentuje pierwszy element w kolekcji.)|  
|`[0-9]{0,3}`|Poszukaj zero do trzech wystąpień od 0 do 9 cyfr dziesiętnych.|  
|`(,[0-9]{3})*`|Poszukaj zero lub więcej wystąpień separatora grupy następuje trzech cyfr dziesiętnych.|  
|`\.`|Poszukaj pojedyncze wystąpienie separatorem dziesiętnym.|  
|`[0-9]+`|Wyszukaj jeden lub więcej cyfr dziesiętnych.|  
|`(\.[0-9]+)?`|Poszukaj wystąpień zero lub jeden separatora dziesiętnego następuje co najmniej jedną cyfrę.|  
  
 W przypadku każdego z tych subpatterns znalezione w ciągu wejściowym dopasowania zakończy się pomyślnie, a <xref:System.Text.RegularExpressions.Match> obiekt, który zawiera informacje o zgodności jest dodawany do <xref:System.Text.RegularExpressions.MatchCollection> obiektu.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Język wyrażeń regularnych — podręczny wykaz](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Zawiera informacje dotyczące zestawu znaków, Operatorzy i konstrukcji, których można użyć do zdefiniowania wyrażeń regularnych.|  
|[Model obiektów wyrażeń regularnych](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Zawiera informacje i przykłady kodu, które przedstawiają sposób użycia klasy wyrażeń regularnych.|  
|[Szczegóły dotyczące zachowania wyrażeń regularnych](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|Zawiera informacje dotyczące możliwości i zachowania wyrażeń regularnych programu .NET.|  
|[Przykłady wyrażeń regularnych](../../../docs/standard/base-types/regular-expression-examples.md)|Zawiera przykłady kodu, które ilustrują typowe używa wyrażeń regularnych.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [Wyrażeń regularnych — podręczny wykaz (do pobrania w formacie programu Word)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Wyrażeń regularnych — podręczny wykaz (do pobrania w formacie PDF)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
