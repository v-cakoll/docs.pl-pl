---
title: Analizowanie ciągów liczbowych w programie .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parsing strings, numeric strings
- numeric strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
ms.assetid: e39324ee-72e5-42d4-a80d-bf3ee7fc6c59
ms.openlocfilehash: ac44282a06b2b3710d3a9e5390c7a514c1632c3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127602"
---
# <a name="parsing-numeric-strings-in-net"></a>Analizowanie ciągów liczbowych w sieci
Wszystkie typy liczbowe mają dwie metody analizy statycznej, `Parse` i `TryParse`, których można użyć do przekonwertowania ciągu reprezentującego liczbę na typ liczbowy. Te metody umożliwiają analizowanie ciągów, które zostały utworzone za pomocą ciągów formatu udokumentowanych w [standardowych ciągach formatu liczbowego](../../../docs/standard/base-types/standard-numeric-format-strings.md) i [niestandardowych ciągów formatu liczbowego](../../../docs/standard/base-types/custom-numeric-format-strings.md). Domyślnie metody `Parse` i `TryParse` mogą pomyślnie konwertować ciągi, które zawierają cyfry dziesiętne tylko do wartości całkowitych. Mogą pomyślnie konwertować ciągi, które zawierają cyfry całkowite i ułamkowe dziesiętne, separatory grup i separator dziesiętny do wartości zmiennoprzecinkowych. Metoda `Parse` zgłasza wyjątek, jeśli operacja nie powiedzie się, a metoda `TryParse` zwróci `false`.  
  
## <a name="parsing-and-format-providers"></a>Analiza składniowa i format dostawców  
 Zazwyczaj reprezentacje ciągów wartości liczbowych różnią się w zależności od kultury. Elementy ciągów liczbowych, takich jak symbole walut, separatory grup (lub tysięcy) i Separatory dziesiętne różnią się w zależności od kultury. Metody analizy niejawnie lub jawnie używają dostawcy formatu, który rozpoznaje te Wariacje specyficzne dla kultury. Jeśli w wywołaniu metody `Parse` lub `TryParse` nie określono dostawcy formatu, jest używany dostawca formatu skojarzony z bieżącą kulturą wątku (obiektem <xref:System.Globalization.NumberFormatInfo> zwróconym przez właściwość <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType>).  
  
 Dostawca formatu jest reprezentowany przez implementację <xref:System.IFormatProvider>. Ten interfejs ma jeden element członkowski, Metoda <xref:System.IFormatProvider.GetFormat%2A>, której pojedynczy parametr jest obiektem <xref:System.Type>, który reprezentuje typ do sformatowania. Ta metoda zwraca obiekt, który dostarcza informacje o formatowaniu. Platforma .NET obsługuje następujące dwie implementacje <xref:System.IFormatProvider> na potrzeby analizowania ciągów liczbowych:  
  
- Obiekt <xref:System.Globalization.CultureInfo>, którego Metoda <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> zwraca obiekt <xref:System.Globalization.NumberFormatInfo>, który dostarcza informacje o formatowaniu specyficzne dla kultury.  
  
- Obiekt <xref:System.Globalization.NumberFormatInfo>, którego Metoda <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> zwraca samą siebie.  
  
 Poniższy przykład próbuje przekonwertować każdy ciąg w tablicy na wartość <xref:System.Double>. Najpierw próbuje przeanalizować ciąg przy użyciu dostawcy formatu, który odzwierciedla konwencje angielskiej (Stany Zjednoczone) kultury. Jeśli ta operacja zgłasza <xref:System.FormatException>, próbuje przeanalizować ciąg przy użyciu dostawcy formatu, który odzwierciedla konwencje kultury francuskiej (Francja).  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Analiza składniowa i wartości NumberStyles  
 Elementy stylu (takie jak odstępy, separatory grup i separator dziesiętny), które może obsłużyć operacja analizy, są definiowane przez <xref:System.Globalization.NumberStyles> wartość wyliczenia. Domyślnie ciągi reprezentujące wartości całkowite są analizowane przy użyciu wartości <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>, która zezwala na tylko cyfry liczbowe, wiodące i końcowe białe znaki oraz znak wiodący. Ciągi reprezentujące wartości zmiennoprzecinkowe są analizowane przy użyciu kombinacji wartości <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> i <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>; Ten styl złożony dopuszcza cyfry dziesiętne oraz odstępy wiodące i końcowe, znak wiodący, separator dziesiętny, separator grupy i wykładnik. Wywołując Przeciążenie metody `Parse` lub `TryParse`, która zawiera parametr typu <xref:System.Globalization.NumberStyles> i ustawiając co najmniej jedną flagę <xref:System.Globalization.NumberStyles>, można kontrolować elementy stylu, które mogą być obecne w ciągu, aby operacja analizy zakończyła się pomyślnie.  
  
 Na przykład ciąg, który zawiera separator grupy nie może zostać skonwertowany na wartość <xref:System.Int32> przy użyciu metody <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType>. Jednak konwersja powiedzie się, jeśli używasz flagi <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
