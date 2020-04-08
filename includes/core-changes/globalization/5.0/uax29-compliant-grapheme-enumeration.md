---
ms.openlocfilehash: f131933f3cf7890939854c46f115e8deb8da1cc2
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888176"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="b19e7-101">StringInfo i TextElementEnumerator są teraz zgodne z UAX29</span><span class="sxs-lookup"><span data-stu-id="b19e7-101">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="b19e7-102">Przed tą <xref:System.Globalization.StringInfo?displayProperty=fullName> zmianą <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> i nie poprawnie obsługiwać wszystkie klastry grafeme.</span><span class="sxs-lookup"><span data-stu-id="b19e7-102">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="b19e7-103">Niektóre grafemy zostały podzielone na ich składniki składowe, a nie trzymane razem.</span><span class="sxs-lookup"><span data-stu-id="b19e7-103">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="b19e7-104">Teraz <xref:System.Globalization.StringInfo> i <xref:System.Globalization.TextElementEnumerator> przetwarzaj klastry grafeme zgodnie z najnowszą wersją standardu Unicode.</span><span class="sxs-lookup"><span data-stu-id="b19e7-104">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="b19e7-105">Ponadto <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> metoda, która odwraca znaki w ciągu w języku Visual Basic, teraz jest również zgodna ze standardem Unicode dla klastrów grafem.</span><span class="sxs-lookup"><span data-stu-id="b19e7-105">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b19e7-106">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="b19e7-106">Change description</span></span>

<span data-ttu-id="b19e7-107">Klaster [grafem lub](https://www.unicode.org/glossary/#grapheme) [rozszerzony grafem](https://www.unicode.org/glossary/#extended_grapheme_cluster) jest pojedynczym znakiem postrzeganym przez użytkownika, który może składać się z wielu punktów kodu Unicode.</span><span class="sxs-lookup"><span data-stu-id="b19e7-107">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="b19e7-108">Na przykład ciąg zawierający tajski znak "kam" (:::no-loc text="กำ":::) składa się z następujących dwóch znaków:</span><span class="sxs-lookup"><span data-stu-id="b19e7-108">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="b19e7-109">:::no-loc text="ก":::(= '\u0e01') TAJSKI CHARAKTER KO KAI</span><span class="sxs-lookup"><span data-stu-id="b19e7-109">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="b19e7-110">:::no-loc text=" ำ":::(= '\u0e3') TAJSKI CHARAKTER SARA AM</span><span class="sxs-lookup"><span data-stu-id="b19e7-110">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="b19e7-111">Po wyświetleniu użytkownikowi system operacyjny łączy dwa znaki, tworząc pojedynczy znak wyświetlania (lub grafem) "kam" lub :::no-loc text="กำ":::.</span><span class="sxs-lookup"><span data-stu-id="b19e7-111">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="b19e7-112">Emoji może również składać się z wielu znaków, które są łączone do wyświetlania w podobny sposób.</span><span class="sxs-lookup"><span data-stu-id="b19e7-112">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="b19e7-113">W dokumentacji .NET czasami używa terminu "element tekstowy" podczas odwoływania się do grapheme.</span><span class="sxs-lookup"><span data-stu-id="b19e7-113">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="b19e7-114">I <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> klasy sprawdzić ciągi i zwracać informacje o graphemes, które zawierają.</span><span class="sxs-lookup"><span data-stu-id="b19e7-114">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="b19e7-115">W programach .NET Framework (wszystkie wersje) i .NET Core 3.x i wcześniejszych, te dwie klasy używają niestandardowej logiki, która obsługuje niektóre łączenie klas, ale nie jest w pełni zgodna ze [standardem Unicode.](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries)</span><span class="sxs-lookup"><span data-stu-id="b19e7-115">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="b19e7-116">Na przykład <xref:System.Globalization.StringInfo> klasy <xref:System.Globalization.TextElementEnumerator> i niepoprawnie podzielić pojedynczy tajski znak "kam" z powrotem do jego składników składników zamiast utrzymywać je razem.</span><span class="sxs-lookup"><span data-stu-id="b19e7-116">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="b19e7-117">Klasy te również niepoprawnie podzielić znak emoji "🤷🏽 ♀️" na cztery klastry (osoba shrugging, modyfikator odcienia skóry, modyfikator płci i niewidoczne kombajnu) zamiast utrzymywać je razem jako pojedynczy klaster grafeme.</span><span class="sxs-lookup"><span data-stu-id="b19e7-117">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="b19e7-118">Począwszy od .NET <xref:System.Globalization.StringInfo> 5, i <xref:System.Globalization.TextElementEnumerator> klasy implementują standard Unicode zgodnie z definicją [standardu Unicode załącznik 29, \#rev. 35, s. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span><span class="sxs-lookup"><span data-stu-id="b19e7-118">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="b19e7-119">W szczególności teraz zwracają [rozszerzone klastry grafeme](https://www.unicode.org/glossary/#extended_grapheme_cluster) dla wszystkich łączących klas.</span><span class="sxs-lookup"><span data-stu-id="b19e7-119">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="b19e7-120">Należy wziąć pod uwagę następujący kod języka C#:</span><span class="sxs-lookup"><span data-stu-id="b19e7-120">Consider the following C# code:</span></span>

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

<span data-ttu-id="b19e7-121">W programach .NET Framework i .NET Core 3.x oraz wcześniejszych wersjach grafimy są dzielone, a dane wyjściowe konsoli są następujące:</span><span class="sxs-lookup"><span data-stu-id="b19e7-121">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

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

<span data-ttu-id="b19e7-122">W wersji .NET 5 i nowszych grafemy są przechowywane razem, a dane wyjściowe konsoli są następujące:</span><span class="sxs-lookup"><span data-stu-id="b19e7-122">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="b19e7-123">Ponadto, począwszy od .NET <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> 5, metoda, która odwraca znaki w ciągu w języku Visual Basic, teraz również następuje standard Unicode dla klastrów grafem.</span><span class="sxs-lookup"><span data-stu-id="b19e7-123">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="b19e7-124">Zmiany te są częścią szerszego zestawu ulepszeń Unicode i UTF-8 w .NET, w tym rozszerzonego interfejsu API wyliczenia klastra grafeme w <xref:System.Text.Rune?displayProperty=fullName> celu uzupełnienia interfejsów API wyliczania skalarnej wartości Unicode, które zostały wprowadzone z typem w programie .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="b19e7-124">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b19e7-125">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="b19e7-125">Version introduced</span></span>

<span data-ttu-id="b19e7-126">.NET 5.0 Wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="b19e7-126">.NET 5.0 Preview 1</span></span>

### <a name="recommended-action"></a><span data-ttu-id="b19e7-127">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="b19e7-127">Recommended action</span></span>

<span data-ttu-id="b19e7-128">Nie trzeba podejmować żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="b19e7-128">You don't need to take any action.</span></span> <span data-ttu-id="b19e7-129">Aplikacje będą automatycznie zachowywać się w sposób bardziej zgodny ze standardami w różnych scenariuszach związanych z globalizacją.</span><span class="sxs-lookup"><span data-stu-id="b19e7-129">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

### <a name="category"></a><span data-ttu-id="b19e7-130">Kategoria</span><span class="sxs-lookup"><span data-stu-id="b19e7-130">Category</span></span>

<span data-ttu-id="b19e7-131">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="b19e7-131">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="b19e7-132">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b19e7-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
