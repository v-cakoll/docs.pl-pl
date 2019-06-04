---
title: Standardowe ciągi formatujące TimeSpan
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e67861a32d5863e4c1b4d9b147c507c1bb54c39
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66491099"
---
# <a name="standard-timespan-format-strings"></a>Standardowe ciągi formatujące TimeSpan
<a name="Top"></a> Standardowa <xref:System.TimeSpan> Ciąg formatujący używa pojedynczego specyfikatora formatu w celu zdefiniowania tekstowa reprezentacja <xref:System.TimeSpan> wartość będącą wynikiem operacji formatowania. Dowolny ciąg formatu, który zawiera więcej niż jeden znak, w tym znak odstępu, jest interpretowany jako niestandardowy <xref:System.TimeSpan> ciąg formatu. Aby uzyskać więcej informacji, zobacz [Custom TimeSpan Format Strings](../../../docs/standard/base-types/custom-timespan-format-strings.md) .  
  
 Ciągów reprezentujących <xref:System.TimeSpan> wartości są tworzone przez wywołania przeciążenia <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> metody, jak również tak, jak za pomocą metod, które obsługują formatowanie złożone, takich jak <xref:System.String.Format%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [typy formatowania](../../../docs/standard/base-types/formatting-types.md) i [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md). Poniższy przykład ilustruje użycie ciągów formatu standardowego w operacjach formatowania.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Standardowa <xref:System.TimeSpan> ciągi formatu są również używane przez <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> i <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> definiują wymagany format parametru metody wejściowe ciągi dla operacji analizowania. (Podczas analizowania konwertuje ciąg reprezentujący wartość tej wartości.) Poniższy przykład ilustruje użycie ciągów formatu standardowego w operacji analizowania.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
<a name="top"></a> Poniższa tabela zawiera listę specyfikatorów formatu interwału (czas standardowy).  
  
