---
title: Formatowanie kompozytowe
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
ms.openlocfilehash: b1ec8cfc0f8c6e660d716c51bf3c3387b73a278f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400345"
---
# <a name="composite-formatting"></a>Formatowanie kompozytowe

Funkcja formatowania złożonego .NET przyjmuje listę obiektów i ciąg formatu złożonego jako dane wejściowe. Ciąg formatu złożonego składa się ze stałego tekstu zmieszanego z indeksowanymi symbolami zastępczymi (nazywanymi też elementami formatu), które odpowiadają obiektom na liście. Operacja formatowania zwraca ciąg wynikowy, który składa się z oryginalnego stałego tekstu zmieszanego z ciągiem reprezentującym obiekty na liście.  
  
> [!IMPORTANT]
> Zamiast używać ciągów formatu złożonego, można użyć *interpolowanych ciągów,* jeśli język i wersja językowa, której używasz, obsługują je. Interpolowany ciąg jest ciągiem zawierającym *interpolowane wyrażenia*. Każde interpolowane wyrażenie jest rozpoznawane za pomocą wartości wyrażenia i uwzględniane w ciągu wynikowym, gdy ciąg jest przypisany. Aby uzyskać więcej informacji, zobacz [Interpolacja ciągów (odwołanie do języka C#](../../csharp/language-reference/tokens/interpolated.md) i [interpolowane ciągi (Visual Basic Reference).](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)

Funkcja formatowania złożonego jest obsługiwana przez metody, takie jak:  
  
- <xref:System.String.Format%2A?displayProperty=nameWithType>, który zwraca sformatowany ciąg wyników.  
  
- <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, który dołącza sformatowany ciąg <xref:System.Text.StringBuilder> wyników do obiektu.
- Niektóre przeciążenia <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metody, które wyświetlają sformatowany ciąg wyników do konsoli.  
  
- Niektóre przeciążenia <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType> metody, które zapisują sformatowany ciąg wynikowy do strumienia lub pliku. Klasy pochodzące z <xref:System.IO.TextWriter>, <xref:System.IO.StreamWriter> takich <xref:System.Web.UI.HtmlTextWriter>jak i , również współużytkowane tej funkcji.  
  
- <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, który generuje sformatowaną wiadomość do śledzenia odbiorników.  
  
- , <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>i <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody, które wyprowadzają sformatowane wiadomości do śledzenia odbiorników.  
  
- Metoda, <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> która zapisuje metodę informacyjną do śledzenia odbiorników.  
  
## <a name="composite-format-string"></a>Złożony ciąg formatujący  
 Ciąg formatu złożonego i lista obiektów są używane jako argumenty metod, które obsługują funkcję formatowania złożonego. Ciąg formatu złożonego składa się z zera lub większej liczby serii stałego tekstu zmieszanego z co najmniej jednym elementem formatu. Stały tekst to dowolnie wybrany ciąg, a każdy element formatu odpowiada obiektowi lub strukturze opakowanej na liście. Funkcja formatowania złożonego zwraca nowy ciąg wynikowy, w którym każdy element formatu jest zamieniany na ciąg reprezentujący odpowiadający mu obiekt na liście.  
  
 Należy wziąć <xref:System.String.Format%2A> pod uwagę następujący fragment kodu.  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Tekst stały to`Name =` "`, hours =` " i " ". Elementy formatu`{0}`to " ", którego indeks wynosi `name`0,`{1:hh}`co odpowiada obiektowi , i " `DateTime.Now`", którego indeks wynosi 1, co odpowiada obiektowi .  
  
## <a name="format-item-syntax"></a>Formatuj element składni  
 Każdy element formatu ma następującą postać i składa się z następujących składników:  
  
 `{`*index*`,`[*wyrównanie*][`:`*formatString*]`}`  
  
 Dopasowujące nawiasy klamrowe („{” i „}”) są wymagane.  
  
### <a name="index-component"></a>Składnik indeksu  
 Składnik *indeksu* obowiązkowego, nazywany również specyfikatorem parametrów, jest liczbą rozpoczynającą się od 0, która identyfikuje odpowiedni element na liście obiektów. Oznacza to, że element formatu, którego specyfikator parametru to 0, formatuje pierwszy obiekt na liście, element formatu, którego specyfikator parametru to 1, formatuje drugi obiekt na liście itd. Poniższy przykład zawiera cztery specyfikatory parametrów, ponumerowane od zera do trzech, reprezentujące liczby pierwsze mniejsze niż dziesięć:  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Wiele elementów formatu może odwoływać się do tego samego elementu na liście obiektów, jeśli będą miały określony taki sam specyfikator parametru. Na przykład można sformatować tę samą wartość liczbową w formacie szesnastkowym, naukowym i{0:X} {0:E} {0:N}liczbowym, określając ciąg formatu złożonego, taki jak : "0x ", jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Każdy element formatu może odwoływać się do dowolnego obiektu na liście. Na przykład jeśli istnieją trzy obiekty, można sformatować drugi, pierwszy i trzeci obiekt,{1} {0} {2}określając ciąg formatu złożonego w stylu: " ". Obiekt, do którego nie odwołuje się element formatu, zostanie zignorowany. A <xref:System.FormatException> jest generowany w czasie wykonywania, jeśli specyfikator parametrów wyznacza element poza granicami listy obiektów.  
  
### <a name="alignment-component"></a>Składnik wyrównania  
 Opcjonalny komponent *wyrównania* jest podpisaną liczbą całkowitą wskazującą preferowaną sformatowaną szerokość pola. Jeśli wartość *wyrównania* jest mniejsza niż długość sformatowanego ciągu, *wyrównanie* jest ignorowane, a długość sformatowanego ciągu jest używana jako szerokość pola. Sformatowane dane w tym polu są wyrównane do prawej, jeśli *wyrównanie* jest dodatnie, a wyrównane do lewej, jeśli *wyrównanie* jest ujemne. Jeśli potrzebne jest dopełnienie, będą używane znaki odstępu. Przecinek jest wymagany, jeśli określono *wyrównanie.*  
  
 W poniższym przykładzie zdefiniowano dwie tablice, z których jedna zawiera nazwiska pracowników, a druga zawiera godziny przepracowane w okresie dwóch tygodni. Ciąg formatu złożonego wyrównuje nazwy w polu 20-znakowym, a w polu 5-znakowym wyrównanie ich godzin w polu 5 znaków. Należy zauważyć, że standardowy ciąg formatu "N1" jest również używany do formatowania godzin za pomocą jednej cyfry ułamkowej.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Element ciągu formatującego  
 Opcjonalny składnik *formatString* jest ciągiem formatu, który jest odpowiedni dla typu formatowanego obiektu. Określ standardowy lub niestandardowy ciąg formatu numerycznego, jeśli odpowiedni obiekt jest wartością liczbową, <xref:System.DateTime> standardowym lub niestandardowym ciągiem formatu daty i godziny, jeśli odpowiedni obiekt jest obiektem, lub [ciągformatu wyliczenia,](../../../docs/standard/base-types/enumeration-format-strings.md) jeśli odpowiedni obiekt jest wartością wyliczenia. Jeśli *formatString* nie jest określony, używany jest ogólny ("G") specyfikator formatu dla typu liczbowego, daty i godziny lub wyliczenia. Dwukropek jest wymagany, jeśli określono *formatString.*  
  
 Poniższa tabela zawiera listę typów lub kategorii typów w bibliotece klas programu .NET Framework, które obsługują wstępnie zdefiniowany zestaw ciągów formatu i zawiera łącza do tematów zawierających opisy obsługiwanych ciągów formatu. Należy zauważyć, że formatowanie ciągów jest rozszerzalnym mechanizmem, który umożliwia definiowanie nowych ciągów formatu dla każdego istniejącego typu, podobnie jak definiowanie zestawu ciągów formatu obsługiwanych przez typ zdefiniowany przez aplikację. Aby uzyskać więcej <xref:System.IFormattable> informacji, zobacz tematy interfejsu i. <xref:System.ICustomFormatter>  
  
|Typ lub kategoria typów|Zobacz|  
|---------------------------|---------|  
|Typy daty i<xref:System.DateTime> <xref:System.DateTimeOffset>godziny ( , )|[Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)<br /><br /> [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|  
|Typy wyliczania (wszystkie <xref:System.Enum?displayProperty=nameWithType>typy pochodzące z)|[Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)|  
|Typy liczbowe <xref:System.Byte> <xref:System.Decimal>( <xref:System.Double><xref:System.Numerics.BigInteger>, <xref:System.Int32> <xref:System.Int64>, <xref:System.SByte> <xref:System.Single>, <xref:System.UInt16> <xref:System.UInt32>, <xref:System.UInt64> <xref:System.Int16>, , , )|[Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)<br /><br /> [Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)<br /><br /> [Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>Unikanie nawiasów klamrowych  
 Klamrowe nawiasy otwierający i zamykający są interpretowane jako rozpoczęcie i zakończenie elementu formatu. W związku z tym należy użyć sekwencji ucieczki, aby wyświetlić literał otwierającego nawiasu klamrowego lub zamykającego nawiasu klamrowego. Należy określić dwa otwierające nawiasy klamrowe („{{”) w stałym tekście, aby wyświetlić jeden otwierający nawias klamrowy („{”), bądź dwa zamykające nawiasy klamrowe („}}”), aby wyświetlić jeden zamykający nawias klamrowy („}”). Nawiasy klamrowe w elemencie formatu są interpretowane sekwencyjnie w kolejności, w jakiej są napotykane. Interpretowanie zagnieżdżonych nawiasów klamrowych nie jest obsługiwane.  
  
 Sposób interpretowania nawiasów klamrowych poprzedzonych znakiem ucieczki może prowadzić do nieoczekiwanych rezultatów. Rozważmy na przykład element formatu "{{{0:D}}}", który ma na celu wyświetlenie nawiasu klamrowego otwarcia, wartości liczbowej sformatowanej jako liczba dziesiętna i nawiasu zamykającego. Jednak element formatu jest w rzeczywistości interpretowany w następujący sposób:  
  
1. Pierwsze dwa otwierające nawiasy klamrowe są traktowane jako nawias i znak ucieczki, przez co są zwracane jako jeden otwierający nawias klamrowy.  
  
2. Kolejne trzy znaki („{0:”) są interpretowane jako początek elementu formatu.  
  
3. Następny znak („D”) powinien zostać zinterpretowany jako standardowy specyfikator formatu liczb dziesiętnych, ale kolejne dwa nawiasy klamrowe („}}”) zostaną zwrócone jako pojedynczy nawias klamrowy. Ponieważ wynikowy ciąg („D}”) nie jest standardowym specyfikatorem formatu liczb, wynikowy ciąg zostanie zinterpretowany jako ciąg formatu niestandardowego, co oznacza wyświetlenie literału ciągu „D}”.  
  
4. Ostatni nawias klamrowy („}”) jest interpretowany jako zakończenie elementu formatu.  
  
