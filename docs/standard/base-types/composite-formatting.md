---
title: Złożone formatowanie
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 156ef0f063219f5e78084dd664b64699d33e6593
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="composite-formatting"></a>Złożone formatowanie
Funkcja formatowania złożonego .NET przyjmuje listę obiektów i ciąg formatu złożonego jako dane wejściowe. Ciąg formatu złożonego składa się ze stałego tekstu zmieszanego z indeksowanymi symbolami zastępczymi (nazywanymi też elementami formatu), które odpowiadają obiektom na liście. Operacja formatowania zwraca ciąg wynikowy, który składa się z oryginalnego stałego tekstu zmieszanego z ciągiem reprezentującym obiekty na liście.  
  
 Funkcja formatowania złożonego jest obsługiwana przez metody, takie jak:  
  
-   <xref:System.String.Format%2A?displayProperty=nameWithType>, która zwraca ciąg sformatowany wynik.  
  
-   <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, które dołącza ciąg sformatowany wynik <xref:System.Text.StringBuilder> obiektu.  
  
-   Niektóre przeciążeń <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metodę, która wyświetlić ciąg sformatowany wynik do konsoli.  
  
-   Niektóre przeciążeń <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType> metodę, która zapisać ciąg sformatowany wynik do strumienia lub pliku. Klasy pochodne <xref:System.IO.TextWriter>, takich jak <xref:System.IO.StreamWriter> i <xref:System.Web.UI.HtmlTextWriter>, także udostępniać te funkcje.  
  
-   <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, które generuje sformatowany komunikat do obiektów nasłuchujących śledzenia.  
  
-   <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, I <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metod, które wyjściowy format wiadomości obiektów nasłuchujących śledzenia.  
  
-   <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> Metodę, która zapisuje metody informacyjną obiektów nasłuchujących śledzenia.  
  
## <a name="composite-format-string"></a>Złożony ciąg formatujący  
 Ciąg formatu złożonego i lista obiektów są używane jako argumenty metod, które obsługują funkcję formatowania złożonego. Ciąg formatu złożonego składa się z zera lub większej liczby serii stałego tekstu zmieszanego z co najmniej jednym elementem formatu. Stały tekst to dowolnie wybrany ciąg, a każdy element formatu odpowiada obiektowi lub strukturze opakowanej na liście. Funkcja formatowania złożonego zwraca nowy ciąg wynikowy, w którym każdy element formatu jest zamieniany na ciąg reprezentujący odpowiadający mu obiekt na liście.  
  
 Należy rozważyć <xref:System.String.Format%2A> fragmentu kodu.  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Stały tekst jest "`Name =` "i"`, hours =` ". Format pozycje "`{0}`", którego indeks ma wartość 0, co odpowiada obiektu `name`, i "`{1:hh}`", którego indeks ma wartość 1, która odnosi się do obiektu `DateTime.Now`.  
  
## <a name="format-item-syntax"></a>Formatuj element składni  
 Każdy element formatu ma następującą postać i składa się z następujących składników:  
  
 `{` *Indeks*[`,`*wyrównanie*] [`:`*formatString*]`}`  
  
 Dopasowujące nawiasy klamrowe („{” i „}”) są wymagane.  
  
### <a name="index-component"></a>Składnik indeksu  
 Obowiązkowe *indeksu* składnika, nazywane również Specyfikator parametru jest liczbą, począwszy od 0, który identyfikuje odpowiadający mu element na liście obiektów. Oznacza to, że element formatu, którego specyfikator parametru to 0, formatuje pierwszy obiekt na liście, element formatu, którego specyfikator parametru to 1, formatuje drugi obiekt na liście itd. Poniższy przykład zawiera cztery specyfikatory parametrów, numerowane zera poprzez trzy, do reprezentowania liczb pierwszych dziesięciu mniejsza niż:  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Wiele elementów formatu może odwoływać się do tego samego elementu na liście obiektów, jeśli będą miały określony taki sam specyfikator parametru. Na przykład można sformatować taką samą wartość liczbową w formacie szesnastkowym, naukowych i numeru, określając ciąg formatu złożonego, takich jak: "0 x {0: x} {0:E} {0: n}", jak pokazano na poniższym przykładzie.  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Każdy element formatu może odwoływać się do dowolnego obiektu na liście. Na przykład jeśli istnieją trzy obiekty, można sformatować obiekt drugi, pierwszy i trzeci, określając ciąg formatu złożonego, taki jak ten: „{1} {0} {2}”. Obiekt, do którego nie odwołuje się element formatu, zostanie zignorowany. A <xref:System.FormatException> jest zgłaszany w czasie wykonywania, jeśli Specyfikator parametru wyznacza elementu poza granice listy obiektów.  
  
