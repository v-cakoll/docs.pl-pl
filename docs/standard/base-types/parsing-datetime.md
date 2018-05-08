---
title: 'Porady: Konwertowanie ciągów na DateTime'
description: Dowiedz się technik w celu analizy ciągów reprezentujących daty i godziny, aby utworzyć wartości daty i godziny na podstawie ciągu daty i godziny.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c093f22f77284d15e56c8f1d4a95afbeb75202d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="parsing-date-and-time-strings-in-net"></a>Analizowanie ciągów daty i godziny w .NET

Analizowanie ciągów je, aby przekonwertować <xref:System.DateTime> obiektów wymaga podania informacji o sposobie daty i godziny są reprezentowane jako tekst. Innych kultur użyć różnych zamówienia na dzień, miesiąc i rok. Niektóre reprezentacje czasu używać 24-godzinnym, inne określ "AM" i "PM". Niektóre aplikacje potrzebują tylko data. Inni użytkownicy potrzebują tylko raz. Nadal inne należy określić zarówno daty i czasu. Konwertowanie ciągów do metody <xref:System.DateTime> obiektów umożliwiają zawierają szczegółowe informacje o formatów spodziewasz się i elementy daty i godziny do potrzeb aplikacji. Istnieją trzy podzadania do poprawnie konwersji tekstu do <xref:System.DateTime>:

1. Należy określić z oczekiwanym formatem tekst reprezentujący datę i godzinę.
1. Można określić kulturę używaną do formatu daty godziny.
1. Można określić sposób brakujące składniki w tekście reprezentacja wartości są ustawiane w datę i godzinę.

<xref:System.DateTime.Parse%2A> i <xref:System.DateTime.TryParse%2A> metody przekonwertować wiele typowych liczbami w postaci daty i godziny. <xref:System.DateTime.ParseExact%2A> i <xref:System.DateTime.TryParseExact%2A> metody konwersji reprezentację ciągu, który jest zgodny z wzorcem określona przez ciąg formatu daty i godziny. (Zobacz artykuły w [standardowa Data i godzina ciągi formatujące](standard-date-and-time-format-strings.md) i [niestandardowa data i godzina ciągi formatujące](custom-date-and-time-format-strings.md) Aby uzyskać więcej informacji.)


Bieżący <xref:System.Globalization.DateTimeFormatInfo> obiekt zapewnia większą kontrolę nad jak tekst powinny być rozumiane jako datę i godzinę. Właściwości <xref:System.Globalization.DateTimeFormatInfo> opisano Data i godzina separatorów i nazwy miesięcy, dni, Arial i format nazw "AM" i "PM". Udostępnia bieżącej kultury wątku <xref:System.Globalization.DateTimeFormatInfo> reprezentujący bieżącej kultury. Jeśli chcesz określoną kulturę lub ustawienia niestandardowe, określ <xref:System.IFormatProvider> parametr metody analizy. Dla <xref:System.IFormatProvider> parametru, określ <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kultury, lub <xref:System.Globalization.DateTimeFormatInfo> obiektu.

Tekst reprezentujący daty lub godziny może brakować niektórych informacji. Większość użytkowników czy Załóżmy na przykład daty "12 marca" reprezentuje w bieżącym roku. Podobnie "Marca 2018" reprezentuje marcu 2018 roku. Tekst, który często reprezentująca czasu jest tylko obejmuje godziny, minuty i oznaczenie AM/PM.  Podczas analizowania metod obsługi brakujących informacji przy użyciu rozsądne wartości domyślne:

- Jeśli jest tylko raz, część daty używa bieżącej daty.
- Występuje tylko data części czasu po północy.
- Po roku nie określono daty, jest używany w bieżącym roku.
- Gdy dzień miesiąca nie jest określony, używany jest pierwszego dnia miesiąca.

Jeśli istnieje w ciągu daty, musi on zawierać miesiąc i dzień lub rok. Jeśli czas jest obecny, musi on zawierać godzinę i protokole lub wskaźnik AM/PM.

