---
title: 'Porady: Konwertowanie ciągów na daty i godziny'
description: Poznaj techniki do analizowania ciągów reprezentujących daty i godziny, aby otrzymać wartość typu DateTime z ciągu daty i godziny.
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
ms.openlocfilehash: 4c8aa10c25fd7459bebb1de6d71a54b6e361e20e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560819"
---
# <a name="parsing-date-and-time-strings-in-net"></a>Analizowanie ciągów daty i godziny na platformie .NET

Analizowanie ciągów w celu przekonwertowania ich do <xref:System.DateTime> obiektów wymaga podania informacji o jak daty i godziny są reprezentowane jako tekst. Różne kultury używają różnych zleceniach dzień, miesiąc i rok. Niektóre reprezentacje czas użycia zegara 24-godzinnego, innych użytkowników określ, "AM" i "PM". Niektóre aplikacje potrzebują tylko data. Inni użytkownicy potrzebują tylko raz. Nadal inni użytkownicy potrzebują do określenia daty i godziny. Metody, które konwertują ciągi do <xref:System.DateTime> obiektów umożliwiają uzyskanie szczegółowych informacji dotyczących formatów oczekujesz, a elementom daty i godziny do potrzeb aplikacji. Istnieją trzy podzadania poprawnie Konwertowanie tekstu do <xref:System.DateTime>:

1. Należy określić oczekiwany format tekstowy reprezentujący datę i godzinę.
1. Użytkownik może określić kulturę używaną do formatu daty, godziny.
1. Można określić sposób brakujących składników w tekście reprezentacji są ustawiane w daty i godziny.

<xref:System.DateTime.Parse%2A> i <xref:System.DateTime.TryParse%2A> konwertują wiele typowych liczbami w postaci daty i godziny. <xref:System.DateTime.ParseExact%2A> i <xref:System.DateTime.TryParseExact%2A> konwertują reprezentację ciągu znaków, który jest zgodny z wzorcem, określona przez ciąg formatu daty i godziny. (Zobacz artykuły w [ciągi formatu standardowego daty i godziny](standard-date-and-time-format-strings.md) i [niestandardowa data i godzina ciągi formatujące](custom-date-and-time-format-strings.md) Aby uzyskać szczegółowe informacje.)


Bieżący <xref:System.Globalization.DateTimeFormatInfo> obiekt zapewnia większą kontrolę nad jak tekst należy interpretować jako daty i godziny. Właściwości <xref:System.Globalization.DateTimeFormatInfo> opisują Data i godzina separatory i nazwy miesięcy, dni, a ery i format oznaczenia "AM" i "PM". Bieżąca kultura wątku dostarcza <xref:System.Globalization.DateTimeFormatInfo> reprezentujący bieżącą kulturę. Jeśli chcesz, aby ustawienia niestandardowe lub określonej kultury, określ <xref:System.IFormatProvider> parametr metody analizy. Dla <xref:System.IFormatProvider> parametru, określ <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kulturę, lub <xref:System.Globalization.DateTimeFormatInfo> obiektu.

Tekst reprezentujący datę lub godzinę może brakować niektórych informacji. Większość użytkowników będzie Załóżmy na przykład daty "12 marca" reprezentuje bieżący rok. Podobnie "Marca 2018 r." przedstawia miesiąc marca w roku 2018 r. Tekst, który często reprezentujące czasu jest tylko obejmuje godziny, minuty i oznaczenie AM/PM.  Metody analizy obsługi brakujących informacji za pomocą odpowiednie wartości domyślne:

- Jeśli występuje tylko przy użyciu część dotycząca daty używa bieżącej daty.
- Jeśli występuje tylko data część godzinowa to północ.
- Po roku nie jest określona w dacie, jest używany w bieżącym roku.
- Jeśli dzień miesiąca nie jest określona, używana jest pierwszego dnia miesiąca.

Jeśli data znajduje się w ciągu, musi on zawierać miesiąc i dzień lub rok. Jeśli czas jest obecna, musi on zawierać godziny i minuty lub oznaczenia AM/PM.

