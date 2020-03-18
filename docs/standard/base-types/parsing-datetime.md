---
title: 'Jak: konwertować ciągi do DateTime'
description: Poznaj techniki analizować ciągi, które reprezentują daty i godziny, aby utworzyć DateTime od ciągu daty i godziny.
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
ms.openlocfilehash: 9555304e570226b2ed3b040735cf099b5a018f93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156546"
---
# <a name="parsing-date-and-time-strings-in-net"></a>Analizowanie ciągów daty i godziny w .NET

Analizowanie ciągów w celu <xref:System.DateTime> przekonwertowania ich na obiekty wymaga określenia informacji o sposobie przedstawiania dat i godzin jako tekstu. Różne kultury używają różnych zamówień w dzień, miesiąc i rok. Niektóre reprezentacje czasu używają zegara 24-godzinnego, inne określają "AM" i "PM". Niektóre aplikacje potrzebują tylko daty. Inni potrzebują tylko czasu. Jeszcze inni muszą określić zarówno datę, jak i godzinę. Metody, które konwertują ciągi do <xref:System.DateTime> obiektów umożliwiają podanie szczegółowych informacji o formatach, których oczekujesz i elementów daty i godziny aplikacji potrzeb. Istnieją trzy podzadania do prawidłowego konwertowania <xref:System.DateTime>tekstu na:

1. Należy określić oczekiwany format tekstu reprezentującego datę i godzinę.
1. Można określić kulturę formatu daty.
1. Można określić, jak brakujące komponenty w reprezentacji tekstu są ustawiane w dacie i godzinie.

Metody <xref:System.DateTime.Parse%2A> <xref:System.DateTime.TryParse%2A> i konwertują wiele wspólnych reprezentacji daty i godziny. Metody <xref:System.DateTime.ParseExact%2A> <xref:System.DateTime.TryParseExact%2A> i konwertuj reprezentację ciągu, która jest zgodna z wzorcem określonym przez ciąg formatu daty i godziny. (Szczegółowe informacje można znaleźć w artykułach dotyczących [standardowych ciągów formatu daty i godziny](standard-date-and-time-format-strings.md) oraz [niestandardowych ciągów formatu daty i godziny).](custom-date-and-time-format-strings.md)

Bieżący <xref:System.Globalization.DateTimeFormatInfo> obiekt zapewnia większą kontrolę nad tym, jak tekst powinien być interpretowany jako data i godzina. Właściwości opisują <xref:System.Globalization.DateTimeFormatInfo> separatory daty i godziny oraz nazwy miesięcy, dni i epok oraz format oznaczeń "AM" i "PM". Bieżąca kultura wątku <xref:System.Globalization.DateTimeFormatInfo> zapewnia, który reprezentuje bieżącą kulturę. Jeśli chcesz określonej kultury lub ustawień niestandardowych, należy określić <xref:System.IFormatProvider> parametr metody analizy. Dla <xref:System.IFormatProvider> parametru należy <xref:System.Globalization.CultureInfo> określić obiekt, który reprezentuje <xref:System.Globalization.DateTimeFormatInfo> kulturę lub obiekt.

W tekście przedstawiającym datę lub godzinę może brakować pewnych informacji. Na przykład większość ludzi zakłada, że data "12 marca" reprezentuje bieżący rok. Podobnie "Marzec 2018" oznacza marzec w roku 2018. Tekst reprezentujący czas często obejmuje tylko godziny, minuty i oznaczenie AM/PM.  Metody analizowania obsługi tych brakujących informacji przy użyciu rozsądnych ustawień domyślnych:

- Gdy bieżąca jest tylko godzina, część daty używa bieżącej daty.
- Gdy obecna jest tylko data, część czasu to północ.
- Jeśli rok nie jest określony w dacie, bieżący rok jest używany.
- Jeśli dzień miesiąca nie jest określony, używany jest pierwszy miesiąc.

Jeśli data jest obecna w ciągu, musi zawierać miesiąc i jeden dzień lub rok. Jeśli czas jest obecny, musi zawierać godzinę i minuty lub oznaczenie AM/PM.

