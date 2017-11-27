---
title: "Analizowanie ciągów liczbowych w .NET"
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
- parsing strings, numeric strings
- numeric strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
ms.assetid: e39324ee-72e5-42d4-a80d-bf3ee7fc6c59
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c9bb58b0d7b45ca197653742844be01ac3bbe41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-numeric-strings-in-net"></a>Analizowanie ciągów liczbowych w sieci
Wszystkie typy liczbowe ma dwie metody analizy statycznej, `Parse` i `TryParse`, której można konwertować reprezentację liczby typu liczbowego. Te metody umożliwiają analizowanie ciągów, które zostały utworzone za pomocą ciągów formatu w [standardowe ciągi formatu liczbowego](../../../docs/standard/base-types/standard-numeric-format-strings.md) i [niestandardowe ciągi formatów liczbowych](../../../docs/standard/base-types/custom-numeric-format-strings.md). Domyślnie `Parse` i `TryParse` metody pomyślnie przekonwertować ciągi zawierające integralną cyfr dziesiętnych tylko do wartości będące liczbami całkowitymi. Umożliwiają one pomyślnie Konwertowanie ciągów zawierających wynikających z zaokrągleń cyfr dziesiętnych, separatorów grup i separator dziesiętny na wartości zmiennoprzecinkowe. `Parse` Metoda zgłasza wyjątek, jeśli operacja nie powiedzie się, natomiast `TryParse` metoda zwraca `false`.  
  
## <a name="parsing-and-format-providers"></a>Analiza składniowa i format dostawców  
 Zazwyczaj reprezentacji ciągu wartości liczbowych różnią się kultury. Elementy separatorów ciągi numeryczne, takich jak waluty symbole, grupy (lub tysięcy) i separatorów dziesiętnych wszystkie zależne od kultury. Podczas analizowania metody jawnie lub użyj dostawcy formatu, który rozpoznaje tych zmian specyficzne dla kultury. Jeśli żaden dostawca formatu jest określony w wywołaniu `Parse` lub `TryParse` metoda, format dostawcy skojarzonego z bieżącej kultury wątku ( <xref:System.Globalization.NumberFormatInfo> obiektu zwróconego przez <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> właściwości) jest używany.  
  
 Dostawca formatu jest reprezentowana przez <xref:System.IFormatProvider> implementacji. Ten interfejs jest jeden element członkowski <xref:System.IFormatProvider.GetFormat%2A> metody, w których pojedynczy parametr jest <xref:System.Type> obiekt, który reprezentuje typ do sformatowania. Ta metoda zwraca obiekt, który zawiera informacje dotyczące formatowania. .NET obsługuje dwa <xref:System.IFormatProvider> implementacji dla analizowanie ciągów liczbowych:  
  
-   A <xref:System.Globalization.CultureInfo> którego <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda zwraca <xref:System.Globalization.NumberFormatInfo> obiekt, który zawiera informacje dotyczące formatowania specyficzne dla kultury.  
  
-   A <xref:System.Globalization.NumberFormatInfo> którego <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> metoda zwraca siebie.  
  
 Poniższy przykład podejmuje próbę przekonwertowania każdy ciąg w tablicy do <xref:System.Double> wartości. Po raz pierwszy próbuje do analizy ciągu przy użyciu dostawcy formatu, które odzwierciedla konwencje kultury angielski (Stany Zjednoczone). Jeśli ta operacja zgłasza <xref:System.FormatException>, próbuje przeanalizować składni ciągu przy użyciu dostawcy formatu, które odzwierciedla konwencje kultury francuski (Francja).  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Analiza składniowa i wartości NumberStyles  
 Elementy stylu (na przykład biały znak, separatorów grup i separator dziesiętny), które może obsłużyć operacji analizowania są definiowane przez <xref:System.Globalization.NumberStyles> wartości wyliczenia. Domyślnie ciągów reprezentujących wartości niecałkowite są parsowane przy użyciu <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> wartość, która zezwala na tylko cyfry, początkowe i końcowe białe i wiodący znak. Ciągi, które reprezentują wartości zmiennoprzecinkowych są parsowane przy użyciu kombinacji <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> i <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> wartości; ten styl złożonego zezwala cyfr dziesiętnych wraz z spacji wiodących i końcowych białych, wiodący znak, separator dziesiętny, grupy Separator i wykładnik. Wywołując przeciążenia `Parse` lub `TryParse` metodę, która zawiera parametr typu <xref:System.Globalization.NumberStyles> i ustawienie jednego lub więcej <xref:System.Globalization.NumberStyles> flagi, można kontrolować elementy style, które mogą być obecne w ciągu na operacji analizy powiodło się.  
  
 Na przykład ciąg, który zawiera separator grupy nie można przekonwertować na <xref:System.Int32> wartość przy użyciu <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> metody. Jednak konwersji zakończy się pomyślnie, jeśli używasz <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> Flaga, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
