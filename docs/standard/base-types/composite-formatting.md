---
title: Złożone formatowanie
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parameter specifiers
- strings [.NET Framework], alignment
- format specifiers, composite formatting
- strings [.NET Framework], composite
- composite formatting
- objects [.NET Framework], formatting multiple objects
ms.assetid: 87b7d528-73f6-43c6-b71a-f23043039a49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17ec17d3b90dc7248d1497be1f7d31a324ad10b2
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070972"
---
# <a name="composite-formatting"></a>Złożone formatowanie
Funkcja formatowania złożonego .NET przyjmuje listę obiektów i ciąg formatu złożonego jako dane wejściowe. Ciąg formatu złożonego składa się ze stałego tekstu zmieszanego z indeksowanymi symbolami zastępczymi (nazywanymi też elementami formatu), które odpowiadają obiektom na liście. Operacja formatowania zwraca ciąg wynikowy, który składa się z oryginalnego stałego tekstu zmieszanego z ciągiem reprezentującym obiekty na liście.  
  
 Funkcja formatowania złożonego jest obsługiwana przez metody, takie jak:  
  
-   <xref:System.String.Format%2A?displayProperty=nameWithType>, która zwraca sformatowany ciąg wynikowy.  
  
-   <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, która dołącza sformatowany ciąg wynikowy do <xref:System.Text.StringBuilder> obiektu.  
  
-   Niektóre przeciążenia <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metody, która wyświetlić sformatowany ciąg wynikowy na konsoli.  
  
-   Niektóre przeciążenia <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType> metody, która zapisuje sformatowany ciąg wynikowy w strumieniu lub pliku. Klasy pochodne <xref:System.IO.TextWriter>, takich jak <xref:System.IO.StreamWriter> i <xref:System.Web.UI.HtmlTextWriter>, także mają tę funkcjonalność.  
  
-   <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, która wysyła sformatowany komunikat do odbiorników śledzenia.  
  
-   <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, I <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metod, które wysyłają sformatowane komunikaty do odbiorników śledzenia.  
  
-   <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> Metody, która zapisuje metodę informacyjną w odbiornikach śledzenia.  
  
## <a name="composite-format-string"></a>Złożony ciąg formatujący  
 Ciąg formatu złożonego i lista obiektów są używane jako argumenty metod, które obsługują funkcję formatowania złożonego. Ciąg formatu złożonego składa się z zera lub większej liczby serii stałego tekstu zmieszanego z co najmniej jednym elementem formatu. Stały tekst to dowolnie wybrany ciąg, a każdy element formatu odpowiada obiektowi lub strukturze opakowanej na liście. Funkcja formatowania złożonego zwraca nowy ciąg wynikowy, w którym każdy element formatu jest zamieniany na ciąg reprezentujący odpowiadający mu obiekt na liście.  
  
 Należy wziąć pod uwagę następujące <xref:System.String.Format%2A> fragmentu kodu.  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Stały tekst to "`Name =` "i"`, hours =` ". Elementy formatu to "`{0}`", którego indeks to 0, co odpowiada obiektowi `name`, i "`{1:hh}`", którego indeks to 1, co odpowiada obiektowi `DateTime.Now`.  
  
## <a name="format-item-syntax"></a>Formatuj element składni  
 Każdy element formatu ma następującą postać i składa się z następujących składników:  
  
 `{` *Indeks*[`,`*wyrównanie*] [`:`*formatString*]`}`  
  
 Dopasowujące nawiasy klamrowe („{” i „}”) są wymagane.  
  