Można określić <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> stałą, aby zastąpić te wartości domyślne. W przypadku korzystania z tej stałej wszystkie brakujące właściwości roku, `1`miesiąca lub dnia są ustawiane na wartość . [Ostatni przykład](#styles-example) <xref:System.DateTime.Parse%2A> za pomocą demonstruje to zachowanie.

Oprócz daty i składnika czasu, reprezentacja ciągu daty i godziny może zawierać przesunięcie, które wskazuje, jak bardzo czas różni się od skoordynowanego czasu uniwersalnego (UTC). Na przykład ciąg "2/14/2007 5:32:00 -7:00" definiuje czas, który jest siedem godzin wcześniej niż UTC. Jeśli przesunięcie zostanie pominięte w reprezentacji ciągu czasu, analizowanie <xref:System.DateTime> zwraca <xref:System.DateTime.Kind%2A> obiekt z <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>jego właściwością ustawioną na . Jeśli określono przesunięcie, analizowanie zwraca <xref:System.DateTime> obiekt z <xref:System.DateTime.Kind%2A> jego <xref:System.DateTimeKind.Local?displayProperty=nameWithType> właściwości ą ustawioną na i jego wartością dostosowaną do lokalnej strefy czasowej komputera. To zachowanie można zmodyfikować <xref:System.Globalization.DateTimeStyles> przy użyciu wartości z metodą analizy.
  
Dostawca formatu jest również używany do interpretowania niejednoznacznej daty liczbowej. Nie jest jasne, które składniki daty reprezentowane przez ciąg "02/03/04" są miesiącem, dniem i rokiem. Składniki są interpretowane zgodnie z kolejnością podobnych formatów dat w dostawcy formatu.

## <a name="parse"></a>Analizuj

Poniższy przykład ilustruje <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> użycie metody `string` do <xref:System.DateTime>konwersji na . W tym przykładzie użyto kultury skojarzonej z bieżącym wątku. Jeśli <xref:System.Globalization.CultureInfo> skojarzony z bieżącej kultury nie <xref:System.FormatException> można przeanalizować ciąg wejściowy, a jest generowany.

> [!TIP]
> Wszystkie przykłady języka C# w tym artykule są uruchamiane w przeglądarce. Naciśnij przycisk **Uruchom,** aby wyświetlić dane wyjściowe. Możesz również edytować je, aby eksperymentować samodzielnie.

> [!NOTE]
> Te przykłady są dostępne w reppo dokumentów GitHub dla [języka C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/conversions) i [Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/how-to/conversions). Możesz też pobrać projekt jako plik zip dla [języka C#](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/conversions.zip) lub [Visual Basic.](https://github.com/dotnet/samples/raw/master/snippets/visualbasic/how-to/conversions.zip)

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Można również jawnie zdefiniować kulturę, której konwencje formatowania są używane podczas analizowania ciągu. Należy określić jeden <xref:System.Globalization.DateTimeFormatInfo> ze standardowych obiektów <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> zwracanych przez właściwość. W poniższym przykładzie użyto dostawcy formatu do <xref:System.DateTime>przeanalizowania ciągu niemieckiego w pliku . Tworzy <xref:System.Globalization.CultureInfo> reprezentujących `de-DE` kultury. Ten `CultureInfo` obiekt zapewnia pomyślne analizowanie tego określonego ciągu. Wyklucza to, niezależnie od <xref:System.Threading.Thread.CurrentCulture> tego, jakie ustawienie znajduje się w <xref:System.Threading.Thread.CurrentThread>pliku .  
  
[!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

Jednak mimo że można użyć <xref:System.DateTime.Parse%2A> przeciążenia metody, aby określić dostawców formatu niestandardowego, metoda nie obsługuje analizowanie formatów niestandardowych. Aby przeanalizować datę i godzinę wyrażoną w formacie <xref:System.DateTime.ParseExact%2A> niestandardowym, należy użyć tej metody.  

<a name="styles-example"></a>W poniższym <xref:System.Globalization.DateTimeStyles> przykładzie użyto wyliczenia, aby określić, że <xref:System.DateTime> bieżące informacje o dacie i godzinie nie powinny być dodawane do dla nieokreślonych pól.  

[!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]

## <a name="parseexact"></a>Parseexact

Metoda <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> konwertuje ciąg <xref:System.DateTime> do obiektu, jeśli jest zgodny z jednym z określonych desek ciągu. Gdy ciąg, który nie jest jednym z określonych form <xref:System.FormatException> jest przekazywany do tej metody, a jest generowany. Można określić jeden ze standardowych specyfikatorów daty i godziny lub kombinację specyfikatorów formatu niestandardowego. Za pomocą specyfikatorów formatu niestandardowego można skonstruować niestandardowy ciąg rozpoznawania. Aby uzyskać wyjaśnienie specyfikatorów, zobacz tematy dotyczące [standardowych ciągów formatu daty i godziny](standard-date-and-time-format-strings.md) oraz [niestandardowych ciągów formatu daty i godziny](custom-date-and-time-format-strings.md).  

W poniższym przykładzie <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> metoda jest przekazywana obiektu ciągu do analizy, a następnie <xref:System.Globalization.CultureInfo> specyfikator formatu, a następnie obiektu. Ta <xref:System.DateTime.ParseExact%2A> metoda może analizować tylko ciągi, które są `en-US` zgodne z wzorcem daty długiej w kulturze.  

[!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Każde przeciążenie <xref:System.DateTime.Parse%2A> <xref:System.DateTime.ParseExact%2A> i metody ma <xref:System.IFormatProvider> również parametr, który zawiera informacje specyficzne dla kultury o formatowaniu ciągu. Ten <xref:System.IFormatProvider> obiekt <xref:System.Globalization.CultureInfo> jest obiektem, który reprezentuje <xref:System.Globalization.DateTimeFormatInfo> kultury standardowej lub <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> obiektu, który jest zwracany przez właściwość.  <xref:System.DateTime.ParseExact%2A>Używa również dodatkowy ciąg lub ciąg tablicy argument, który definiuje jeden lub więcej niestandardowych formatów daty i godziny.  

## <a name="see-also"></a>Zobacz też

- [Analiza składniowa ciągów](parsing-strings.md)
- [Formatowanie typów](formatting-types.md)
- [Konwersja typów w programie .NET](type-conversion.md)
- [Standardowe formaty daty i godziny](standard-date-and-time-format-strings.md)
- [Niestandardowe ciągi formatu daty i godziny](custom-date-and-time-format-strings.md)