5. Wyświetlony wynik końcowy będzie ciągiem literału „{D}”. Wartość liczbowa, która miała zostać sformatowana, nie zostanie wyświetlona.  
  
 Jednym ze sposobów pisania kodu tak, aby uniknąć błędnej interpretacji nawiasów klamrowych ze znakami ucieczki jest formatowanie nawiasów klamrowych i elementów formatu rozdzielnie. Oznacza to, że w pierwszej operacji formatowania wyświetlany jest otwierający nawias klamrowy literału, w następnej operacji wyświetlany jest wynik elementu formatu, a następnie w ostatniej operacji wyświetlany jest zamykający nawias klamrowy literału. To podejście pokazano w poniższym przykładzie.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>Kolejność przetwarzania  
 Jeśli wywołanie metody formatowania złożonego <xref:System.IFormatProvider> zawiera argument, `null`którego wartość nie <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> jest , <xref:System.ICustomFormatter> czas wykonywania wywołuje jego metodę, aby zażądać implementacji. Jeśli metoda jest w <xref:System.ICustomFormatter> stanie zwrócić implementacji, jest buforowany na czas trwania wywołania metody formatowania złożonego.
  
 Każda wartość na liście parametrów odpowiadająca elementowi formatu jest konwertowana na ciąg w następujący sposób:  
  