### <a name="alignment-component"></a>Składnik wyrównania  
 Opcjonalny *wyrównanie* składnik jest całkowita wskazującą szerokość preferowanych sformatowane pola. Jeśli wartość *wyrównanie* jest mniejsza niż długość ciągu sformatowaną *wyrównanie* jest ignorowany i długość sformatowany ciąg jest używany jako szerokość pola. Sformatowane dane w tym polu jest wyrównany do prawej czy *wyrównanie* jest dodatnia i wyrównane do lewej w przypadku *wyrównanie* jest ujemna. Jeśli potrzebne jest dopełnienie, będą używane znaki odstępu. Przecinek jest wymagany, jeśli *wyrównanie* jest określona.  
  
 W poniższym przykładzie zdefiniowano dwie tablice, jeden zawierający nazwy pracowników i innych zawierające godziny, w których działały one w okresie dwóch tygodni. Ciąg formatu złożonego lewej wyrównuje nazwy w polu 20 znaków i prawej wyrównuje godzin w polu 5 znaków. Należy pamiętać, że ciąg formatu standardowych "N1" służy również do formatu godziny z jedną cyfrę ułamkową.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Element ciągu formatującego  
 Opcjonalny *formatString* składnik jest ciąg formatu, który jest odpowiedni dla typu obiektu jest sformatowana. Określ ciąg formatu liczbowego standardowych lub niestandardowych Jeśli odpowiedni obiekt jest wartością liczbową standardowych lub niestandardowych datę i godzinę ciąg formatu w przypadku odpowiedni obiekt <xref:System.DateTime> obiekt, lub [ciąg formatu wyliczenie](../../../docs/standard/base-types/enumeration-format-strings.md)Jeśli odpowiedni obiekt jest wartością wyliczenia. Jeśli *formatString* nie zostanie określony, ogólne specyfikator formatu ("G") dla typu liczbowego, daty i godziny lub wyliczenia jest używany. Dwukropkiem jest wymagany, jeśli *formatString* jest określona.  
  
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
  
 Sposób interpretowania nawiasów klamrowych poprzedzonych znakiem ucieczki może prowadzić do nieoczekiwanych rezultatów. Na przykład rozważmy element formatu „{{{0:D}}}”, który jest przeznaczony do wyświetlenia otwierającego nawiasu klamrowego, wartości liczbowej sformatowanej w postaci liczby dziesiętnej i zamykającego nawiasu klamrowego. Jednak element formatu jest w rzeczywistości interpretowany w następujący sposób:  
  
1.  Pierwsze dwa otwierające nawiasy klamrowe są traktowane jako nawias i znak ucieczki, przez co są zwracane jako jeden otwierający nawias klamrowy.  
  
2.  Kolejne trzy znaki („{0:”) są interpretowane jako początek elementu formatu.  
  
3.  Następny znak („D”) powinien zostać zinterpretowany jako standardowy specyfikator formatu liczb dziesiętnych, ale kolejne dwa nawiasy klamrowe („}}”) zostaną zwrócone jako pojedynczy nawias klamrowy. Ponieważ wynikowy ciąg („D}”) nie jest standardowym specyfikatorem formatu liczb, wynikowy ciąg zostanie zinterpretowany jako ciąg formatu niestandardowego, co oznacza wyświetlenie literału ciągu „D}”.  
  
4.  Ostatni nawias klamrowy („}”) jest interpretowany jako zakończenie elementu formatu.  
  
5.  Wyświetlony wynik końcowy będzie ciągiem literału „{D}”. Wartość liczbowa, która miała zostać sformatowana, nie zostanie wyświetlona.  
  
 Jednym ze sposobów pisania kodu tak, aby uniknąć błędnej interpretacji nawiasów klamrowych ze znakami ucieczki jest formatowanie nawiasów klamrowych i elementów formatu rozdzielnie. Oznacza to, że w pierwszej operacji formatowania wyświetlany jest otwierający nawias klamrowy literału, w następnej operacji wyświetlany jest wynik elementu formatu, a następnie w ostatniej operacji wyświetlany jest zamykający nawias klamrowy literału. To podejście pokazano w poniższym przykładzie.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>Kolejność przetwarzania  
 Jeśli wywołanie złożone formatowanie metoda zawiera <xref:System.IFormatProvider> argumentu, którego wartość nie jest `null`, wywołania środowiska uruchomieniowego jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody, aby zażądać <xref:System.ICustomFormatter> implementacji. Jeśli metoda jest może zwrócić <xref:System.ICustomFormatter> implementacji, jest buforowany do późniejszego użycia.  
  
 Każda wartość na liście parametrów, która odpowiada elementowi formatu, jest konwertowana na ciąg przez wykonanie wymienionych poniżej kroków. Jeśli dowolny warunek z pierwszych trzech kroków będzie spełniony, reprezentacja ciągu dla wartości zostanie zwrócona w tym kroku, a kolejne kroki nie zostaną wykonane.  
  
