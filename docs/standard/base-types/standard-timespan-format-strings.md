---
title: Standardowe ciągi formatu TimeSpan
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, standard time interval
- format strings
- standard time interval format strings
- standard format strings, time intervals
- format specifiers, time intervals
- time intervals [.NET Framework], formatting
- time [.NET Framework], formatting
- formatting [.NET Framework], time
- standard TimeSpan format strings
- formatting [.NET Framework], time intervals
ms.assetid: 9f6c95eb-63ae-4dcc-9c32-f81985c75794
ms.openlocfilehash: ec06edc16829c6d4caf8c760922aac1471e365c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75346629"
---
# <a name="standard-timespan-format-strings"></a>Standardowe ciągi formatu TimeSpan

Standardowy <xref:System.TimeSpan> ciąg formatu używa specyfikatora pojedynczego <xref:System.TimeSpan> formatu do zdefiniowania reprezentacji tekstowej wartości wynikającej z operacji formatowania. Dowolny ciąg formatu zawierający więcej niż jeden znak, w <xref:System.TimeSpan> tym biały znak, jest interpretowany jako ciąg formatu niestandardowego. Aby uzyskać więcej informacji, zobacz [Niestandardowe ciągi formatu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md) .  
  
 Reprezentacje ciągów <xref:System.TimeSpan> wartości są tworzone przez wywołania <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> przeciążenia metody, a także za pomocą metod <xref:System.String.Format%2A?displayProperty=nameWithType>obsługujących formatowanie złożone, takie jak . Aby uzyskać więcej informacji, zobacz [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md) i [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md). W poniższym przykładzie przedstawiono użycie standardowych ciągów formatu w operacjach formatowania.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Ciągi formatu standardowego <xref:System.TimeSpan> <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> są <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> również używane przez i metody do definiowania wymaganego formatu ciągów wejściowych dla operacji analizy. (Analizowanie konwertuje reprezentację ciągu wartości na tę wartość). W poniższym przykładzie przedstawiono użycie standardowych ciągów formatu w operacjach analizy.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
W poniższej tabeli wymieniono specyfikatory formatu standardowego interwału czasowego.  
  
