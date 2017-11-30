---
title: "Standardowe ciągi formatujące TimeSpan"
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c4c486728ee4f98a6718c4d019976fccd6f380d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="standard-timespan-format-strings"></a>Standardowe ciągi formatujące TimeSpan
<a name="Top"></a>Standard <xref:System.TimeSpan> ciąg formatu używa specyfikator jeden format w celu zdefiniowania Reprezentacja tekstowa typu <xref:System.TimeSpan> wartość będącą wynikiem operacji formatowania. Interpretowany jako niestandardowego ciągu formatu, który zawiera więcej niż jeden znak odstępu, w tym <xref:System.TimeSpan> ciąg formatu. Aby uzyskać więcej informacji, zobacz [ciągi formatujące TimeSpan niestandardowe](../../../docs/standard/base-types/custom-timespan-format-strings.md) .  
  
 Reprezentacji ciągu <xref:System.TimeSpan> wartości są produkowane przez wywołania przeciążenia metody <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> metody, a także jako metodami, które obsługuje złożone, takich jak <xref:System.String.Format%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [typy formatowania](../../../docs/standard/base-types/formatting-types.md) i [złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md). Poniższy przykład przedstawia użycie standardowe ciągi formatujące w operacji formatowania.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Standardowe <xref:System.TimeSpan> ciągi formatujące są również używane przez <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> i <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody, aby zdefiniować wymagany format wejściowy ciągi do analizowania operacji. (Podczas analizowania konwertuje reprezentacja ciągu wartości do tej wartości.) Poniższy przykład przedstawia użycie standardowe ciągi formatujące podczas analizowania operacji.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
<a name="top"></a>W poniższej tabeli wymieniono specyfikatory formatu interwał czasu standardowego.  
  
