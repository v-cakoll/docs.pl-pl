---
title: 'Instrukcje: konwertowanie ciągów na DateTime'
description: Poznaj techniki analizowania ciągów, które reprezentują daty i godziny, aby utworzyć datę i godzinę z ciągu daty i godziny.
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parsing strings, date and time strings
- date and time strings
- ParseExact method
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- DateTime object
- time strings
ms.openlocfilehash: 16daa0ef3133b6cd04dc48b7f79fd365098e4bdf
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348072"
---
# <a name="parsing-date-and-time-strings-in-net"></a>Analizowanie ciągów daty i godziny w programie .NET

Analizowanie ciągów w celu przekonwertowania ich do obiektów <xref:System.DateTime> wymaga określenia informacji o tym, jak daty i godziny są reprezentowane jako tekst. Różne kultury używają różnej kolejności dla dnia, miesiąca i roku. Niektóre reprezentacje czasu używają zegara 24-godzinnego, inne określają "AM" i "PM". Niektóre aplikacje wymagają tylko daty. Inne osoby potrzebują tylko czasu. Nadal inne osoby muszą określić datę i godzinę. Metody, które konwertują ciągi na <xref:System.DateTime> obiektów, umożliwiają dostarczenie szczegółowych informacji na temat oczekiwanych formatów oraz elementów daty i czasu potrzebnych aplikacji. Istnieją trzy podzadania, które umożliwiają poprawne Konwertowanie tekstu na <xref:System.DateTime>:

1. Należy określić oczekiwany format tekstu reprezentującego datę i godzinę.
1. Można określić kulturę dla formatu daty i godziny.
1. Możesz określić, jak brakujące składniki w reprezentacji tekstowej są ustawiane w dacie i godzinie.

Metody <xref:System.DateTime.Parse%2A> i <xref:System.DateTime.TryParse%2A> konwertują wiele typowych reprezentacji daty i godziny. Metody <xref:System.DateTime.ParseExact%2A> i <xref:System.DateTime.TryParseExact%2A> konwertują reprezentację ciągu, która jest zgodna ze wzorcem określonym przez ciąg formatu daty i godziny. (Aby uzyskać szczegółowe informacje, zobacz artykuły dotyczące [standardowych ciągów formatu daty i godziny](standard-date-and-time-format-strings.md) oraz [niestandardowych ciągów formatu daty i godziny](custom-date-and-time-format-strings.md) ).

Bieżący obiekt <xref:System.Globalization.DateTimeFormatInfo> zapewnia większą kontrolę nad sposobem interpretowania tekstu jako daty i godziny. Właściwości <xref:System.Globalization.DateTimeFormatInfo> opisują separatory daty i godziny oraz nazwy miesięcy, dni i wymazywania oraz format oznaczeń "AM" i "PM". Bieżąca kultura wątku zawiera <xref:System.Globalization.DateTimeFormatInfo>, która reprezentuje bieżącą kulturę. Jeśli potrzebujesz określonych kultur lub ustawień niestandardowych, określisz parametr <xref:System.IFormatProvider> metody analizy. Dla parametru <xref:System.IFormatProvider> Określ obiekt <xref:System.Globalization.CultureInfo>, który reprezentuje kulturę lub obiekt <xref:System.Globalization.DateTimeFormatInfo>.

Tekst reprezentujący datę lub godzinę może nie zawierać pewnych informacji. Na przykład większość osób przyjmuje datę "12 marca" reprezentującą bieżący rok. Podobnie "marzec 2018" oznacza miesiąc marca w roku 2018. Tekst reprezentujący czas często obejmuje tylko godziny, minuty i oznaczenie AM/PM.  Metody analizy obsługują te brakujące informacje przy użyciu odpowiednich wartości domyślnych:

- Gdy jest obecny tylko czas, część daty używa bieżącej daty.
- Gdy tylko data jest obecna, częścią czasu jest północ.
- Jeśli rok nie jest określony w dacie, używany jest bieżący rok.
- Gdy nie jest określony dzień miesiąca, jest używany pierwszy miesiąc.

Jeśli data jest obecna w ciągu, musi zawierać miesiąc i jeden dzień lub rok. Jeśli czas jest obecny, musi zawierać godzinę oraz liczbę minut lub oznaczenie AM/PM.