### <a name="index-component"></a>Składnik indeksu  
 Obowiązkowy *indeksu* składnika jest określana skrótem Specyfikator parametru to numer, rozpoczynający się od 0, która identyfikuje odpowiedni element na liście obiektów. Oznacza to, że element formatu, którego specyfikator parametru to 0, formatuje pierwszy obiekt na liście, element formatu, którego specyfikator parametru to 1, formatuje drugi obiekt na liście itd. Poniższy przykład zawiera cztery specyfikatory parametrów, numerowane zero za pomocą trzech, do reprezentowania liczb pierwszych mniej niż dziesięć:  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Wiele elementów formatu może odwoływać się do tego samego elementu na liście obiektów, jeśli będą miały określony taki sam specyfikator parametru. Na przykład można sformatować taką samą wartość liczbową w formacie szesnastkowym, wykładniczym i liczbowym, określając ciąg formatu złożonego, takich jak: "0 x{0:X} {0:E} {0:N}", jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Każdy element formatu może odwoływać się do dowolnego obiektu na liście. Na przykład, jeśli istnieją trzy obiekty, można sformatować drugi, pierwszy i trzeci obiekt, określając ciąg formatu złożonego w następujący sposób: "{1} {0} {2}". Obiekt, do którego nie odwołuje się element formatu, zostanie zignorowany. Element <xref:System.FormatException> jest generowany w czasie wykonywania, jeśli Specyfikator parametru wyznacza element spoza listy obiektów.  
  
### <a name="alignment-component"></a>Składnik wyrównania  
 Opcjonalny *wyrównanie* składnik to liczba całkowita ze znakiem wskazującą preferowaną szerokość sformatowanego pola. Jeśli wartość *wyrównanie* jest mniejsza niż długość sformatowanego ciągu *wyrównanie* jest ignorowany i długość sformatowanego ciągu jest używany jako szerokość pola. Sformatowane dane w tym polu jest wyrównany do prawej Jeśli *wyrównanie* jest dodatnia i wyrównane do lewej, jeśli *wyrównanie* jest ujemna. Jeśli potrzebne jest dopełnienie, będą używane znaki odstępu. Wymagany jest przecinek, jeśli *wyrównanie* jest określony.  
  
 W poniższym przykładzie zdefiniowano dwie tablice, jeden zawierający nazwy pracowników i inne zawierające godzin, które zapewniałyby w okresie dwóch tygodni. Ciąg formatu złożonego lewy wyrównuje nazwy w polu 20 znaków i prawy wyrównuje godziny w polu 5 znaków. Należy pamiętać, że ciąg formatu standardowego "N1" jest również używany do formatowania godziny z jednej cyfry ułamkowe.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Element ciągu formatującego  
 Opcjonalny *formatString* składnik jest ciągiem formatu, który jest odpowiedni dla typu formatowanego obiektu. Określ ciąg standardowego lub niestandardowego formatu liczb, gdy odpowiedni obiekt jest wartością liczbową standardowego lub niestandardowego formatu daty i godziny ciąg Jeśli odpowiedni obiekt jest <xref:System.DateTime> obiektu lub [ciąg formatu wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)Jeśli odpowiedni obiekt jest wartością wyliczenia. Jeśli *formatString* nie zostanie określony, specyfikator formatu ogólnego ("G") dla typu liczbowego, daty i godziny lub wyliczenie jest używane. Dwukropek jest wymagany, jeśli *formatString* jest określony.  
  
 Poniższa tabela zawiera listę typów lub kategorii typów w bibliotece klas programu .NET Framework, które obsługują wstępnie zdefiniowany zestaw ciągów formatu i zawiera łącza do tematów zawierających opisy obsługiwanych ciągów formatu. Należy zauważyć, że formatowanie ciągów jest rozszerzalnym mechanizmem, który umożliwia definiowanie nowych ciągów formatu dla każdego istniejącego typu, podobnie jak definiowanie zestawu ciągów formatu obsługiwanych przez typ zdefiniowany przez aplikację. Aby uzyskać więcej informacji, zobacz <xref:System.IFormattable> i <xref:System.ICustomFormatter> interfejsu tematów.  
  