> Operacja analizy zawsze używa Konwencji formatowania określonej kultury. Jeśli nie określisz kultury przez przekazanie obiektu <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.NumberFormatInfo>, używana jest kultura skojarzona z bieżącym wątkiem.  
  
 W poniższej tabeli wymieniono elementy członkowskie wyliczenia <xref:System.Globalization.NumberStyles> i opisano wpływ operacji analizowania.  
  
|Wartość wyliczenia NumberStyles|Wpływ na ciąg, który ma zostać przeanalizowany|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Dozwolone są tylko cyfry numeryczne.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Dozwolone są Separatory dziesiętne i cyfry ułamkowe. W przypadku wartości całkowitych jako cyfry ułamkowej dozwolony jest tylko zero. Prawidłowe Separatory dziesiętne są określane przez właściwość <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> lub <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|Znak "e" lub "E" może służyć do wskazania notacji wykładniczej. Aby uzyskać dodatkowe informacje, zobacz <xref:System.Globalization.NumberStyles>.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Jest dozwolony wiodący biały znak.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Białe znaki końcowe są dozwolone.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Znak dodatni lub ujemny może poprzedzać cyfry cyfr.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Znak dodatni lub ujemny może następować po cyfrach numerycznych.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Nawiasy mogą służyć do wskazania wartości ujemnych.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Separator grupy jest dozwolony. Znak separatora grupy jest określany przez właściwość <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> lub <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Symbol waluty jest dozwolony. Symbol waluty jest definiowany przez właściwość <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Ciąg, który ma być analizowany, jest interpretowany jako liczba szesnastkowa. Może zawierać cyfry szesnastkowe 0-9, A-F i a-f. Ta flaga może być używana tylko do analizowania wartości całkowitych.|  
  
 Ponadto Wyliczenie <xref:System.Globalization.NumberStyles> zawiera następujące style złożone, które obejmują wiele flag <xref:System.Globalization.NumberStyles>.  
  
|Złożona wartość wyliczenia NumberStyles|Obejmuje członków|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|Zawiera style <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>i <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>. Jest to domyślny styl używany do analizowania wartości całkowitych.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|Zawiera style <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>i <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|Zawiera style <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>i <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Zawiera wszystkie style, z wyjątkiem <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> i <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Zawiera wszystkie style, z wyjątkiem <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|Zawiera style <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>i <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
  
## <a name="parsing-and-unicode-digits"></a>Analiza składniowa i cyfry Unicode  
 Standard Unicode definiuje punkty kodów dla cyfr w różnych systemach pisania. Na przykład punkty kodów z U + 0030 do U + 0039 reprezentują podstawowe cyfry łacińskie od 0 do 9, punkty kodów z U + 09E6 do U + 09EF reprezentują cyfry bengalskie od 0 do 9, a punkty kodu z U + FF10 do U + FF19 reprezentują cyfry pełnej od 0 do 9. Jednak jedynymi cyframi, które są rozpoznawane przez metody analizy, są podstawowe cyfry łacińskie 0-9 z punktami kodu od U + 0030 do U + 0039. Jeśli metoda analizy liczbowej została przeniesiona jako ciąg, który zawiera inne cyfry, metoda zgłasza <xref:System.FormatException>.  
  
 W poniższym przykładzie zastosowano metodę <xref:System.Int32.Parse%2A?displayProperty=nameWithType>, aby przeanalizować ciągi, które składają się z cyfr w różnych systemach pisania. Jak wynika z przykładu, próba przeanalizowania podstawowych cyfr szesnastkowych powiedzie się, ale próba przeanalizowania cyfr pełnej, arabskiej-indyjskich i bengalskich kończy się niepowodzeniem.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Globalization.NumberStyles>
- [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
