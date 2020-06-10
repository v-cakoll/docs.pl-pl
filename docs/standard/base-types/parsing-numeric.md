---
title: Analizowanie ciągów liczbowych w programie .NET
description: Dowiedz się więcej na temat analizowania ciągów liczbowych w programie .NET. Dowiedz się, jak analizować przy użyciu dostawców formatów, wyliczenia NumberStyles wartości wyliczenia i cyfry Unicode.
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
ms.openlocfilehash: b184bad10b816c1eae798302337b5c901732ad7f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589542"
---
# <a name="parsing-numeric-strings-in-net"></a>Analizowanie ciągów liczbowych w sieci
Wszystkie typy liczbowe mają dwie metody statycznej analizy `Parse` i `TryParse` , których można użyć do przekonwertowania ciągu reprezentującego liczbę do typu liczbowego. Te metody umożliwiają analizowanie ciągów, które zostały utworzone za pomocą ciągów formatu udokumentowanych w [standardowych ciągach formatu liczbowego](standard-numeric-format-strings.md) i [niestandardowych ciągów formatu liczbowego](custom-numeric-format-strings.md). Domyślnie `Parse` `TryParse` metody i mogą pomyślnie konwertować ciągi, które zawierają cyfry dziesiętne tylko do wartości całkowitych. Mogą pomyślnie konwertować ciągi, które zawierają cyfry całkowite i ułamkowe dziesiętne, separatory grup i separator dziesiętny do wartości zmiennoprzecinkowych. `Parse`Metoda zgłasza wyjątek, jeśli operacja nie powiedzie się, a `TryParse` Metoda zwraca `false` .  
  
## <a name="parsing-and-format-providers"></a>Analiza składniowa i format dostawców  
 Zazwyczaj reprezentacje ciągów wartości liczbowych różnią się w zależności od kultury. Elementy ciągów liczbowych, takich jak symbole walut, separatory grup (lub tysięcy) i Separatory dziesiętne różnią się w zależności od kultury. Metody analizy niejawnie lub jawnie używają dostawcy formatu, który rozpoznaje te Wariacje specyficzne dla kultury. Jeśli w wywołaniu metody lub nie określono dostawcy formatu `Parse` `TryParse` , jest używany dostawca formatu skojarzony z bieżącą kulturą wątku ( <xref:System.Globalization.NumberFormatInfo> obiekt zwracany przez <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> Właściwość).  
  
 Dostawca formatu jest reprezentowany przez <xref:System.IFormatProvider> implementację. Ten interfejs ma jeden element członkowski, <xref:System.IFormatProvider.GetFormat%2A> Metoda, której pojedynczy parametr jest <xref:System.Type> obiektem, który reprezentuje typ do sformatowania. Ta metoda zwraca obiekt, który dostarcza informacje o formatowaniu. Platforma .NET obsługuje następujące dwie <xref:System.IFormatProvider> implementacje analizy ciągów liczbowych:  
  
- <xref:System.Globalization.CultureInfo>Obiekt, którego <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> Metoda zwraca <xref:System.Globalization.NumberFormatInfo> obiekt, który dostarcza informacje o formatowaniu specyficzne dla kultury.  
  
- <xref:System.Globalization.NumberFormatInfo>Obiekt, którego <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> Metoda zwraca samą siebie.  
  
 Poniższy przykład próbuje skonwertować każdy ciąg w tablicy do <xref:System.Double> wartości. Najpierw próbuje przeanalizować ciąg przy użyciu dostawcy formatu, który odzwierciedla konwencje angielskiej (Stany Zjednoczone) kultury. Jeśli ta operacja zgłasza <xref:System.FormatException> , próbuje przeanalizować ciąg przy użyciu dostawcy formatu, który odzwierciedla konwencje kultury francuskiej (Francja).  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Analiza składniowa i wartości NumberStyles  
 Elementy stylu (takie jak odstępy, separatory grup i separator dziesiętny), które może obsłużyć operacja analizy, są definiowane przez <xref:System.Globalization.NumberStyles> wartość wyliczenia. Domyślnie ciągi reprezentujące wartości całkowite są analizowane przy użyciu <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> wartości, która zezwala na tylko cyfry liczbowe, wiodące i końcowe białe znaki oraz znak wiodący. Ciągi reprezentujące wartości zmiennoprzecinkowe są analizowane przy użyciu kombinacji <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> i <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> wartości; ten styl złożony dopuszcza cyfry dziesiętne oraz wiodące i końcowe białe znaki, znak wiodący, separator dziesiętny, separator grupy i wykładnik. Wywołując Przeciążenie `Parse` `TryParse` metody lub, która zawiera parametr typu <xref:System.Globalization.NumberStyles> i ustawiając jedną lub więcej <xref:System.Globalization.NumberStyles> flag, można kontrolować elementy stylu, które mogą być obecne w ciągu, aby operacja analizy powiodła się.  
  
 Na przykład ciąg zawierający separator grupy nie może zostać skonwertowany na <xref:System.Int32> wartość za pomocą <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> metody. Jednak konwersja powiedzie się, jeśli używasz <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> flagi, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
