---
ms.openlocfilehash: c0c1c9c9d8e3aeb6f689f754d09b50b208b54112
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702324"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="f55fc-101">StringInfo i TextElementEnumerator są teraz zgodne UAX29</span><span class="sxs-lookup"><span data-stu-id="f55fc-101">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="f55fc-102">Przed tą zmianą <xref:System.Globalization.StringInfo?displayProperty=fullName> i <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> nieprawidłowo obsługiwała wszystkie klastry Grapheme.</span><span class="sxs-lookup"><span data-stu-id="f55fc-102">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="f55fc-103">Niektóre graphemes zostały podzielone na składniki składowe, a nie ze sobą.</span><span class="sxs-lookup"><span data-stu-id="f55fc-103">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="f55fc-104">Teraz <xref:System.Globalization.StringInfo> i <xref:System.Globalization.TextElementEnumerator> Przetwarzaj klastry Grapheme zgodnie z najnowszą wersją standardu Unicode.</span><span class="sxs-lookup"><span data-stu-id="f55fc-104">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="f55fc-105">Ponadto <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> Metoda, która odwraca znaki w ciągu w Visual Basic, jest teraz również zgodna ze standardem Unicode dla klastrów Grapheme.</span><span class="sxs-lookup"><span data-stu-id="f55fc-105">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f55fc-106">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="f55fc-106">Change description</span></span>

<span data-ttu-id="f55fc-107">[Grapheme](https://www.unicode.org/glossary/#grapheme) lub [rozszerzony klaster Grapheme](https://www.unicode.org/glossary/#extended_grapheme_cluster) jest pojedynczym postrzeganym przez użytkownika znakiem, który może składać się z wielu punktów kodowych Unicode.</span><span class="sxs-lookup"><span data-stu-id="f55fc-107">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="f55fc-108">Na przykład ciąg zawierający znak tajlandzki "Kam" ( :::no-loc text="กำ"::: ) składa się z następujących dwóch znaków:</span><span class="sxs-lookup"><span data-stu-id="f55fc-108">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="f55fc-109">:::no-loc text="ก":::(= "\u0e01") TAJSKI ZNAK KO KAI</span><span class="sxs-lookup"><span data-stu-id="f55fc-109">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="f55fc-110">:::no-loc text=" ำ":::(= "\u0e33") TAJSKI ZNAK SARA AM</span><span class="sxs-lookup"><span data-stu-id="f55fc-110">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="f55fc-111">W przypadku wyświetlania użytkownikowi system operacyjny łączy dwa znaki, aby utworzyć pojedynczy znak wyświetlania (lub Grapheme) "Kam" lub :::no-loc text="กำ"::: .</span><span class="sxs-lookup"><span data-stu-id="f55fc-111">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="f55fc-112">Emoji może również składać się z wielu znaków, które są połączone do wyświetlania w podobny sposób.</span><span class="sxs-lookup"><span data-stu-id="f55fc-112">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="f55fc-113">Dokumentacja platformy .NET czasami używa terminu "element tekstowy" podczas odwoływania się do Grapheme.</span><span class="sxs-lookup"><span data-stu-id="f55fc-113">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="f55fc-114"><xref:System.Globalization.StringInfo>Klasy i <xref:System.Globalization.TextElementEnumerator> sprawdzają ciągi i zwracają informacje o graphemes, które zawierają.</span><span class="sxs-lookup"><span data-stu-id="f55fc-114">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="f55fc-115">W .NET Framework (wszystkie wersje) i .NET Core 3. x i wcześniejszych te dwie klasy używają logiki niestandardowej, która obsługuje niektóre łączące się klasy, ale nie jest w pełni zgodna ze [standardem Unicode](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span><span class="sxs-lookup"><span data-stu-id="f55fc-115">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="f55fc-116">Na przykład <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> klasy i niepoprawnie dzielą pojedynczy znak tajlandzki "Kam" na jego składniki składowe, zamiast przechowywać je jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="f55fc-116">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="f55fc-117">Te klasy również niepoprawnie dzielą znak emoji "🤷🏽 ♀️" na cztery klastry (shrugging osoby, modyfikator odcienia skórki, modyfikator płci i niewidoczny program łączący), zamiast przechowywać je razem jako pojedynczy klaster Grapheme.</span><span class="sxs-lookup"><span data-stu-id="f55fc-117">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="f55fc-118">Począwszy od platformy .NET 5, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> klasy i implementują standard Unicode zgodnie z definicją w [standardzie Unicode w załączniku \# 29, Rev. 35, sek. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span><span class="sxs-lookup"><span data-stu-id="f55fc-118">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="f55fc-119">W szczególności zwracają one [rozbudowane klastry Grapheme](https://www.unicode.org/glossary/#extended_grapheme_cluster) dla wszystkich łączonych klas.</span><span class="sxs-lookup"><span data-stu-id="f55fc-119">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="f55fc-120">Rozważmy następujący kod w języku C#:</span><span class="sxs-lookup"><span data-stu-id="f55fc-120">Consider the following C# code:</span></span>

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

<span data-ttu-id="f55fc-121">W .NET Framework i .NET Core 3. x i starszych wersji graphemes są dzielone, a dane wyjściowe konsoli są następujące:</span><span class="sxs-lookup"><span data-stu-id="f55fc-121">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

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

<span data-ttu-id="f55fc-122">W programie .NET 5 i nowszych wersjach graphemes są połączone, a dane wyjściowe konsoli są następujące:</span><span class="sxs-lookup"><span data-stu-id="f55fc-122">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="f55fc-123">Ponadto począwszy od platformy .NET 5 <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> Metoda, która odwraca znaki w ciągu w Visual Basic, teraz jest również zgodna ze standardem Unicode dla klastrów Grapheme.</span><span class="sxs-lookup"><span data-stu-id="f55fc-123">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="f55fc-124">Te zmiany są częścią szerszego zestawu ulepszeń Unicode i UTF-8 w programie .NET, w tym rozszerzonego interfejsu API wyliczania klastrów Grapheme, który uzupełnia interfejsy API wyliczania wartości skalarnych Unicode, które zostały wprowadzone z <xref:System.Text.Rune?displayProperty=fullName> typem w programie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="f55fc-124">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f55fc-125">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="f55fc-125">Version introduced</span></span>

<span data-ttu-id="f55fc-126">.NET 5,0 — wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="f55fc-126">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f55fc-127">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="f55fc-127">Recommended action</span></span>

<span data-ttu-id="f55fc-128">Nie trzeba podejmować żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="f55fc-128">You don't need to take any action.</span></span> <span data-ttu-id="f55fc-129">Aplikacje będą automatycznie działać w sposób zgodny ze standardami w różnych scenariuszach związanych z globalizacją.</span><span class="sxs-lookup"><span data-stu-id="f55fc-129">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

#### <a name="category"></a><span data-ttu-id="f55fc-130">Kategoria</span><span class="sxs-lookup"><span data-stu-id="f55fc-130">Category</span></span>

<span data-ttu-id="f55fc-131">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="f55fc-131">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f55fc-132">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f55fc-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