>  Operacji analizowania zawsze używa konwencji formatowania określonej kultury. Jeśli nie określisz kultury przez przekazanie <xref:System.Globalization.CultureInfo> lub <xref:System.Globalization.NumberFormatInfo> obiekt kultury skojarzone z bieżącym wątku jest używany.  
  
 Poniższa tabela zawiera listę elementów członkowskich <xref:System.Globalization.NumberStyles> wyliczenie i opisano wpływ, jaki mają one na operację analizy.  
  
|Wartość wyliczenia NumberStyles|Wpływ na ciąg do przeanalizowania|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Dozwolone są tylko cyfry.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Separator dziesiętny i cyfr ułamkowych jest dozwolone. Na liczby całkowite tylko zerowe jest dozwolone jako cyfr ułamkowych. Nieprawidłowa separatorów dziesiętnych są określane przez <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> lub <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|"E" lub "E" znak można wskazać notacji wykładniczej. Zobacz <xref:System.Globalization.NumberStyles> Aby uzyskać dodatkowe informacje.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Wiodące biały znak jest dozwolone.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Końcowe biały znak jest dozwolone.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Znak dodatnie lub ujemne może poprzedzać cyfr.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Znak dodatnie lub ujemne, mogą wykonać cyfr.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Nawiasy można wskazać wartości ujemnych.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Separator grupy jest dozwolone. Znak separatora grupy jest określana przez <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> lub <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Symbol waluty jest dozwolone. Symbol waluty jest definiowana za pomocą <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Ciąg do przeanalizowania jest interpretowany jako liczbę szesnastkową. Może zawierać cyfry szesnastkowe 0-9, A-F i a-f. Ta flaga może służyć tylko do analizy wartości będące liczbami całkowitymi.|  
  
 Ponadto <xref:System.Globalization.NumberStyles> wyliczenie zawiera następujące style złożonego, obejmujących wiele <xref:System.Globalization.NumberStyles> flagi.  
  
|Wartość NumberStyles złożone|Zawiera elementy członkowskie|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|Obejmuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, i <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> style. Jest to domyślny styl używany do analizowania wartości będące liczbami całkowitymi.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|Obejmuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, i <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> style.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|Obejmuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, i <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> style.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Zawiera wszystkie style, z wyjątkiem <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> i <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Zawiera wszystkie style, z wyjątkiem <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|Obejmuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, i <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> style.|  
  
## <a name="parsing-and-unicode-digits"></a>Analiza składniowa i cyfry Unicode  
 Unicode standard definiuje punktów kodowych cyfr w różnych systemach zapisu. Na przykład wskazuje kod z U + 0030 U + 0039 reprezentują podstawowe alfabetu łacińskiego cyfry od 0 do 9, wskazuje kod z 09E6 U + U + 09EF reprezentują bengalskim cyfry od 0 do 9 oraz wskazuje kod z U + FF10 U + FF19 reprezentuje cyfr o pełnej szerokości od 0 do 9. Jednak tylko cyfry rozpoznał analizowania metody są podstawowe alfabetu łacińskiego cyfry 0-9 z punktami kodu z U + 0030 do U + 0039. Jeśli liczbową analizy metody jest przekazywany Ciąg zawierający inne cyfr, metoda wygeneruje <xref:System.FormatException>.  
  
 W poniższym przykładzie użyto <xref:System.Int32.Parse%2A?displayProperty=nameWithType> metodę, aby przeanalizować ciągów, które składają się z cyfr w różnych systemów pisania. Jak dane wyjściowe w przykładzie pokazano, próba analizy podstawowych cyfr alfabetu łacińskiego zakończy się pomyślnie, ale próba przeanalizować o pełnej szerokości, arabskiego indyjskiego i bengalskim cyfr kończy się niepowodzeniem.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Globalization.NumberStyles>  
 [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)  
 [Formatowanie tekstu](../../../docs/standard/base-types/formatting-types.md)
