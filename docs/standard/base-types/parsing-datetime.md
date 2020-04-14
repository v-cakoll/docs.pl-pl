---
title: Konwertowanie ciągów na DateTime
description: Dowiedz się techniki analizowania ciągów, które reprezentują daty i godziny, aby utworzyć DateTime z daty i ciągu godziny.
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
ms.openlocfilehash: 4b3f0bdb3ade784f929718a3350ed3dec0c572f1
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242650"
---
# <a name="parse-date-and-time-strings-in-net"></a>Analizuj ciągi daty i godziny w .NET

Analizowanie ciągów w celu <xref:System.DateTime> przekonwertowania ich na obiekty wymaga określenia informacji o sposobie przedstawiania dat i godzin jako tekstu. Różne kultury używają różnych zamówień na dzień, miesiąc i rok. Niektóre reprezentacje czasu używają zegara 24-godzinnego, inne określają "AM" i "PM". Niektóre aplikacje potrzebują tylko daty. Inni potrzebują tylko czasu. Jeszcze inni muszą określić zarówno datę, jak i godzinę. Metody konwertowania <xref:System.DateTime> ciągów na obiekty umożliwiają dostarczenie szczegółowych informacji o oczekiwanych formatach oraz elementach daty i godziny, których potrzebuje aplikacja. Istnieją trzy podzadania, aby poprawnie <xref:System.DateTime>konwertować tekst na:

1. Należy określić oczekiwany format tekstu reprezentującego datę i godzinę.
1. Można określić kulturę dla formatu daty.
1. Można określić sposób ustawiania brakujących składników w reprezentacji tekstu w dniu i godzinie.

I <xref:System.DateTime.Parse%2A> <xref:System.DateTime.TryParse%2A> metody konwertować wiele wspólnych reprezentacji daty i godziny. I <xref:System.DateTime.ParseExact%2A> <xref:System.DateTime.TryParseExact%2A> metody konwertować reprezentację ciągu, który jest zgodny ze wzorcem określonym przez ciąg formatu daty i godziny. (Aby uzyskać szczegółowe informacje, zobacz artykuły dotyczące [standardowych ciągów formatu daty i](standard-date-and-time-format-strings.md) godziny oraz [niestandardowe ciągi formatu daty i godziny).](custom-date-and-time-format-strings.md)

Bieżący <xref:System.Globalization.DateTimeFormatInfo> obiekt zapewnia większą kontrolę nad tym, jak tekst powinien być interpretowany jako data i godzina. Właściwości opisują <xref:System.Globalization.DateTimeFormatInfo> separatory daty i godziny oraz nazwy miesięcy, dni i epok oraz format oznaczeń "AM" i "PM". Bieżąca kultura wątku <xref:System.Globalization.DateTimeFormatInfo> zapewnia, który reprezentuje bieżącą kulturę. Jeśli chcesz określonej kultury lub ustawienia <xref:System.IFormatProvider> niestandardowe, należy określić parametr metody analizy. Dla <xref:System.IFormatProvider> parametru należy <xref:System.Globalization.CultureInfo> określić obiekt, który <xref:System.Globalization.DateTimeFormatInfo> reprezentuje kulturę lub obiekt.

W tekście reprezentującym datę lub godzinę mogą brakować pewnych informacji. Na przykład większość osób zakłada, że data "12 marca" reprezentuje bieżący rok. Podobnie "Marzec 2018" oznacza miesiąc marzec w roku 2018. Tekst reprezentujący czas często zawiera tylko godziny, minuty i oznaczenie AM/PM.  Metody analizowania obsługi tych brakujących informacji przy użyciu rozsądnych ustawień domyślnych:

- Gdy tylko czas jest obecny, część daty używa bieżącej daty.
- Gdy tylko data jest obecna, część czasu jest północ.
- Jeśli rok nie jest określony w dacie, używany jest bieżący rok.
- Gdy dzień miesiąca nie jest określony, używany jest pierwszy miesiąc.

Jeśli data jest obecna w ciągu, musi zawierać miesiąc i jeden z dnia lub roku. Jeśli czas jest obecny, musi zawierać godzinę i protokół lub am/pm oznaczacza.