1. Jeśli wartość, która ma `null`być sformatowana, zwracany jest pusty ciąg. <xref:System.String.Empty?displayProperty=nameWithType>  
  
2. Jeśli <xref:System.ICustomFormatter> implementacja jest dostępna, czas <xref:System.ICustomFormatter.Format%2A> wykonywania wywołuje jego metodę. Przekazuje metodę *format uformatować* wartość string elementu, jeśli `null` jest obecny lub jeśli nie <xref:System.IFormatProvider> jest, wraz z implementacji. Jeśli wywołanie <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metody `null`zwraca , wykonanie przechodzi do następnego kroku; w przeciwnym razie <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> zostanie zwrócony wynik wywołania.
  
3. Jeśli wartość implementuje <xref:System.IFormattable> interfejs, <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> wywoływana jest metoda interfejsu. Metoda jest przekazywana *formatString* wartość, jeśli jeden jest `null` obecny w elemencie formatu lub jeśli nie jest. Argument <xref:System.IFormatProvider> jest określany w następujący sposób:  
  
    - Dla wartości liczbowej, jeśli metoda formatowania złożonego <xref:System.IFormatProvider> z argumentem innych niż <xref:System.Globalization.NumberFormatInfo> null jest <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> wywoływana, czas wykonywania żąda obiektu z jego metody. Jeśli nie można podać jeden, jeśli wartość argumentu jest `null`, lub jeśli metoda formatowania <xref:System.IFormatProvider> złożonego <xref:System.Globalization.NumberFormatInfo> nie ma parametru, obiekt dla bieżącej kultury wątku jest używany.  
  
    - Dla wartości daty i godziny, jeśli metoda formatowania złożonego z argumentem innych niż null <xref:System.IFormatProvider> jest wywoływana, czas wykonywania <xref:System.Globalization.DateTimeFormatInfo> żąda obiektu z jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody. Jeśli nie można podać jeden, jeśli wartość argumentu jest `null`, lub jeśli metoda formatowania <xref:System.IFormatProvider> złożonego <xref:System.Globalization.DateTimeFormatInfo> nie ma parametru, obiekt dla bieżącej kultury wątku jest używany.  
  
    - Dla obiektów innych typów, jeśli metoda formatowania złożonego jest wywoływana z <xref:System.IFormatProvider> <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> argumentem, jego wartość jest przekazywana bezpośrednio do implementacji. W `null` przeciwnym razie <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> jest przekazywana do implementacji.  
  
