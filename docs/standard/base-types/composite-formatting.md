---
title: Złożone formatowanie
description: Dowiedz się więcej na temat formatowania złożonego .NET, które przyjmuje jako dane wejściowe listę obiektów i ciąg formatu złożonego, zawierający stały tekst z indeksowanymi symbolami zastępczymi.
ms.date: 10/26/2018
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
ms.openlocfilehash: 36197b382c449a2570e1d5530f307c4e66b0d983
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447267"
---
# <a name="composite-formatting"></a>Złożone formatowanie

Funkcja formatowania złożonego .NET przyjmuje listę obiektów i ciąg formatu złożonego jako dane wejściowe. Ciąg formatu złożonego składa się ze stałego tekstu zmieszanego z indeksowanymi symbolami zastępczymi (nazywanymi też elementami formatu), które odpowiadają obiektom na liście. Operacja formatowania zwraca ciąg wynikowy, który składa się z oryginalnego stałego tekstu zmieszanego z ciągiem reprezentującym obiekty na liście.  
  
> [!IMPORTANT]
> Zamiast korzystać z ciągów formatu złożonego, można użyć *interpolowanych ciągów* , jeśli używany język i wersja językowa są obsługiwane. Ciąg interpolowany jest ciągiem, który zawiera *interpolowane wyrażenia*. Każde wyrażenie interpolowane jest rozpoznawane za pomocą wartości wyrażenia i uwzględniane w ciągu wynikowym, gdy ciąg jest przypisany. Aby uzyskać więcej informacji, zobacz [Interpolacja ciągów (odwołanie w C#)](../../csharp/language-reference/tokens/interpolated.md) i [ciągi interpolowane (odwołanie Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md).

Funkcja formatowania złożonego jest obsługiwana przez metody, takie jak:  
  
- <xref:System.String.Format%2A?displayProperty=nameWithType>, która zwraca sformatowany ciąg wynikowy.  
  
- <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, która dołącza sformatowany ciąg wynikowy do <xref:System.Text.StringBuilder> obiektu.
- Niektóre przeciążenia <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metody, które wyświetlają sformatowany ciąg wynikowy w konsoli programu.  
  
- Niektóre przeciążenia <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType> metody, które zapisują sformatowany ciąg wynikowy do strumienia lub pliku. Klasy pochodne <xref:System.IO.TextWriter> , takie jak <xref:System.IO.StreamWriter> i <xref:System.Web.UI.HtmlTextWriter> , również udostępniają tę funkcję.  
  
- <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, która wyświetla sformatowany komunikat do śledzenia odbiorników.  
  
- <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>Metody, <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> i, <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> które wyprowadzają komunikaty z sformatowanego do detektorów śledzenia.  
  
- <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>Metoda, która zapisuje metodę informacyjną do śledzenia odbiorników.  
  
## <a name="composite-format-string"></a>Złożony ciąg formatujący  
 Ciąg formatu złożonego i lista obiektów są używane jako argumenty metod, które obsługują funkcję formatowania złożonego. Ciąg formatu złożonego składa się z zera lub większej liczby serii stałego tekstu zmieszanego z co najmniej jednym elementem formatu. Stały tekst to dowolnie wybrany ciąg, a każdy element formatu odpowiada obiektowi lub strukturze opakowanej na liście. Funkcja formatowania złożonego zwraca nowy ciąg wynikowy, w którym każdy element formatu jest zamieniany na ciąg reprezentujący odpowiadający mu obiekt na liście.  
  
 Rozważmy następujący <xref:System.String.Format%2A> fragment kodu.  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Stały tekst to " `Name =` " i " `, hours =` ". Elementy formatu są " `{0}` ", których indeks jest równy 0, który odnosi się do obiektu `name` i " `{1:hh}` ", którego indeks wynosi 1, co odpowiada obiektowi `DateTime.Now` .  
  
## <a name="format-item-syntax"></a>Formatuj element składni  
 Każdy element formatu ma następującą postać i składa się z następujących składników:  
  
 `{`*indeks*[ `,` *wyrównanie*] [ `:` *FormatString*]`}`  
  
 Dopasowujące nawiasy klamrowe („{” i „}”) są wymagane.  
  
### <a name="index-component"></a>Składnik indeksu  
 Obowiązkowy składnik *indeksu* , nazywany także specyfikatorem parametru, jest liczbą rozpoczynającą się od 0, która identyfikuje odpowiadający element na liście obiektów. Oznacza to, że element formatu, którego specyfikator parametru to 0, formatuje pierwszy obiekt na liście, element formatu, którego specyfikator parametru to 1, formatuje drugi obiekt na liście itd. Poniższy przykład zawiera cztery specyfikatory parametrów, numerowane od zera do trzech, aby reprezentować liczby podstawowe mniejsze niż dziesięć:  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Wiele elementów formatu może odwoływać się do tego samego elementu na liście obiektów, jeśli będą miały określony taki sam specyfikator parametru. Na przykład można sformatować tę samą wartość liczbową w formacie szesnastkowym, naukowym i liczbowym, określając ciąg formatu złożonego, taki jak: "0x {0:X} {0:E} {0:N} ", jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Każdy element formatu może odwoływać się do dowolnego obiektu na liście. Na przykład jeśli istnieją trzy obiekty, można sformatować drugi, pierwszy i trzeci obiekt przez określenie ciągu formatu złożonego, takiego jak: " {1} {0} {2} ". Obiekt, do którego nie odwołuje się element formatu, zostanie zignorowany. <xref:System.FormatException>Jest generowany w czasie wykonywania, jeśli specyfikator parametru wyznacza element poza granicami listy obiektów.  
  
### <a name="alignment-component"></a>Składnik wyrównania  
 Opcjonalny składnik *wyrównania* jest ze znakiem liczby całkowitej wskazującej preferowaną szerokość pola sformatowanego. Jeśli wartość *wyrównania* jest mniejsza niż długość sformatowanego ciągu, *wyrównanie* jest ignorowane i długość sformatowanego ciągu jest używana jako szerokość pola. Sformatowane dane w polu są wyrównane do prawej, jeśli *wyrównanie* jest dodatnie i wyrównane do lewej, jeśli *wyrównanie* jest ujemne. Jeśli potrzebne jest dopełnienie, będą używane znaki odstępu. Przecinek jest wymagany w przypadku określenia *wyrównania* .  
  
 W poniższym przykładzie zdefiniowano dwie tablice, z których jedna zawiera nazwy pracowników i drugi zawierający godziny, w których pracują w okresie dwóch tygodni. Ciąg formatu złożonego w lewo — wyrównuje nazwy w polu 20 znaków, a następnie w polu 5-znakowym wyrównanym do prawej godziny. Należy zauważyć, że ciąg formatu standardowego "N1" służy również do formatowania godzin przy użyciu jednej cyfry ułamkowej.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Element ciągu formatującego  
 Opcjonalny składnik *FormatString* jest ciągiem formatu, który jest odpowiedni dla typu formatowanego obiektu. Określ standardowy lub niestandardowy ciąg formatu liczbowego, jeśli odpowiedni obiekt jest wartością liczbową, standardowym lub niestandardowym ciągiem formatu daty i godziny, jeśli odpowiedni obiekt jest <xref:System.DateTime> obiektem lub [ciągiem formatu wyliczenia](enumeration-format-strings.md) , jeśli odpowiedni obiekt jest wartością wyliczenia. Jeśli element *FormatString* nie zostanie określony, używany jest specyfikator formatu ogólnego ("G") dla typu liczbowego, daty i godziny lub wyliczenia. Dwukropek jest wymagany, jeśli jest określony parametr *FormatString* .  
  
 Poniższa tabela zawiera listę typów lub kategorii typów w bibliotece klas programu .NET Framework, które obsługują wstępnie zdefiniowany zestaw ciągów formatu i zawiera łącza do tematów zawierających opisy obsługiwanych ciągów formatu. Należy zauważyć, że formatowanie ciągów jest rozszerzalnym mechanizmem, który umożliwia definiowanie nowych ciągów formatu dla każdego istniejącego typu, podobnie jak definiowanie zestawu ciągów formatu obsługiwanych przez typ zdefiniowany przez aplikację. Aby uzyskać więcej informacji, zobacz <xref:System.IFormattable> <xref:System.ICustomFormatter> Tematy dotyczące interfejsu i.  
  
|Typ lub kategoria typów|Zobacz|  
|---------------------------|---------|  
|Typy daty i godziny ( <xref:System.DateTime> , <xref:System.DateTimeOffset> )|[Standardowe ciągi formatujące datę i godzinę](standard-date-and-time-format-strings.md)<br /><br /> [Niestandardowe ciągi formatujące datę i godzinę](custom-date-and-time-format-strings.md)|  
|Typy wyliczeniowe (wszystkie typy pochodne od <xref:System.Enum?displayProperty=nameWithType> )|[Ciągi formatujące Wyliczenie](enumeration-format-strings.md)|  
|Typy liczbowe ( <xref:System.Numerics.BigInteger> ,,,,,,,,, <xref:System.Byte> <xref:System.Decimal> <xref:System.Double> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.SByte> <xref:System.Single> <xref:System.UInt16> , <xref:System.UInt32> , <xref:System.UInt64> )|[Standardowe ciągi formatujące liczby](standard-numeric-format-strings.md)<br /><br /> [Niestandardowe ciągi formatujące liczby](custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[Standardowe ciągi formatujące TimeSpan](standard-timespan-format-strings.md)<br /><br /> [Niestandardowe ciągi formatujące TimeSpan](custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>Unikanie nawiasów klamrowych  
 Klamrowe nawiasy otwierający i zamykający są interpretowane jako rozpoczęcie i zakończenie elementu formatu. W związku z tym należy użyć sekwencji ucieczki, aby wyświetlić literał otwierającego nawiasu klamrowego lub zamykającego nawiasu klamrowego. Należy określić dwa otwierające nawiasy klamrowe („{{”) w stałym tekście, aby wyświetlić jeden otwierający nawias klamrowy („{”), bądź dwa zamykające nawiasy klamrowe („}}”), aby wyświetlić jeden zamykający nawias klamrowy („}”). Nawiasy klamrowe w elemencie formatu są interpretowane sekwencyjnie w kolejności, w jakiej są napotykane. Interpretowanie zagnieżdżonych nawiasów klamrowych nie jest obsługiwane.  
  
 Sposób interpretowania nawiasów klamrowych poprzedzonych znakiem ucieczki może prowadzić do nieoczekiwanych rezultatów. Rozważmy na przykład element formatu "{{ {0:D} }}", który jest przeznaczony do wyświetlania nawiasu otwierającego, wartości liczbowej sformatowanej jako liczba dziesiętna i zamykającego nawiasu klamrowego. Jednak element formatu jest w rzeczywistości interpretowany w następujący sposób:  
  
1. Pierwsze dwa otwierające nawiasy klamrowe są traktowane jako nawias i znak ucieczki, przez co są zwracane jako jeden otwierający nawias klamrowy.  
  
2. Kolejne trzy znaki („{0:”) są interpretowane jako początek elementu formatu.  
  
3. Następny znak („D”) powinien zostać zinterpretowany jako standardowy specyfikator formatu liczb dziesiętnych, ale kolejne dwa nawiasy klamrowe („}}”) zostaną zwrócone jako pojedynczy nawias klamrowy. Ponieważ wynikowy ciąg („D}”) nie jest standardowym specyfikatorem formatu liczb, wynikowy ciąg zostanie zinterpretowany jako ciąg formatu niestandardowego, co oznacza wyświetlenie literału ciągu „D}”.  
  
4. Ostatni nawias klamrowy („}”) jest interpretowany jako zakończenie elementu formatu.  
  