> Operacja analizy zawsze używa Konwencji formatowania określonej kultury. Jeśli nie określisz kultury przez przekazanie <xref:System.Globalization.CultureInfo> <xref:System.Globalization.NumberFormatInfo> obiektu, używana jest kultura skojarzona z bieżącym wątkiem.  
  
 W poniższej tabeli wymieniono elementy członkowskie <xref:System.Globalization.NumberStyles> wyliczenia i opisano wpływ ich działania na operację analizowania.  
  
|Wartość wyliczenia NumberStyles|Wpływ na ciąg, który ma zostać przeanalizowany|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Dozwolone są tylko cyfry numeryczne.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Dozwolone są Separatory dziesiętne i cyfry ułamkowe. W przypadku wartości całkowitych jako cyfry ułamkowej dozwolony jest tylko zero. Prawidłowe Separatory dziesiętne są określane przez <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> Właściwość or.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|Znak "e" lub "E" może służyć do wskazania notacji wykładniczej. <xref:System.Globalization.NumberStyles>Aby uzyskać dodatkowe informacje, zobacz.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Jest dozwolony wiodący biały znak.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Białe znaki końcowe są dozwolone.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Znak dodatni lub ujemny może poprzedzać cyfry cyfr.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Znak dodatni lub ujemny może następować po cyfrach numerycznych.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Nawiasy mogą służyć do wskazania wartości ujemnych.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Separator grupy jest dozwolony. Znak separatora grupy jest określany przez <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> Właściwość or.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Symbol waluty jest dozwolony. Symbol waluty jest definiowany przez <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> Właściwość.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Ciąg, który ma być analizowany, jest interpretowany jako liczba szesnastkowa. Może zawierać cyfry szesnastkowe 0-9, A-F i a-f. Ta flaga może być używana tylko do analizowania wartości całkowitych.|  
  
 Ponadto <xref:System.Globalization.NumberStyles> Wyliczenie zawiera następujące style złożone, które obejmują wiele <xref:System.Globalization.NumberStyles> flag.  
  
|Złożona wartość wyliczenia NumberStyles|Obejmuje członków|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|Zawiera <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType> Style, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> i <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> . Jest to domyślny styl używany do analizowania wartości całkowitych.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|Zawiera <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType> Style, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> ,,, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType> i <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> .|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|Zawiera <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType> Style, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> , <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> , <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType> i <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> .|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Zawiera wszystkie style z wyjątkiem <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> i <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> .|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Zawiera wszystkie style z wyjątkiem <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> .|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|Zawiera <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType> Style, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> i <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> .|  
  
## <a name="parsing-and-unicode-digits"></a>Analiza składniowa i cyfry Unicode  
 Standard Unicode definiuje punkty kodów dla cyfr w różnych systemach pisania. Na przykład punkty kodów z U + 0030 do U + 0039 reprezentują podstawowe cyfry łacińskie od 0 do 9, punkty kodów z U + 09E6 do U + 09EF reprezentują cyfry bengalskie od 0 do 9, a punkty kodu z U + FF10 do U + FF19 reprezentują cyfry pełnej od 0 do 9. Jednak jedynymi cyframi, które są rozpoznawane przez metody analizy, są podstawowe cyfry łacińskie 0-9 z punktami kodu od U + 0030 do U + 0039. Jeśli metoda analizy liczbowej została przeniesiona jako ciąg, który zawiera inne cyfry, metoda zgłasza <xref:System.FormatException> .  
  
 Poniższy przykład używa <xref:System.Int32.Parse%2A?displayProperty=nameWithType> metody do analizowania ciągów, które składają się z cyfr w różnych systemach pisania. Jak wynika z przykładu, próba przeanalizowania podstawowych cyfr szesnastkowych powiedzie się, ale próba przeanalizowania cyfr pełnej, arabskiej-indyjskich i bengalskich kończy się niepowodzeniem.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Globalization.NumberStyles>
- [Analiza składniowa ciągów](parsing-strings.md)
- [Formatowanie typów](formatting-types.md)