Możesz określić stałą <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault>, aby zastąpić te ustawienia domyślne. Gdy używasz tej stałej, wszystkie brakujące właściwości Year, Month lub Day są ustawiane na wartość `1`. W [ostatnim przykładzie](#styles-example) użyto <xref:System.DateTime.Parse%2A> przedstawiono to zachowanie.

Oprócz daty i składnika czasu, Reprezentacja ciągu daty i godziny może zawierać przesunięcie, które wskazuje, ile czasu różni się od uniwersalnego czasu koordynowanego (UTC). Na przykład ciąg "2/14/2007 5:32:00 -7:00" definiuje godzinę, która jest siedem godzin wcześniejsza od czasu UTC. Jeśli przesunięcie zostanie pominięte na podstawie ciągu reprezentującego godzinę, analiza zwraca obiekt <xref:System.DateTime> z właściwością <xref:System.DateTime.Kind%2A> ustawioną na <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Jeśli wartość przesunięcia jest określona, funkcja analizowania zwraca obiekt <xref:System.DateTime> z właściwością <xref:System.DateTime.Kind%2A> ustawioną na <xref:System.DateTimeKind.Local?displayProperty=nameWithType> i jego wartości dostosowuje się do lokalnej strefy czasowej maszyny. Możesz zmodyfikować to zachowanie przy użyciu wartości <xref:System.Globalization.DateTimeStyles> z metodą analizy.
  
Dostawca formatu jest również używany do interpretowania niejednoznacznej daty liczbowej. Nie jest jasne, które składniki daty reprezentowanej przez ciąg "02/03/04" to miesiąc, dzień i rok. Składniki są interpretowane zgodnie z kolejnością podobnych formatów daty w dostawcy formatu.

## <a name="parse"></a>Analizuj

Poniższy przykład ilustruje użycie metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, aby skonwertować `string` do <xref:System.DateTime>. W tym przykładzie zastosowano kulturę skojarzoną z bieżącym wątkiem. Jeśli <xref:System.Globalization.CultureInfo> skojarzona z bieżącą kulturą nie może przeanalizować ciągu wejściowego, zostanie zgłoszony <xref:System.FormatException>.

> [!TIP]
> Wszystkie C# przykłady w tym artykule działają w przeglądarce. Naciśnij przycisk **Run (Uruchom** ), aby wyświetlić dane wyjściowe. Możesz również edytować je, aby samodzielnie eksperymentować.

> [!NOTE]
> Te przykłady są dostępne w repozytorium docs w witrynie GitHub dla [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/conversions) obu i [Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/how-to/conversions). Lub można pobrać projekt jako plik ZIP dla [C#](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/conversions.zip) lub [Visual Basic](https://github.com/dotnet/samples/raw/master/snippets/visualbasic/how-to/conversions.zip).

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Można również jawnie zdefiniować kulturę, której konwencje formatowania są używane podczas analizowania ciągu. Należy określić jeden ze standardowych obiektów <xref:System.Globalization.DateTimeFormatInfo> zwracanych przez właściwość <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>. Poniższy przykład używa dostawcy formatu do analizy ciągu niemieckiego w <xref:System.DateTime>. Tworzy <xref:System.Globalization.CultureInfo> reprezentujący `de-DE` kulturę. Ten obiekt `CultureInfo` gwarantuje pomyślne analizowanie tego określonego ciągu. Wyklucza to, niezależnie od tego, jakie ustawienie znajduje się w <xref:System.Threading.Thread.CurrentCulture> <xref:System.Threading.Thread.CurrentThread>.  
  
[!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

Jednak chociaż można użyć przeciążenia metody <xref:System.DateTime.Parse%2A>, aby określić dostawców formatów niestandardowych, metoda nie obsługuje analizowania formatów niestandardowych. Aby przeanalizować datę i godzinę wyrażoną w formacie niestandardowym, należy zamiast tego użyć metody <xref:System.DateTime.ParseExact%2A>.  

<a name="styles-example"></a>Poniższy przykład używa wyliczenia <xref:System.Globalization.DateTimeStyles>, aby określić, że bieżące informacje o dacie i godzinie nie powinny być dodawane do <xref:System.DateTime> dla nieokreślonych pól.  

[!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]
 
## <a name="parseexact"></a>ParseExact

Metoda <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> konwertuje ciąg na obiekt <xref:System.DateTime>, jeśli jest zgodny z jednym z określonych wzorców ciągu. Gdy ciąg, który nie jest jednym z określonych formularzy jest przenoszona do tej metody, zostanie zgłoszony <xref:System.FormatException>. Można określić jeden z standardowych specyfikatorów formatu daty i godziny lub kombinację niestandardowych specyfikatorów formatu. Przy użyciu specyfikatorów formatu niestandardowego można utworzyć niestandardowy ciąg rozpoznawania. Aby uzyskać wyjaśnienie specyfikatorów, zobacz tematy dotyczące [standardowych ciągów formatu daty i godziny](standard-date-and-time-format-strings.md) oraz [niestandardowych ciągów formatu daty i godziny](custom-date-and-time-format-strings.md).  

W poniższym przykładzie metoda <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> jest przenoszona przez obiekt ciągu do analizy, po którym następuje specyfikator formatu, po którym następuje obiekt <xref:System.Globalization.CultureInfo>. Ta metoda <xref:System.DateTime.ParseExact%2A> może analizować tylko ciągi, które są zgodne ze wzorcem daty długiej w kulturze `en-US`.  

[!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Każde Przeciążenie metod <xref:System.DateTime.Parse%2A> i <xref:System.DateTime.ParseExact%2A> również ma <xref:System.IFormatProvider> parametr, który zawiera informacje specyficzne dla kultury dotyczące formatowania ciągu. Ten obiekt <xref:System.IFormatProvider> jest obiektem <xref:System.Globalization.CultureInfo>, który reprezentuje kulturę standardową lub obiekt <xref:System.Globalization.DateTimeFormatInfo>, który jest zwracany przez właściwość <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>.  <xref:System.DateTime.ParseExact%2A> używa również dodatkowego argumentu ciągu lub tablicy ciągów, który definiuje jeden lub więcej niestandardowych formatów daty i godziny.  

## <a name="see-also"></a>Zobacz także

- [Analizowanie ciągów](parsing-strings.md)
- [Formatowanie typów](formatting-types.md)
- [Konwersja typów w programie .NET](type-conversion.md)
- [Standardowe formaty daty i godziny](standard-date-and-time-format-strings.md)
- [Niestandardowe ciągi formatujące datę i godzinę](custom-date-and-time-format-strings.md)