|Specyfikator formatu|Nazwa|Opis|Przykłady|  
|----------------------|----------|-----------------|--------------|  
|"c"|Format stały (niezmienny)|Ten specyfikator nie jest zależny od kultury. Przyjmuje formę `[-][d'.']hh':'mm':'ss['.'fffffff]`.<br /><br /> (Ciągi formatu "t" i "T" dają te same wyniki).<br /><br /> Więcej informacji: [Stały ("c") Specyfikator formatu](#the-constant-c-format-specifier).|`TimeSpan.Zero`- > 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)`- > 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)`-> 3.17:25:30.50000000|  
|„g”|Ogólny krótki format|Ten specyfikator wyprowadza tylko to, co jest potrzebne. Jest wrażliwy na kulturę `[-][d':']h':'mm':'ss[.FFFFFFF]`i przybiera formę.<br /><br /> Więcej informacji: [Ogólny krótki ("g") Specyfikator formatu](#the-general-short-g-format-specifier).|`New TimeSpan(1, 3, 16, 50, 500)`-> 1:3:16:50.5 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)`-> 1:3:16:50,5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`- > 1:3:16:50.599 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3:16:50,599 (fr-FR)|  
|„G”|Ogólny format długi|Ten specyfikator zawsze generuje dni i siedem cyfr ułamkowych. Jest wrażliwy na kulturę `[-]d':'hh':'mm':'ss.fffffff`i przybiera formę.<br /><br /> Więcej informacji: [Specyfikator formatu Ogólnego Długiego ("G")](#the-general-long-g-format-specifier).|`New TimeSpan(18, 30, 0)`-> 0:18:30:00.0000000 (en-US)<br /><br /> `New TimeSpan(18, 30, 0)`-> 0:18:30:00,00000000 (fr-FR)|  

## <a name="the-constant-c-format-specifier"></a>Konstyntor formatu constant ("c")  
 Specyfikator formatu "c" zwraca <xref:System.TimeSpan> reprezentację ciągu wartości w następującej formie:  
  
 [-] [*d*.] *hh*:*mm*:*ss*[.* fffffff*]  
  
 Elementy w nawiasach kwadratowych ([ i ]) są opcjonalne. Okres (.) i dwukropek (:) są symbolami dosłownymi. W poniższej tabeli opisano pozostałe elementy.  
  
|Element|Opis|  
|-------------|-----------------|  
|*-*|Opcjonalny znak ujemny, który wskazuje ujemny przedział czasu.|  
|*D*|Opcjonalna liczba dni, bez zer wiodących.|  
|*hh*|Liczba godzin, która waha się od "00" do "23".|  
|*Mm*|Liczba minut, która waha się od "00" do "59".|  
|*Ss*|Liczba sekund, która waha się od "0" do "59".|  
|*Fffffff*|Opcjonalna ułamkowa część sekundy.  Jego wartość może wahać się od "0000001" (jeden kleszcz, lub jedna dziesiąta milionowa sekundy) do "9999999" (9 999 999 dziesięć milionowych części sekundy, lub jedna sekunda mniej jeden kleszcz).|  
  
 W przeciwieństwie do specyfikatorów formatu "g" i "G", specyfikator formatu "c" nie jest zależny od kultury. Tworzy reprezentację ciągu <xref:System.TimeSpan> wartości, która jest niezmienna i która jest wspólna dla wszystkich poprzednich wersji .NET Framework przed .NET Framework 4. "c" jest <xref:System.TimeSpan> domyślnym ciągiem formatu; <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metoda formatuje wartość interwału czasu przy użyciu ciągu formatu "c".  
  
> [!NOTE]
> <xref:System.TimeSpan>obsługuje również standardowe ciągi formatu "t" i "T", które są identyczne pod względem zachowania do ciągu standardowego formatu "c".  
  
 Poniższy przykład tworzy wystąpienia <xref:System.TimeSpan> dwóch obiektów, używa ich do wykonywania operacji arytmetycznych i wyświetla wynik. W każdym przypadku używa formatowania złożonego <xref:System.TimeSpan> do wyświetlania wartości przy użyciu specyfikatora formatu "c".  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  

## <a name="the-general-short-g-format-specifier"></a>Specyfikator formatu ogólnego krótkiego ("g")  
 Specyfikator <xref:System.TimeSpan> formatu "g" zwraca <xref:System.TimeSpan> reprezentację ciągu wartości w formie kompaktowej, dołączając tylko elementy, które są niezbędne. Ma następującą formę:  
  
 [-] [*d*:] *h*:*mm*:*ss*[.* FFFFFFF*]  
  
 Elementy w nawiasach kwadratowych ([ i ]) są opcjonalne. Dwukropek (:) jest symbolem dosłownym. W poniższej tabeli opisano pozostałe elementy.  
  
|Element|Opis|  
|-------------|-----------------|  
|*-*|Opcjonalny znak ujemny, który wskazuje ujemny przedział czasu.|  
|*D*|Opcjonalna liczba dni, bez zer wiodących.|  
|*H*|Liczba godzin, która waha się od "0" do "23", bez zer wiodących.|  
|*Mm*|Liczba minut, która waha się od "00" do "59"..|  
|*Ss*|Liczba sekund, która waha się od "00" do "59"..|  
|*.*|Separator ułamków sekund. Jest to równoważne właściwości określonej <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> kultury bez zastępowania użytkownika.|  
|*Fffffff*|Ułamków sekund. Wyświetlana jest jak najmniejsza liczba cyfr.|  
  
 Podobnie jak specyfikator formatu "G", specyfikator formatu "g" jest zlokalizowany. Jego separator ułamków sekund jest oparty na bieżącej kultury <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> lub właściwości określonej kultury.  
  
 Poniższy przykład tworzy wystąpienia <xref:System.TimeSpan> dwóch obiektów, używa ich do wykonywania operacji arytmetycznych i wyświetla wynik. W każdym przypadku używa formatowania kompozytowego <xref:System.TimeSpan> do wyświetlania wartości przy użyciu specyfikatora formatu "g". Ponadto formatuje <xref:System.TimeSpan> wartość przy użyciu konwencji formatowania bieżącej kultury systemu (która w tym przypadku jest angielska - Stany Zjednoczone lub en-US) i francuska - Francja (fr-FR) kultury.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  

## <a name="the-general-long-g-format-specifier"></a>Specyfikator formatu Ogólne long ("G")  
 Specyfikator <xref:System.TimeSpan> formatu "G" zwraca <xref:System.TimeSpan> reprezentację ciągu wartości w długiej formie, która zawsze zawiera zarówno dni, jak i ułamki sekund. Ciąg, który wynika z specyfikatora standardowego formatu "G" ma następujący formularz:  
  
 [-] *d*:*hh*:*mm*:*ss*. *fffffff*  
  
 Elementy w nawiasach kwadratowych ([ i ]) są opcjonalne. Dwukropek (:) jest symbolem dosłownym. W poniższej tabeli opisano pozostałe elementy.  
  
|Element|Opis|  
|-------------|-----------------|  
|*-*|Opcjonalny znak ujemny, który wskazuje ujemny przedział czasu.|  
|*D*|Liczba dni, bez zer wiodących.|  
|*hh*|Liczba godzin, która waha się od "00" do "23".|  
|*Mm*|Liczba minut, która waha się od "00" do "59".|  
|*Ss*|Liczba sekund, która waha się od "00" do "59".|  
|*.*|Separator ułamków sekund. Jest to równoważne właściwości określonej <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> kultury bez zastępowania użytkownika.|  
|*Fffffff*|Ułamków sekund.|  
  
 Podobnie jak specyfikator formatu "G", specyfikator formatu "g" jest zlokalizowany. Jego separator ułamków sekund jest oparty na bieżącej kultury <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> lub właściwości określonej kultury.  
  
 Poniższy przykład tworzy wystąpienia <xref:System.TimeSpan> dwóch obiektów, używa ich do wykonywania operacji arytmetycznych i wyświetla wynik. W każdym przypadku używa formatowania kompozytowego <xref:System.TimeSpan> do wyświetlania wartości przy użyciu specyfikatora formatu "G". Ponadto formatuje <xref:System.TimeSpan> wartość przy użyciu konwencji formatowania bieżącej kultury systemu (która w tym przypadku jest angielska - Stany Zjednoczone lub en-US) i francuska - Francja (fr-FR) kultury.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]
  
## <a name="see-also"></a>Zobacz też

- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
- [Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Analiza składniowa ciągów](../../../docs/standard/base-types/parsing-strings.md)