5. Wyświetlony wynik końcowy będzie ciągiem literału „{D}”. Wartość liczbowa, która miała zostać sformatowana, nie zostanie wyświetlona.  
  
 Jednym ze sposobów pisania kodu tak, aby uniknąć błędnej interpretacji nawiasów klamrowych ze znakami ucieczki jest formatowanie nawiasów klamrowych i elementów formatu rozdzielnie. Oznacza to, że w pierwszej operacji formatowania wyświetlany jest otwierający nawias klamrowy literału, w następnej operacji wyświetlany jest wynik elementu formatu, a następnie w ostatniej operacji wyświetlany jest zamykający nawias klamrowy literału. To podejście pokazano w poniższym przykładzie.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>Kolejność przetwarzania  
 Jeśli wywołanie metody formatowania złożonego zawiera <xref:System.IFormatProvider> argument, którego wartość nie jest `null` , środowisko uruchomieniowe wywołuje metodę, <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> Aby zażądać <xref:System.ICustomFormatter> implementacji. Jeśli metoda może zwrócić <xref:System.ICustomFormatter> implementację, jest buforowana na czas trwania wywołania metody formatowania złożonego.
  
 Każda wartość na liście parametrów, która odnosi się do elementu formatu, jest konwertowana na ciąg w następujący sposób:  
  
