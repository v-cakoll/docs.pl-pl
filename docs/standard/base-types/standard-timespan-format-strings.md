---
title: Standardowe ciągi formatujące TimeSpan
description: Przejrzyj Standardowe ciągi formatujące TimeSpan, które używają pojedynczego specyfikatora formatu do definiowania tekstowej reprezentacji wartości TimeSpan w programie .NET.
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
ms.openlocfilehash: 31e4158d42d794e830d9acfe666729846c43a1ee
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768121"
---
# <a name="standard-timespan-format-strings"></a>Standardowe ciągi formatujące TimeSpan

<xref:System.TimeSpan>Ciąg formatu standardowego używa pojedynczego specyfikatora formatu do definiowania tekstowej reprezentacji <xref:System.TimeSpan> wartości będącej wynikiem operacji formatowania. Dowolny ciąg formatu, który zawiera więcej niż jeden znak, w tym znak odstępu, jest interpretowany jako <xref:System.TimeSpan> ciąg formatu niestandardowego. Aby uzyskać więcej informacji, zobacz [Niestandardowe ciągi formatujące TimeSpan](custom-timespan-format-strings.md) .  
  
 Ciąg reprezentujący <xref:System.TimeSpan> wartości są tworzone przez wywołania przeciążeń <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> metody, a także metody obsługujące formatowanie złożone, takie jak <xref:System.String.Format%2A?displayProperty=nameWithType> . Aby uzyskać więcej informacji, zobacz [Typy formatowania](formatting-types.md) i [formatowanie złożone](composite-formatting.md). Poniższy przykład ilustruje użycie standardowych ciągów formatu w operacjach formatowania.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 <xref:System.TimeSpan>Ciągi formatu standardowego są również używane przez <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> metody i <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> do definiowania wymaganego formatu ciągów wejściowych na potrzeby analizowania operacji. (Analizowanie konwertuje ciąg reprezentujący wartość na tę wartość). Poniższy przykład ilustruje użycie standardowych ciągów formatu podczas analizowania operacji.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
Poniższa tabela zawiera listę specyfikatorów formatu standardowego interwału czasu.  
  
