---
title: Niestandardowe ciągi formatujące liczby
ms.date: 06/25/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- format strings
- custom numeric format strings
- numbers [.NET Framework], formatting
- format specifiers, numeric
- formatting numbers [.NET Framework]
- format specifiers, custom numeric format strings
ms.assetid: 6f74fd32-6c6b-48ed-8241-3c2b86dea5f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b9cf18c4893b618d16ef24bab83a19154e19a9c
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106531"
---
# <a name="custom-numeric-format-strings"></a>Niestandardowe ciągi formatujące liczby

Można utworzyć ciąg niestandardowego formatu liczb, który składa się z jednego lub większej liczby niestandardowych specyfikatorów liczbowych, aby zdefiniować sposób formatowania danych liczbowych. Ciąg niestandardowego formatu liczbowego jest dowolny ciąg formatu, który nie jest [ciągu standardowego formatu liczbowego](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  

 Niestandardowe ciągi formatujące liczby obsługiwanych przez niektóre przeciążeń `ToString` metody wszystkie typy liczbowe. Na przykład można podać ciąg formatu liczbowego <xref:System.Int32.ToString%28System.String%29> i <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29> metody <xref:System.Int32> typu. Niestandardowe ciągi formatujące liczby są również obsługiwane przez .NET [złożonych funkcji formatowania](../../../docs/standard/base-types/composite-formatting.md), który jest używany przez niektóre `Write` i `WriteLine` metody <xref:System.Console> i <xref:System.IO.StreamWriter> klasy <xref:System.String.Format%2A?displayProperty=nameWithType>metody i <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> metody. [Ciąg interpolacji](../../csharp/language-reference/tokens/interpolated.md) funkcji obsługuje również niestandardowe ciągi formatujące liczby.  
  
> [!TIP]
>  Możesz pobrać [formatowania narzędzie](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)ciągi aplikacji, która umożliwia zastosowanie formatu liczbowego lub daty i czasu wartości i wyświetla ciąg wyniku.  
  
<a name="table"></a> Poniższa tabela opisuje specyfikatory niestandardowego formatu liczbowego i wyświetla przykładowe dane wyjściowe generowane przez każdego specyfikator formatu. Zobacz [uwagi](#NotesCustomFormatting) sekcji, aby uzyskać dodatkowe informacje o używaniu niestandardowe ciągi formatujące liczby i [przykład](#example) sekcji ilustracyjną kompleksowe ich użycia.  
  
|Specyfikator formatu|Nazwa|Opis|Przykłady|  
|----------------------|----------|-----------------|--------------|  
|„0”|Symbol zastępczy zero|Zamienia zero na odpowiednią cyfrę, jeżeli jest ona obecna. W przeciwnym wypadku zero występuje w ciągu wynikowym.<br /><br /> Więcej informacji: ["0" specyfikator niestandardowe](#Specifier0).|1234.5678 ("00000") -> 01235<br /><br /> 0.46 -> 0.45678 ("0,00" en US)<br /><br /> 0,46 -> 0.45678 ("0,00", fr-FR)|  
|"#"|Symbol zastępczy cyfry|Zamienia symbol „#” na odpowiednią cyfrę, jeżeli jest ona obecna. W przeciwnym wypadku żadna cyfra nie występuje w ciągu wynikowym.<br /><br /> Należy zauważyć, że nie cyfrę pojawia się w ciągu wynik Jeśli odpowiedni cyfr w ciągu wejściowym jest 0 znaczące. Na przykład 0003 ("###") -> 3.<br /><br /> Więcej informacji: ["#" specyfikator niestandardowe](#SpecifierD).|1234.5678 ("#####") -> 1235<br /><br /> 0.45678 ("#. ##", en US) ->.46<br /><br /> 0.45678 ("#. ##", fr-FR) -> 46|  
|"."|Punkt dziesiętny|Określa lokalizację separatora dziesiętnego w ciągu wynikowym.<br /><br /> Więcej informacji: ["." Specyfikator niestandardowych](#SpecifierPt).|0.46 -> 0.45678 ("0,00" en US)<br /><br /> 0,46 -> 0.45678 ("0,00", fr-FR)|  
|","|Separator grup i skalowania liczby|Jest używany zarówno jako separator grup, jak i specyfikator skalowania liczby. Jako separator grup wstawia zlokalizowany znak separatora grup między grupami. Jako specyfikator skalowania liczb dzieli liczbę przez 1000 dla każdej liczby z określonym przecinkiem.<br /><br /> Więcej informacji: ["," specyfikator niestandardowe](#SpecifierTh).|Specyfikator separatora grup:<br /><br /> 2147483647 ("##, #", en US) -> 2 147 483 647<br /><br /> 2147483647 ("##,#", es-ES) -> 2.147.483.647<br /><br /> Specyfikator skalowania:<br /><br /> 2147483647 ("#, #,", en US) -> 2 147<br /><br /> 2.147 -> 2147483647 ("#, #,", es-ES)|  
|"%"|Symbol zastępczy procentu|Mnoży liczbę przez 100 i wstawia zlokalizowany symbol procentu do ciągu wynikowego.<br /><br /> Więcej informacji: ["%" specyfikator niestandardowe](#SpecifierPct).|0.3697 ("% #0.00" en US) -> % 36.97<br /><br /> 0.3697 ("% #0.00" el-GR) -> % 36,97<br /><br /> 0.3697 ("% ##.0," pl pl) -> 37.0%<br /><br /> 0.3697 ("% ##.0", el GR) -> 37,0%|  
|"‰"|Symbol zastępczy promil|Mnoży liczbę przez 1000 i wstawia zlokalizowany symbol promila do ciągu wynikowego.<br /><br /> Więcej informacji: ["‰" specyfikator niestandardowe](#SpecifierPerMille).|0.03697 ("#0.00‰," pl pl) -> 36.97‰<br /><br /> 0.03697 ("#0.00‰", ru-RU) -> 36 97‰|  
|„E0”<br /><br /> „E+0”<br /><br /> „E-0”<br /><br /> „e0”<br /><br /> „e+0”<br /><br /> „e-0”|Notacja wykładnicza|Jeżeli występuje po nim przynajmniej jedno 0 (zero), formatuje wynik za pomocą notacji wykładniczej. Wielkość litery „E” lub „e” wskazuje wielkość symbolu wykładnika w ciągu wynikowym. Liczba zer po znaku „E” lub „e” określa minimalną liczbę cyfr wykładnika. Znak plus (+) wskazuje, że znak zawsze poprzedza wykładnik potęgi. Znak minus (-) wskazuje, że znak poprzedza tylko ujemny wykładnik potęgi.<br /><br /> Więcej informacji: ["E" i "e" specyfikatory niestandardowe](#SpecifierExponent).|987654 ("#0.0e0") -> 98.8e4<br /><br /> 1503.92311 ("0.0##e+00") -> 1.504e+03<br /><br /> 1.8901385E-16 ("0.0e+00") -> 1.9e-16|  
|"\\"|Znak ucieczki|Powoduje, że następny znak należy interpretować jako literał, a nie jako specyfikator formatu niestandardowego.<br /><br /> Więcej informacji: ["\\" znak zmiany znaczenia](#SpecifierEscape).|987654 ("\\###00\\#") -> #987654#|  
|"*ciąg*"<br /><br /> "*ciąg*"|Ogranicznik ciągu literału|Wskazuje, że znaki w cudzysłowie powinny zostać skopiowane do ciągu wynikowego bez zmian.<br/><br/>Więcej informacji: [znak literały](#character-literals).|68 ("#" stopni"") -> 68 stopni<br /><br /> 68 ("#" stopni ") -> 68 stopni|  
|;|Separator sekcji|Definiuje sekcje z oddzielnymi ciągami formatu dla liczb dodatnich, ujemnych i dla zera.<br /><br /> Więcej informacji: [";" Separator sekcji](#SectionSeparator).|12.345 ("#0.0#;(#0.0#);-\0-") -> 12.35<br /><br /> 0 ("#0.0#;(#0.0#);-\0-") -> -0-<br /><br /> -12.345 ("#0.0#;(#0.0#);-\0-") -> (12.35)<br /><br /> 12.345 ("#0.0#;(#0.0#)") -> 12.35<br /><br /> 0 ("#0.0#;(#0.0#)") -> 0.0<br /><br /> -12.345 ("#0.0#;(#0.0#)") -> (12.35)|  
|Inne|Wszystkie inne znaki|Znak jest kopiowany do ciągu wynikowego bez zmian.<br/><br/>Więcej informacji: [znak literały](#character-literals).|68 ("# °") -> 68 °|  
  
 W poniższych sekcjach znajdują się szczegółowe informacje o poszczególnych niestandardowych specyfikatorach formatu liczb.  

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-culture-note.md)] 
  
<a name="Specifier0"></a>   
## <a name="the-0-custom-specifier"></a>"0" specyfikator niestandardowych  
 Niestandardowy specyfikator formatu „0” pełni rolę symbolu zastępczego zera. Jeżeli formatowana wartość zawiera cyfrę w miejscu, w którym w ciągu formatu występuje zero, ta cyfra jest kopiowana do ciągu wynikowego. W innym przypadku w ciągu wynikowym występuje zero. Położenie zera znajdującego się najdalej po lewej stronie od punktu dziesiętnego i położenie zera znajdującego się najdalej po prawej stronie od punktu dziesiętnego określa zakres cyfr, które są zawsze obecne w ciągu wynikowym.  
  
 Specyfikator „00” powoduje, że wartość zostaje zaokrąglona do najbliższej cyfry poprzedzającej miejsce dziesiętne, gdzie używane jest zawsze zaokrąglanie od zera. Na przykład wynikiem formatowania liczby 34,5 z pomocą specyfikatora „00” byłaby wartość 35.  
  
 W poniższym przykładzie pokazano kilka wartości formatowanych za pomocą ciągów formatu niestandardowego, które zawierają symbole zastępcze zera.  
  
 [!code-cpp[Formatting.Numeric.Custom#1](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#1)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#1)]
 [!code-vb[Formatting.Numeric.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#1)]  
  
 [Powrót do tabeli](#table)  
  
<a name="SpecifierD"></a>   
## <a name="the--custom-specifier"></a>Specyfikator niestandardowe "#"  
 Niestandardowy specyfikator formatu „#” służy jako symbol zastępczy cyfry. Jeżeli formatowana wartość zawiera cyfrę w miejscu, w którym w ciągu formatu znajduje się symbol „#”, ta cyfra jest kopiowana do ciągu wynikowego. W przeciwnym wypadku nic nie jest umieszczane w tym miejscu w ciągu wynikowym.  
  
 Należy zauważyć, że ten specyfikator nigdy nie wyświetla zera niebędącego cyfrą znaczącą, nawet jeśli zero jest jedyną cyfrą w ciągu. Zero zostanie wyświetlone tylko wtedy, gdy jest cyfrą znaczącą w wyświetlanej liczbie.  
  
 Ciąg formatu „##” powoduje, że wartość zostaje zaokrąglona do najbliższej cyfry poprzedzającej miejsce dziesiętne, gdzie używane jest zawsze zaokrąglanie od zera. Na przykład wynikiem formatowania liczby 34,5 za pomocą specyfikatora „##” byłaby wartość 35.  
  
 W poniższym przykładzie pokazano kilka wartości formatowanych za pomocą ciągów formatu niestandardowego, które zawierają symbole zastępcze cyfr.  
  
 [!code-cpp[Formatting.Numeric.Custom#2](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#2)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#2)]
 [!code-vb[Formatting.Numeric.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#2)]  
  
 Aby zwrócony ciąg wyniku w którym brak cyfry lub zera wiodące są zastępowane przez spacje, użyj [złożonych funkcji formatowania](../../../docs/standard/base-types/composite-formatting.md) i określić szerokość pola, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[Formatting.Numeric.Custom#12](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/SpaceOrDigit1.cpp#12)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/SpaceOrDigit1.cs#12)]
 [!code-vb[Formatting.Numeric.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/SpaceOrDigit1.vb#12)]  
  
 [Powrót do tabeli](#table)  
  
<a name="SpecifierPt"></a>   
## <a name="the--custom-specifier"></a>"." Specyfikator niestandardowych  
 Niestandardowy specyfikator formatu „.” wstawia zlokalizowany separator dziesiętny do ciągu wynikowego. Pierwszy kropka w ciągu formatu określa lokalizację separatora dziesiętnego w sformatowanej wartości. Wszelkie dodatkowe kropki są ignorowane.  
  
 Znak używany jako separator dziesiętny w ciągu wynik nie zawsze jest okres; jest określany przez <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> właściwość <xref:System.Globalization.NumberFormatInfo> obiekt, który kontroluje formatowania.  
  
 W poniższym przykładzie użyto specyfikatora formatu „.” aby zdefiniować lokalizację punktu dziesiętnego w kilku ciągach wynikowych.  
  
 [!code-cpp[Formatting.Numeric.Custom#3](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#3)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#3)]
 [!code-vb[Formatting.Numeric.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#3)]  
  
 [Powrót do tabeli](#table)  
  
<a name="SpecifierTh"></a>   
## <a name="the--custom-specifier"></a>Specyfikator niestandardowe ""  
 Znak „,” jest używany zarówno jako separator grup, jak i specyfikator skalowania liczb.  
  
-   Separator grup: jeśli jeden lub więcej przecinków jest określonych między dwoma symbolami zastępczymi cyfr (0 lub #), które formatują całkowite cyfry danej liczby, znak separatora grupy jest wstawiany między poszczególne grupy liczby w całkowitej części wyniku.  
  
     <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A> i <xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A> właściwości bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu określić znak używany jako separatora liczb grupy, a rozmiar każdej grupy numerów. Na przykład jeśli ciąg „#,#” i niezmienna kultura są użyte do formatowania liczby 1000, wynikiem będzie „1 000”.  
  
-   Specyfikator skalowania liczb: jeśli jeden lub większa liczba przecinków jest określonych natychmiast z lewej strony jawnego lub niejawnego punktu dziesiętnego, formatowana liczba jest dzielona przez 1000 dla każdego przecinka. Na przykład jeśli ciąg „0,,” jest używany do formatowania liczby 100 milionów, wynikiem jest „100”.  
  
 Specyfikatorów skalowania liczb i separatorów grup można użyć w tym samym ciągu formatu. Na przykład jeśli ciąg „#,0,,” i niezmienna kultura są używane do formatowania liczby jeden miliard, wynikiem jest „1 000”.  
  
 W poniższym przykładzie pokazano użycie przecinka jako separatora grup.  
  
 [!code-cpp[Formatting.Numeric.Custom#4](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#4)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#4)]
 [!code-vb[Formatting.Numeric.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#4)]  
  
 W poniższym przykładzie pokazano użycie przecinka jako specyfikatora skalowania liczb.  
  
 [!code-cpp[Formatting.Numeric.Custom#5](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#5)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#5)]
 [!code-vb[Formatting.Numeric.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#5)]  
  
 [Powrót do tabeli](#table)  
  
<a name="SpecifierPct"></a>   
## <a name="the--custom-specifier"></a>Specyfikator niestandardowej "%"  
 Znak procentu (%) w ciągu formatu powoduje pomnożenie liczby przez 100 przed formatowaniem. Zlokalizowany symbol procentu jest wstawiany do liczby, w lokalizacji, na której znak % znajduje się w ciągu formatu. Użyć znaku procentu jest definiowana za pomocą <xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A> właściwości bieżącego <xref:System.Globalization.NumberFormatInfo> obiektu.  
  
 W poniższym przykładzie zdefiniowano kilka ciągów formatu niestandardowego, które zawierają niestandardowy specyfikator „%”.  
  
 [!code-cpp[Formatting.Numeric.Custom#6](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#6)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#6)]
 [!code-vb[Formatting.Numeric.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#6)]  
  
 [Powrót do tabeli](#table)  
  
<a name="SpecifierPerMille"></a>   
## <a name="the--custom-specifier"></a>Specyfikator niestandardowe "‰"  
 Znak promila (‰ lub \u2030) w ciągu formatu powoduje pomnożenie liczby przez 1000 przed formatowaniem. Odpowiedni symbol promila jest wstawiony w zwracanym ciągu w lokalizacji, w której symbol ‰ pojawia się w ciągu formatu. Na mille znak używany jest definiowana za pomocą <xref:System.Globalization.NumberFormatInfo.PerMilleSymbol%2A?displayProperty=nameWithType> właściwość obiektu, który zawiera informacje dotyczące formatowania specyficzne dla kultury.  
  
 W poniższym przykładzie zdefiniowano ciąg formatu niestandardowego, który zawiera niestandardowy specyfikator „‰”.  
  
 [!code-cpp[Formatting.Numeric.Custom#9](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#9)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#9)]
 [!code-vb[Formatting.Numeric.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#9)]  
  
 [Powrót do tabeli](#table)  
  
<a name="SpecifierExponent"></a>   
## <a name="the-e-and-e-custom-specifiers"></a>Specyfikatory niestandardowe "E" i "e"  
 Jeśli którykolwiek z ciągów „E”, „E+”, „E-”, „e”, „e+” lub „e-” jest obecny w ciągu formatu i natychmiast po nim następuje co najmniej jedno zero, liczba jest formatowana przy użyciu notacji wykładniczej z symbolem „E” lub „e” wstawionym między liczbą a wykładnikiem potęgi. Liczba zer po wskaźniku notacji wykładniczej określa minimalną liczbę cyfr wykładnika potęgi. Formaty „E+” i „e+” wskazują, że znak plus lub znak minus powinien zawsze poprzedzać wykładnik potęgi. Formaty „E”, „E-”, „e” i „e-” wskazują, że znak powinien poprzedzać tylko ujemne wykładniki potęgi.  
  
 W poniższym przykładzie sformatowano kilka wartości liczbowych przy użyciu specyfikatorów notacji wykładniczej.  
  
 [!code-cpp[Formatting.Numeric.Custom#7](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#7)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#7)]
 [!code-vb[Formatting.Numeric.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#7)]  
  
 [Powrót do tabeli](#table)  
  
<a name="SpecifierEscape"></a>   
## <a name="the--escape-character"></a>"\\" Znak ucieczki  
 Symbole „#”, „0”, „.”, „,”, „%” i „‰” w ciągu formatu są interpretowane jako specyfikatory formatu, a nie jako znaki literału. W zależności od ich pozycji w ciągu formatu niestandardowego, wielkie i małe litery „E” oraz symbole + i - także mogą być interpretowane jako specyfikatory formatu.  
  
 Aby zapobiec interpretacji znaku jako specyfikatora formatu, można poprzedzić go ukośnikiem odwrotnym, który jest znakiem ucieczki. Znak ucieczki oznacza, że następnym znakiem jest znak literału, który należy bez zmian umieścić w ciągu wynikowym.  
  
 Aby dołączyć ciąg wyniku ukośnik odwrotny, musi escape go z innym ukośnik odwrotny (`\\`).  
  
> [!NOTE]
>  Niektóre kompilatory, takie jak kompilatory języków C++ i C#, mogą również interpretować pojedynczy ukośnik odwrotny jako znak ucieczki. Aby zapewnić poprawną interpretację ciągu podczas formatowania, można użyć dosłownego znaku literału ciągu (znaku @) przed ciągiem w języku C# lub dodać inny znak ukośnika odwrotnego przed każdym ukośnikiem odwrotnym w ciągu w językach C# i C++. W poniższym przykładzie dla języka C# pokazano oba podejścia.  
  
 W poniższym przykładzie użyto znaku ucieczki do formatowania operacja interpretowanie "#", "0" i "\\" znaków jako znaki specjalne lub specyfikatory formatu. W przykładach w języku C# są używane dodatkowe ukośniki odwrotne w celu zagwarantowania, że ukośnik odwrotny będzie interpretowany jako znak literału.  
  
 [!code-cpp[Formatting.Numeric.Custom#11](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/escape1.cpp#11)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/escape1.cs#11)]
 [!code-vb[Formatting.Numeric.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/escape1.vb#11)]  
  
 [Powrót do tabeli](#table)  
  
<a name="SectionSeparator"></a>   
## <a name="the--section-separator"></a>Separator sekcji ";"  
 Średnik (;) jest warunkowym specyfikatorem formatu, który stosuje do liczby różne formatowania, w zależności od tego, czy wartość jest dodatnia, ujemna, czy równa zero. Aby utworzyć takie zachowanie, ciąg formatu niestandardowego może zawierać maksymalnie trzy sekcje rozdzielone średnikami. Te sekcje opisano w poniższej tabeli.  
  
|Liczba sekcji|Opis|  
|------------------------|-----------------|  
|Jedna sekcja|Ciąg formatu jest stosowany do wszystkich wartości.|  
|Dwie sekcje|Pierwsza sekcja jest stosowana do wartości dodatnich i zer, a druga sekcja do wartości ujemnych.<br /><br /> Jeżeli formatowana liczba jest ujemna, ale staje się zerem po zaokrągleniu zgodnym z formatem w drugiej sekcji, wynikowa wartość zero jest formatowana zgodnie z pierwszą sekcją.|  
|Trzy sekcje|Pierwsza sekcja jest stosowana do wartości dodatnich, druga sekcja jest stosowana do wartości ujemnych, a trzecia sekcja jest stosowana do zer.<br /><br /> Druga sekcja może być pozostawiona pusta (nic nie znajduje się między średnikami); w takim przypadku pierwsza sekcja jest stosowana do wszystkich wartości niezerowych.<br /><br /> Jeżeli formatowana liczba jest niezerowa, ale staje się zerem po zaokrągleniu zgodnym z formatem w pierwszej lub drugiej sekcji, wynikowa wartość zero jest formatowana zgodnie z trzecią sekcją.|  
  
 Separatory sekcji ignorują wszelkie istniejące wcześniej formatowanie skojarzone z liczbą podczas formatowania wartości końcowej. Na przykład wartości ujemne są zawsze wyświetlane bez znaku minus, gdy używane są separatory sekcji. Jeśli końcowa sformatowana wartość ma mieć znak minus, należy jawnie dołączyć znak minus jako część niestandardowego specyfikatora formatu.  
  
 W poniższym przykładzie użyto specyfikatora formatu „;”, aby inaczej formatować liczby dodatnie, ujemne i zera.  
  
 [!code-cpp[Formatting.Numeric.Custom#8](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#8)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#8)]
 [!code-vb[Formatting.Numeric.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#8)]  
  
 [Powrót do tabeli](#table)  

## <a name="character-literals"></a>Literały znaków  
 
Specyfikatory formatu, które są widoczne w ciąg niestandardowego formatu liczbowego zawsze będą interpretowane jako formatowanie znaków i nigdy nie jako literał znaków. Obejmuje to następujące znaki:  

- [0](#Specifier0)
- [\#](#SpecifierD)
- [%](#SpecifierPct)
- [‰](#SpecifierPerMille)
- '
- [\\](#SpecifierEscape)
- [.](#SpecifierPt)
- [,](#SpecifierTh)
- [E lub e](#SpecifierExponent), w zależności od jej położenie w ciągu formatu.

Wszystkie inne znaki są zawsze interpretowane jako literały znaków, a w ramach operacji formatowania, znajdują się w ciągu wyniku bez zmian.  W ramach operacji analizy muszą one odpowiadać znaków w ciągu wejściowym dokładnie; porównanie jest rozróżniana wielkość liter.  
  
Poniższy przykład przedstawia jeden użycia dosłownego znaku jednostki (w tym przypadku tysięcy):
  
 [!code-csharp-interactive[literal characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/literal2.cs#1)]
 [!code-vb[literal characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/literal2.vb#1)]  
  
 Istnieją dwa sposoby, aby wskazać, czy znaki są interpretowane jako literał znaków i nie jak formatowanie znaków, tak aby może być uwzględniona w parametrach wynik lub pomyślnie przeanalizowano w ciągu wejściowym:  
  
- Przez anulowanie formatowania znaków. Aby uzyskać więcej informacji, zobacz ["\\" znak ucieczki](#SpecifierEscape).
  
- Umieszczając cały ciąg literału w apostrofy oferty.

W poniższym przykładzie użyto obu podejść, aby uwzględnić zarezerwowanych znaków w ciągu niestandardowego formatu liczbowego.  
  
     [!code-csharp-interactive[including reserved characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/literal1.cs#1)]
     [!code-vb[including reserved characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/literal1.vb#1)]  
    
<a name="NotesCustomFormatting"></a>   
## <a name="notes"></a>Uwagi  
  
### <a name="floating-point-infinities-and-nan"></a>Zmiennoprzecinkowe infinities i NaN  
 Niezależnie od ciąg formatu Jeśli wartość <xref:System.Single> lub <xref:System.Double> typ zmiennoprzecinkowy nieskończoności dodatniej, nieskończoności ujemnej lub niebędące liczbą (NaN), sformatowanego ciągu jest wartością odpowiednio <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>, <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>, lub <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> właściwości określone przez stosowane obecnie <xref:System.Globalization.NumberFormatInfo> obiektu.  
  
### <a name="control-panel-settings"></a>Ustawienia Panelu sterowania  
 Ustawienia w **Opcje regionalne i językowe** elementu w Panelu sterowania wpływ ciąg wyniku utworzone przez operację formatowania. Te ustawienia są używane do zainicjowania <xref:System.Globalization.NumberFormatInfo> obiekt skojarzony z bieżącej kultury wątku i udostępnia wartości używane do sterowania formatowania w bieżącej kultury wątku. Na komputerach, na których są używane różne ustawienia, są generowane różne ciągi wynikowe.  
  
 Ponadto, jeśli używasz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> konstruktora, aby utworzyć obiekt klasy <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje tego samego kultury bieżącej kultury systemu, wszelkie dostosowania ustala **Opcje regionalne i językowe** w Panelu sterowania zostaną zastosowane do nowego <xref:System.Globalization.CultureInfo> obiektu. Można użyć <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktora w celu utworzenia <xref:System.Globalization.CultureInfo> obiekt, który nie odzwierciedla dostosowania systemu.  
  
### <a name="rounding-and-fixed-point-format-strings"></a>Ciągi formatujące zaokrąglania i Stałoprzecinkowym  
 Dla ciągów formatu stałoprzecinkowego (czyli ciągów formatu, które nie zawierają znaków formatu notacji wykładniczej) liczby są zaokrąglane do tylu miejsc dziesiętnych, ile jest symboli zastępczych cyfr po prawej stronie punktu dziesiętnego. Jeśli ciąg formatu nie zawiera punktu dziesiętnego, liczba jest zaokrąglana do najbliższej liczby całkowitej. Jeśli liczba ma więcej cyfr niż jest symboli zastępczych cyfr po lewej stronie punktu dziesiętnego, to dodatkowe cyfry są kopiowane do ciągu wynikowego bezpośrednio przed pierwszym symbolem zastępczym cyfry.  
  
 [Powrót do tabeli](#table)  
  
<a name="example"></a>   
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano dwa ciągi niestandardowego formatu liczb. W obu przypadkach symbol zastępczy cyfry (`#`) wyświetla dane numeryczne i wszystkie inne znaki są kopiowane do ciągu wynik.  
  
 [!code-cpp[Formatting.Numeric.Custom#10](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/example1.cpp#10)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/example1.cs#10)]
 [!code-vb[Formatting.Numeric.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/example1.vb#10)]  
  
 [Powrót do tabeli](#table)  
  
## <a name="see-also"></a>Zobacz także  
 <xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>  
 [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
 [Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [Instrukcje: Uzupełnianie liczby zerami wiodącymi](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)  
 [Przykład: .NET Framework 4 formatowania narzędzia](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