1. Jeśli wartość do sformatowania jest `null` , zwracany jest pusty ciąg <xref:System.String.Empty?displayProperty=nameWithType> .  
  
2. Jeśli <xref:System.ICustomFormatter> implementacja jest dostępna, środowisko uruchomieniowe wywołuje jego <xref:System.ICustomFormatter.Format%2A> metodę. Przekazuje ona metodę, jeśli jest obecny, *formatString* lub `null` Jeśli nie, wraz z <xref:System.IFormatProvider> implementacją. Jeśli wywołanie <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metody zwróci metodę `null` , wykonanie przechodzi do następnego kroku; w przeciwnym razie <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> zwracany jest wynik wywołania.
  
3. Jeśli wartość implementuje <xref:System.IFormattable> interfejs, <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> wywoływana jest metoda interfejsu. Metoda jest przenoszona przez wartość *FormatString* , jeśli jest obecna w elemencie formatu lub `null` Jeśli nie jest. <xref:System.IFormatProvider>Argument jest określany w następujący sposób:  
  
    - W przypadku wartości liczbowej, jeśli wywoływana jest złożona Metoda formatowania z argumentem innym niż null <xref:System.IFormatProvider> , środowisko uruchomieniowe żąda <xref:System.Globalization.NumberFormatInfo> obiektu od jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody. Jeśli nie jest to możliwe, jeśli wartość argumentu jest `null` lub Metoda formatowania złożonego nie ma <xref:System.IFormatProvider> parametru, <xref:System.Globalization.NumberFormatInfo> używany jest obiekt dla bieżącej kultury wątku.  
  
    - W przypadku wartości daty i godziny, jeśli wywoływana jest złożona Metoda formatowania z argumentem innym niż null <xref:System.IFormatProvider> , środowisko uruchomieniowe żąda <xref:System.Globalization.DateTimeFormatInfo> obiektu od jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody. Jeśli nie jest to możliwe, jeśli wartość argumentu jest `null` lub Metoda formatowania złożonego nie ma <xref:System.IFormatProvider> parametru, <xref:System.Globalization.DateTimeFormatInfo> używany jest obiekt dla bieżącej kultury wątku.  
  
    - W przypadku obiektów innych typów, jeśli Metoda formatowania złożonego jest wywoływana z <xref:System.IFormatProvider> argumentem, jego wartość jest przenoszona bezpośrednio do <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> implementacji. W przeciwnym razie `null` jest przenoszona do <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> implementacji.  
  