|Typ lub kategoria typów|Zobacz|  
|---------------------------|---------|  
|Typy daty i godziny (<xref:System.DateTime>, <xref:System.DateTimeOffset>)|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)<br /><br /> [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|  
|Typy wyliczeniowe (wszystkie typy pochodne <xref:System.Enum?displayProperty=nameWithType>)|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|  
|Typy liczbowe (<xref:System.Numerics.BigInteger>, <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>)|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)<br /><br /> [Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)<br /><br /> [Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>Unikanie nawiasów klamrowych  
 Klamrowe nawiasy otwierający i zamykający są interpretowane jako rozpoczęcie i zakończenie elementu formatu. W związku z tym należy użyć sekwencji ucieczki, aby wyświetlić literał otwierającego nawiasu klamrowego lub zamykającego nawiasu klamrowego. Należy określić dwa otwierające nawiasy klamrowe („{{”) w stałym tekście, aby wyświetlić jeden otwierający nawias klamrowy („{”), bądź dwa zamykające nawiasy klamrowe („}}”), aby wyświetlić jeden zamykający nawias klamrowy („}”). Nawiasy klamrowe w elemencie formatu są interpretowane sekwencyjnie w kolejności, w jakiej są napotykane. Interpretowanie zagnieżdżonych nawiasów klamrowych nie jest obsługiwane.  
  
 Sposób interpretowania nawiasów klamrowych poprzedzonych znakiem ucieczki może prowadzić do nieoczekiwanych rezultatów. Na przykład rozważmy element formatu "{{{0:D}}}", który jest przeznaczony do wyświetlania otwierający nawias klamrowy, wartość liczbową w formacie liczby dziesiętnej i zamykającego nawiasu klamrowego. Jednak element formatu jest w rzeczywistości interpretowany w następujący sposób:  
  
1.  Pierwsze dwa otwierające nawiasy klamrowe są traktowane jako nawias i znak ucieczki, przez co są zwracane jako jeden otwierający nawias klamrowy.  
  
2.  Kolejne trzy znaki („{0:”) są interpretowane jako początek elementu formatu.  
  
3.  Następny znak („D”) powinien zostać zinterpretowany jako standardowy specyfikator formatu liczb dziesiętnych, ale kolejne dwa nawiasy klamrowe („}}”) zostaną zwrócone jako pojedynczy nawias klamrowy. Ponieważ wynikowy ciąg („D}”) nie jest standardowym specyfikatorem formatu liczb, wynikowy ciąg zostanie zinterpretowany jako ciąg formatu niestandardowego, co oznacza wyświetlenie literału ciągu „D}”.  
  
4.  Ostatni nawias klamrowy („}”) jest interpretowany jako zakończenie elementu formatu.  
  
5.  Wyświetlony wynik końcowy będzie ciągiem literału „{D}”. Wartość liczbowa, która miała zostać sformatowana, nie zostanie wyświetlona.  
  
 Jednym ze sposobów pisania kodu tak, aby uniknąć błędnej interpretacji nawiasów klamrowych ze znakami ucieczki jest formatowanie nawiasów klamrowych i elementów formatu rozdzielnie. Oznacza to, że w pierwszej operacji formatowania wyświetlany jest otwierający nawias klamrowy literału, w następnej operacji wyświetlany jest wynik elementu formatu, a następnie w ostatniej operacji wyświetlany jest zamykający nawias klamrowy literału. To podejście pokazano w poniższym przykładzie.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>Kolejność przetwarzania  
 Jeśli wywołanie metody formatowania złożonego zawiera <xref:System.IFormatProvider> argumentu, którego wartość nie jest `null`, środowisko uruchomieniowe wywołuje swoją <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metodę, aby zażądać <xref:System.ICustomFormatter> implementacji. Jeśli metoda jest w stanie zwrócić <xref:System.ICustomFormatter> wdrażania, jest ona buforowana na czas trwania wywołania metody formatowania złożonego.
  
 Każda wartość na liście parametrów, który odpowiada elementowi formatu jest konwertowana na ciąg w następujący sposób:  
  
1.  Jeśli wartość do sformatowania `null`, ciągiem pustym <xref:System.String.Empty?displayProperty=nameWithType> jest zwracana.  
  
2.  Jeśli <xref:System.ICustomFormatter> implementacja jest dostępna, środowisko uruchomieniowe wywołuje swoją <xref:System.ICustomFormatter.Format%2A> metody. Przekazuje do metody w elemencie formatu *formatString* wartość, jeśli jest obecna, lub `null` , jeśli nie jest dostępna, wraz z <xref:System.IFormatProvider> implementacji. Jeśli wywołanie <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metoda zwraca `null`, wykonanie przechodzi do następnego kroku; w przeciwnym razie wynik <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> wywołanie jest zwracana.
  
