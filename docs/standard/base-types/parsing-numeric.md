---
title: Analizowanie ciągów liczbowych na platformie .NET
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07ad8b278f6a44fce78bccc980acdc0dc93b1a7a
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743790"
---
# <a name="parsing-numeric-strings-in-net"></a>Analizowanie ciągów liczbowych w sieci
Wszystkie typy numeryczne mają dwie metody analizy statycznej, `Parse` i `TryParse`, której można przekonwertować ciąg reprezentujący liczbę na typ liczbowy. Te metody umożliwiają analizowanie ciągów, które zostały utworzone za pomocą ciągów formatu w [Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md) i [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md). Domyślnie `Parse` i `TryParse` może pomyślnie konwertują ciągi, które zawierają całkowite cyfry dziesiętne tylko dla wartości całkowitych. Można pomyślnie konwertują ciągi zawierające zaokrągleń cyfry dziesiętne, separatory grup i separator dziesiętny na wartości zmiennoprzecinkowe. `Parse` Metoda zgłasza wyjątek, jeśli operacja zakończy się niepowodzeniem, natomiast `TryParse` metoda zwraca `false`.  
  
## <a name="parsing-and-format-providers"></a>Analiza składniowa i format dostawców  
 Zazwyczaj ciągów reprezentujących wartości numeryczne różnią się od kultury. Elementy separatory liczbowe ciągów, takich jak waluty symbole, grupy (lub tysięcy) oraz separatory dziesiętne wszystkich zależą od kultury. Analiza kodu metody jawnie lub niejawnie Użyj dostawcę formatu, który rozpoznaje te różnice właściwe dla kultury. Jeśli żaden dostawca formatu jest określony w wywołaniu `Parse` lub `TryParse` metody, format skojarzonego z bieżącą kulturą wątku ( <xref:System.Globalization.NumberFormatInfo> obiektu zwróconego przez <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> właściwość) jest używany.  
  
 Dostawca formatu jest reprezentowany przez <xref:System.IFormatProvider> implementacji. Ten interfejs ma jeden element członkowski <xref:System.IFormatProvider.GetFormat%2A> metody, w której jeden parametr jest <xref:System.Type> obiekt, który reprezentuje typ do sformatowania. Ta metoda zwraca obiekt, który dostarcza informacje o formatowaniu. .NET wspomaga następujące dwa <xref:System.IFormatProvider> niedotyczące analizowanie ciągów numerycznych:  
  
-   A <xref:System.Globalization.CultureInfo> którego <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda zwraca <xref:System.Globalization.NumberFormatInfo> obiekt, który dostarcza informacje o formatowaniu specyficzne dla kultury.  
  
-   A <xref:System.Globalization.NumberFormatInfo> którego <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> metoda zwraca samą siebie.  
  
 Poniższy przykład podejmuje próbę przekonwertowania każdego ciągu w tablicy <xref:System.Double> wartość. Próbuje najpierw przeanalizować składni ciągu przy użyciu dostawcy formatu, który odzwierciedla Konwencji kultury angielski (Stany Zjednoczone). Jeśli operacja zgłosi <xref:System.FormatException>, próbuje przeanalizować składni ciągu przy użyciu dostawcy formatu, który odzwierciedla konwencje kultury francuski (Francja).  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Analiza składniowa i wartości NumberStyles  
 Elementy stylu (takie jak biały znak, separatory grup i separator dziesiętny), które może obsłużyć operacji analizy są definiowane przez <xref:System.Globalization.NumberStyles> wartość wyliczenia. Domyślnie ciągów reprezentujących wartości całkowitych są analizowane za pomocą <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> wartość, która zezwala na tylko cyfry, początkowe i końcowe białe znaki i wiodącym znakiem. Ciągów reprezentujących wartości zmiennoprzecinkowe są analizowane przy użyciu kombinacji <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> i <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> wartości; ten styl zezwala cyfr dziesiętnych oraz początkowe i końcowe biały znak, wiodący znak, separator dziesiętny, grupy Separator i wykładnika. Poprzez wywołanie przeciążenia `Parse` lub `TryParse` metodę, która zawiera parametr typu <xref:System.Globalization.NumberStyles> i ustawienia co najmniej jeden <xref:System.Globalization.NumberStyles> flagi, można kontrolować elementy stylu, które mogą być obecne w ciągu dla udanej operacji analizy powiodła się.  
  
 Na przykład ciąg, który zawiera separator grupy nie można przekonwertować na <xref:System.Int32> wartości za pomocą <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> metody. Jednak konwersja powiedzie się, jeśli używasz <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> Flaga, tak jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