|Specyfikator formatu|Nazwa|Opis|Przykłady|  
|----------------------|----------|-----------------|--------------|  
|s|Stały format (niezmienny)|Ten specyfikator nie jest uwzględniany w kulturze. Formularz `[-][d'.']hh':'mm':'ss['.'fffffff]` .<br /><br /> (Ciągi formatu "t" i "T" dają te same wyniki).<br /><br /> Więcej informacji: [specyfikator formatu stałej ("c")](#the-constant-c-format-specifier).|`TimeSpan.Zero`-> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)`-> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)`-> 3.17:25:30.5000000|  
|„g”|Ogólny krótki format|Ten specyfikator wyprowadza tylko to, co jest potrzebne. Jest ona zależna od kultury i ma postać `[-][d':']h':'mm':'ss[.FFFFFFF]` .<br /><br /> Więcej informacji: [specyfikator formatu ogólnego ("g")](#the-general-short-g-format-specifier).|`New TimeSpan(1, 3, 16, 50, 500)`-> 1:3: 50.5 (pl-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)`-> 1:3: 16:50, 5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3: 50.599 (pl-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3: 16:50599 (fr-FR)|  
|„G”|Format ogólnie długi|Ten specyfikator zawsze Wyprowadza dni i siedem cyfr. Jest ona zależna od kultury i ma postać `[-]d':'hh':'mm':'ss.fffffff` .<br /><br /> Więcej informacji: [specyfikator formatu ogólnego ("G")](#the-general-long-g-format-specifier).|`New TimeSpan(18, 30, 0)`-> 0:18:30:00.0000000 (EN-US)<br /><br /> `New TimeSpan(18, 30, 0)`-> 0:18:30:00, 0000000 (fr-FR)|  

## <a name="the-constant-c-format-specifier"></a>Specyfikator formatu stałej ("c")  
 Specyfikator formatu "c" zwraca reprezentację ciągu <xref:System.TimeSpan> wartości w następującej postaci:  
  
 [-] [*d*.] *hh*:*mm*:*SS*[.* fffffff*]  
  
 Elementy w nawiasach kwadratowych ([ i ]) są opcjonalne. Kropka (.) i dwukropek (:) są symbolami literału. W poniższej tabeli opisano pozostałe elementy.  
  
|Element|Opis|  
|-------------|-----------------|  
|*-*|Opcjonalny znak ujemny, który wskazuje ujemny przedział czasu.|  
|*Wykres*|Opcjonalna liczba dni bez zer wiodących.|  
|*formacie*|Liczba godzin z zakresu od "00" do "23".|  
|*–*|Liczba minut obejmująca wartość "00" do "59".|  
|*RR*|Liczba sekund określająca zakres od "0" do "59".|  
|*fffffff*|Opcjonalna część ułamkowa sekundy.  Jego wartość może być z zakresu od "0000001" (jeden takt lub 1 10-milionowego sekundy) do "9999999" (9 999 999 10-dziesięciomilionowych sekundy lub jeden drugi z więcej niż jeden takt).|  
  
 W przeciwieństwie do specyfikatorów formatu "g" i "G", specyfikator formatu "c" nie jest uwzględniany w kulturze. Generuje ciąg reprezentujący <xref:System.TimeSpan> wartość, która jest niezmienna i która jest wspólna dla wszystkich poprzednich wersji .NET Framework przed .NET Framework 4. "c" jest domyślnym <xref:System.TimeSpan> ciągiem formatu; <xref:System.TimeSpan.ToString?displayProperty=nameWithType> Metoda formatuje wartość przedziału czasu przy użyciu ciągu formatu "c".  
  
> [!NOTE]
> <xref:System.TimeSpan>obsługuje również ciągi formatu standardowego "t" i "T", które są takie same jak w przypadku standardowego ciągu formatu "c".  
  
 Poniższy przykład tworzy wystąpienie dwóch <xref:System.TimeSpan> obiektów, używa ich do wykonywania operacji arytmetycznych i wyświetla wynik. W każdym przypadku używa formatowania złożonego do wyświetlania wartości przy <xref:System.TimeSpan> użyciu specyfikatora formatu "c".  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  

## <a name="the-general-short-g-format-specifier"></a>Specyfikator formatu ogólnego ("g")  
 Specyfikator formatu "g" <xref:System.TimeSpan> zwraca reprezentację ciągu <xref:System.TimeSpan> wartości w postaci kompaktowej przez uwzględnienie tylko tych elementów, które są niezbędne. Ma następującą postać:  
  
 [-] [*d*:] *h*:*mm*:*SS*[.* FFFFFFF*]  
  
 Elementy w nawiasach kwadratowych ([ i ]) są opcjonalne. Dwukropek (:) jest symbolem literału. W poniższej tabeli opisano pozostałe elementy.  
  
|Element|Opis|  
|-------------|-----------------|  
|*-*|Opcjonalny znak ujemny, który wskazuje ujemny przedział czasu.|  
|*Wykres*|Opcjonalna liczba dni bez zer wiodących.|  
|*c*|Liczba godzin z zakresu od "0" do "23" bez zer wiodących.|  
|*–*|Liczba minut obejmująca wartość "00" do "59".|  
|*RR*|Liczba sekund określająca zakres od "00" do "59"..|  
|*.*|Separator sekund ułamkowych. Jest ona równoważna z określoną <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> właściwością kultury bez zastąpień użytkownika.|  
|*FFFFFFF*|Ułamki sekund. Zostanie wyświetlona najmniejsza liczba cyfr.|  
  
 Podobnie jak specyfikator formatu "G", specyfikator formatu "g" jest lokalizowany. Separator ułamków sekund jest oparty na bieżącej kulturze lub właściwości określonej kultury <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> .  
  
 Poniższy przykład tworzy wystąpienie dwóch <xref:System.TimeSpan> obiektów, używa ich do wykonywania operacji arytmetycznych i wyświetla wynik. W każdym przypadku używa formatowania złożonego do wyświetlania wartości przy <xref:System.TimeSpan> użyciu specyfikatora formatu "g". Ponadto formatuje <xref:System.TimeSpan> wartość przy użyciu Konwencji formatowania bieżącej kultury systemu (w tym przypadku jest to angielski-Stany Zjednoczone lub EN-US) oraz kulturę Francuska-Francja (fr-fr).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  

## <a name="the-general-long-g-format-specifier"></a>Specyfikator formatu ogólnego ("G")  
 Specyfikator formatu "G" <xref:System.TimeSpan> zwraca reprezentację ciągu <xref:System.TimeSpan> wartości w postaci długiej, która zawsze zawiera dni i ułamki sekund. Ciąg, który jest wynikiem specyfikatora formatu standardowego "G", ma następującą postać:  
  
 [-] *d*:*hh*:*mm*:*SS*. *fffffff*  
  
 Elementy w nawiasach kwadratowych ([ i ]) są opcjonalne. Dwukropek (:) jest symbolem literału. W poniższej tabeli opisano pozostałe elementy.  
  
|Element|Opis|  
|-------------|-----------------|  
|*-*|Opcjonalny znak ujemny, który wskazuje ujemny przedział czasu.|  
|*Wykres*|Liczba dni bez zer wiodących.|  
|*formacie*|Liczba godzin z zakresu od "00" do "23".|  
|*–*|Liczba minut obejmująca wartość "00" do "59".|  
|*RR*|Liczba sekund określająca zakres od "00" do "59".|  
|*.*|Separator sekund ułamkowych. Jest ona równoważna z określoną <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> właściwością kultury bez zastąpień użytkownika.|  
|*fffffff*|Ułamki sekund.|  
  
 Podobnie jak specyfikator formatu "G", specyfikator formatu "g" jest lokalizowany. Separator ułamków sekund jest oparty na bieżącej kulturze lub właściwości określonej kultury <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> .  
  
 Poniższy przykład tworzy wystąpienie dwóch <xref:System.TimeSpan> obiektów, używa ich do wykonywania operacji arytmetycznych i wyświetla wynik. W każdym przypadku używa formatowania złożonego do wyświetlania wartości przy <xref:System.TimeSpan> użyciu specyfikatora formatu "G". Ponadto formatuje <xref:System.TimeSpan> wartość przy użyciu Konwencji formatowania bieżącej kultury systemu (w tym przypadku jest to angielski-Stany Zjednoczone lub EN-US) oraz kulturę Francuska-Francja (fr-fr).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]
  
## <a name="see-also"></a>Zobacz też

- [Formatowanie typów](formatting-types.md)
- [Niestandardowe ciągi formatujące TimeSpan](custom-timespan-format-strings.md)
- [Analiza składniowa ciągów](parsing-strings.md)
