---
title: Standardowe ciągi formatujące liczby
ms.date: 09/10/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- standard format strings, numeric
- format strings
- numbers [.NET Framework], formatting
- format specifiers, numeric
- standard numeric format strings
- formatting numbers [.NET Framework]
- format specifiers, standard numeric format strings
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 34fe406dac4cbbc0c25e43f479154fd3e398ffc2
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="standard-numeric-format-strings"></a>Standardowe ciągi formatujące liczby
Ciągi standardowych formatów liczb służą do formatowania popularnych typów liczbowych. Ciąg formatu liczbowego standardowe mają postać `Axx`, gdzie:  
  
-   `A` jest nazywana pojedynczy znak alfabetu *specyfikatorze formatu*. Dowolny ciąg formatu liczb, który zawiera więcej niż jeden znak alfabetyczny, w tym znak odstępu, jest interpretowany jako ciąg niestandardowego formatu liczb. Aby uzyskać więcej informacji, zobacz [niestandardowe ciągi formatów liczbowych](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
-   `xx` jest nazywana całkowitą opcjonalne *Specyfikator dokładności*. Specyfikator dokładności ma zakres od 0 do 99 i wpływa na liczbę cyfr w wyniku. Należy pamiętać, że Specyfikator dokładności określa liczbę cyfr w reprezentacji ciągu z liczbą. Nie zaokrągla samej liczby. Aby wykonać operację zaokrąglania, użyj <xref:System.Math.Ceiling%2A?displayProperty=nameWithType>, <xref:System.Math.Floor%2A?displayProperty=nameWithType>, lub <xref:System.Math.Round%2A?displayProperty=nameWithType> metody.  
  
     Gdy *Specyfikator dokładności* określa liczbę cyfr ułamkowych w ciągu wynik, ciągów wynikowych odzwierciedlają numery, które są zaokrąglane w kierunku od zera (oznacza to, za pomocą <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType>).  
  
    > [!NOTE]
    >  Specyfikator dokładności określa liczbę cyfr w ciągu wynik. Aby konsoli ciągu wyników z początkowe lub końcowe spacje, użyj [złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md) funkcji oraz definiowania *składnika wyrównanie* w elemencie formatu.  
  
Standardowe ciągi formatujące liczby obsługiwanych przez:

- Niektóre przeciążeń `ToString` metody wszystkie typy liczbowe. Na przykład można podać ciąg formatu liczbowego <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> i <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody. 
 
- Programu .NET [złożonych funkcji formatowania](../../../docs/standard/base-types/composite-formatting.md), który jest używany przez niektóre `Write` i `WriteLine` metody <xref:System.Console> i <xref:System.IO.StreamWriter> klas, <xref:System.String.Format%2A?displayProperty=nameWithType> metody i <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> — metoda. Funkcja format złożonego umożliwia obejmują jako jeden ciąg znaków, aby określić szerokość pola i dopasowanie liczb w polu reprezentacja ciągu wielu elementów danych. Aby uzyskać więcej informacji, zobacz [złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md).  

- [Ciągi interpolowane](../../csharp/language-reference/tokens/interpolated.md) w języku C# i Visual Basic, które zapewniają uproszczoną składnię w porównaniu do ciągi formatujące złożonego.
 
> [!TIP]
>  Możesz pobrać [formatowania narzędzie](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)ciągi aplikacji, która umożliwia zastosowanie formatu liczbowego lub daty i czasu wartości i wyświetla ciąg wyniku.  
  
<a name="table"></a> Poniższej tabeli opisano specyfikatorów formatu liczbowego standardowe i zawiera przykładowe dane wyjściowe generowane przez każdego specyfikator formatu. Zobacz [uwagi](#NotesStandardFormatting) sekcji, aby uzyskać dodatkowe informacje o używaniu standardowe ciągi formatujące liczby i [przykład](#example) sekcji ilustracyjną kompleksowe ich użycia.  
  
|Specyfikator formatu|Nazwa|Opis|Przykłady|  
|----------------------|----------|-----------------|--------------|  
|„C” lub „c”|Waluta|Wynik: wartość waluty.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr dziesiętnych.<br /><br /> Domyślna Specyfikator dokładności: zdefiniowane przez <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Więcej informacji: [waluty specyfikator formatu ("C")](#CFormatString).|123.456 ("C", en-US) -> $123.46<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> ¥123<br /><br /> -123.456 ("C3", en US) -> ($123.456)<br /><br /> €-123,456 ->-123.456 ("C3", fr-FR)<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|  
|„D” lub „d”|Wartość dziesiętna|Wynik: liczby całkowite z opcjonalnym znakiem minus.<br /><br /> Obsługiwane przez: tylko typy całkowite.<br /><br /> Specyfikator dokładności: minimalna liczba cyfr.<br /><br /> Domyślny specyfikator dokładności: minimalna liczba wymaganych cyfr.<br /><br /> Więcej informacji: [specyfikator formatu Decimal("D")](#DFormatString).|1234 ("D") -> 1234<br /><br /> -1234 ("D6") -> -001234|  
|„E” lub „e”|Wartość wykładnicza (naukowa)|Wynik: zapis wykładniczy.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr dziesiętnych.<br /><br /> Domyślny specyfikator dokładności: 6.<br /><br /> Więcej informacji: [wykładniczej ("E") specyfikator formatu](#EFormatString).|1052.0329112756 ("E", en-US) -> 1.052033E+003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1, 052033e + 003<br /><br /> -1052.0329112756 ("e2", en-US) -> -1.05e+003<br /><br /> -1052.0329112756 ("E2", fr_FR) -> -1, 05E + 003|  
|„F” lub „f”|Wartość stałoprzecinkowa|Wynik: cyfry całkowite i dziesiętne z opcjonalnym znakiem minus.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr dziesiętnych.<br /><br /> Domyślna Specyfikator dokładności: zdefiniowane przez <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Więcej informacji: [stałoprzecinkowe specyfikator ("F") w formacie](#FFormatString).|1234.567 ("F" en US) -> 1234,57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1" en US) -> 1234.0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234.5600 ->-1234.56 ("F4", en US)<br /><br /> -1234.56 ("F4", de-DE) -> - 1234,5600|  
|„G” lub „g”|Ogólne|Wynik: Więcej compact stałoprzecinkowej lub naukowych notacji.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr znaczących.<br /><br /> Domyślny specyfikator dokładności: zależy od typu liczbowego.<br /><br /> Więcej informacji: [ogólny ("G") specyfikator formatu](#GFormatString).|-123.456 ->-123.456 ("G", en US)<br /><br /> -123.456 ("G", sv-SE) -> -123,456<br /><br /> 123.4546 ("G4", en-US) -> 123.5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1.234567890e-25 ("G", en-US) -> -1.23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -> -1,23456789E-25|  
|„N” lub „n”|Wartość liczbowa|Wynik: cyfry całkowite i dziesiętne, separatory grup i separator dziesiętny z opcjonalnym znaku minus.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: wymagana liczba miejsc dziesiętnych.<br /><br /> Domyślna Specyfikator dokładności: zdefiniowane przez <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Więcej informacji: [specyfikator formatu liczbowego ("N")](#NFormatString).|1234.567 ("N" en US) -> 1234,57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1" en US) -> 1,234.0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1,234.560 ->-1234.56 ("N3", en US)<br /><br /> 234,560-1 ->-1234.56 ("N3", ru-RU)|  
|„P” lub „p”|Wartość procentowa|Wynik: liczba pomnożona przez 100 i wyświetlana z symbolem procentu.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: wymagana liczba miejsc dziesiętnych.<br /><br /> Domyślna Specyfikator dokładności: zdefiniowane przez <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Więcej informacji: [Percent ("P"), specyfikator formatu](#PFormatString).|1 ("P" en US) -> % 100,00<br /><br /> 1 ("P", fr-FR) -> 100,00%<br /><br /> -0.39678 ("P1" en US) ->-39.7%<br /><br /> -0.39678 ("1", fr-FR) -> - 39,7%|  
|„R” lub „r”|Wartość dwustronna|Wynik: ciąg, który można dwustronnie konwertować na identyczny numer.<br /><br /> Obsługiwane przez: <xref:System.Single>, <xref:System.Double>, i <xref:System.Numerics.BigInteger>.<br /><br /> Uwaga: Zalecane w przypadku <xref:System.Numerics.BigInteger> tylko typu. Aby uzyskać <xref:System.Double> typów, użyj "G17"; dla <xref:System.Single> typów, użyj "G9". </br> Specyfikator dokładności: ignorowany.<br /><br /> Więcej informacji: [wyrównana specyfikator formatu ("R")](#RFormatString).|123456789.12345678 ("R") -> 123456789.12345678<br /><br /> -1234567890.12345678 ("R") -> -1234567890.1234567|  
|„X” lub „x”|Wartość szesnastkowa|Wynik: ciąg szesnastkowy.<br /><br /> Obsługiwane przez: tylko typy całkowite.<br /><br /> Specyfikator dokładności: liczba cyfr w ciągu wynikowym.<br /><br /> Więcej informacji: [szesnastkowym ("X") specyfikator formatu](#XFormatString).|255 ("X") -> FF<br /><br /> one -> -1 ("x")<br /><br /> 00ff -> 255 ("x4")<br /><br /> -1 ("X4") -> 00FF|  
|Jakikolwiek inny pojedynczy znak|Nieznany specyfikator|Wynik: Zwraca <xref:System.FormatException> w czasie wykonywania.||  
  
<a name="Using"></a>   
## <a name="using-standard-numeric-format-strings"></a>Korzystając ze standardowego, numerycznego ciągu formatującego  
 Ciąg standardowego formatu liczb może służyć do definiowania formatowania wartości liczbowej na jeden z dwóch sposobów:  
  
-   Mogą zostać przekazane do przeciążenia `ToString` metodę, która ma `format` parametru. Poniższy przykład formatuje wartość numeryczną jako ciąg waluty w bieżącej kultury (w tym przypadku kultury en US).  
  
     [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
     [!code-csharp[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
     [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]  
  
-   Można podać jako `formatString` argumentów w elemencie format używany z tych metod jako <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, i <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md). W poniższym przykładzie element formatu jest używany do wstawienia wartości waluty w ciągu.  
  
     [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
     [!code-csharp[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
     [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]  
  
     Opcjonalnie możesz podać `alignment` argumentu, aby określić szerokość pola numerycznego i czy jej wartość jest wyrównany do prawej lub lewej strony. Poniższy przykład powoduje wyrównanie lewej wartości waluty w polu 28 znaków, a jego prawej wyrównuje wartości waluty w polu 14 znaków.  
  
     [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
     [!code-csharp[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
     [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]  
  
-   Można podać jako `formatString` argumentów w elemencie interpolowanego wyrażenia w ciągu interpolowanym. Aby uzyskać więcej informacji, zobacz [ciągu interpolacji](../../csharp/language-reference/tokens/interpolated.md) tematu w odwołanie w C# lub [ciągi interpolowane](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) tematu w odwołanie w Visual Basic.  
  
 Poniższe sekcje zawierają szczegółowe informacje o poszczególnych ciągach standardowego formatu liczb.  
  
<a name="CFormatString"></a>   
## <a name="the-currency-c-format-specifier"></a>Specyfikator formatu waluty („C”)  
 Specyfikator formatu C (currency) konwertuje liczbę na ciąg przedstawiający kwotę w walucie. Specyfikator dokładności określa żądaną liczbę miejsc dziesiętnych w wynikowym ciągu. W przypadku pominięcia Specyfikator dokładności domyślna dokładność jest definiowana za pomocą <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> właściwości.  
  
 Jeśli wartość do sformatowania ma więcej miejsc dziesiętnych niż określona lub domyślna liczba miejsc dziesiętnych, wartość ułamkowa zostanie zaokrąglona w wynikowym ciągu. Jeśli wartość na prawo od określonej liczby miejsc dziesiętnych wynosi 5 lub więcej, ostatnia cyfra w ciągu wynikowym jest zaokrąglana w kierunku od zera.  
  
 Wpływ na informacje dotyczące formatowania bieżącego ciąg wyniku <xref:System.Globalization.NumberFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.NumberFormatInfo> właściwości sterujące formatowania zwracany ciąg.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|Definiuje położenie symbolu waluty dla wartości dodatnich.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|Definiuje położenie symbol waluty dla wartości ujemnych i określa, czy znakiem minus jest reprezentowana przez nawiasy lub <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> właściwości.|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje znakiem minus używane, jeśli <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> wskazuje, że nawiasy nie są używane.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|Definiuje symbol waluty.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych w wartości waluty. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite i cyfry dziesiętne.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|Definiuje ciąg oddzielający grupy liczb całkowitych.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|Definiuje liczbę cyfr liczby całkowitej, które pojawiają się w grupie.|  
  
 Następujące przykładowe formaty <xref:System.Double> wartość ze specyfikatorem formacie waluty.  
  
 [!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
 [!code-csharp[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
 [!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]  
  
 [Powrót do tabeli](#table)  
  
<a name="DFormatString"></a>   
## <a name="the-decimal-d-format-specifier"></a>Specyfikator formatu dziesiętnego („D”)  
 Specyfikator formatu D (decimal) konwertuje liczbę na ciąg cyfr dziesiętnych (0–9), poprzedzony znakiem minus, jeśli liczba jest ujemna. Ten format jest obsługiwany tylko w przypadku typów całkowitych.  
  
 Specyfikator dokładności określa minimalną liczbę miejsc dziesiętnych w ciągu wynikowym. Jeśli to konieczne, liczba jest dopełniana zerami po lewej stronie w celu uzyskania liczby cyfr określonej przez specyfikator dokładności. Jeśli nie zostanie określony specyfikator dokładności, wartością domyślną jest wartość minimalna wymagana do przedstawienia wartości całkowitej bez zer wiodących.  
  
 Wpływ na informacje dotyczące formatowania bieżącego ciąg wyniku <xref:System.Globalization.NumberFormatInfo> obiektu. Jak pokazano w poniższej tabeli, jedna właściwość ma wpływ na formatowanie ciągu wynikowego.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|  
  
 Następujące przykładowe formaty <xref:System.Int32> wartość ze specyfikatorem formatu dziesiętnego.  
  
 [!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
 [!code-csharp[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
 [!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]  
  
 [Powrót do tabeli](#table)  
  
<a name="EFormatString"></a>   
## <a name="the-exponential-e-format-specifier"></a>Specyfikator formatu wykładniczego („E”)  
 Specyfikator formatu wykładniczego („E”) konwertuje liczbę na ciąg w postaci „-d,ddd...E + ddd” lub „-d,ddd...e+ddd”, gdzie każda litera „d” wskazuje cyfrę (0–9). Ciąg rozpoczyna się od znaku minus, jeśli liczba jest ujemna. Zawsze dokładnie jedna cyfra poprzedza punkt dziesiętny.  
  
 Specyfikator dokładności określa żądaną liczbę cyfr po punkcie dziesiętnym. Jeśli specyfikator dokładności zostanie pominięty, domyślnie będzie używanych sześć cyfr po punkcie dziesiętnym.  
  
 Wielkość liter specyfikatora formatu wskazuje, czy wykładnik potęgi ma być poprzedzany prefiksem „E”, czy „e”. Wykładnik zawsze składa się ze znaku plus lub minus i co najmniej trzech cyfr. W razie potrzeby wykładnik jest dopełniany zerami w celu spełnienia tego minimum.  
  
 Wpływ na informacje dotyczące formatowania bieżącego ciąg wyniku <xref:System.Globalization.NumberFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.NumberFormatInfo> właściwości sterujące formatowania zwracany ciąg.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna zarówno dla współczynnika, jak i wykładnika.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Określa ciąg oddzielający cyfry całkowite od cyfr dziesiętnych we współczynniku.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Określa ciąg, który wskazuje, że wykładnik jest dodatni.|  
  
 Następujące przykładowe formaty <xref:System.Double> wartość ze specyfikatorem notacji wykładniczej.  
  
 [!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
 [!code-csharp[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
 [!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]  
  
 [Powrót do tabeli](#table)  
  
<a name="FFormatString"></a>   
## <a name="the-fixed-point-f-format-specifier"></a>Specyfikator formatu stałoprzecinkowego („F”)  
 Stałoprzecinkowe specyfikator formatu ("F") konwertuje liczbę na ciąg w formie "-CCC, CCC..." gdzie każdy "d" oznacza cyfrę (0 – 9). Ciąg rozpoczyna się od znaku minus, jeśli liczba jest ujemna.  
  
 Specyfikator dokładności określa żądaną liczbę miejsc dziesiętnych. W przypadku pominięcia Specyfikator dokładności bieżącego <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> właściwości dostarcza dokładność liczbowych.  
  
 Wpływ na informacje dotyczące formatowania bieżącego ciąg wyniku <xref:System.Globalization.NumberFormatInfo> obiektu. W poniższej tabeli wymieniono właściwości <xref:System.Globalization.NumberFormatInfo> obiekt, który kontrolować sposób formatowania ciągu wynik.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite od cyfr dziesiętnych.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|  
  
 Następujące przykładowe formaty <xref:System.Double> i <xref:System.Int32> wartość ze specyfikatorem formatu stałoprzecinkowe.  
  
 [!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
 [!code-csharp[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
 [!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]  
  
 [Powrót do tabeli](#table)  
  
<a name="GFormatString"></a>   
## <a name="the-general-g-format-specifier"></a>Specyfikator formatu ogólnego („G”)  
 Ogólne specyfikator formatu ("G") konwertuje liczbę więcej compact notacji stałoprzecinkowej lub naukowych, w zależności od liczby i określa, czy znajduje się Specyfikator dokładności. Specyfikator dokładności określa maksymalną liczbę cyfr znaczących, które mogą być wyświetlane w ciągu wynikowym. Jeżeli specyfikator dokładności zostanie pominięty lub będzie równy zero, typ liczby określa dokładność domyślną, tak jak opisano w poniższej tabeli.  
  
|Typ liczbowy|Dokładność domyślna|  
|------------------|-----------------------|  
|<xref:System.Byte> lub <xref:System.SByte>|3 cyfry|  
|<xref:System.Int16> lub <xref:System.UInt16>|5 cyfr|  
|<xref:System.Int32> lub <xref:System.UInt32>|10 cyfr|  
|<xref:System.Int64>|19 cyfr|  
|<xref:System.UInt64>|20 cyfr|  
|<xref:System.Numerics.BigInteger>|Nieograniczone (taki sam jak ["R"](#RFormatString))|  
|<xref:System.Single>|7 cyfr|  
|<xref:System.Double>|15 cyfr.|  
|<xref:System.Decimal>|29 cyfr|  
  
 Notacja stałoprzecinkowa jest używana, jeśli wykładnik, który byłby wynikiem wyrażenia liczby w notacji wykładniczej, jest większy niż -5 i mniejszy niż specyfikator dokładności. W przeciwnym wypadku jest używana notacja wykładnicza. Wynik zawiera punkt dziesiętny, jeśli jest to wymagane, a zera końcowe po punkcie dziesiętnym są pomijane. Jeśli specyfikator dokładności jest obecny i liczba cyfr znaczących w wyniku przekracza określoną dokładność, nadmiarowe cyfry końcowe są usuwane przez zaokrąglenie.  
  
 Jednak jeśli liczba jest <xref:System.Decimal> Specyfikator dokładności zostanie pominięty, notacji stałoprzecinkowej jest zawsze używana usługa i końcowe zera zostaną zachowane.  
  
 Jeśli jest używana notacja wykładnicza, wykładnik w wyniku otrzymuje prefiks „E”, jeśli specyfikatorem formatu jest „G”, lub „e”, jeśli specyfikatorem formatu jest „g”. Wykładnik zawiera co najmniej dwie cyfry. Różni się to od formatu notacji wykładniczej tworzonej przez specyfikator formatu wykładniczego, który obejmuje co najmniej trzy cyfry wykładnika.  
 
Należy zauważyć, że w przypadku użycia z <xref:System.Double> wartość specyfikator formatu "G17" upewnia się, że oryginalne <xref:System.Double> wartość pomyślnie przechodzenia. Jest to spowodowane <xref:System.Double> jest IEEE 754 2008-CLS podwójnej precyzji (`binary64`) zawierający maksymalnie 17 cyfr znaczących dokładności liczba zmiennoprzecinkowa. Firma Microsoft zaleca użycie zamiast [specyfikatorze formatu "R"](#RFormatString), ponieważ w niektórych przypadkach "R" nie może pomyślnie obustronne podwójnej precyzji wartości zmiennoprzecinkowych. Poniższy przykład przedstawia w takim przypadku.

[!code-csharp[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs)]   
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]   

W przypadku użycia z <xref:System.Single> wartość specyfikator formatu "G9" zapewnia, że oryginalne <xref:System.Single> wartość pomyślnie przechodzenia. Jest to spowodowane <xref:System.Single> jest IEEE 754 2008-CLS pojedynczej precyzji (`binary32`) zawierający maksymalnie dziewięć cyfr znaczących dokładności liczba zmiennoprzecinkowa. Firma Microsoft zaleca użycie zamiast [specyfikatorze formatu "R"](#RFormatString), ponieważ w niektórych przypadkach "R" nie może pomyślnie obustronne pojedynczej precyzji wartości zmiennoprzecinkowych.

 Wpływ na informacje dotyczące formatowania bieżącego ciąg wyniku <xref:System.Globalization.NumberFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.NumberFormatInfo> właściwości sterujące formatowania ciągu wynik.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite od cyfr dziesiętnych.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Określa ciąg, który wskazuje, że wykładnik jest dodatni.|  
  
 W poniższym przykładzie różne wartości zmiennoprzecinkowe są formatowane przy użyciu specyfikatora formatu ogólnego.  
  
 [!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
 [!code-csharp[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
 [!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]  
  
 [Powrót do tabeli](#table)  
  
<a name="NFormatString"></a>   
## <a name="the-numeric-n-format-specifier"></a>Specyfikator formatu numerycznego („N”)  
 Specyfikator formatu liczbowego („N”) konwertuje liczbę na ciąg w postaci „-d ddd ddd,ddd…”, gdzie „-” oznacza w razie potrzeby liczbę ujemną, „d” oznacza cyfrę (0–9), „ ” oznacza separator grupy, a „,” oznacza symbol punktu dziesiętnego. Specyfikator dokładności określa żądaną liczbę cyfr po punkcie dziesiętnym. W przypadku pominięcia Specyfikator dokładności liczbę miejsc dziesiętnych jest zdefiniowana przez bieżące <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> właściwości.  
  
 Wpływ na informacje dotyczące formatowania bieżącego ciąg wyniku <xref:System.Globalization.NumberFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.NumberFormatInfo> właściwości sterujące formatowania ciągu wynik.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|  
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|Definiuje format wartości ujemnych i określa, czy znakiem minus jest reprezentowana przez nawiasy lub <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> właściwości.|  
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|Definiuje liczbę cyfr liczby całkowitej, które pojawiają się pomiędzy separatorami grup.|  
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|Definiuje ciąg oddzielający grupy liczb całkowitych.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite i cyfry dziesiętne.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|  
  
 W poniższym przykładzie różne wartości zmiennoprzecinkowe są formatowane przy użyciu specyfikatora formatu liczby.  
  
 [!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
 [!code-csharp[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
 [!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]  
  
 [Powrót do tabeli](#table)  
  
<a name="PFormatString"></a>   
## <a name="the-percent-p-format-specifier"></a>Specyfikator formatu procenta („P”)  
 Specyfikator formatu procentowego („P”) mnoży liczbę przez 100 i konwertuje ją na ciąg, który przedstawia wartość procentową. Specyfikator dokładności określa żądaną liczbę miejsc dziesiętnych. W przypadku pominięcia Specyfikator dokładności domyślna dokładność liczbowych dostarczonych przez bieżący <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> właściwość jest używana.  
  
 W poniższej tabeli wymieniono <xref:System.Globalization.NumberFormatInfo> właściwości sterujące formatowania zwracany ciąg.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.PercentPositivePattern%2A>|Definiuje położenie symbolu procentu dla wartości dodatnich.|  
|<xref:System.Globalization.NumberFormatInfo.PercentNegativePattern%2A>|Definiuje położenie symbol procentu i symbolu wartości ujemnej dla wartości ujemnych.|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|  
|<xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A>|Definiuje symbol procentu.|  
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych w wartości procentowej. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|  
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite i cyfry dziesiętne.|  
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSeparator%2A>|Definiuje ciąg oddzielający grupy liczb całkowitych.|  
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSizes%2A>|Definiuje liczbę cyfr liczby całkowitej, które pojawiają się w grupie.|  
  
 W poniższym przykładzie wartości zmiennoprzecinkowe są formatowane przy użyciu specyfikatora formatu wartości procentowej.  
  
 [!code-cpp[Formatting.Numeric.Standard#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#7)]
 [!code-csharp[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
 [!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]  
  
 [Powrót do tabeli](#table)  
  
<a name="RFormatString"></a>   
## <a name="the-round-trip-r-format-specifier"></a>Specyfikator formatu obustronnej konwersji („R”)  
 Obustronne specyfikator formatu ("R") próbuje upewnij się, że wartość numeryczną, która jest konwertowana na ciąg jest analizowana wrócić do tego samego wartość liczbową. Ten format jest obsługiwany tylko w przypadku <xref:System.Single>, <xref:System.Double>, i <xref:System.Numerics.BigInteger> typów.  

Aby uzyskać <xref:System.Double> i <xref:System.Single> wartości, specyfikator formatu "R" w niektórych przypadkach nie powiedzie się pomyślnie obustronne oryginalnej wartości i oferuje również stosunkowo niska wydajność. Zamiast tego zaleca się używanie ["G17"](#GFormatString) specyfikatora formatu <xref:System.Double> wartości i ["G9"](#GFormatString) specyfikatorze do pomyślnie obustronne formatu <xref:System.Single> wartości.

 Gdy <xref:System.Numerics.BigInteger> wartość jest sformatowany za pomocą tego specyfikatora, reprezentacji ciągu zawiera cyfr znaczących w <xref:System.Numerics.BigInteger> wartość.  
  
 Można dodawać specyfikator dokładności, ale jest on ignorowany. W przypadku korzystania z tego specyfikatora konwersje dwustronne mają pierwszeństwo przed dokładnością.    
 Wpływ na informacje dotyczące formatowania bieżącego ciąg wyniku <xref:System.Globalization.NumberFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.NumberFormatInfo> właściwości sterujące formatowania ciągu wynik.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite od cyfr dziesiętnych.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Określa ciąg, który wskazuje, że wykładnik jest dodatni.|  
  
 Następujące przykładowe formaty <xref:System.Numerics.BigInteger> wartość ze specyfikatorem formatu błądzenia.  
  
 [!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
 [!code-csharp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
 [!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]  
  
> [!IMPORTANT]
>  W niektórych przypadkach <xref:System.Double> wartości sformatowany w systemie nie pomyślnie obustronne ciągu standardowego formatu liczbowego "R" Jeśli skompilowana przy użyciu `/platform:x64` lub `/platform:anycpu` przełączników i wykonywania na 64-bitowym. Zobacz poniższe akapitu, aby uzyskać więcej informacji.  
  
 Aby obejść ten problem z <xref:System.Double> wartości sformatowane przy użyciu standardowego formatu liczbowego "R" string nie zostało pomyślnie dwustronną komunikację, jeśli skompilowana przy użyciu `/platform:x64` lub `/platform:anycpu` przełączników i wykonywania w systemach 64-bitowych. można też <xref:System.Double> wartości przy użyciu ciągu standardowego formatu liczbowego "G17". W poniższym przykładzie użyto ciągu formatu "R" z <xref:System.Double> wartość tego obustronne nie ma pomyślnie, a także format używa "G17" ciąg pomyślnie obustronne oryginalnej wartości.  
  
 [!code-csharp[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#5)]
 [!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]  
  
 [Powrót do tabeli](#table)  
  
<a name="XFormatString"></a>   
## <a name="the-hexadecimal-x-format-specifier"></a>Specyfikator formatu szesnastkowego („X”)  
 Specyfikator formatu szesnastkowego („X”) konwertuje liczbę na ciąg cyfr szesnastkowych. Wielkość liter specyfikatora formatu wskazuje, czy w przypadku cyfr szesnastkowych, które są większe niż 9, należy używać wielkich, czy małych liter. Na przykład użycie specyfikatora „X” umożliwia uzyskanie cyfr „ABCDEF”, a specyfikatora „x” — cyfr „abcdef”. Ten format jest obsługiwany tylko w przypadku typów całkowitych.  
  
 Specyfikator dokładności określa minimalną liczbę miejsc dziesiętnych w ciągu wynikowym. Jeśli to konieczne, liczba jest dopełniana zerami po lewej stronie w celu uzyskania liczby cyfr określonej przez specyfikator dokładności.  
  
 Ciąg wyniku nie ma wpływu na informacje dotyczące formatowania bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu.  
  
 Następujące przykładowe formaty <xref:System.Int32> specyfikatorze formatu wartości szesnastkowym.  
  
 [!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
 [!code-csharp[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
 [!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]  
  
 [Powrót do tabeli](#table)  
  
<a name="NotesStandardFormatting"></a>   
## <a name="notes"></a>Uwagi  
  
### <a name="control-panel-settings"></a>Ustawienia panelu sterowania  
 Ustawienia w **Opcje regionalne i językowe** elementu w Panelu sterowania wpływ ciąg wyniku utworzone przez operację formatowania. Te ustawienia są używane do zainicjowania <xref:System.Globalization.NumberFormatInfo> obiekt skojarzony z bieżącej kultury wątku, co zapewnia wartości używane do sterowania formatowania. Na komputerach, na których są używane różne ustawienia, są generowane różne ciągi wynikowe.  
  
 Ponadto jeśli <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> Konstruktor jest używany do utworzenia wystąpienia nowy <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje tego samego kultury bieżącej kultury systemu, wszelkie dostosowania ustala **Opcje regionalne i językowe** w Panelu sterowania zostaną zastosowane do nowego <xref:System.Globalization.CultureInfo> obiektu. Można użyć <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktora w celu utworzenia <xref:System.Globalization.CultureInfo> obiekt, który nie odzwierciedla dostosowania systemu.  
  
### <a name="numberformatinfo-properties"></a>Właściwości klasy NumberFormatInfo  
 Formatowanie ma wpływ właściwości bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu, który jest dostarczany niejawnie według bieżącej kultury wątku lub jawnie <xref:System.IFormatProvider> parametru metody, która wywołuje formatowania. Określ <xref:System.Globalization.NumberFormatInfo> lub <xref:System.Globalization.CultureInfo> obiekt dla tego parametru.  
  
> [!NOTE]
>  Uzyskać informacji o dostosowywaniu wzorców i ciągi używaną w formatowaniu wartości liczbowe, zobacz <xref:System.Globalization.NumberFormatInfo> klasy tematu.  
  
### <a name="integral-and-floating-point-numeric-types"></a>Całkowite i zmiennoprzecinkowe rodzaje wartości numerycznych  
 Niektóre opisy specyfikatorów standardowego formatu liczb odnoszą się do całkowitych lub zmiennoprzecinkowych typów liczbowych. Typy całkowite liczbowych są <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, i <xref:System.Numerics.BigInteger>. Typy liczbowe zmiennoprzecinkowe są <xref:System.Decimal>, <xref:System.Single>, i <xref:System.Double>.  
  
### <a name="floating-point-infinities-and-nan"></a>Zmiennoprzecinkowe nieskończoności i NaN  
 Niezależnie od ciąg formatu Jeśli wartość <xref:System.Single> lub <xref:System.Double> typ zmiennoprzecinkowy nieskończoności dodatniej, nieskończoności ujemnej lub niebędące liczbą (NaN), sformatowanego ciągu jest wartością odpowiednio <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>, <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>, lub <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> właściwość, która jest określona przez stosowane obecnie <xref:System.Globalization.NumberFormatInfo> obiektu.  
  
<a name="example"></a>   
## <a name="example"></a>Przykład  
 W poniższym przykładzie całkowita i zmiennoprzecinkowa wartość liczbowa jest formatowana przy użyciu kultury en-US i wszystkich specyfikatorów standardowego formatu liczb. W tym przykładzie używane są dwa typy liczbowe konkretnego (<xref:System.Double> i <xref:System.Int32>), ale będzie podobne wyniki dla każdego z innych liczbowych typów podstawowych (<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Numerics.BigInteger>, <xref:System.Decimal>, i <xref:System.Single>).  
  
 [!code-csharp[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#1)]
 [!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Globalization.NumberFormatInfo>  
 [Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
 [Instrukcje: Uzupełnianie liczby zerami wiodącymi](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)  
 [Przykład: .NET Framework 4 formatowania narzędzia](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)  
 [Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)