4. Metoda bezparametrowa `ToString` typu, która zastępuje <xref:System.Object.ToString?displayProperty=nameWithType> lub dziedziczy zachowanie jego klasy podstawowej, jest wywoływana. W takim przypadku ciąg formatu określony przez składnik *formatString* w elemencie formatu, jeśli jest obecny, jest ignorowany.  
  
 Wyrównanie zostanie zastosowane po wykonaniu poprzednich kroków.  
  
## <a name="code-examples"></a>Przykłady kodu  
 W poniższym przykładzie przedstawiono jeden ciąg utworzony przy użyciu formatowania `ToString` złożonego i inny utworzony przy użyciu metody obiektu. Oba typy formatowania dają równoważne wyniki.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 Zakładając, że bieżący dzień jest czwartek w maju, wartość obu `Thursday May` ciągów w poprzednim przykładzie jest w kulturze angielskiej USA.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>udostępnia te same funkcje, co <xref:System.String.Format%2A?displayProperty=nameWithType>. Jedyną różnicą między dwiema <xref:System.String.Format%2A?displayProperty=nameWithType> metodami jest, że <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> zwraca jego wynik jako ciąg, <xref:System.Console> podczas gdy zapisuje wynik do strumienia wyjściowego skojarzonego z obiektem. W poniższym <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> przykładzie użyto metody `MyInt` do formatowania wartości do wartości waluty.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 W poniższym przykładzie pokazano formatowanie wielu obiektów, w tym formatowanie jednego obiektu na dwa różne sposoby.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 W poniższym przykładzie pokazano użycie wyrównania w formatowaniu. Argumenty, które są formatowane są umieszczane między pionowymi znakami paska (&#124;) w celu podkreślenia wynikowego wyrównania.  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Console.WriteLine%2A>
- <xref:System.String.Format%2A?displayProperty=nameWithType>
- [Interpolacja ciągów (C#)](../../csharp/language-reference/tokens/interpolated.md)
- [Interpolacja ciągów (Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
- [Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)
- [Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)