|Specyfikator formatu|Nazwa|Opis|Przykłady|  
|----------------------|----------|-----------------|--------------|  
|"c"|Stałe formatu (niezmiennego)|Specyfikator to nie jest zależne od kultury. Ma formę `[-][d’.’]hh’:’mm’:’ss[‘.’fffffff]`.<br /><br /> ("T" i "T" ciągi formatujące utworzyć takie same wyniki).<br /><br /> Więcej informacji: [stałych ("c") specyfikator formatu](#Constant).|`TimeSpan.Zero` -> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)` -> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)` -> 3.17:25:30.5000000|  
|„g”|Ogólny format krótki|To specyfikator danych wyjściowych, co jest wymagane tylko. Jest zależne od kultury i ma postać `[-][d’:’]h’:’mm’:’ss[.FFFFFFF]`.<br /><br /> Więcej informacji: [ogólne krótkich ("g") specyfikator formatu](#GeneralShort).|`New TimeSpan(1, 3, 16, 50, 500)`-> 1:3:16:50.5 (en US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)`-> 1:3:16:50, 5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3:16:50.599 (en US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3:16:50, 599 (fr-FR)|  
|„G”|Ogólny format długi|To specyfikator zawsze generuje dni i siedmiu cyfr ułamkowych. Jest zależne od kultury i ma postać `[-]d’:’hh’:’mm’:’ss.fffffff`.<br /><br /> Więcej informacji: [ogólne długi ("G") specyfikator formatu](#GeneralLong).|`New TimeSpan(18, 30, 0)`-> 0:18:30:00.0000000 (en US)<br /><br /> `New TimeSpan(18, 30, 0)`-> 0:18:30:00, 0000000 (fr-FR)|  
  
<a name="Constant"></a>   
## <a name="the-constant-c-format-specifier"></a>Specyfikator formatu ("c") w stałej  
 Specyfikator formatu "c" zwraca reprezentację ciągu <xref:System.TimeSpan> wartość w następującym formacie:  
  
 [-] [*d*.] *hh*:*mm*:*ss*[. *fffffff*]  
  
 Elementy w nawiasach kwadratowych ([ i ]) są opcjonalne. Kropka (.) i dwukropka (:) są symbolami literału. W poniższej tabeli opisano wszystkie pozostałe elementy.  
  
|Element|Opis|  
|-------------|-----------------|  
|*-*|Opcjonalne znaku minus, co oznacza ujemna interwału.|  
|*d*|Opcjonalne liczbę dni, nie zera wiodące.|  
|*hh*|Liczba godzin, które zakresu od "00" do "23".|  
|*mm*|Liczba minut, która zakresu od "00" do "59".|  
|*ss*|Liczba sekund, które zakresu od "0" do "59".|  
|*fffffff*|Opcjonalne ułamkowych części sekundy.  Wartość może należeć do zakresu od "0000001" (co znaczników lub co 10 milionowych sekundy) do "9999999" (mniej znaczników co drugi 9 999 999 milionowych-dziesięć sekund lub jeden).|  
  
 W odróżnieniu od "g" i "G" specyfikatory formatu specyfikator formatu "c" nie jest zależne od kultury. Generuje reprezentację ciągu <xref:System.TimeSpan> wartość jest niezmienne i który jest wspólny dla wszystkich poprzednich wersji programu .NET Framework, przed [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Wartość domyślna to "c" <xref:System.TimeSpan> ciąg formatu; <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metody formatuje wartość interwału czasu za pomocą ciągu formatu "c".  
  
> [!NOTE]
>  <xref:System.TimeSpan>obsługuje również "t" i "T" standardowe ciągi formatujące, które są takie same jak w zachowanie standardowego formatu ciągu "c".  
  
 Poniższy przykład tworzy dwa <xref:System.TimeSpan> obiektów, używa ich do wykonania operacji arytmetycznych i wyświetla wyniki. W każdym przypadku używa złożone formatowanie do wyświetlenia <xref:System.TimeSpan> wartość przy użyciu specyfikatora formatu "c".  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  
  
 [Powrót do tabeli](#Top)  
  
<a name="GeneralShort"></a>   
## <a name="the-general-short-g-format-specifier"></a>Specyfikator formatu krótkiej ogólne ("g")  
 "g" <xref:System.TimeSpan> specyfikator formatu zwraca reprezentację ciągu <xref:System.TimeSpan> wartości w postaci compact, umieszczając w niej elementów, które są niezbędne. Ma następujący format:  
  
 [-] [*d*:]*h*:*mm*:*ss*[. *FFFFFFF*]  
  
 Elementy w nawiasach kwadratowych ([ i ]) są opcjonalne. Dwukropka (:) jest symbolem literału. W poniższej tabeli opisano wszystkie pozostałe elementy.  
  
|Element|Opis|  
|-------------|-----------------|  
|*-*|Opcjonalne znaku minus, co oznacza ujemna interwału.|  
|*d*|Opcjonalne liczbę dni, nie zera wiodące.|  
|*h*|Liczba godzin, które w zakresie od "0" do "23" nie zera wiodące.|  
|*mm*|Liczba minut, która zakresu od "00" do "59"...|  
|*ss*|Liczba sekund, które zakresu od "00" do "59"...|  
|*.*|Separator ułamkowych części sekundy. Jest to równoważne określonej kultury <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> przesłania właściwość bez użytkowników.|  
|*FFFFFFF*|Ułamkowych części sekundy. Jak wyświetlanych jest kilka cyfr, jak to możliwe.|  
  
 Podobnie jak specyfikatora formatu "G" jest zlokalizowana specyfikator formatu "g". Separator jego ułamkowych części sekundy opiera się na bieżącej kultury lub określonej kultury <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> właściwości.  
  
 Poniższy przykład tworzy dwa <xref:System.TimeSpan> obiektów, używa ich do wykonania operacji arytmetycznych i wyświetla wyniki. W każdym przypadku używa złożone formatowanie do wyświetlenia <xref:System.TimeSpan> wartość przy użyciu specyfikatora formatu "g". Ponadto formatuje <xref:System.TimeSpan> wartość przy użyciu konwencji formatowania bieżącej kultury systemu (czyli, w tym przypadku Polski — Polska lub en US) i francuskim - kultury Francja (fr-FR).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  
  
 [Powrót do tabeli](#Top)  
  
<a name="GeneralLong"></a>   
## <a name="the-general-long-g-format-specifier"></a>Specyfikator formatu Ogólne Long ("G")  
 "G" <xref:System.TimeSpan> specyfikator formatu zwraca reprezentację ciągu <xref:System.TimeSpan> wartość długich fragmentów, który zawsze zawiera dni i ułamkowych części sekundy. Ciąg, który jest wynikiem specyfikator formatu standardowych "G" ma następującą postać:  
  
 [-] *d*:*hh*:*mm*:*ss*. *fffffff*  
  
 Elementy w nawiasach kwadratowych ([ i ]) są opcjonalne. Dwukropka (:) jest symbolem literału. W poniższej tabeli opisano wszystkie pozostałe elementy.  
  
|Element|Opis|  
|-------------|-----------------|  
|*-*|Opcjonalne znaku minus, co oznacza ujemna interwału.|  
|*d*|Liczba dni nie zera wiodące.|  
|*hh*|Liczba godzin, które zakresu od "00" do "23".|  
|*mm*|Liczba minut, która zakresu od "00" do "59".|  
|*ss*|Liczba sekund, które zakresu od "00" do "59".|  
|*.*|Separator ułamkowych części sekundy. Jest to równoważne określonej kultury <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> przesłania właściwość bez użytkowników.|  
|*fffffff*|Ułamkowych części sekundy.|  
  
 Podobnie jak specyfikatora formatu "G" jest zlokalizowana specyfikator formatu "g". Separator jego ułamkowych części sekundy opiera się na bieżącej kultury lub określonej kultury <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> właściwości.  
  
 Poniższy przykład tworzy dwa <xref:System.TimeSpan> obiektów, używa ich do wykonania operacji arytmetycznych i wyświetla wyniki. W każdym przypadku używa złożone formatowanie do wyświetlenia <xref:System.TimeSpan> wartość przy użyciu specyfikatora formatu "G". Ponadto formatuje <xref:System.TimeSpan> wartość przy użyciu konwencji formatowania bieżącej kultury systemu (czyli, w tym przypadku Polski — Polska lub en US) i francuskim - kultury Francja (fr-FR).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]  
  
 [Powrót do tabeli](#Top)  
  
## <a name="see-also"></a>Zobacz też  
 [Formatowanie tekstu](../../../docs/standard/base-types/formatting-types.md)  
 [Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)  
 [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)