Można określić <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> stałą, aby zastąpić te wartości domyślne. W przypadku użycia tej stałej wszystkie brakujące właściwości roku, `1`miesiąca lub dnia są ustawiane na wartość . [Ostatni przykład](#styles-example) <xref:System.DateTime.Parse%2A> przy użyciu demonstruje to zachowanie.

Oprócz składnika daty i czasu reprezentacja ciągu daty i godziny może zawierać przesunięcie, które wskazuje, jak bardzo czas różni się od skoordynowanego czasu uniwersalnego (UTC). Na przykład ciąg "2/14/2007 5:32:00 -7:00" definiuje czas, który jest siedem godzin wcześniej niż UTC. Jeśli przesunięcie zostanie pominięte w reprezentacji ciągu czasu, <xref:System.DateTime> analizowanie <xref:System.DateTime.Kind%2A> zwraca obiekt <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>z jego właściwością ustawioną na . Jeśli określono przesunięcie, analizowanie zwraca <xref:System.DateTime> obiekt <xref:System.DateTime.Kind%2A> z ustawioną właściwością <xref:System.DateTimeKind.Local?displayProperty=nameWithType> i jego wartością dostosowaną do lokalnej strefy czasowej komputera. To zachowanie można zmodyfikować <xref:System.Globalization.DateTimeStyles> przy użyciu wartości przy użyciu metody analizy.
  
Dostawca formatu jest również używany do interpretowania niejednoznacznej daty liczbowej. Nie jest jasne, które składniki daty reprezentowane przez ciąg "02/03/04" są miesiąc, dzień i rok. Składniki są interpretowane zgodnie z kolejnością podobnych formatów dat w dostawcy formatów.

## <a name="parse"></a>Analizuj

Poniższy przykład ilustruje <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> użycie metody `string` do <xref:System.DateTime>konwersji a na . W tym przykładzie użyto kultury skojarzonej z bieżącym wątkiem. Jeśli <xref:System.Globalization.CultureInfo> skojarzone z bieżącej kultury nie można przeanalizować ciąg wejściowy, a <xref:System.FormatException> jest generowany.

> [!TIP]
> Wszystkie przykłady języka C# w tym artykule są uruchamiane w przeglądarce. Naciśnij przycisk **Uruchom,** aby wyświetlić dane wyjściowe. Można je również edytować, aby eksperymentować samodzielnie.

> [!NOTE]
> Te przykłady są dostępne w repozytorium dokumentów GitHub dla języka [C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/conversions) i [Visual Basic.](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/how-to/conversions) Możesz też pobrać projekt jako plik zip dla [języka C#](https://github.com/dotnet/docs/blob/master/samples/snippets/csharp/how-to/conversions.zip) lub [Visual Basic](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/how-to/conversions.zip).

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Można również jawnie zdefiniować kultury, których konwencje formatowania są używane podczas analizowania ciągu. Należy określić jeden <xref:System.Globalization.DateTimeFormatInfo> ze standardowych <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> obiektów zwracanych przez właściwość. W poniższym przykładzie użyto dostawcy formatu do <xref:System.DateTime>przeanalizowania niemieckiego ciągu w pliku . Tworzy reprezentującą <xref:System.Globalization.CultureInfo> `de-DE` kulturę. Ten `CultureInfo` obiekt zapewnia pomyślne analizowanie tego określonego ciągu. Wyklucza to, cokolwiek <xref:System.Threading.Thread.CurrentCulture> ustawienie <xref:System.Threading.Thread.CurrentThread>jest w .  
  
[!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

Jednak chociaż można użyć przeciążenia <xref:System.DateTime.Parse%2A> metody, aby określić dostawców formatu niestandardowego, metoda nie obsługuje analizowania formatów niestandardowych. Aby przeanalizować datę i godzinę wyrażoną w niestandardowym <xref:System.DateTime.ParseExact%2A> formacie, należy użyć metody.  

<a name="styles-example"></a>W poniższym przykładzie użyto wyliczenia, <xref:System.Globalization.DateTimeStyles> aby określić, że <xref:System.DateTime> informacje o bieżącej dacie i godzinie nie powinny być dodawane do nieokreślonych pól.  

[!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]

## <a name="parseexact"></a>Parseexact

Metoda <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> konwertuje ciąg <xref:System.DateTime> do obiektu, jeśli jest zgodny z jednym z określonych wzorców ciągu. Gdy ciąg, który nie jest jednym z określonych formularzy jest przekazywana do tej metody, a <xref:System.FormatException> jest generowany. Można określić jeden ze standardowych specyfikatorów formatu daty i godziny lub kombinację specyfikatorów formatu niestandardowego. Za pomocą specyfikatorów formatu niestandardowego możliwe jest skonstruowanie niestandardowego ciągu rozpoznawania. Aby uzyskać wyjaśnienie specyfikatorów, zobacz tematy dotyczące [standardowych ciągów formatu daty i godziny](standard-date-and-time-format-strings.md) oraz [ciągów niestandardowego formatu daty i godziny](custom-date-and-time-format-strings.md).  

W poniższym przykładzie <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> metoda jest przekazywana obiekt ciąg do analizy, a <xref:System.Globalization.CultureInfo> następnie specyfikator formatu, a następnie obiekt. Ta <xref:System.DateTime.ParseExact%2A> metoda może analizować tylko ciągi, które `en-US` są zgodne ze wzorcem daty długiej w kulturze.  

[!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Każde przeciążenie <xref:System.DateTime.Parse%2A> <xref:System.DateTime.ParseExact%2A> i metody <xref:System.IFormatProvider> ma również parametr, który zawiera informacje specyficzne dla kultury o formatowaniu ciągu. Ten <xref:System.IFormatProvider> obiekt <xref:System.Globalization.CultureInfo> jest obiektem reprezentującym <xref:System.Globalization.DateTimeFormatInfo> standardową kulturę lub <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> obiekt zwracany przez właściwość.  <xref:System.DateTime.ParseExact%2A>używa również dodatkowego argumentu tablicy ciągu lub ciągu, który definiuje jeden lub więcej niestandardowych formatów daty i godziny.  

## <a name="see-also"></a>Zobacz też

- [Analiza składniowa ciągów](parsing-strings.md)
- [Formatowanie typów](formatting-types.md)
- [Wpisz konwersję w .NET](type-conversion.md)
- [Standardowe formaty daty i godziny](standard-date-and-time-format-strings.md)
- [Niestandardowe ciągi formatujące datę i godzinę](custom-date-and-time-format-strings.md)
