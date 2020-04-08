---
ms.openlocfilehash: f131933f3cf7890939854c46f115e8deb8da1cc2
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888176"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a>StringInfo i TextElementEnumerator są teraz zgodne z UAX29

Przed tą <xref:System.Globalization.StringInfo?displayProperty=fullName> zmianą <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> i nie poprawnie obsługiwać wszystkie klastry grafeme. Niektóre grafemy zostały podzielone na ich składniki składowe, a nie trzymane razem. Teraz <xref:System.Globalization.StringInfo> i <xref:System.Globalization.TextElementEnumerator> przetwarzaj klastry grafeme zgodnie z najnowszą wersją standardu Unicode.

Ponadto <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> metoda, która odwraca znaki w ciągu w języku Visual Basic, teraz jest również zgodna ze standardem Unicode dla klastrów grafem.

#### <a name="change-description"></a>Zmień opis

Klaster [grafem lub](https://www.unicode.org/glossary/#grapheme) [rozszerzony grafem](https://www.unicode.org/glossary/#extended_grapheme_cluster) jest pojedynczym znakiem postrzeganym przez użytkownika, który może składać się z wielu punktów kodu Unicode. Na przykład ciąg zawierający tajski znak "kam" (:::no-loc text="กำ":::) składa się z następujących dwóch znaków:

- :::no-loc text="ก":::(= '\u0e01') TAJSKI CHARAKTER KO KAI
- :::no-loc text=" ำ":::(= '\u0e3') TAJSKI CHARAKTER SARA AM

Po wyświetleniu użytkownikowi system operacyjny łączy dwa znaki, tworząc pojedynczy znak wyświetlania (lub grafem) "kam" lub :::no-loc text="กำ":::. Emoji może również składać się z wielu znaków, które są łączone do wyświetlania w podobny sposób.

> [!TIP]
> W dokumentacji .NET czasami używa terminu "element tekstowy" podczas odwoływania się do grapheme.

I <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> klasy sprawdzić ciągi i zwracać informacje o graphemes, które zawierają. W programach .NET Framework (wszystkie wersje) i .NET Core 3.x i wcześniejszych, te dwie klasy używają niestandardowej logiki, która obsługuje niektóre łączenie klas, ale nie jest w pełni zgodna ze [standardem Unicode.](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries) Na przykład <xref:System.Globalization.StringInfo> klasy <xref:System.Globalization.TextElementEnumerator> i niepoprawnie podzielić pojedynczy tajski znak "kam" z powrotem do jego składników składników zamiast utrzymywać je razem. Klasy te również niepoprawnie podzielić znak emoji "🤷🏽 ♀️" na cztery klastry (osoba shrugging, modyfikator odcienia skóry, modyfikator płci i niewidoczne kombajnu) zamiast utrzymywać je razem jako pojedynczy klaster grafeme.

Począwszy od .NET <xref:System.Globalization.StringInfo> 5, i <xref:System.Globalization.TextElementEnumerator> klasy implementują standard Unicode zgodnie z definicją [standardu Unicode załącznik 29, \#rev. 35, s. 3](https://www.unicode.org/reports/tr29/tr29-35.html). W szczególności teraz zwracają [rozszerzone klastry grafeme](https://www.unicode.org/glossary/#extended_grapheme_cluster) dla wszystkich łączących klas.

Należy wziąć pod uwagę następujący kod języka C#:

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

W programach .NET Framework i .NET Core 3.x oraz wcześniejszych wersjach grafimy są dzielone, a dane wyjściowe konsoli są następujące:

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

W wersji .NET 5 i nowszych grafemy są przechowywane razem, a dane wyjściowe konsoli są następujące:

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

Ponadto, począwszy od .NET <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> 5, metoda, która odwraca znaki w ciągu w języku Visual Basic, teraz również następuje standard Unicode dla klastrów grafem.

Zmiany te są częścią szerszego zestawu ulepszeń Unicode i UTF-8 w .NET, w tym rozszerzonego interfejsu API wyliczenia klastra grafeme w <xref:System.Text.Rune?displayProperty=fullName> celu uzupełnienia interfejsów API wyliczania skalarnej wartości Unicode, które zostały wprowadzone z typem w programie .NET Core 3.0.

#### <a name="version-introduced"></a>Wprowadzono wersję

.NET 5.0 Wersja zapoznawcza 1

### <a name="recommended-action"></a>Zalecana akcja

Nie trzeba podejmować żadnych działań. Aplikacje będą automatycznie zachowywać się w sposób bardziej zgodny ze standardami w różnych scenariuszach związanych z globalizacją.

### <a name="category"></a>Kategoria

Globalizacja

### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
