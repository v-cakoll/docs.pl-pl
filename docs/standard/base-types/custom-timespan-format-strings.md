---
title: Niestandardowe ciągi formatujące TimeSpan
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format spexifiers, custom time interval
- format strings
- formatting [.NET Framework], time interval
- custom time interval format strings
- formatting [.NET Framework], time
- custom TimeSpan format strings
ms.assetid: a63ebf55-7269-416b-b4f5-286f6c03bf0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f65e8bb1a61bad458cb33a3bf9d2553479c750e
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208518"
---
# <a name="custom-timespan-format-strings"></a>Niestandardowe ciągi formatujące TimeSpan
A <xref:System.TimeSpan> ciąg formatu definiuje reprezentację ciągu <xref:System.TimeSpan> wartość będącą wynikiem operacji formatowania. Niestandardowy ciąg formatu, który składa się z co najmniej jeden niestandardowy <xref:System.TimeSpan> sformatować specyfikatory wraz z dowolnej liczby znaków literału. Dowolny ciąg, który nie jest [standardowy ciąg formatu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md) jest interpretowana jako niestandardowego <xref:System.TimeSpan> ciąg formatu.  
  
> [!IMPORTANT]
>  Niestandardowa <xref:System.TimeSpan> specyfikatory formatu nie ma separatora symbole zastępcze, takie jak symbole, oddzielające dni od godziny, godziny od minut i sekund z ułamkowych części sekundy. Zamiast tego tych symboli muszą być uwzględnione w ciągu formatu niestandardowego jako literały. Na przykład `"dd\.hh\:mm"` definiuje kropki (.) jako separatora między dni i godziny i dwukropka (:) jako separator godziny i minuty.  
>   
>  Niestandardowe <xref:System.TimeSpan> specyfikatory formatu nie obejmować symbol znaku, który umożliwia rozróżnianie między przedziały czasu ujemnych i dodatnich. Aby uwzględnić znak symbolu, należy utworzyć ciągu formatu za pomocą reguł warunkowych. [Inne znaki](#Other) sekcja zawiera przykład.  
  
 Reprezentacji ciągu <xref:System.TimeSpan> wartości są produkowane przez wywołania przeciążenia metody <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> metody oraz metody, które obsługuje złożone, takich jak <xref:System.String.Format%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [typy formatowania](../../../docs/standard/base-types/formatting-types.md) i [złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md). Poniższy przykład przedstawia użycie niestandardowych ciągów formatu w operacji formatowania.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customformatexample1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customformatexample1.vb#1)]  
  
 Niestandardowe <xref:System.TimeSpan> ciągi formatujące są również używane przez <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> i <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody, aby zdefiniować wymagany format wejściowy ciągi do analizowania operacji. (Podczas analizowania konwertuje reprezentacja ciągu wartości do tej wartości.) Poniższy przykład przedstawia użycie standardowe ciągi formatujące podczas analizowania operacji.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customparseexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customparseexample1.vb#2)]  
  
<a name="table"></a> W poniższej tabeli opisano niestandardowa data i godzina specyfikatory formatu.  
  
|Specyfikator formatu|Opis|Przykład|  
|----------------------|-----------------|-------------|  
|"d", "%d"|Liczba dni w interwale czasu.<br /><br /> Więcej informacji: ["D" specyfikatora formatu niestandardowego](#dSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%d` --> "6"<br /><br /> `d\.hh\:mm` --> "6.14:32"|  
|"dd"-"dddddddd"|Liczba dni w interwale czasu wypełniane zerami, zgodnie z potrzebami.<br /><br /> Więcej informacji: ["dd"-"dddddddd" specyfikatory formatu niestandardowego](#ddSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `ddd` --> "006"<br /><br /> `dd\.hh\:mm` --> "06.14:32"|  
|"h", "%h"|Liczba godzin całego w interwale czasu, które nie są liczone jako część dni. Godziny jednocyfrowe nie mają zerem.<br /><br /> Więcej informacji: ["H" specyfikatora formatu niestandardowego](#hSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%h` --> "14"<br /><br /> `hh\:mm` --> "14:32"|  
|„hh”|Liczba godzin całego w interwale czasu, które nie są liczone jako część dni. Godziny jednocyfrowe ma zerem.<br /><br /> Więcej informacji: ["Hh" specyfikatora formatu niestandardowego](#hhSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `hh` --> "14"<br /><br /> `new TimeSpan(6, 8, 32, 17, 685):`<br /><br /> `hh` --> 08|  
|"m", "%m"|Liczba minut całego w przedziale czasu, które nie są dołączane jako część godzin lub dni. Minut jednocyfrowej nie mają zerem.<br /><br /> Więcej informacji: ["M" specyfikatora formatu niestandardowego](#mSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `%m` --> "8"<br /><br /> `h\:m` --> "14:8"|  
|„mm”|Liczba minut całego w przedziale czasu, które nie są dołączane jako część godzin lub dni. Minut jednocyfrowej ma zerem.<br /><br /> Więcej informacji: ["Mm" specyfikatora formatu niestandardowego](#mmSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `mm` --> "08"<br /><br /> `new TimeSpan(6, 8, 5, 17, 685):`<br /><br /> `d\.hh\:mm\:ss` --> 6.08:05:17|  
|"s", "%s"|Liczba sekund całego w przedziale czasu, które nie są dołączane jako część godziny, dni lub minut. Sekund jednocyfrowej nie mają zerem.<br /><br /> Więcej informacji: ["S" specyfikator formatu niestandardowego](#sSpecifier).|`TimeSpan.FromSeconds(12.965)`:<br /><br /> `%s` --> 12<br /><br /> `s\.fff` --> 12.965|  
|„ss”|Liczba sekund całego w przedziale czasu, które nie są dołączane jako część godziny, dni lub minut.  Sekund jednocyfrowej ma zerem.<br /><br /> Więcej informacji: ["Ss" specyfikatora formatu niestandardowego](#ssSpecifier).|`TimeSpan.FromSeconds(6.965)`:<br /><br /> `ss` --> 06<br /><br /> `ss\.fff` --> 06.965|  
|"f", "%f"|Dziesiąte części sekundy w przedziale czasu.<br /><br /> Więcej informacji: ["F" specyfikatora formatu niestandardowego](#fSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `f` --> 8<br /><br /> `ss\.f` --> 06.8|  
|„ff”|Setnych sekundy w przedziale czasu.<br /><br /> Więcej informacji:["Ff" specyfikatora formatu niestandardowego](#ffSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `ff` --> 89<br /><br /> `ss\.ff` --> 06.89|  
|„fff”|Milisekund w przedziale czasu.<br /><br /> Więcej informacji: ["Fff" specyfikatora formatu niestandardowego](#f3Specifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `fff` --> 895<br /><br /> `ss\.fff` --> 06.895|  
|„ffff”|10-000 sekund w przedziale czasu.<br /><br /> Więcej informacji: ["Ffff" specyfikatora formatu niestandardowego](#f4Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffff` --> 8954<br /><br /> `ss\.ffff` --> 06.8954|  
|„fffff”|Sto tysięczne sekundy w przedziale czasu.<br /><br /> Więcej informacji: ["Fffff" specyfikatora formatu niestandardowego](#f5Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffff` --> 89543<br /><br /> `ss\.fffff` --> 06.89543|  
|„ffffff”|Milionowych drugiej w przedziale czasu.<br /><br /> Więcej informacji: ["Ffffff" specyfikatora formatu niestandardowego](#f6Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffffff` --> 895432<br /><br /> `ss\.ffffff` --> 06.895432|  
|„fffffff”|10-milionowych drugi (lub ułamkową Takty) w przedziale czasu.<br /><br /> Więcej informacji: ["Fffffff" specyfikatora formatu niestandardowego](#f7Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffffff` --> 8954321<br /><br /> `ss\.fffffff` --> 06.8954321|  
|"F", "%F"|Dziesiąte części sekundy w przedziale czasu. Nic nie jest wyświetlane, jeśli cyfra jest równa zero.<br /><br /> Więcej informacji: [specyfikator formatu "F" Custom](#F_Specifier).|`TimeSpan.Parse("00:00:06.32")`:<br /><br /> `%F`: 3<br /><br /> `TimeSpan.Parse("0:0:3.091")`:<br /><br /> `ss\.F`: 03.|  
|„FF”|Setnych sekundy w przedziale czasu. Wszystkie ułamkowych końcowe zero lub dwa zero cyfr nie są uwzględniane.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FF"](#FF_Specifier).|`TimeSpan.Parse("00:00:06.329")`:<br /><br /> `FF`: 32<br /><br /> `TimeSpan.Parse("0:0:3.101")`:<br /><br /> `ss\.FF`: 03.1|  
|„FFF”|Milisekund w przedziale czasu. Końcowe zera ułamkowych nie są uwzględniane.<br /><br /> Więcej informacji:|`TimeSpan.Parse("00:00:06.3291")`:<br /><br /> `FFF`: 329<br /><br /> `TimeSpan.Parse("0:0:3.1009")`:<br /><br /> `ss\.FFF`: 03.1|  
|„FFFF”|10-000 sekund w przedziale czasu. Końcowe zera ułamkowych nie są uwzględniane.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFF"](#F4_Specifier).|`TimeSpan.Parse("00:00:06.32917")`:<br /><br /> `FFFFF`: 3291<br /><br /> `TimeSpan.Parse("0:0:3.10009")`:<br /><br /> `ss\.FFFF`: 03.1|  
|„FFFFF”|Sto tysięczne sekundy w przedziale czasu. Końcowe zera ułamkowych nie są uwzględniane.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFF"](#F5_Specifier).|`TimeSpan.Parse("00:00:06.329179")`:<br /><br /> `FFFFF`: 32917<br /><br /> `TimeSpan.Parse("0:0:3.100009")`:<br /><br /> `ss\.FFFFF`: 03.1|  
|„FFFFFF”|Milionowych drugiej w przedziale czasu. Końcowe zera ułamkowych nie są wyświetlane.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFFF"](#F6_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 329179<br /><br /> `TimeSpan.Parse("0:0:3.1000009")`:<br /><br /> `ss\.FFFFFF`: 03.1|  
|„FFFFFFF”|10 milionów sekundy w przedziale czasu. Nie są wyświetlane ułamkowych końcowe zera lub siedem zer.<br /><br /> Więcej informacji: [specyfikator formatu niestandardowego "FFFFFFF"](#F7_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 3291791<br /><br /> `TimeSpan.Parse("0:0:3.1900000")`:<br /><br /> `ss\.FFFFFF`: 03.19|  
|*"ciągu*"|Ogranicznik ciągu literału.<br /><br /> Więcej informacji: [inne znaki](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh':'mm':'ss` --> "14:32:17"|  
|\\| Znak ucieczki.<br /><br /> Więcej informacji:[inne znaki](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|  
|Jakikolwiek inny znak|Dowolny znak niezmienionym znaczeniu jest interpretowany jako specyfikator formatu niestandardowego.<br /><br /> Więcej informacji: [innych znaków](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|  
  
<a name="dSpecifier"></a>   
## <a name="the-d-custom-format-specifier"></a>Specyfikator formatu niestandardowego „d”  
 Specyfikator formatu niestandardowego "d" Wyświetla wartość <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę dni w interwale czasu. Generuje on pełną liczbę dni w <xref:System.TimeSpan> wartości, nawet jeśli wartość ma więcej niż jedna cyfra. Jeśli wartość <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> właściwości jest równa zero, specyfikatora danych wyjściowych "0".  
  
 Jeśli specyfikator formatu niestandardowego "d" jest używana samodzielnie, określ "%d", aby jest nieprawidłowo interpretowane jako ciąg w formacie. Poniższy przykład stanowi ilustrację.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#3)]  
  
 Poniższy przykład przedstawia użycie specyfikatora formatu niestandardowego "d".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#4)]  
  
 [Powrót do tabeli](#table)  
  
<a name="ddSpecifier"></a>   
## <a name="the-dd-dddddddd-custom-format-specifiers"></a>"dd"-"dddddddd" niestandardowe specyfikatory formatu  
 "Dd", "ddd", "dddd", "ddddd", "dddddd", "ddddddd" i "dddddddd" specyfikatorów formatu niestandardowego output wartość <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę dni w interwale czasu.  
  
 Ciąg danych wyjściowych zawiera minimalną liczbę cyfr określony przez liczbę znaków "d" w specyfikatorze formatu i jest uzupełniana zerami prowadzącymi zgodnie z potrzebami. Jeśli cyfr w liczbie dni przekracza liczbę znaków "d" w specyfikatorze formatu, pełną liczbę dni, jest dane wyjściowe w ciągu wynik.  
  
 W poniższym przykładzie użyto tych specyfikatory formatu, aby wyświetlić reprezentację dwa <xref:System.TimeSpan> wartości. Wartość składnik dni z pierwszym interwale wynosi zero; wartość dni składnika drugiej danej wejściowej jest 365.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#5)]  
  
 [Powrót do tabeli](#table)  
  
<a name="hSpecifier"></a>   
## <a name="the-h-custom-format-specifier"></a>Specyfikator formatu niestandardowego „h”  
 Specyfikator formatu niestandardowego "h" Wyświetla wartość <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę godzin całego przedział czasu, który nie jest traktowane jako część jej składnik dni. Zwraca wartość ciągu jedną cyfrę, jeśli wartość <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> właściwości jest równa 0 do 9 i zwraca wartość typu ciąg dwucyfrowe, jeśli wartość <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> właściwości może się wahać od 10 do 23.  
  
 Jeśli specyfikator formatu niestandardowego "h" jest używana samodzielnie, należy określić "%h", tak aby jest nieprawidłowo interpretowane jako ciąg w formacie. Poniższy przykład stanowi ilustrację.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
 [!code-vb[Conceptual.TimeSpan.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]  
  
 Zwykle w operacji analizy wejściowy ciąg, który zawiera tylko jeden numer jest interpretowany jako liczbę dni. Specyfikator formatu niestandardowego "%h" można użyć aby zinterpretować ciąg numeryczny jako liczbę godzin. Poniższy przykład stanowi ilustrację.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#8)]
 [!code-vb[Conceptual.TimeSpan.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#8)]  
  
 Poniższy przykład przedstawia użycie specyfikatora formatu niestandardowego "h".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#7)]
 [!code-vb[Conceptual.TimeSpan.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#7)]  
  
 [Powrót do tabeli](#table)  
  
<a name="hhSpecifier"></a>   
## <a name="the-hh-custom-format-specifier"></a>Specyfikator formatu niestandardowego „hh”  
 Specyfikator formatu niestandardowego "hh" Wyświetla wartość <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę godzin całego przedział czasu, który nie jest traktowane jako część jej składnik dni. W przypadku wartości z zakresu od 0 do 9 ciągu wyjściowego obejmuje zerem.  
  
 Zwykle w operacji analizy wejściowy ciąg, który zawiera tylko jeden numer jest interpretowany jako liczbę dni. Specyfikator formatu niestandardowego "hh" można użyć aby zinterpretować ciąg numeryczny jako liczbę godzin. Poniższy przykład stanowi ilustrację.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#9)]
 [!code-vb[Conceptual.TimeSpan.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#9)]  
  
 Poniższy przykład przedstawia użycie specyfikatora formatu niestandardowego "hh".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#10)]
 [!code-vb[Conceptual.TimeSpan.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#10)]  
  
 [Powrót do tabeli](#table)  
  
<a name="mSpecifier"></a>   
## <a name="the-m-custom-format-specifier"></a>Specyfikator formatu niestandardowego „m”  
 Specyfikator formatu niestandardowego "m" Wyświetla wartość <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę pełnych minutach czas, który nie jest traktowane jako część jej składnik dni. Zwraca wartość ciągu jedną cyfrę, jeśli wartość <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> właściwości jest równa 0 do 9 i zwraca wartość typu ciąg dwucyfrowe, jeśli wartość <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> właściwości może się wahać od 10 do 59.  
  
 Jeśli specyfikator formatu niestandardowego "m" jest używana samodzielnie, należy określić "%m", tak aby jest nieprawidłowo interpretowane jako ciąg w formacie. Poniższy przykład stanowi ilustrację.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
 [!code-vb[Conceptual.TimeSpan.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]  
  
 Zwykle w operacji analizy wejściowy ciąg, który zawiera tylko jeden numer jest interpretowany jako liczbę dni. Specyfikator formatu niestandardowego "%m" można użyć aby zinterpretować ciąg numeryczny jako liczbę minut. Poniższy przykład stanowi ilustrację.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#11)]
 [!code-vb[Conceptual.TimeSpan.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#11)]  
  
 Poniższy przykład przedstawia użycie specyfikatora formatu niestandardowego "m".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#12)]
 [!code-vb[Conceptual.TimeSpan.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#12)]  
  
 [Powrót do tabeli](#table)  
  
<a name="mmSpecifier"></a>   
## <a name="the-mm-custom-format-specifier"></a>Specyfikator formatu niestandardowego „mm”  
 Specyfikator formatu niestandardowego "mm" Wyświetla wartość <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę pełnych minutach czas, który nie jest zawarte w ramach składnika godzin lub dni. W przypadku wartości z zakresu od 0 do 9 ciągu wyjściowego obejmuje zerem.  
  
 Zwykle w operacji analizy wejściowy ciąg, który zawiera tylko jeden numer jest interpretowany jako liczbę dni. Specyfikator formatu niestandardowego "mm" można użyć aby zinterpretować ciąg numeryczny jako liczbę minut. Poniższy przykład stanowi ilustrację.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#13)]
 [!code-vb[Conceptual.TimeSpan.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#13)]  
  
 Poniższy przykład przedstawia użycie specyfikatora formatu niestandardowego "mm".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#14)]
 [!code-vb[Conceptual.TimeSpan.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#14)]  
  
 [Powrót do tabeli](#table)  
  
<a name="sSpecifier"></a>   
## <a name="the-s-custom-format-specifier"></a>Specyfikator formatu niestandardowego „s”  
 "S" specyfikator formatu niestandardowego Wyświetla wartość <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę sekund całego w przedziale czasu, który nie jest częścią jego godziny, dni lub składnik minut. Zwraca wartość ciągu jedną cyfrę, jeśli wartość <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> właściwości jest równa 0 do 9 i zwraca wartość typu ciąg dwucyfrowe, jeśli wartość <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> właściwości może się wahać od 10 do 59.  
  
 Jeśli specyfikator formatu niestandardowego "s" jest używana samodzielnie, określ "%s", aby jest nieprawidłowo interpretowane jako ciąg w formacie. Poniższy przykład stanowi ilustrację.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#15)]
 [!code-vb[Conceptual.TimeSpan.Custom#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#15)]  
  
 Zwykle w operacji analizy wejściowy ciąg, który zawiera tylko jeden numer jest interpretowany jako liczbę dni. Specyfikator formatu niestandardowego "%s" można użyć aby zinterpretować ciąg numeryczny jako liczbę sekund. Poniższy przykład stanowi ilustrację.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#17)]
 [!code-vb[Conceptual.TimeSpan.Custom#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#17)]  
  
 Poniższy przykład przedstawia użycie specyfikatora formatu niestandardowego "s".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#16)]
 [!code-vb[Conceptual.TimeSpan.Custom#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#16)]  
  
 [Powrót do tabeli](#table)  
  
<a name="ssSpecifier"></a>   
## <a name="the-ss-custom-format-specifier"></a>Specyfikator formatu niestandardowego „ss”  
 Specyfikator formatu niestandardowego "ss" Wyświetla wartość <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> właściwość, która reprezentuje liczbę sekund całego w przedziale czasu, który nie jest częścią jego godziny, dni lub składnik minut. W przypadku wartości z zakresu od 0 do 9 ciągu wyjściowego obejmuje zerem.  
  
 Zwykle w operacji analizy wejściowy ciąg, który zawiera tylko jeden numer jest interpretowany jako liczbę dni. Specyfikator formatu niestandardowego "ss" można użyć aby zinterpretować ciąg numeryczny jako liczbę sekund. Poniższy przykład stanowi ilustrację.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#18)]
 [!code-vb[Conceptual.TimeSpan.Custom#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#18)]  
  
 Poniższy przykład przedstawia użycie specyfikatora formatu niestandardowego "ss".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#19)]
 [!code-vb[Conceptual.TimeSpan.Custom#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#19)]  
  
 [Powrót do tabeli](#table)  
  
<a name="fSpecifier"></a>   
## <a name="thef-custom-format-specifier"></a>Specyfikator formatu niestandardowego "f"  
 Specyfikator formatu niestandardowego "f" generuje dziesiąte części sekundy w przedziale czasu. W ramach operacji formatowania wszystkie pozostałe cyfr ułamkowych są obcinane. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie jeden cyfr ułamkowych.  
  
 Jeśli używana jest jedynym specyfikator formatu niestandardowego "f", należy określić "%f", tak aby jest nieprawidłowo interpretowane jako ciąg w formacie.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "f", aby wyświetlić dziesiąte części sekundy w <xref:System.TimeSpan> wartość. "f" jest używana w pierwszej kolejności, jak tylko specyfikator formatu, a następnie łączyć się ze specyfikatorem "s" w ciągu formatu niestandardowego.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Powrót do tabeli](#table)  
  
<a name="ffSpecifier"></a>   
## <a name="the-ff-custom-format-specifier"></a>Specyfikator formatu niestandardowego „ff”  
 Specyfikator formatu niestandardowego "ff" generuje setnych sekundy w przedziale czasu. W ramach operacji formatowania wszystkie pozostałe cyfr ułamkowych są obcinane. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie dwie cyfr ułamkowych.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "one", aby wyświetlić setnych sekundy w <xref:System.TimeSpan> wartość. "ff" jest używana w pierwszej kolejności, jak tylko specyfikator formatu, a następnie łączyć się ze specyfikatorem "s" w ciągu formatu niestandardowego.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Powrót do tabeli](#table)  
  
<a name="f3Specifier"></a>   
## <a name="the-fff-custom-format-specifier"></a>Specyfikator formatu niestandardowego „fff”  
 Specyfikator formatu niestandardowego "fff" (z trzech znaków "f") danych wyjściowych milisekund w przedziale czasu. W ramach operacji formatowania wszystkie pozostałe cyfr ułamkowych są obcinane. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie trzy cyfr ułamkowych.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "fff", aby wyświetlić milisekund w <xref:System.TimeSpan> wartość. "fff" jest używana w pierwszej kolejności, jak tylko specyfikator formatu, a następnie łączyć się ze specyfikatorem "s" w ciągu formatu niestandardowego.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Powrót do tabeli](#table)  
  
<a name="f4Specifier"></a>   
## <a name="the-ffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego „ffff”  
 Specyfikator formatu niestandardowego "ffff" (z czterech znaków "f") danych wyjściowych 10-000 sekund w przedziale czasu. W ramach operacji formatowania wszystkie pozostałe cyfr ułamkowych są obcinane. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie czterech cyfr ułamkowych.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "ffff", aby wyświetlić 10 000 do drugiej w <xref:System.TimeSpan> wartość. "ffff" jest używana w pierwszej kolejności, jak tylko specyfikator formatu, a następnie łączyć się ze specyfikatorem "s" w ciągu formatu niestandardowego.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Powrót do tabeli](#table)  
  
<a name="f5Specifier"></a>   
## <a name="the-fffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego „fffff”  
 Specyfikator formatu niestandardowego "fffff" (z pięciu znaków "f") danych wyjściowych sto tysięczne sekundy w przedziale czasu. W ramach operacji formatowania wszystkie pozostałe cyfr ułamkowych są obcinane. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie pięciu cyfr ułamkowych.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "fffff" do wyświetlenia tysięcznych sto sekundę w <xref:System.TimeSpan> wartość. "fffff" jest używana w pierwszej kolejności, jak tylko specyfikator formatu, a następnie łączyć się ze specyfikatorem "s" w ciągu formatu niestandardowego.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Powrót do tabeli](#table)  
  
<a name="f6Specifier"></a>   
## <a name="the-ffffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego „ffffff”  
 Specyfikator formatu niestandardowego "ffffff" (z sześciu znaków "f") danych wyjściowych milionowych sekundy w przedziale czasu. W ramach operacji formatowania wszystkie pozostałe cyfr ułamkowych są obcinane. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie sześciu cyfr ułamkowych.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "ffffff", aby wyświetlić milionowych sekundy w <xref:System.TimeSpan> wartość. Jest używany w pierwszej kolejności, jak tylko specyfikator formatu i następnie łączyć się ze specyfikatorem "s" w ciągu formatu niestandardowego.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Powrót do tabeli](#table)  
  
<a name="f7Specifier"></a>   
## <a name="the-fffffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego „fffffff”  
 Specyfikator formatu niestandardowego "fffffff" (z siedmiu znaków "f") danych wyjściowych milionowych dziesięć drugi (lub ich ułamkowych liczba) w przedziale czasu. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody ciąg wejściowy musi zawierać dokładnie siedmiu cyfr ułamkowych.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "fffffff", aby wyświetlić liczbę ułamkową znaczników w <xref:System.TimeSpan> wartość. Jest używany w pierwszej kolejności, jak tylko specyfikator formatu i następnie łączyć się ze specyfikatorem "s" w ciągu formatu niestandardowego.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Powrót do tabeli](#table)  
  
<a name="F_Specifier"></a>   
## <a name="the-f-custom-format-specifier"></a>Specyfikator formatu niestandardowego „F”  
 Specyfikator formatu niestandardowego "F" generuje dziesiąte części sekundy w przedziale czasu. W ramach operacji formatowania wszystkie pozostałe cyfr ułamkowych są obcinane. Jeśli wartość przedział czasu dziesiąte części sekundy wynosi zero, nie jest uwzględniony w ciągu wynik. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> , obecności dziesiąte części cyfrą drugi jest opcjonalne.  
  
 Jeśli używana jest jedynym specyfikator formatu niestandardowego "F", należy określić "%F", tak aby jest nieprawidłowo interpretowane jako ciąg w formacie.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "F", aby wyświetlić dziesiąte części sekundy w <xref:System.TimeSpan> wartość. Używa również to specyfikator formatu niestandardowego w operacji analizy.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#21)]
 [!code-vb[Conceptual.TimeSpan.Custom#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#21)]  
  
 [Powrót do tabeli](#table)  
  
<a name="FF_Specifier"></a>   
## <a name="the-ff-custom-format-specifier"></a>Specyfikator formatu niestandardowego „FF”  
 Specyfikator formatu niestandardowego "FF" generuje setnych sekundy w przedziale czasu. W ramach operacji formatowania wszystkie pozostałe cyfr ułamkowych są obcinane. W przypadku końcowe zera ułamkowych ich nie znajdują się w ciągu wynik. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> , obecności dziesiąte i setnych cyfrą drugi jest opcjonalne.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "One", aby wyświetlić setnych sekundy w <xref:System.TimeSpan> wartość. Używa również to specyfikator formatu niestandardowego w operacji analizy.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#22)]
 [!code-vb[Conceptual.TimeSpan.Custom#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#22)]  
  
 [Powrót do tabeli](#table)  
  
<a name="F3_Specifier"></a>   
## <a name="the-fff-custom-format-specifier"></a>Specyfikator formatu niestandardowego „FFF”  
 Specyfikator formatu niestandardowego "FFF" (z trzech znaków "F") danych wyjściowych milisekund w przedziale czasu. W ramach operacji formatowania wszystkie pozostałe cyfr ułamkowych są obcinane. W przypadku końcowe zera ułamkowych ich nie znajdują się w ciągu wynik. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> , obecności dziesiętnych, setnych i tysięczne cyfrą drugi jest opcjonalne.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "FFF", aby wyświetlić tysięczne sekundę w <xref:System.TimeSpan> wartość. Używa również to specyfikator formatu niestandardowego w operacji analizy.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#23)]
 [!code-vb[Conceptual.TimeSpan.Custom#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#23)]  
  
 [Powrót do tabeli](#table)  
  
<a name="F4_Specifier"></a>   
## <a name="the-ffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego „FFFF”  
 Specyfikator formatu niestandardowego "FFFF" (z czterech znaków "F") danych wyjściowych 10-000 sekund w przedziale czasu. W ramach operacji formatowania wszystkie pozostałe cyfr ułamkowych są obcinane. W przypadku końcowe zera ułamkowych ich nie znajdują się w ciągu wynik. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> , obecności dziesiętnych, setnych tysięczne i 10-000 z drugiego cyfrę jest opcjonalne.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "FFFF", aby wyświetlić 10 000 do drugiej w <xref:System.TimeSpan> wartość. Używa również specyfikator formatu niestandardowego "FFFF" w operacji analizy.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#24)]
 [!code-vb[Conceptual.TimeSpan.Custom#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#24)]  
  
 [Powrót do tabeli](#table)  
  
<a name="F5_Specifier"></a>   
## <a name="the-fffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego „FFFFF”  
 Specyfikator formatu niestandardowego "FFFFF" (z pięciu znaków "F") danych wyjściowych sto tysięczne sekundy w przedziale czasu. W ramach operacji formatowania wszystkie pozostałe cyfr ułamkowych są obcinane. W przypadku końcowe zera ułamkowych ich nie znajdują się w ciągu wynik. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> , dziesiętnych, setnych, tysięcznych, 10 000, oraz sto tysięcznych cyfrą drugi jest opcjonalne.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "FFFFF" do wyświetlenia tysięcznych sto sekundę w <xref:System.TimeSpan> wartość. Używa również specyfikator formatu niestandardowego "FFFFF" w operacji analizy.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#25)]
 [!code-vb[Conceptual.TimeSpan.Custom#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#25)]  
  
 [Powrót do tabeli](#table)  
  
<a name="F6_Specifier"></a>   
## <a name="the-ffffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego „FFFFFF”  
 Specyfikator formatu niestandardowego "FFFFFF" (z sześciu znaków "F") danych wyjściowych milionowych sekundy w przedziale czasu. W ramach operacji formatowania wszystkie pozostałe cyfr ułamkowych są obcinane. W przypadku końcowe zera ułamkowych ich nie znajdują się w ciągu wynik. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> , obecności dziesiętnych, setnych, tysięcznych, 10 000, sto tysięczne i milionowych cyfrą drugi jest opcjonalne.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "FFFFFF", aby wyświetlić milionowych sekundy w <xref:System.TimeSpan> wartość. Używa również to specyfikator formatu niestandardowego w operacji analizy.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#26](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#26)]
 [!code-vb[Conceptual.TimeSpan.Custom#26](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#26)]  
  
 [Powrót do tabeli](#table)  
  
<a name="F7_Specifier"></a>   
## <a name="the-fffffff-custom-format-specifier"></a>Specyfikator formatu niestandardowego „FFFFFFF”  
 Specyfikator formatu niestandardowego "FFFFFFF" (z siedmiu znaków "F") danych wyjściowych milionowych dziesięć drugi (lub ich ułamkowych liczba) w przedziale czasu. W przypadku końcowe zera ułamkowych ich nie znajdują się w ciągu wynik. W ramach operacji analizy, która wywołuje <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> lub <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> , obecności siedmiu cyfr ułamkowych w ciągu wejściowym jest opcjonalne.  
  
 W poniższym przykładzie użyto specyfikator formatu niestandardowego "FFFFFFF", aby wyświetlić ułamkowych części sekundy w <xref:System.TimeSpan> wartość. Używa również to specyfikator formatu niestandardowego w operacji analizy.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#27](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#27)]
 [!code-vb[Conceptual.TimeSpan.Custom#27](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#27)]  
  
 [Powrót do tabeli](#table)  
  
<a name="Other"></a>   
## <a name="other-characters"></a>Inne znaki.  
 Inne niezmienionym znaczeniu znaku w ciągu formatu, w tym biały znak, jest interpretowany jako specyfikator formatu niestandardowego. W większości przypadków obecność wszelkich innych niezmienionym znaczeniu powoduje znak <xref:System.FormatException>.  
  
 Istnieją dwa sposoby, aby uwzględnić znak w ciągu formatu:  
  
-   Należy ująć ją w pojedynczym cudzysłowie (ogranicznik literału ciągu).  
  
-   Należy poprzedzić go znakiem kreski ułamkowej odwróconej ("\\"), który jest interpretowany jako znak ucieczki. Oznacza to, że w języku C#, ciąg formatu, który musi być @-quoted, lub znak musi być poprzedzona dodatkowe ukośnika odwrotnego.  
  
     W niektórych przypadkach może być konieczne Użyj logikę warunkową, aby uwzględnić zmienionym literał w ciągu formatu. W poniższym przykładzie użyto logikę warunkową, aby objąć symbol znaku przedziały czasu ujemna.  
  
     [!code-csharp[Conceptual.TimeSpan.Custom#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/negativevalues1.cs#29)]
     [!code-vb[Conceptual.TimeSpan.Custom#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/negativevalues1.vb#29)]  
  
 .NET nie definiuje gramatyki dla separatorów w odstępach czasu. Oznacza to, że separatory między dni i godziny, godziny i minuty, minut i sekund i sekund i części sekundy muszą wszystkie być traktowane jako literały znaków w ciągu formatu.  
  
 W poniższym przykładzie użyto zarówno znak kontrolny, jak i pojedynczy cudzysłów, aby zdefiniować niestandardowy ciąg formatu zawierający słowo "min" w ciągu wyjściowego.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/literal1.cs#28)]
 [!code-vb[Conceptual.TimeSpan.Custom#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/literal1.vb#28)]  
  
 [Powrót do tabeli](#table)  
  
## <a name="see-also"></a>Zobacz też  
 [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
 [Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)