4. Metoda bez parametrów typu `ToString` , która zastępuje <xref:System.Object.ToString?displayProperty=nameWithType> lub dziedziczy zachowanie klasy podstawowej, jest wywoływana. W tym przypadku ciąg formatu określony przez składnik *FormatString* w elemencie formatu, jeśli jest obecny, jest ignorowany.  
  
 Wyrównanie zostanie zastosowane po wykonaniu poprzednich kroków.  
  
## <a name="code-examples"></a>Przykłady kodu  
 W poniższym przykładzie pokazano jeden ciąg utworzony przy użyciu formatowania złożonego i inny utworzony przy użyciu `ToString` metody obiektu. Oba typy formatowania dają równoważne wyniki.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 Przy założeniu, że bieżący dzień jest czwartek w maju, wartość obu ciągów w powyższym przykładzie znajduje się `Thursday May` w kulturze angielskiej w Stanach Zjednoczonych.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>udostępnia te same funkcje co <xref:System.String.Format%2A?displayProperty=nameWithType> . Jedyną różnicą między dwoma metodami jest <xref:System.String.Format%2A?displayProperty=nameWithType> zwrócenie wyniku w postaci ciągu, podczas gdy <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> zapisuje wynik do strumienia wyjściowego skojarzonego z <xref:System.Console> obiektem. W poniższym przykładzie zastosowano <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metodę, aby sformatować wartość `MyInt` do wartości walutowej.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 W poniższym przykładzie pokazano formatowanie wielu obiektów, w tym formatowanie jednego obiektu na dwa różne sposoby.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 W poniższym przykładzie pokazano użycie wyrównania w formatowaniu. Sformatowane argumenty są umieszczane między pionowymi znakami kreski (&#124;), aby wyróżnić wyniki wyrównania.  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Console.WriteLine%2A>
- <xref:System.String.Format%2A?displayProperty=nameWithType>
- [Interpolacja ciągów (C#)](../../csharp/language-reference/tokens/interpolated.md)
- [Interpolacja ciągów (Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)
- [Formatowanie typów](formatting-types.md)
- [Standardowe ciągi formatujące liczby](standard-numeric-format-strings.md)
- [Niestandardowe ciągi formatujące liczby](custom-numeric-format-strings.md)
- [Standardowe ciągi formatujące datę i godzinę](standard-date-and-time-format-strings.md)
- [Niestandardowe ciągi formatujące datę i godzinę](custom-date-and-time-format-strings.md)
- [Standardowe ciągi formatujące TimeSpan](standard-timespan-format-strings.md)
- [Niestandardowe ciągi formatujące TimeSpan](custom-timespan-format-strings.md)
- [Ciągi formatujące Wyliczenie](enumeration-format-strings.md)