1.  Jeśli wartość zostanie sformatowany jest `null`, ciąg pusty ("") jest zwracany.  
  
2.  Jeśli <xref:System.ICustomFormatter> implementacja jest dostępna, wywołania środowiska uruchomieniowego jego <xref:System.ICustomFormatter.Format%2A> metody. Przekazuje metody w element formatu *formatString* wartość, jeśli jest dostępny, lub `null` Jeśli nie, wraz z <xref:System.IFormatProvider> implementacji.  
  
3.  Jeśli wartość implementuje <xref:System.IFormattable> interfejsu, interfejsu <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> metoda jest wywoływana. Metoda jest przekazywana *formatString* wartość, jeśli jest obecny w elemencie formatu lub `null` Jeśli nie jest. <xref:System.IFormatProvider> Argument jest określane w następujący sposób:  
  
    -   Wartości liczbowe, jeśli złożone formatowanie metody z inną niż null <xref:System.IFormatProvider> argumentu po wywołaniu żądania środowiska uruchomieniowego <xref:System.Globalization.NumberFormatInfo> obiekt z jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> — metoda. Jeśli nie można podać, jeśli wartość argumentu jest `null`, lub jeśli złożone formatowanie — metoda nie ma <xref:System.IFormatProvider> parametru <xref:System.Globalization.NumberFormatInfo> obiektu dla bieżącej kultury wątku jest używana.  
  
    -   Wartości daty i godziny, jeśli złożone formatowanie metody z inną niż null <xref:System.IFormatProvider> argumentu po wywołaniu żądania obsługi <xref:System.Globalization.DateTimeFormatInfo> obiekt z jego <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody. Jeśli nie można podać, jeśli wartość argumentu jest `null`, lub jeśli złożone formatowanie — metoda nie ma <xref:System.IFormatProvider> parametru <xref:System.Globalization.DateTimeFormatInfo> obiektu dla bieżącej kultury wątku jest używana.  
  
    -   Dla obiektów inne typy złożone formatowanie jest wywoływana z <xref:System.IFormatProvider> argumentu, jego wartość (w tym `null`, jeśli nie <xref:System.IFormatProvider> obiektu jest dostarczany) jest przekazywane bezpośrednio do <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> implementacji.  W przeciwnym razie <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje bieżącej kultury wątku jest przekazywany do <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> implementacji.  
  
4.  Typ obiektu bez parametrów `ToString` metody, co użytkownik zastępuje <xref:System.Object.ToString?displayProperty=nameWithType> lub dziedziczy zachowanie klasy podstawowej, nosi nazwę. W takim przypadku ciąg formatu określona przez *formatString* składnika w elemencie formatu, jeśli jest obecny, jest ignorowana.  
  
 Wyrównanie zostanie zastosowane po wykonaniu poprzednich kroków.  
  
## <a name="code-examples"></a>Przykłady kodu  
 W poniższym przykładzie przedstawiono jeden ciąg utworzony przy użyciu złożone formatowanie i drugą utworzone za pomocą obiektu `ToString` metody. Oba typy formatowania dają równoważne wyniki.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 Przy założeniu, że w bieżącym dniu jest czwartek w maju, wartości obu parametrów w poprzednim przykładzie jest `Thursday May` w Stanach Zjednoczonych Kultura angielskiej wersji językowej.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> Opisuje te same funkcje co <xref:System.String.Format%2A?displayProperty=nameWithType>. Jedyną różnicą między obiema metodami jest to, że <xref:System.String.Format%2A?displayProperty=nameWithType> zwraca wynik jako ciąg znaków, podczas <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> zapisu do strumienia wyjściowego wynik skojarzony z <xref:System.Console> obiektu. W poniższym przykładzie użyto <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metody do formatowania wartości `MyInt` na wartość waluty.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 W poniższym przykładzie pokazano formatowanie wielu obiektów, w tym formatowanie jednego obiektu na dwa różne sposoby.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 W poniższym przykładzie pokazano użycie wyrównania w formatowaniu. Argumenty, które są sformatowane umieszcza się pomiędzy pionowy pasek znaków (&#124;) aby wyróżnić wynikowy wyrównania.  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Console.WriteLine%2A>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 [Ciąg interpolacji (C#)](../../csharp/language-reference/tokens/interpolated.md)  
 [Ciąg interpolacji (Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)  
 [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
 [Standardowe ciągi formatujące liczby](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [Niestandardowe ciągi formatujące liczby](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Niestandardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [Standardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)  
 [Niestandardowe ciągi formatujące TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)  
 [Ciągi formatujące wyliczenia](../../../docs/standard/base-types/enumeration-format-strings.md)
