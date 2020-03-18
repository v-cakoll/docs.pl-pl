---
title: Analizowanie ciągów liczbowych w .NET
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127602"
---
# <a name="parsing-numeric-strings-in-net"></a>Analizowanie ciągów liczbowych w sieci
Wszystkie typy liczbowe mają dwie statyczne `Parse` `TryParse`metody analizowania i , które można użyć do konwersji reprezentacji ciągu liczby na typ liczbowy. Metody te umożliwiają analizowanie ciągów, które zostały wyprodukowane przy użyciu ciągów formatu udokumentowanych w [standardowych ciągach formatu numerycznego](../../../docs/standard/base-types/standard-numeric-format-strings.md) i [niestandardowych ciągach formatu numerycznego](../../../docs/standard/base-types/custom-numeric-format-strings.md). Domyślnie `Parse` metody `TryParse` i mogą pomyślnie konwertować ciągi zawierające integralne cyfry dziesiętne tylko na wartości całkowite. Mogą pomyślnie konwertować ciągi zawierające cyfry dziesiętne, separatory grup i separator dziesiętny na wartości zmiennoprzecinkowe. Metoda `Parse` zgłasza wyjątek, jeśli operacja nie powiedzie się, podczas `TryParse` gdy metoda zwraca `false`.  
  
## <a name="parsing-and-format-providers"></a>Analiza składniowa i format dostawców  
 Zazwyczaj reprezentacje ciągów wartości liczbowych różnią się w zależności od kultury. Elementy ciągów liczbowych, takich jak symbole waluty, separatory grup (lub tysiące) i separatory dziesiętne różnią się w zależności od kultury. Metody analizowania niejawnie lub jawnie używają dostawcy formatu, który rozpoznaje te odmiany specyficzne dla kultury. Jeśli żaden dostawca formatu nie jest `Parse` `TryParse` określony w wywołaniu lub metody, używany <xref:System.Globalization.NumberFormatInfo> jest dostawca <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> formatu skojarzony z bieżącą kulturą wątku (obiekt zwrócony przez właściwość).  
  
 Dostawca formatu jest reprezentowany <xref:System.IFormatProvider> przez implementację. Ten interfejs ma jeden <xref:System.IFormatProvider.GetFormat%2A> element członkowski, <xref:System.Type> metodę, której pojedynczy parametr jest obiektem reprezentującym typ, który ma być sformatowany. Ta metoda zwraca obiekt, który zawiera informacje o formatowaniu. .NET obsługuje następujące <xref:System.IFormatProvider> dwie implementacje do analizowania ciągów liczbowych:  
  
- Obiekt, <xref:System.Globalization.CultureInfo> <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> którego metoda <xref:System.Globalization.NumberFormatInfo> zwraca obiekt, który zawiera informacje o formatowaniu specyficzne dla kultury.  
  
- Obiekt, <xref:System.Globalization.NumberFormatInfo> <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> którego metoda zwraca się.  
  
 Poniższy przykład próbuje przekonwertować każdy ciąg <xref:System.Double> w tablicy do wartości. Najpierw próbuje przeanalizować ciąg przy użyciu dostawcy formatu, który odzwierciedla konwencje kultury angielski (Stany Zjednoczone). Jeśli ta operacja <xref:System.FormatException>powoduje wysuwanie ciąg , próbuje przeanalizować ciąg przy użyciu dostawcy formatu, który odzwierciedla konwencje kultury francuskiej (Francja).  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Analiza składniowa i wartości NumberStyles  
 Elementy stylu (takie jak biały znak, separatory grup i separator dziesiętny), które operacja <xref:System.Globalization.NumberStyles> analizy może obsłużyć, są definiowane przez wartość wyliczenia. Domyślnie ciągi reprezentujące wartości całkowite są analizowane <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> przy użyciu wartości, która zezwala tylko na cyfry, początkowe i końcowe białe znaki oraz znak wiodący. Ciągi reprezentujące wartości zmiennoprzecinkowe są <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> analizowane przy użyciu kombinacji i <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> wartości; ten styl złożony umożliwia cyfry dziesiętne wraz z białym znakiem wiodącym i sutkowym, znakiem wiodącym, separatorem dziesiętnym, separatorem grupy i wykładnikiem. Wywołując przeciążenie `Parse` lub `TryParse` metody, która zawiera <xref:System.Globalization.NumberStyles> parametr typu i <xref:System.Globalization.NumberStyles> ustawienie jednej lub więcej flag, można kontrolować elementy stylu, które mogą być obecne w ciągu dla operacji analizy, aby odnieść sukces.  
  
 Na przykład ciąg zawierający separator grupy nie można <xref:System.Int32> przekonwertować <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> na wartość przy użyciu metody. Jednak konwersja powiedzie się, <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> jeśli używasz flagi, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