Można określić <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> stała, aby zastąpić wartości domyślne. Gdy używasz tej stałej, wszelkie brakujące roku, miesiąca lub dnia właściwości są ustawione na wartość `1`. [Przykładu](#styles-example) przy użyciu <xref:System.DateTime.Parse%2A> pokazano to zachowanie.

Oprócz daty i czasu składnika reprezentację ciągu daty i godziny mogą obejmować przesunięcie, która wskazuje, ile czasu różni się od uniwersalny czas koordynowany (UTC). Na przykład ciąg "2007-2-14 5:32:00 -7:00" definiuje czas, który jest siedem godziny wcześniejszy niż czas UTC. W przypadku pominięcia przesunięcie z reprezentacji ciągu czas analizowania zwraca <xref:System.DateTime> obiekt z jego <xref:System.DateTime.Kind%2A> ustawioną właściwość <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Jeśli określono przesunięcia, analizowania zwraca <xref:System.DateTime> obiekt z jego <xref:System.DateTime.Kind%2A> ustawioną właściwość <xref:System.DateTimeKind.Local?displayProperty=nameWithType> i jego wartość dostosowana do lokalnej strefy czasowej komputera. To zachowanie można zmienić za pomocą <xref:System.Globalization.DateTimeStyles> wartości z metody analizy.
  
Dostawca formatu służy również do interpretowania niejednoznaczne daty liczbowych. Nie jest jasne, są składniki daty reprezentowany przez ciąg "02/03/04" dzień, miesiąc i rok. Składniki są interpretowane zgodnie z kolejnością podobne formaty daty w formacie dostawcy.

## <a name="parse"></a>analizy

Poniższy przykład przedstawia użycie <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> metodę, aby przekonwertować `string` do <xref:System.DateTime>. W tym przykładzie użyto kultury skojarzone z bieżącego wątku. Jeśli <xref:System.Globalization.CultureInfo> skojarzone z bieżącej kultury nie może przeanalizować składni ciągu wejściowego <xref:System.FormatException> jest generowany.

> [!TIP]
> Uruchom wszystkie C# przykłady w tym artykule w przeglądarce. Naciśnij klawisz **Uruchom** przycisk, aby wyświetlić dane wyjściowe. Można również edytować je, aby wypróbować samodzielnie.

> [!NOTE]
> Te przykłady są dostępne w repozytorium GitHub dokumentów dla obu [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/conversions) i [VB](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/how-to/conversions). Można również pobrać projekt jako ścieżki dla [C#](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/conversions.zip) lub [VB](https://github.com/dotnet/samples/raw/master/snippets/visualbasic/how-to/conversions.zip).

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Można również jawnie definiować kultury, na których Konwencji formatowania są używane podczas analizy ciągu. Można określić jeden ze standardowych <xref:System.Globalization.DateTimeFormatInfo> obiekty zwrócone przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości. W poniższym przykładzie użyto dostawcy formatu do analizowania niemieckim do <xref:System.DateTime>. Tworzy <xref:System.Globalization.CultureInfo> reprezentujący `de-DE` kultury. Czy `CultureInfo` obiektu zapewnia powiodło się podczas analizowania tego określonego ciągu. Wykluczy to niezależnie od ustawienie znajduje się w <xref:System.Threading.Thread.CurrentCulture> z <xref:System.Threading.Thread.CurrentThread>.  
  
[!code-csharp-interactive[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

Jednak mimo że używasz przeciążeń <xref:System.DateTime.Parse%2A> metodę, aby określić dostawców formatu niestandardowego, metoda nie obsługuje analizowania niestandardowych formatów. Aby przeanalizować daty i czasu wyrażona w niestandardowym formacie, użyj <xref:System.DateTime.ParseExact%2A> metody zamiast tego.  

<a name="styles-example"></a>W poniższym przykładzie użyto <xref:System.Globalization.DateTimeStyles> wyliczeniu, aby określić, że nie można dodać bieżących informacji o datę i godzinę do <xref:System.DateTime> pól nieokreślony.  

[!code-csharp-interactive[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]
 
## <a name="parseexact"></a>ParseExact

<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> Metoda konwertuje ciąg na <xref:System.DateTime> obiektu, jeśli odpowiada jednemu wzorców określonego ciągu. Ciąg, który nie jest jednym z formularzy określony jest przekazany do tej metody <xref:System.FormatException> jest generowany. Można określić jeden z standardowa Data i godzina specyfikatory formatu lub kombinacja specyfikatorów formatu niestandardowego. Używanie specyfikatorów formatu niestandardowego, jest można skonstruować ciąg rozpoznawania niestandardowych. Aby uzyskać informacje o Specyfikatory, zobacz Tematy w [standardowa Data i godzina ciągi formatujące](standard-date-and-time-format-strings.md) i [niestandardowa data i godzina ciągi formatujące](custom-date-and-time-format-strings.md).  

W poniższym przykładzie <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> metody jest przekazywany obiekt ciągu do analizy, następuje specyfikatora formatu, a następnie <xref:System.Globalization.CultureInfo> obiektu. To <xref:System.DateTime.ParseExact%2A> metody można analizować tylko ciągów, które są zgodne ze wzorcem daty długiej w `en-US` kultury.  

[!code-csharp-interactive[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Każdy przeciążenia <xref:System.DateTime.Parse%2A> i <xref:System.DateTime.ParseExact%2A> ma również metody <xref:System.IFormatProvider> parametr, który zawiera informacje specyficzne dla kultury dotyczące formatowania ciągu. To <xref:System.IFormatProvider> obiekt jest <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje standardowe kultury lub <xref:System.Globalization.DateTimeFormatInfo> obiektu, który jest zwracany przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości.  <xref:System.DateTime.ParseExact%2A> używa również dodatkowy ciąg lub argument tablicy ciąg, który definiuje co najmniej jeden niestandardowa data i godzina formatów.  

## <a name="see-also"></a>Zobacz też  
 [Analizowanie ciągów](parsing-strings.md)  
 [Formatowanie typów](formatting-types.md)  
 [Konwersja typów w programie .NET](type-conversion.md)  
 [Formatuje standardowa Data i godzina](standard-date-and-time-format-strings.md)  
 [Niestandardowa data i godzina ciągi formatujące](custom-date-and-time-format-strings.md)
