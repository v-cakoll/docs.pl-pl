---
title: Standardowe ciągi formatujące liczby
ms.date: 06/10/2018
ms.technology: dotnet-standard
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
ms.openlocfilehash: 7f304adb567e3568fb4624b3c5e9ec4585009a05
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565745"
---
# <a name="standard-numeric-format-strings"></a>Standardowe ciągi formatujące liczby

Ciągi standardowych formatów liczb służą do formatowania popularnych typów liczbowych. Ciąg standardowego formatu liczb ma postać `Axx`, gdzie:  
  
-   `A` nosi nazwę jednego znaku alfabetycznego *specyfikatora formatu*. Dowolny ciąg formatu liczb, który zawiera więcej niż jeden znak alfabetyczny, w tym znak odstępu, jest interpretowany jako ciąg niestandardowego formatu liczb. Aby uzyskać więcej informacji, zobacz [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
-   `xx` jest opcjonalną liczbą całkowitą o nazwie *Specyfikator dokładności*. Specyfikator dokładności ma zakres od 0 do 99 i wpływa na liczbę cyfr w wyniku. Należy pamiętać, że Specyfikator dokładności określa liczbę cyfr w ciągu reprezentującym liczbę. Nie zaokrągla samej liczby. Aby wykonać operację zaokrąglenia, użyj <xref:System.Math.Ceiling%2A?displayProperty=nameWithType>, <xref:System.Math.Floor%2A?displayProperty=nameWithType>, lub <xref:System.Math.Round%2A?displayProperty=nameWithType> metody.  
  
    Gdy *Specyfikator dokładności* formantów liczba cyfr dziesiętnych w ciągu wynikowym, ciąg wynikowy odzwierciedla liczbę, która jest zaokrąglana do stałego wyniku najbardziej zbliżona nieskończenie dokładny wynik. Jeśli istnieją dwa jednakowo blisko stałego wyniki:
    - **W programie .NET Framework i .NET Core do platformy .NET Core 2.0**, środowisko uruchomieniowe wybiera wynik z większą najmniej znaczącą cyfrę (czyli używania <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType>).
    - **W programie .NET Core 2.1 lub nowszym**, środowisko uruchomieniowe wybiera wynik z nawet najmniej znaczące cyfry (czyli używania <xref:System.MidpointRounding.ToEven?displayProperty=nameWithType>). 

    > [!NOTE]
    >  Specyfikator dokładności określa liczbę cyfr w ciągu wynikowym. Aby uzupełnić ciąg wynikowy, za pomocą spacji wiodących albo końcowych, użycia [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md) funkcji oraz definiowania *składnik wyrównania* w elemencie formatu.  
  
Ciągi standardowego formatu liczb są obsługiwane przez:

- Niektóre przeciążenia `ToString` metoda wszystkich typów liczbowych. Na przykład można podać ciąg w formacie liczbowym do <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> i <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody. 
 
- .NET [funkcję formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md), która jest używana przez niektóre `Write` i `WriteLine` metody <xref:System.Console> i <xref:System.IO.StreamWriter> klas, <xref:System.String.Format%2A?displayProperty=nameWithType> metody i <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> metody. Funkcja formatowania złożonego umożliwia obejmują reprezentację ciągu wielu elementów danych jako jeden ciąg znaków, aby określić szerokość pola i wyrównanie liczb w polu. Aby uzyskać więcej informacji, zobacz [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md).  

- [Ciągi interpolowane](../../csharp/language-reference/tokens/interpolated.md) w języku C# i Visual Basic, które zapewniają uproszczoną składnię, w porównaniu do ciągów formatowania złożonego.
 
> [!TIP]
>  Możesz pobrać [narzędzie do formatowania](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), aplikację, która umożliwia zastosowanie formatu ciągów liczbowego lub daty i godziny, wartości oraz wyświetlenie ciągu wynikowego.  
  
<a name="table"></a> Poniższej tabeli opisano specyfikatory standardowych formatów liczb i pokazano przykładowe dane wyjściowe wytwarzane przez każdy specyfikator formatu. Zobacz [uwagi](#NotesStandardFormatting) sekcji, aby uzyskać dodatkowe informacje dotyczące używania ciągów standardowego formatu liczb oraz [przykład](#example) sekcji, w której dokładnie opisano ich użycie.  
  
|Specyfikator formatu|Nazwa|Opis|Przykłady|  
|----------------------|----------|-----------------|--------------|  
|„C” lub „c”|Waluta|Wynik: wartość waluty.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr dziesiętnych.<br /><br /> Domyślny Specyfikator dokładności: zdefiniowany przez <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Więcej informacji: [("C") specyfikator formatu waluty](#CFormatString).|123.456 ("C", en-US) -> $123.46<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> ¥123<br /><br /> -123.456 ("C3", en US) -> ($123.456)<br /><br /> -123.456 ("C3", fr-FR) ->-123,456 €<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|  
|„D” lub „d”|Wartość dziesiętna|Wynik: liczby całkowite z opcjonalnym znakiem minus.<br /><br /> Obsługiwane przez: tylko typy całkowite.<br /><br /> Specyfikator dokładności: minimalna liczba cyfr.<br /><br /> Domyślny specyfikator dokładności: minimalna liczba wymaganych cyfr.<br /><br /> Więcej informacji: [specyfikator formatu Decimal("D")](#DFormatString).|1234 ("D") -> 1234<br /><br /> -1234 ("D6") -> -001234|  
|„E” lub „e”|Wartość wykładnicza (naukowa)|Wynik: zapis wykładniczy.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr dziesiętnych.<br /><br /> Domyślny specyfikator dokładności: 6.<br /><br /> Więcej informacji: [specyfikator formatu wykładniczego ("E")](#EFormatString).|1052.0329112756 ("E", en-US) -> 1.052033E+003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1, 052033e + 003<br /><br /> -1052.0329112756 ("e2", en-US) -> -1.05e+003<br /><br /> -1052.0329112756 ("E2", fr-FR) -> -1, 05E + 003|  
|„F” lub „f”|Wartość stałoprzecinkowa|Wynik: cyfry całkowite i dziesiętne z opcjonalnym znakiem minus.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr dziesiętnych.<br /><br /> Domyślny Specyfikator dokładności: zdefiniowany przez <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Więcej informacji: [specyfikator formatu stałoprzecinkowego ("F")](#FFormatString).|1234.567 ("F", en US) -> 1234,57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1", en US) -> 1234.0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234.56 ("F4", en US) ->-1234.5600<br /><br /> -1234.56 ("F4", de-DE) -> - 1234,5600|  
|„G” lub „g”|Ogólne|Wynik: Więcej zwartą notację stałoprzecinkową lub naukową.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: liczba cyfr znaczących.<br /><br /> Domyślny specyfikator dokładności: zależy od typu liczbowego.<br /><br /> Więcej informacji: [specyfikator formatu ogólnego ("G")](#GFormatString).|-123.456 ("G", en US) ->-123.456<br /><br /> -123.456 ("G", sv-SE) -> -123,456<br /><br /> 123.4546 ("G4", en-US) -> 123.5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1.234567890e-25 ("G", en-US) -> -1.23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -> -1,23456789E-25|  
|„N” lub „n”|Wartość liczbowa|Wynik: cyfry całkowite i dziesiętne, separatory grup i separator dziesiętny z opcjonalnym znaku minus.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: wymagana liczba miejsc dziesiętnych.<br /><br /> Domyślny Specyfikator dokładności: zdefiniowany przez <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Więcej informacji: [specyfikator formatu liczbowego ("N")](#NFormatString).|1234.567 ("N", en US) -> 1234,57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1", en US) -> 1,234.0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1234.56 ("N3", en US) ->-1,234.560<br /><br /> -1234.56 ("N3", ru-RU) -> 234,560-1|  
|„P” lub „p”|Wartość procentowa|Wynik: liczba pomnożona przez 100 i wyświetlana z symbolem procentu.<br /><br /> Obsługiwany przez: wszystkie typy liczbowe.<br /><br /> Specyfikator dokładności: wymagana liczba miejsc dziesiętnych.<br /><br /> Domyślny Specyfikator dokładności: zdefiniowany przez <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Więcej informacji: [specyfikator formatu procentowego ("P")](#PFormatString).|1 ("P", en US) -> 100.00%<br /><br /> 1 ("P", fr-FR) -> 100,00%<br /><br /> -0.39678 ("P1", en US) ->-39.7%<br /><br /> -0.39678 ("P1", fr-FR) -> - 39,7%|  
|„R” lub „r”|Wartość dwustronna|Wynik: ciąg, który można dwustronnie konwertować na identyczny numer.<br /><br /> Obsługiwane przez: <xref:System.Single>, <xref:System.Double>, i <xref:System.Numerics.BigInteger>.<br /><br /> Uwaga: Zalecane w przypadku <xref:System.Numerics.BigInteger> tylko typu. Aby uzyskać <xref:System.Double> typów, użyj "G17"; w przypadku <xref:System.Single> typów, użyj "G9". </br> Specyfikator dokładności: ignorowany.<br /><br /> Więcej informacji: [("R") specyfikator formatu dwustronnej konwersji](#RFormatString).|123456789.12345678 ("R") -> 123456789.12345678<br /><br /> -1234567890.12345678 ("R") -> -1234567890.1234567|  
|„X” lub „x”|Wartość szesnastkowa|Wynik: ciąg szesnastkowy.<br /><br /> Obsługiwane przez: tylko typy całkowite.<br /><br /> Specyfikator dokładności: liczba cyfr w ciągu wynikowym.<br /><br /> Więcej informacji: [specyfikator formatu szesnastkowego ("X")](#XFormatString).|255 ("X") -> FF<br /><br /> -1 ("x") -> ff<br /><br /> 255 ("x4") -> 00ff<br /><br /> -1 ("X4") -> 00FF|  
|Jakikolwiek inny pojedynczy znak|Nieznany specyfikator|Wynik: Generuje wyjątek <xref:System.FormatException> w czasie wykonywania.||  
  
<a name="Using"></a>   
## <a name="using-standard-numeric-format-strings"></a>Korzystając ze standardowego, numerycznego ciągu formatującego  

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Ciąg standardowego formatu liczb może służyć do definiowania formatowania wartości liczbowej na jeden z dwóch sposobów:  
  
-   Może być przekazywany do przeciążenia `ToString` metody, która ma `format` parametru. Poniższy przykład formatuje wartość numeryczną jako ciąg waluty w bieżącej kultury (w tym przypadku kultury en US).  
  
     [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
     [!code-csharp-interactive[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
     [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]  
  
-   Może być podany jako `formatString` argumentów w elemencie formatu używangoe z takich metod jako <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, i <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md). W poniższym przykładzie element formatu jest używany do wstawienia wartości waluty w ciągu.  
  
     [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
     [!code-csharp-interactive[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
     [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]  
  
     Opcjonalnie możesz podać `alignment` argumentu, aby określić szerokość pola numerycznego i czy jej wartość jest wyrównany do prawej lub lewej strony. Poniższy przykład powoduje wyrównanie po lewej stronie wartości waluty w polu 28-znakowego, a jej prawej wyrównuje wartość waluty w polu 14 znaków.  
  
     [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
     [!code-csharp-interactive[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
     [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]  
  
-   Może być podany jako `formatString` argumentów w elemencie wyrażenie interpolowane w ciągu interpolowanym. Aby uzyskać więcej informacji, zobacz [Interpolacja ciągów](../../csharp/language-reference/tokens/interpolated.md) temat w dokumentacji języka C# lub [ciągi interpolowane](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) tematu w odwołanie w Visual Basic.  
  
 Poniższe sekcje zawierają szczegółowe informacje o poszczególnych ciągach standardowego formatu liczb.  
  
<a name="CFormatString"></a>   
## <a name="the-currency-c-format-specifier"></a>Specyfikator formatu waluty („C”)  
 Specyfikator formatu C (currency) konwertuje liczbę na ciąg przedstawiający kwotę w walucie. Specyfikator dokładności określa żądaną liczbę miejsc dziesiętnych w wynikowym ciągu. W przypadku pominięcia specyfikatora dokładności domyślna dokładność jest definiowana przez <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> właściwości.  
  
 Jeśli wartość do sformatowania ma więcej miejsc dziesiętnych niż określona lub domyślna liczba miejsc dziesiętnych, wartość ułamkowa zostanie zaokrąglona w wynikowym ciągu. Jeśli wartość na prawo od określonej liczby miejsc dziesiętnych wynosi 5 lub więcej, ostatnia cyfra w ciągu wynikowym jest zaokrąglana w kierunku od zera.  
  
 Ciąg wynikowy mają wpływ informacje o formatowaniu bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.NumberFormatInfo> właściwości, które sterują formatowaniem zwracanego ciągu.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|Definiuje położenie symbolu waluty dla wartości dodatnich.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|Definiuje położenie symbolu waluty dla wartości ujemnych i określa, czy znak minus jest reprezentowany przez nawiasy lub <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> właściwości.|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje znak minus używany, jeśli <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> wskazuje, że nawiasy nie są używane.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|Definiuje symbol waluty.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych w wartości waluty. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite i cyfry dziesiętne.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|Definiuje ciąg oddzielający grupy liczb całkowitych.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|Definiuje liczbę cyfr liczby całkowitej, które pojawiają się w grupie.|  
  
 Poniższy przykład formatuje <xref:System.Double> przy użyciu specyfikatora formatu waluty.  
  
 [!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
 [!code-csharp-interactive[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
 [!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]  
  
 [Powrót do tabeli](#table)  
  
<a name="DFormatString"></a>   
## <a name="the-decimal-d-format-specifier"></a>Specyfikator formatu dziesiętnego („D”)  
 Specyfikator formatu D (decimal) konwertuje liczbę na ciąg cyfr dziesiętnych (0–9), poprzedzony znakiem minus, jeśli liczba jest ujemna. Ten format jest obsługiwany tylko w przypadku typów całkowitych.  
  
 Specyfikator dokładności określa minimalną liczbę miejsc dziesiętnych w ciągu wynikowym. Jeśli to konieczne, liczba jest dopełniana zerami po lewej stronie w celu uzyskania liczby cyfr określonej przez specyfikator dokładności. Jeśli nie zostanie określony specyfikator dokładności, wartością domyślną jest wartość minimalna wymagana do przedstawienia wartości całkowitej bez zer wiodących.  
  
 Ciąg wynikowy mają wpływ informacje o formatowaniu bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu. Jak pokazano w poniższej tabeli, jedna właściwość ma wpływ na formatowanie ciągu wynikowego.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|  
  
 Poniższy przykład formatuje <xref:System.Int32> przy użyciu specyfikatora formatu dziesiętnego.  
  
 [!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
 [!code-csharp-interactive[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
 [!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]  
  
 [Powrót do tabeli](#table)  
  
<a name="EFormatString"></a>   
## <a name="the-exponential-e-format-specifier"></a>Specyfikator formatu wykładniczego („E”)  
 Specyfikator formatu wykładniczego („E”) konwertuje liczbę na ciąg w postaci „-d,ddd...E + ddd” lub „-d,ddd...e+ddd”, gdzie każda litera „d” wskazuje cyfrę (0–9). Ciąg rozpoczyna się od znaku minus, jeśli liczba jest ujemna. Zawsze dokładnie jedna cyfra poprzedza punkt dziesiętny.  
  
 Specyfikator dokładności określa żądaną liczbę cyfr po punkcie dziesiętnym. Jeśli specyfikator dokładności zostanie pominięty, domyślnie będzie używanych sześć cyfr po punkcie dziesiętnym.  
  
 Wielkość liter specyfikatora formatu wskazuje, czy wykładnik potęgi ma być poprzedzany prefiksem „E”, czy „e”. Wykładnik zawsze składa się ze znaku plus lub minus i co najmniej trzech cyfr. W razie potrzeby wykładnik jest dopełniany zerami w celu spełnienia tego minimum.  
  
 Ciąg wynikowy mają wpływ informacje o formatowaniu bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.NumberFormatInfo> właściwości, które sterują formatowaniem zwracanego ciągu.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna zarówno dla współczynnika, jak i wykładnika.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Określa ciąg oddzielający cyfry całkowite od cyfr dziesiętnych we współczynniku.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Określa ciąg, który wskazuje, że wykładnik jest dodatni.|  
  
 Poniższy przykład formatuje <xref:System.Double> przy użyciu specyfikatora formatu wykładniczego.  
  
 [!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
 [!code-csharp-interactive[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
 [!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]  
  
 [Powrót do tabeli](#table)  
  
<a name="FFormatString"></a>   
## <a name="the-fixed-point-f-format-specifier"></a>Specyfikator formatu stałoprzecinkowego („F”)  
 Specyfikator formatu stałoprzecinkowego ("F") konwertuje liczbę na ciąg w formie "-CCC..." gdzie każdy "d" oznacza cyfrę (0 – 9). Ciąg rozpoczyna się od znaku minus, jeśli liczba jest ujemna.  
  
 Specyfikator dokładności określa żądaną liczbę miejsc dziesiętnych. Jeśli Specyfikator dokładności zostanie pominięty, bieżące <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> właściwości dostarcza wartość dokładności liczbowej.  
  
 Ciąg wynikowy mają wpływ informacje o formatowaniu bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu. Poniższa tabela zawiera listę właściwości <xref:System.Globalization.NumberFormatInfo> obiektów, które sterują formatowaniem ciągu wynikowego.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite od cyfr dziesiętnych.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|  
  
 Poniższy przykład formatuje <xref:System.Double> i <xref:System.Int32> przy użyciu specyfikatora formatu stałoprzecinkowego.  
  
 [!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
 [!code-csharp-interactive[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
 [!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]  
  
 [Powrót do tabeli](#table)  
  
<a name="GFormatString"></a>   
## <a name="the-general-g-format-specifier"></a>Specyfikator formatu ogólnego („G”)  
 Specyfikator formatu ogólnego ("G") konwertuje liczbę na więcej zwartą notację stałoprzecinkową lub naukową notacji, w zależności od typu liczby i tego, czy jest obecny Specyfikator dokładności. Specyfikator dokładności określa maksymalną liczbę cyfr znaczących, które mogą być wyświetlane w ciągu wynikowym. Jeżeli specyfikator dokładności zostanie pominięty lub będzie równy zero, typ liczby określa dokładność domyślną, tak jak opisano w poniższej tabeli.  
  
|Typ liczbowy|Dokładność domyślna|  
|------------------|-----------------------|  
|<xref:System.Byte> lub <xref:System.SByte>|3 cyfry|  
|<xref:System.Int16> lub <xref:System.UInt16>|5 cyfr|  
|<xref:System.Int32> lub <xref:System.UInt32>|10 cyfr|  
|<xref:System.Int64>|19 cyfr|  
|<xref:System.UInt64>|20 cyfr|  
|<xref:System.Numerics.BigInteger>|Bez ograniczeń (taka sama jak ["R"](#RFormatString))|  
|<xref:System.Single>|7 cyfr|  
|<xref:System.Double>|do 15 cyfr|  
|<xref:System.Decimal>|29 cyfr|  
  
 Notacja stałoprzecinkowa jest używana, jeśli wykładnik, który byłby wynikiem wyrażenia liczby w notacji wykładniczej, jest większy niż -5 i mniejszy niż specyfikator dokładności. W przeciwnym wypadku jest używana notacja wykładnicza. Wynik zawiera punkt dziesiętny, jeśli jest to wymagane, a zera końcowe po punkcie dziesiętnym są pomijane. Jeśli specyfikator dokładności jest obecny i liczba cyfr znaczących w wyniku przekracza określoną dokładność, nadmiarowe cyfry końcowe są usuwane przez zaokrąglenie.  
  
 Jednakże jeśli liczba jest <xref:System.Decimal> i pominięto Specyfikator dokładności, stałoprzecinkowa Notacja jest zawsze używana i końcowe zera zostaną zachowane.  
  
 Jeśli jest używana notacja wykładnicza, wykładnik w wyniku otrzymuje prefiks „E”, jeśli specyfikatorem formatu jest „G”, lub „e”, jeśli specyfikatorem formatu jest „g”. Wykładnik zawiera co najmniej dwie cyfry. Różni się to od formatu notacji wykładniczej tworzonej przez specyfikator formatu wykładniczego, który obejmuje co najmniej trzy cyfry wykładnika.  
 
Należy zauważyć, że gdy jest używane z <xref:System.Double> wartości, specyfikator formatu "G17" zapewnia, że oryginalna <xref:System.Double> wartość pomyślnie rund. Jest to spowodowane <xref:System.Double> jest IEEE 754 2008-CLS podwójnej precyzji (`binary64`) zapewniającej z dokładnością do 17 cyfr znaczących liczbę zmiennoprzecinkową. Zaleca się jej użycie zamiast [specyfikatora formatu "R"](#RFormatString), ponieważ w niektórych przypadkach "R" nie może pomyślnie obustronne podwójnej precyzji wartości zmiennoprzecinkowe. Poniższy przykład ilustruje takiej sytuacji.

[!code-csharp-interactive[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs)]   
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]   

Gdy jest używane z <xref:System.Single> wartości, specyfikator formatu "G9" zapewnia, że oryginalna <xref:System.Single> wartość pomyślnie rund. Jest to spowodowane <xref:System.Single> jest IEEE 754 2008-CLS pojedynczej precyzji (`binary32`) zapewniającej maksymalnie dziewięć cyfr znaczących liczbę zmiennoprzecinkową. Ze względu na wydajność zaleca się jej użycie zamiast [specyfikatora formatu "R"](#RFormatString).

 Ciąg wynikowy mają wpływ informacje o formatowaniu bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.NumberFormatInfo> właściwości, które sterują formatowaniem ciągu wynikowego.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite od cyfr dziesiętnych.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Określa ciąg, który wskazuje, że wykładnik jest dodatni.|  
  
 W poniższym przykładzie różne wartości zmiennoprzecinkowe są formatowane przy użyciu specyfikatora formatu ogólnego.  
  
 [!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
 [!code-csharp-interactive[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
 [!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]  
  
 [Powrót do tabeli](#table)  
  
<a name="NFormatString"></a>   
## <a name="the-numeric-n-format-specifier"></a>Specyfikator formatu numerycznego („N”)  
 Specyfikator formatu liczbowego („N”) konwertuje liczbę na ciąg w postaci „-d ddd ddd,ddd…”, gdzie „-” oznacza w razie potrzeby liczbę ujemną, „d” oznacza cyfrę (0–9), „ ” oznacza separator grupy, a „,” oznacza symbol punktu dziesiętnego. Specyfikator dokładności określa żądaną liczbę cyfr po punkcie dziesiętnym. W przypadku pominięcia specyfikatora dokładności liczba miejsc dziesiętnych jest definiowany przez bieżącą <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> właściwości.  
  
 Ciąg wynikowy mają wpływ informacje o formatowaniu bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.NumberFormatInfo> właściwości, które sterują formatowaniem ciągu wynikowego.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|  
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|Definiuje format wartości ujemnych i określa, czy znak minus jest reprezentowany przez nawiasy lub <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> właściwości.|  
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|Definiuje liczbę cyfr liczby całkowitej, które pojawiają się pomiędzy separatorami grup.|  
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|Definiuje ciąg oddzielający grupy liczb całkowitych.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite i cyfry dziesiętne.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definiuje domyślną liczbę cyfr dziesiętnych. Tę wartość można zastąpić przy użyciu specyfikatora dokładności.|  
  
 W poniższym przykładzie różne wartości zmiennoprzecinkowe są formatowane przy użyciu specyfikatora formatu liczby.  
  
 [!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
 [!code-csharp-interactive[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
 [!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]  
  
 [Powrót do tabeli](#table)  
  
<a name="PFormatString"></a>   
## <a name="the-percent-p-format-specifier"></a>Specyfikator formatu procenta („P”)  
 Specyfikator formatu procentowego („P”) mnoży liczbę przez 100 i konwertuje ją na ciąg, który przedstawia wartość procentową. Specyfikator dokładności określa żądaną liczbę miejsc dziesiętnych. W przypadku pominięcia specyfikatora dokładności domyślna dokładność liczbowa dostarczona przez bieżącą <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> właściwość jest używana.  
  
 W poniższej tabeli wymieniono <xref:System.Globalization.NumberFormatInfo> właściwości, które sterują formatowaniem zwracanego ciągu.  
  
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
 [!code-csharp-interactive[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
 [!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]  
  
 [Powrót do tabeli](#table)  
  
<a name="RFormatString"></a>   
## <a name="the-round-trip-r-format-specifier"></a>Specyfikator formatu obustronnej konwersji („R”)  
 Obustronne specyfikator formatu ("R") próbuje upewnij się, że wartość liczbowa, która jest konwertowana na ciąg jest przetworzona z powrotem na tę samą wartość liczbową. Ten format jest obsługiwany tylko w przypadku <xref:System.Single>, <xref:System.Double>, i <xref:System.Numerics.BigInteger> typów.  

Aby uzyskać <xref:System.Double> wartości, specyfikator formatu "R" w niektórych przypadkach nie może pomyślnie obustronne oryginalną wartość. Dla obu <xref:System.Double> i <xref:System.Single> wartości, zapewnia ona również stosunkowo niska wydajność. Zamiast tego zaleca się używanie ["G17"](#GFormatString) specyfikatora dla formatu <xref:System.Double> wartości i ["G9"](#GFormatString) specyfikatora, aby pomyślnie obustronne formatu <xref:System.Single> wartości.

 Gdy <xref:System.Numerics.BigInteger> wartość jest formatowana przy użyciu tego specyfikatora, reprezentujący ją ciąg zawiera wszystkie znaczące cyfry w <xref:System.Numerics.BigInteger> wartość.  
  
 Można dodawać specyfikator dokładności, ale jest on ignorowany. W przypadku korzystania z tego specyfikatora konwersje dwustronne mają pierwszeństwo przed dokładnością.    
 Ciąg wynikowy mają wpływ informacje o formatowaniu bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu. W poniższej tabeli wymieniono <xref:System.Globalization.NumberFormatInfo> właściwości, które sterują formatowaniem ciągu wynikowego.  
  
|Właściwość NumberFormatInfo|Opis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definiuje ciąg, który wskazuje, że liczba jest ujemna.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definiuje ciąg oddzielający cyfry całkowite od cyfr dziesiętnych.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Określa ciąg, który wskazuje, że wykładnik jest dodatni.|  
  
 Poniższy przykład formatuje <xref:System.Numerics.BigInteger> przy użyciu specyfikatora formatu Rundy.  
  
 [!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
 [!code-csharp-interactive[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
 [!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]  
  
> [!IMPORTANT]
>  W niektórych przypadkach <xref:System.Double> wartości sformatowane przy użyciu nie pomyślnie obustronne czy ciąg standardowego formatu liczb "R", gdy skompilowano przy użyciu `/platform:x64` lub `/platform:anycpu` przełączników i działają na 64-bitowym. Zobacz następujący akapit, aby uzyskać więcej informacji.  
  
 Aby obejść ten problem z <xref:System.Double> wartości sformatowane przy użyciu standardowego formatu liczb "R" ciągu nie zostało pomyślnie Pełna zgodnooć wersji, gdy skompilowano przy użyciu `/platform:x64` lub `/platform:anycpu` przełączników i wykonywania w systemach 64-bitowych. możesz sformatować <xref:System.Double> wartości przy użyciu ciągu standardowego formatu liczb "G17". W poniższym przykładzie użyto ciągu formatu "R", przy użyciu <xref:System.Double> wartość, która nie obustronne nie pomyślnie i również używa "G17" format ciąg, który ma pomyślnie obustronne oryginalną wartość.  
  
 [!code-csharp-interactive[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#5)]
 [!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]  
  
 [Powrót do tabeli](#table)  
  
<a name="XFormatString"></a>   
## <a name="the-hexadecimal-x-format-specifier"></a>Specyfikator formatu szesnastkowego („X”)  
 Specyfikator formatu szesnastkowego („X”) konwertuje liczbę na ciąg cyfr szesnastkowych. Wielkość liter specyfikatora formatu wskazuje, czy w przypadku cyfr szesnastkowych, które są większe niż 9, należy używać wielkich, czy małych liter. Na przykład użycie specyfikatora „X” umożliwia uzyskanie cyfr „ABCDEF”, a specyfikatora „x” — cyfr „abcdef”. Ten format jest obsługiwany tylko w przypadku typów całkowitych.  
  
 Specyfikator dokładności określa minimalną liczbę miejsc dziesiętnych w ciągu wynikowym. Jeśli to konieczne, liczba jest dopełniana zerami po lewej stronie w celu uzyskania liczby cyfr określonej przez specyfikator dokładności.  
  
 Informacje o formatowaniu bieżącego nie są stosowane do ciągu wynikowego <xref:System.Globalization.NumberFormatInfo> obiektu.  
  
 Poniższy przykład formatuje <xref:System.Int32> specyfikatora formatu wartości szesnastkowych.  
  
 [!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
 [!code-csharp-interactive[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
 [!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]  
  
 [Powrót do tabeli](#table)  
  
<a name="NotesStandardFormatting"></a>   
## <a name="notes"></a>Uwagi  
  
### <a name="control-panel-settings"></a>Ustawienia panelu sterowania  
 Ustawienia w **Opcje regionalne i językowe** elementu w Panelu sterowania wpływają na ciągi wynikowe generowane przez operację formatowania. Te ustawienia są stosowane do inicjalizacji <xref:System.Globalization.NumberFormatInfo> obiekt skojarzony z bieżącą kulturą wątku, która zapewnia wartości stosowane do zarządzania formatowaniem. Na komputerach, na których są używane różne ustawienia, są generowane różne ciągi wynikowe.  
  
 Ponadto jeśli <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> Konstruktor jest używany do tworzenia wystąpienia nowego <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje tę samą kulturę co bieżąca kultura systemu, wszelkie dostosowania ustanowione przez **Opcje regionalne i językowe** w Panelu sterowania zostaną zastosowane do nowego <xref:System.Globalization.CultureInfo> obiektu. Możesz użyć <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Konstruktor do tworzenia <xref:System.Globalization.CultureInfo> obiektu, który nie będzie odzwierciedlał dostosowań systemu.  
  
### <a name="numberformatinfo-properties"></a>Właściwości klasy NumberFormatInfo  
 Formatowanie mają wpływ właściwości bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu, dostarczane niejawnie przez bieżącą kulturę wątku lub jawnie przez <xref:System.IFormatProvider> parametru metody, która wywołuje formatowanie. Określ <xref:System.Globalization.NumberFormatInfo> lub <xref:System.Globalization.CultureInfo> obiektu dla tego parametru.  
  
> [!NOTE]
>  Aby uzyskać informacje na temat dostosowywania wzorców lub ciągów używanych w formatowaniu wartości numerycznych, zobacz <xref:System.Globalization.NumberFormatInfo> temat poświęcony klasie.  
  
### <a name="integral-and-floating-point-numeric-types"></a>Całkowite i zmiennoprzecinkowe rodzaje wartości numerycznych  
 Niektóre opisy specyfikatorów standardowego formatu liczb odnoszą się do całkowitych lub zmiennoprzecinkowych typów liczbowych. Całkowite typy liczbowe to <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, i <xref:System.Numerics.BigInteger>. Zmiennoprzecinkowe typy liczbowe to <xref:System.Decimal>, <xref:System.Single>, i <xref:System.Double>.  
  
### <a name="floating-point-infinities-and-nan"></a>Zmiennoprzecinkowe nieskończoności i NaN  
 Bez względu na ciąg formatu Jeśli wartość <xref:System.Single> lub <xref:System.Double> typu zmiennoprzecinkowego jest nieskończoności dodatniej, minus nieskończonością lub nie jest liczbą (NaN), sformatowany ciąg ma wartość omawianych <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>, <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>, lub <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> właściwość, która jest określona przez stosowany obecnie <xref:System.Globalization.NumberFormatInfo> obiektu.  
  
## <a name="example"></a>Przykład  
 
[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]
 
 W poniższym przykładzie całkowita i zmiennoprzecinkowa wartość liczbowa jest formatowana przy użyciu kultury en-US i wszystkich specyfikatorów standardowego formatu liczb. W tym przykładzie użyto określone typy liczbowe (<xref:System.Double> i <xref:System.Int32>), ale wyniki byłyby podobne jakichkolwiek innych typów podstawowych (<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Numerics.BigInteger>, <xref:System.Decimal>, i <xref:System.Single>).  
  
 [!code-csharp-interactive[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#1)]
 [!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Globalization.NumberFormatInfo>  
 [Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
 [Instrukcje: Uzupełnianie liczby zerami wiodącymi](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)  
 [Przykład: .NET Framework 4 formatowanie narzędzia](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)  
 [Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)