> Operacja analizy zawsze używa konwencji formatowania określonej kultury. Jeśli nie określisz kultury <xref:System.Globalization.CultureInfo> <xref:System.Globalization.NumberFormatInfo> przez przekazywanie lub obiektu, kultura skojarzona z bieżącym wątku jest używany.  
  
 W poniższej tabeli wymieniono elementy członkowskie <xref:System.Globalization.NumberStyles> wyliczenia i opisano ich wpływ na operację analizy.  
  
|Wartość wyliczenia NumberStyles|Wpływ na ciąg do przeanalizowania|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Dozwolone są tylko cyfry.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Separator dziesiętny i cyfry ułamkowe są dozwolone. W przypadku wartości całkowitych tylko zero jest dozwolone jako cyfra ułamkowa. Prawidłowe separatory dziesiętne <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> są <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> określane przez lub właściwość.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|Znak "e" lub "E" może służyć do wskazania notacji wykładniczej. Dodatkowe <xref:System.Globalization.NumberStyles> informacje można znaleźć w centrum uwagi.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Dozwolone jest prowadzenie biały znak.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Dozwolone jest spływu biały znak.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Znak dodatni lub ujemny może poprzedzać cyfry liczbowe.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Znak dodatni lub ujemny może być zgodny z cyframi.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Nawiasy mogą służyć do wskazywania wartości ujemnych.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Separator grupy jest dozwolony. Znak separatora grupy jest <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> określana przez lub właściwość.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Symbol waluty jest dozwolony. Symbol waluty jest definiowany <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> przez właściwość.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Ciąg do przeanalizowania jest interpretowany jako liczba szesnastkowa. Może zawierać cyfry szesnastkowe 0-9, A-F i a-f. Ta flaga może służyć tylko do analizowania wartości całkowitych.|  
  
 Ponadto <xref:System.Globalization.NumberStyles> wyliczenie zawiera następujące style złożone, <xref:System.Globalization.NumberStyles> które zawierają wiele flag.  
  
|Wartość złożonych stylów liczb|Obejmuje członków|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|Zawiera <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>i <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> style. Jest to styl domyślny używany do analizowania wartości całkowitych.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|Zawiera <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>style <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> , i style.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|Zawiera <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> i style.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Zawiera wszystkie <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> style <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>z wyjątkiem i .|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Zawiera wszystkie <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>style z wyjątkiem .|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|Zawiera <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>i <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> style.|  
  
## <a name="parsing-and-unicode-digits"></a>Analiza składniowa i cyfry Unicode  
 Standard Unicode definiuje punkty kodowe dla cyfr w różnych systemach pisania. Na przykład punkty kodu od U +0030 do U +0039 reprezentują podstawowe cyfry łacińskie od 0 do 9, punkty kodu od U +09E6 do U +09EF reprezentują cyfry Bangla od 0 do 9, a punkty kodu od U +FF10 do U +FF19 reprezentują cyfry fullwidth od 0 do 9. Jednak tylko cyfry rozpoznawane przez metody analizy są podstawowe cyfry łacińskie 0-9 z punktów kodu od U + 0030 do U + 0039. Jeśli metoda analizy liczbowej jest przekazywana ciąg zawierający inne cyfry, <xref:System.FormatException>metoda zgłasza .  
  
 W poniższym <xref:System.Int32.Parse%2A?displayProperty=nameWithType> przykładzie użyto metody do analizowania ciągów, które składają się z cyfr w różnych systemach pisania. Jak pokazuje dane wyjściowe z przykładu, próba przeanalizowania podstawowych cyfr łacińskich powiedzie się, ale próba przeanalizowania cyfr Fullwidth, Arabska indic i Bangla nie powiedzie się.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Globalization.NumberStyles>
- [Analiza składniowa ciągów](../../../docs/standard/base-types/parsing-strings.md)
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