>  Operacja analizy zawsze używa konwencji formatowania określonej kultury. Jeśli nie określisz kultury, przekazując <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.NumberFormatInfo> obiektu jest używana kultura skojarzone z bieżącym wątkiem.  
  
 Poniższa tabela zawiera listę elementów członkowskich <xref:System.Globalization.NumberStyles> wyliczenie i opisano wpływ, jaki mają one na operacji analizowania.  
  
|Wartość wyliczenia NumberStyles|Wpływ na ciąg, który ma być analizowany|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Dozwolone są tylko cyfry.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Separator dziesiętny i cyfry ułamkowe są dozwolone. Dla wartości całkowitych tylko zerowe jest dozwolona, wyświetlaną cyfrą ułamkową. Nieprawidłowa separatory dziesiętne są określane przez <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> lub <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|"E" lub znak "E", może służyć do wskazania notacji wykładniczej. Zobacz <xref:System.Globalization.NumberStyles> Aby uzyskać dodatkowe informacje.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Wiodący biały znak jest dozwolony.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Końcowe biały znak jest dozwolony.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Dodatnia lub ujemna znak może poprzedzać cyfr.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Cyfry po znaku dodatniego lub ujemnego.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Nawiasów może służyć do wskazywania wartości ujemnych.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Separator grupy jest dozwolone. Znak separatora grupy jest określana przez <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> lub <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Symbol waluty jest dozwolone. Symbol waluty jest definiowany przez <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Ciąg, który ma być analizowany, jest interpretowany jako liczbę szesnastkową. Może zawierać cyfry szesnastkowe 0-9, A-F i a-f. Ta flaga może służyć tylko do analizowania wartości całkowitych.|  
  
 Ponadto <xref:System.Globalization.NumberStyles> wyliczenie zawiera następujące style złożonego, obejmujących wiele <xref:System.Globalization.NumberStyles> flag.  
  
|Złożonej wartości wyliczenia NumberStyles|Zawiera elementy członkowskie|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|Obejmuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, i <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> style. Jest to domyślny styl używany do analizowania wartości całkowitych.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|Obejmuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, i <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> style.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|Obejmuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, i <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> style.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Zawiera wszystkie style, z wyjątkiem <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> i <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Zawiera wszystkie style, z wyjątkiem <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|Obejmuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, i <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> style.|  
  
## <a name="parsing-and-unicode-digits"></a>Analiza składniowa i cyfry Unicode  
 W standardzie Unicode definiuje punkty kodowe cyfr w różnych systemach zapisu. Na przykład punkty kodowe od U + 0030 do U + 0039 reprezentują podstawowe alfabetu łacińskiego cyfr od 0 do 9, punkty kodowe od U + 09E6 do U + 09EF reprezentują Bengalski cyfr od 0 do 9 i punkty kodowe od U + FF10 do U + FF19 reprezentują cyfr o od 0 do 9. Jednak tylko cyfry rozpoznawane przez analizowanie metody są podstawowe alfabetu łacińskiego cyfry 0-9 z punktami kodu od U + 0030 do U + 0039. Jeśli liczbowa analizy metody jest przekazywany Ciąg zawierający inne cyfr, metoda zgłasza <xref:System.FormatException>.  
  
 W poniższym przykładzie użyto <xref:System.Int32.Parse%2A?displayProperty=nameWithType> metodę, aby przeanalizować ciągi składające się z cyfr w różnych systemów pisania. Dane wyjściowe z przykładu pokazują, próba analizy podstawowych alfabetu łacińskiego cyfr zakończy się pomyślnie, ale próba analizy pozostawiany bez zmian, hindi arabski i Bengalski cyfr kończy się niepowodzeniem.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Globalization.NumberStyles>  
- [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)  
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