|Specyfikator formatu|Nazwa|Opis|Przykłady|  
|----------------------|----------|-----------------|--------------|  
|"c"|Stałe formatu (niezmiennego)|Ten specyfikator nie jest uwzględniana kultura. Ma postać `[-][d'.']hh':'mm':'ss['.'fffffff]`.<br /><br /> ("T" i ciągi formatu "T" generuje te same wyniki).<br /><br /> Więcej informacji: [Specyfikator formatu ("c") stałej](#Constant).|`TimeSpan.Zero` -> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)` -> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)` -> 3.17:25:30.5000000|  
|„g”|Ogólnym formacie krótkim|Dane wyjściowe tego specyfikatora, tylko potrzebne elementy. Jest uwzględniana kultura i ma postać `[-][d':']h':'mm':'ss[.FFFFFFF]`.<br /><br /> Więcej informacji: [Specyfikator formatu ogólnego krótkiej ("g")](#GeneralShort).|`New TimeSpan(1, 3, 16, 50, 500)` -> 1:3:16:50.5 (en US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)` -> 1:3:16:50, 5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)` -> 1:3:16:50.599 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)` -> 1:3:16:50, 599 (fr-FR)|  
|„G”|Ogólny format długi|Ten specyfikator zawsze generuje dni i siedmiu cyfr dziesiętnych. Jest uwzględniana kultura i ma postać `[-]d':'hh':'mm':'ss.fffffff`.<br /><br /> Więcej informacji: [Specyfikator formatu ogólnego długiej ("G")](#GeneralLong).|`New TimeSpan(18, 30, 0)` -> 0:18:30:00.0000000 (en US)<br /><br /> `New TimeSpan(18, 30, 0)` -> 0:18:30:00, 0000000 (fr-FR)|  
  
<a name="Constant"></a>   
## <a name="the-constant-c-format-specifier"></a>Specyfikator stałej formatu ("c")  
 Specyfikator formatu "c" zwraca reprezentację ciągu <xref:System.TimeSpan> wartości w następującej postaci:  
  
 [-][*d*.]*hh*:*mm*:*ss*[.*fffffff*]  
  
 Elementy w nawiasach kwadratowych ([ i ]) są opcjonalne. Kropka (.) i dwukropek (:) to literał symbole. W poniższej tabeli opisano wszystkie pozostałe elementy.  
  
|Element|Opis|  
|-------------|-----------------|  
|*-*|Opcjonalnym znakiem minus, co oznacza ujemny przedział czasu.|  
|*d*|Opcjonalna liczba dni, bez zer wiodących.|  
|*hh*|Liczba godzin, które zakresu od "00" do "23".|  
|*mm*|Liczba minut, która zakresu od "00" do "59".|  
|*ss*|Liczba sekund, która zakresu od "0" do "59".|  
|*fffffff*|Opcjonalną część ułamkową sekund.  Wartość do zakresu od "0000001" (jeden znaczników lub co 10 milionowych części sekundy) do "9999999" (mniej cykli co drugi 9 999 999 dziesięciomilionowych części sekundy lub jeden).|  
  
 W odróżnieniu od "g" i specyfikatora formatu "G" specyfikator formatu "c" nie jest uwzględniana kultura. Generuje reprezentację ciągu <xref:System.TimeSpan> wartość jest niezmienny i które są wspólne dla wszystkich wcześniejszych wersji programu .NET Framework przed programu .NET Framework 4. "c" jest ustawieniem domyślnym <xref:System.TimeSpan> ciąg formatu; <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metoda formatuje wartość interwału czasu przy użyciu ciągu formatu "c".  
  
> [!NOTE]
>  <xref:System.TimeSpan> obsługuje również "t" i ciągi formatu standardowego "T", które są takie same jak w zachowaniu ciąg formatu standardowego "c".  
  
 Poniższy przykład tworzy dwie <xref:System.TimeSpan> obiekty, są one używane do wykonywania operacji arytmetycznych i wyświetla wynik. W obu przypadkach używa formatowania złożonego do wyświetlenia <xref:System.TimeSpan> wartości za pomocą specyfikatora formatu "c".  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  
  
 [Powrót do tabeli](#Top)  
  
<a name="GeneralShort"></a>   
## <a name="the-general-short-g-format-specifier"></a>Specyfikator formatu ogólnego krótkiej ("g")  
 "g" <xref:System.TimeSpan> specyfikator formatu zwraca reprezentację ciągu <xref:System.TimeSpan> wartości w postaci compact, umieszczając elementy, które są niezbędne. Ma następującą postać:  
  
 [-] [*d*:]*h*:*mm*:*ss*[. *FFFFFFF*]  
  
 Elementy w nawiasach kwadratowych ([ i ]) są opcjonalne. Dwukropek (:) jest symbolem literału. W poniższej tabeli opisano wszystkie pozostałe elementy.  
  
|Element|Opis|  
|-------------|-----------------|  
|*-*|Opcjonalnym znakiem minus, co oznacza ujemny przedział czasu.|  
|*d*|Opcjonalna liczba dni, bez zer wiodących.|  
|*h*|Liczba godzin, które w zakresie od "0" do "23", bez zer wiodących.|  
|*mm*|Liczba minut, która zakresu od "00" do "59"...|  
|*ss*|Liczba sekund, która zakresu od "00" do "59"...|  
|*.*|Separator ułamków sekund. Jest to równoważne do określonej kultury <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> zastępuje właściwość bez użytkowników.|  
|*FFFFFFF*|Ułamków sekund. Jak najmniejszej liczby cyfr, jak to możliwe, są wyświetlane.|  
  
 Specyfikator formatu "G", np. specyfikator formatu "g" jest zlokalizowana. Separator jego ułamków sekund jest oparty na bieżącej kultury lub określonej kultury <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> właściwości.  
  
 Poniższy przykład tworzy dwie <xref:System.TimeSpan> obiekty, są one używane do wykonywania operacji arytmetycznych i wyświetla wynik. W obu przypadkach używa formatowania złożonego do wyświetlenia <xref:System.TimeSpan> wartości za pomocą specyfikatora formatu "g". Ponadto, formatuje <xref:System.TimeSpan> wartość przy użyciu konwencji formatowania bieżącej kultury systemu (co w tym przypadku jest angielski - Stany Zjednoczone lub en US) i Francuski — Francja (fr-FR) kultury.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  
  
 [Powrót do tabeli](#Top)  
  
<a name="GeneralLong"></a>   
## <a name="the-general-long-g-format-specifier"></a>Specyfikator formatu ogólnego długiej ("G")  
 "G" <xref:System.TimeSpan> specyfikator formatu zwraca reprezentację ciągu <xref:System.TimeSpan> wartości w długich fragmentów, który zawsze zawiera dni i ułamków sekund. Ciąg, który jest wynikiem specyfikator formatu standardowego "G" ma następującą postać:  
  
 [-] *d*:*hh*:*mm*:*ss*. *fffffff*  
  
 Elementy w nawiasach kwadratowych ([ i ]) są opcjonalne. Dwukropek (:) jest symbolem literału. W poniższej tabeli opisano wszystkie pozostałe elementy.  
  
|Element|Opis|  
|-------------|-----------------|  
|*-*|Opcjonalnym znakiem minus, co oznacza ujemny przedział czasu.|  
|*d*|Liczba dni, bez zer wiodących.|  
|*hh*|Liczba godzin, które zakresu od "00" do "23".|  
|*mm*|Liczba minut, która zakresu od "00" do "59".|  
|*ss*|Liczba sekund, która zakresu od "00" do "59".|  
|*.*|Separator ułamków sekund. Jest to równoważne do określonej kultury <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> zastępuje właściwość bez użytkowników.|  
|*fffffff*|Ułamków sekund.|  
  
 Specyfikator formatu "G", np. specyfikator formatu "g" jest zlokalizowana. Separator jego ułamków sekund jest oparty na bieżącej kultury lub określonej kultury <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> właściwości.  
  
 Poniższy przykład tworzy dwie <xref:System.TimeSpan> obiekty, są one używane do wykonywania operacji arytmetycznych i wyświetla wynik. W obu przypadkach używa formatowania złożonego do wyświetlenia <xref:System.TimeSpan> wartości za pomocą specyfikatora formatu "G". Ponadto, formatuje <xref:System.TimeSpan> wartość przy użyciu konwencji formatowania bieżącej kultury systemu (co w tym przypadku jest angielski - Stany Zjednoczone lub en US) i Francuski — Francja (fr-FR) kultury.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]  
  
 [Powrót do tabeli](#Top)  
  
## <a name="see-also"></a>Zobacz także

- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
- [Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)