3.  Jeśli wartość implementuje <xref:System.IFormattable> interfejsu, interfejs <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> metoda jest wywoływana. Metoda jest przekazywana *formatString* wartość, jeśli jest obecna w elemencie formatu lub `null` Jeśli tak nie jest. <xref:System.IFormatProvider> Argument jest określany w następujący sposób:  
  
    -   Wartość numeryczna, jeśli metoda formatowania złożonego z inną niż null <xref:System.IFormatProvider> argument jest wywoływana, środowisko uruchomieniowe zażąda <xref:System.Globalization.NumberFormatInfo> obiekt z jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody. Jeśli nie można jej dostarczyć, jeśli wartość argumentu jest `null`, lub jeśli nie ma metody formatowania złożonego <xref:System.IFormatProvider> parametru <xref:System.Globalization.NumberFormatInfo> obiekt jest używany przez bieżącą kulturę wątku.  
  
    -   Dla wartości daty i godziny, jeśli metoda formatowania złożonego z inną niż null <xref:System.IFormatProvider> argument jest wywoływana, środowisko uruchomieniowe zażąda <xref:System.Globalization.DateTimeFormatInfo> obiekt z jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody. Jeśli nie można jej dostarczyć, jeśli wartość argumentu jest `null`, lub jeśli nie ma metody formatowania złożonego <xref:System.IFormatProvider> parametru <xref:System.Globalization.DateTimeFormatInfo> obiekt jest używany przez bieżącą kulturę wątku.  
  
    -   W przypadku obiektów innych typów, jeśli formatowanie złożone metoda jest wywoływana z <xref:System.IFormatProvider> argument, jego wartość jest przekazywana bezpośrednio do <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> implementacji. W przeciwnym razie `null` jest przekazywany do <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> implementacji.  
  
4.  Bez parametrów danego typu `ToString` metody, która zastępuje <xref:System.Object.ToString?displayProperty=nameWithType> lub dziedziczy zachowanie jej klasy bazowej, jest wywoływana. W tym przypadku ciąg formatu określony przez *formatString* składnika w elemencie formatu, jeśli jest obecny, jest ignorowany.  
  
 Wyrównanie zostanie zastosowane po wykonaniu poprzednich kroków.  
  
## <a name="code-examples"></a>Przykłady kodu  
 W poniższym przykładzie przedstawiono jeden ciąg utworzony za pomocą formatowania złożonego, a drugiego za pomocą obiektu `ToString` metody. Oba typy formatowania dają równoważne wyniki.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 Przy założeniu, że bieżący dzień jest czwartkiem w maju, wartość obu ciągów w poprzednim przykładzie jest `Thursday May` w Stanach Zjednoczonych Kultura angielski.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> udostępnia taką samą funkcjonalność jak <xref:System.String.Format%2A?displayProperty=nameWithType>. Jedyną różnicą między tymi dwoma metodami jest to, że <xref:System.String.Format%2A?displayProperty=nameWithType> zwraca wynik jako ciąg, podczas gdy <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> zapisuje wynik w strumieniu wyjściowym skojarzone z <xref:System.Console> obiektu. W poniższym przykładzie użyto <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metody formatowania wartości `MyInt` jako wartość waluty.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 W poniższym przykładzie pokazano formatowanie wielu obiektów, w tym formatowanie jednego obiektu na dwa różne sposoby.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 W poniższym przykładzie pokazano użycie wyrównania w formatowaniu. Argumenty, które są formatowane, są umieszczone między znakami kreski pionowej (&#124;) w celu wyróżnienia wynikowego wyrównania.  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Console.WriteLine%2A>  
- <xref:System.String.Format%2A?displayProperty=nameWithType>  
- [Interpolacja ciągów (C#)](../../csharp/language-reference/tokens/interpolated.md)  
- [Ciąg interpolacji (Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)  
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
- [Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
- [Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
- [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
- [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
- [Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)  
- [Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)  
- [Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)
