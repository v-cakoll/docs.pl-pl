---
ms.openlocfilehash: c0c1c9c9d8e3aeb6f689f754d09b50b208b54112
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702324"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a>StringInfo i TextElementEnumerator są teraz zgodne UAX29

Przed tą zmianą <xref:System.Globalization.StringInfo?displayProperty=fullName> i <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> nieprawidłowo obsługiwała wszystkie klastry Grapheme. Niektóre graphemes zostały podzielone na składniki składowe, a nie ze sobą. Teraz <xref:System.Globalization.StringInfo> i <xref:System.Globalization.TextElementEnumerator> Przetwarzaj klastry Grapheme zgodnie z najnowszą wersją standardu Unicode.

Ponadto <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> Metoda, która odwraca znaki w ciągu w Visual Basic, jest teraz również zgodna ze standardem Unicode dla klastrów Grapheme.

#### <a name="change-description"></a>Zmień opis

[Grapheme](https://www.unicode.org/glossary/#grapheme) lub [rozszerzony klaster Grapheme](https://www.unicode.org/glossary/#extended_grapheme_cluster) jest pojedynczym postrzeganym przez użytkownika znakiem, który może składać się z wielu punktów kodowych Unicode. Na przykład ciąg zawierający znak tajlandzki "Kam" ( :::no-loc text="กำ"::: ) składa się z następujących dwóch znaków:

- :::no-loc text="ก":::(= "\u0e01") TAJSKI ZNAK KO KAI
- :::no-loc text=" ำ":::(= "\u0e33") TAJSKI ZNAK SARA AM

W przypadku wyświetlania użytkownikowi system operacyjny łączy dwa znaki, aby utworzyć pojedynczy znak wyświetlania (lub Grapheme) "Kam" lub :::no-loc text="กำ"::: . Emoji może również składać się z wielu znaków, które są połączone do wyświetlania w podobny sposób.

> [!TIP]
> Dokumentacja platformy .NET czasami używa terminu "element tekstowy" podczas odwoływania się do Grapheme.

<xref:System.Globalization.StringInfo>Klasy i <xref:System.Globalization.TextElementEnumerator> sprawdzają ciągi i zwracają informacje o graphemes, które zawierają. W .NET Framework (wszystkie wersje) i .NET Core 3. x i wcześniejszych te dwie klasy używają logiki niestandardowej, która obsługuje niektóre łączące się klasy, ale nie jest w pełni zgodna ze [standardem Unicode](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries). Na przykład <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> klasy i niepoprawnie dzielą pojedynczy znak tajlandzki "Kam" na jego składniki składowe, zamiast przechowywać je jednocześnie. Te klasy również niepoprawnie dzielą znak emoji "🤷🏽 ♀️" na cztery klastry (shrugging osoby, modyfikator odcienia skórki, modyfikator płci i niewidoczny program łączący), zamiast przechowywać je razem jako pojedynczy klaster Grapheme.

Począwszy od platformy .NET 5, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> klasy i implementują standard Unicode zgodnie z definicją w [standardzie Unicode w załączniku \# 29, Rev. 35, sek. 3](https://www.unicode.org/reports/tr29/tr29-35.html). W szczególności zwracają one [rozbudowane klastry Grapheme](https://www.unicode.org/glossary/#extended_grapheme_cluster) dla wszystkich łączonych klas.

Rozważmy następujący kod w języku C#:

```cs
using System.Globalization;

static void Main(string[] args)
{
    PrintGraphemes("กำ");
    PrintGraphemes("🤷🏽‍♀️");
}

static void PrintGraphemes(string str)
{
    Console.WriteLine($"Printing graphemes of \"{str}\"...");
    int i = 0;

    TextElementEnumerator enumerator = StringInfo.GetTextElementEnumerator(str);
    while (enumerator.MoveNext())
    {
        Console.WriteLine($"Grapheme {++i}: \"{enumerator.Current}\"");
    }

    Console.WriteLine($"({i} grapheme(s) total.)");
    Console.WriteLine();
}
```

W .NET Framework i .NET Core 3. x i starszych wersji graphemes są dzielone, a dane wyjściowe konsoli są następujące:

```txt
Printing graphemes of "กำ"...
Grapheme 1: "ก"
Grapheme 2: "ำ"
(2 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷"
Grapheme 2: "🏽"
Grapheme 3: "‍"
Grapheme 4: "♀️"
(4 grapheme(s) total.)
```

W programie .NET 5 i nowszych wersjach graphemes są połączone, a dane wyjściowe konsoli są następujące:

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

Ponadto począwszy od platformy .NET 5 <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> Metoda, która odwraca znaki w ciągu w Visual Basic, teraz jest również zgodna ze standardem Unicode dla klastrów Grapheme.

Te zmiany są częścią szerszego zestawu ulepszeń Unicode i UTF-8 w programie .NET, w tym rozszerzonego interfejsu API wyliczania klastrów Grapheme, który uzupełnia interfejsy API wyliczania wartości skalarnych Unicode, które zostały wprowadzone z <xref:System.Text.Rune?displayProperty=fullName> typem w programie .NET Core 3,0.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET 5,0 — wersja zapoznawcza 1

#### <a name="recommended-action"></a>Zalecana akcja

Nie trzeba podejmować żadnych działań. Aplikacje będą automatycznie działać w sposób zgodny ze standardami w różnych scenariuszach związanych z globalizacją.

#### <a name="category"></a>Kategoria

Globalizacja

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