Można określić <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> stałą, aby zastąpić te ustawienia domyślne. Gdy używasz tej stałej, wszelkie brakujące rok, miesiąc lub dzień właściwości są ustawione na wartość `1`. [Przykład ostatniego](#styles-example) przy użyciu <xref:System.DateTime.Parse%2A> przedstawia tego zachowania.

Oprócz datę i składnik czasu reprezentację ciągu daty i godziny mogą obejmować przesunięcia, która wskazuje, ile czasu różni się od skoordynowanego czasu uniwersalnego (UTC). Na przykład ciąg "2/14/2007 5:32:00 -7:00" definiuje czas oznacza to siedem godziny wcześniejszy niż w formacie UTC. W przypadku pominięcia przesunięcie z ciągu reprezentującego czas analizy zwraca <xref:System.DateTime> obiekt z jego <xref:System.DateTime.Kind%2A> właściwością <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Jeśli określono wartość przesunięcia, analizowania zwraca <xref:System.DateTime> obiekt z jego <xref:System.DateTime.Kind%2A> właściwością <xref:System.DateTimeKind.Local?displayProperty=nameWithType> , jego wartość dostosowane do lokalnej strefy czasowej komputera. To zachowanie można zmienić za pomocą <xref:System.Globalization.DateTimeStyles> wartość przy użyciu metody analizy.
  
Dostawca formatu służy także do interpretacji datę liczbowych niejednoznaczne. Nie jest jasne, które składniki Data jest reprezentowana przez ciąg "02/03/04" to dzień, miesiąc i rok. Składniki są interpretowane zgodnie z porządkiem podobne formatów daty w formacie dostawcy.

## <a name="parse"></a>Analizy

Poniższy przykład ilustruje użycie <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> metodę, aby przekonwertować `string` do <xref:System.DateTime>. W tym przykładzie użyto kultury skojarzonej z bieżącym wątkiem. Jeśli <xref:System.Globalization.CultureInfo> skojarzony z bieżącą kulturę nie można przeanalizować ciągu wejściowego <xref:System.FormatException> zgłaszany.

> [!TIP]
> Uruchom wszystkie C# przykłady w tym artykule w przeglądarce. Naciśnij klawisz **Uruchom** przycisk, aby wyświetlić dane wyjściowe. Można również edytować je samodzielnie wypróbować.

> [!NOTE]
> Te przykłady są dostępne w repozytorium GitHub docs dla obu [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/conversions) i [VB](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/how-to/conversions). Możesz też pobrać projekt jako zipfile dla [C#](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/conversions.zip) lub [VB](https://github.com/dotnet/samples/raw/master/snippets/visualbasic/how-to/conversions.zip).

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Można również jawnie określić kulturę, której konwencje formatowania są używane podczas analizy ciągu. Należy podać jedną z standard <xref:System.Globalization.DateTimeFormatInfo> obiektów zwróconych przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości. W poniższym przykładzie użyto dostawcę formatu, aby przeanalizować ciąg niemieckim do <xref:System.DateTime>. Tworzy <xref:System.Globalization.CultureInfo> reprezentujący `de-DE` kultury. Czy `CultureInfo` obiektu zapewnia pomyślne analizowania tego określonego ciągu. Wyklucza to, niezależnie od ustawienie znajduje się w <xref:System.Threading.Thread.CurrentCulture> z <xref:System.Threading.Thread.CurrentThread>.  
  
[!code-csharp-interactive[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

Jednak mimo że można użyć przeciążenia <xref:System.DateTime.Parse%2A> metodę, aby określić niestandardowych dostawców formatu, metoda nie obsługuje analizowania formatów niestandardowych. Aby przeanalizować daty i godziny wyrażony w postaci niestandardowych, należy użyć <xref:System.DateTime.ParseExact%2A> metody zamiast tego.  

<a name="styles-example"></a>W poniższym przykładzie użyto <xref:System.Globalization.DateTimeStyles> wyliczeniu, aby określić, czy bieżące informacje o daty i godziny nie można dodać do <xref:System.DateTime> dla pola nieokreślony.  

[!code-csharp-interactive[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]
 
## <a name="parseexact"></a>Parseexact —

<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> Metoda konwertuje ciąg na <xref:System.DateTime> obiektu, jeśli go jest zgodny z jednym z wzorców określonego ciągu. Gdy ciąg, który nie jest jednym z formularze określona jest przekazywany do tej metody <xref:System.FormatException> zgłaszany. Można określić jeden standardowy daty i godziny specyfikatorów formatu lub kombinację specyfikatorów formatu niestandardowego. Przy użyciu specyfikatorów formatu niestandardowego, jest możliwe do konstruowania ciągu niestandardowe rozpoznawanie. Objaśnienia dotyczące specyfikatorów, zobacz Tematy w [ciągi formatu standardowego daty i godziny](standard-date-and-time-format-strings.md) i [niestandardowa data i godzina ciągi formatujące](custom-date-and-time-format-strings.md).  

W poniższym przykładzie <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> metody jest przekazywany obiekt ciągu, aby analizować, następuje specyfikatora formatu, a następnie <xref:System.Globalization.CultureInfo> obiektu. To <xref:System.DateTime.ParseExact%2A> metoda można analizować tylko ciągi, które należy wykonać wzorzec daty długiej w `en-US` kultury.  

[!code-csharp-interactive[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Każdy przeciążenia <xref:System.DateTime.Parse%2A> i <xref:System.DateTime.ParseExact%2A> ma również metody <xref:System.IFormatProvider> parametr, który dostarcza specyficzne dla kultury informacje o formatowanie ciągu. To <xref:System.IFormatProvider> obiekt jest <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje standardowej kultury lub <xref:System.Globalization.DateTimeFormatInfo> obiektu, który jest zwracany przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości.  <xref:System.DateTime.ParseExact%2A> używa również dodatkowy ciąg znaków lub argument tablica ciągu, który definiuje co najmniej jeden niestandardowa data i godzina formatów.  

## <a name="see-also"></a>Zobacz także

- [Analizowanie ciągów](parsing-strings.md)
- [Formatowanie typów](formatting-types.md)
- [Konwersja typów w programie .NET](type-conversion.md)
- [Standardowa Data i godzina formatów](standard-date-and-time-format-strings.md)
- [Niestandardowa data i godzina ciągi formatujące](custom-date-and-time-format-strings.md)
