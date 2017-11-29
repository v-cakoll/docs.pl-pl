---
title: "Porady: uzupełnianie liczby zerami prowadzącymi"
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
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6266807a01e8119ae1410a1ba09cab55c788b4d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Porady: uzupełnianie liczby zerami prowadzącymi
Można dodać zera wiodące na liczbę całkowitą za pomocą "D" [ciągu standardowego formatu liczbowego](../../../docs/standard/base-types/standard-numeric-format-strings.md) z Specyfikator dokładności. Można dodać zera wiodące do liczby całkowitej i liczby zmiennoprzecinkowe przy użyciu [ciąg niestandardowego formatu liczbowego](../../../docs/standard/base-types/custom-numeric-format-strings.md). W tym temacie pokazano, jak uzupełnianie liczby zerami prowadzącymi przy użyciu obu metod.  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Liczba całkowita z zerami określoną długość służących do  
  
1.  Określ minimalną liczbę cyfr ma wartość całkowita do wyświetlenia. Dołącz wszystkie wiodące cyfry ten numer.  
  
2.  Określ, czy mają być wyświetlane liczb całkowitych jako wartość dziesiętną lub szesnastkową wartość.  
  
    -   Aby wyświetlić liczb całkowitych jako wartości dziesiętnej, należy wywołać jej `ToString(String)` — metoda i przekazać ciąg "D*n*" jako wartości `format` parametru, gdzie  *n*  reprezentuje minimalna długość ciągu.  
  
    -   Aby wyświetlić liczb całkowitych jako wartości szesnastkowej, należy wywołać jej `ToString(String)` — metoda i przekazać ciąg "X*n*" jako wartości `format` parametru, gdzie  *n*  reprezentuje minimalna długość ciągu.  
  
     Umożliwia także ciąg formatu w metodzie, takie jak <xref:System.String.Format%2A> lub <xref:System.Console.WriteLine%2A>, która używa [złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md).  
  
 Poniższy przykład formatuje kilka wartości całkowitych z zerami, dzięki czemu sformatowana liczba całkowita długość co najmniej osiem znaków.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Aby uzupełnić liczbą całkowitą o określonej liczby zer  
  
1.  Określ, ile zera wiodące całkowitą do wyświetlenia.  
  
2.  Określ, czy mają być wyświetlane liczb całkowitych jako wartość dziesiętną lub szesnastkową wartość. Formatowanie jej jako wartości dziesiętnej wymaga użycia specyfikator formatu standardowych "D"; Formatowanie go jako wartość szesnastkowa wymaga użycia specyfikator formatu standardowych "X".  
  
3.  Ustalić długość ciągu numerycznego unpadded wywołując wartość całkowita `ToString("D").Length` lub `ToString("X").Length` metody.  
  
4.  Dodanie liczby zer, które chcesz uwzględnić w ciągu sformatowany, długość unpadded ciągu numerycznego. Definiuje całkowita długość ciągu wypełniony.  
  
5.  Wywołaj wartość całkowita `ToString(String)` — metoda i przekazać ciąg "D*n*" decimal ciągów i "X*n*" dla ciągów szesnastkowych, gdzie  *n*  reprezentuje całkowita długość ciągu wypełniony. Można również użyć "D*n*" lub "X*n*" ciąg w metodzie, która obsługuje złożone formatowanie formatu.  
  
 Poniższy przykład dopełnia całkowitą pięć zera wiodące.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Aby uzupełnić wartość liczbową z zerami określoną długość  
  
1.  Określ liczbę miejsc po przecinku numer ma reprezentację ciągu. Obejmują wszystkie zera wiodące w tym łączna liczba cyfr.  
  
2.  Zdefiniuj ciąg niestandardowego formatu liczbowego, który używa zero symbolu zastępczego ("0") do reprezentowania minimalnej liczby zer.  
  
3.  Liczba wywołań `ToString(String)` — metoda i przekaż go niestandardowy ciąg formatu. Umożliwia także niestandardowy ciąg formatu za pomocą metody, która obsługuje złożone formatowanie.  
  
 Poniższy przykład formatuje kilka wartości liczbowych zerami prowadzącymi tak, aby sformatowana liczba całkowita długość co najmniej osiem miejsc po przecinku.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Aby uzupełnić wartość liczbową z określonej liczby zer  
  
1.  Określ, ile zera wiodące ma wartość liczbowa.  
  
2.  Określić liczbę miejsc po przecinku w unpadded ciągów liczbowych. W tym celu:  
  
    1.  Ustal, czy reprezentacja ciągu z liczbą zawiera symbol punktu dziesiętnego.  
  
    2.  Jeśli posiada symbol punktu dziesiętnego, określ liczbę znaków z lewej strony punktu dziesiętnego.  
  
         —lub—  
  
         Jeśli nie ma symbolu dziesiętnym, określ długość ciągu.  
  
3.  Utwórz niestandardowy ciąg formatu używającą zero symbolu zastępczego ("0") dla każdego zera wiodące pojawią się w ciągu i używającą do reprezentowania każdej cyfry w domyślny ciąg zastępczy zero lub symbol zastępczy cyfry ("#").  
  
4.  Dostarcza niestandardowy ciąg formatu jako parametr do liczby `ToString(String)` metodę lub metody, która obsługuje złożone formatowanie.  
  
 Poniższy przykład dopełnia dwa <xref:System.Double> wartości z pięciu zera wiodące.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)
