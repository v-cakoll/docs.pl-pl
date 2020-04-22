---
ms.openlocfilehash: 843c78bb4e4f88d9ac58308a91ab8278364c9580
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021583"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="f3a16-101">Program .NET Core 3.0 jest zgodny z najlepszymi rozwiązaniami firmy Unicode podczas zastępowania źle sformułowanych sekwencji bajtów UTF-8</span><span class="sxs-lookup"><span data-stu-id="f3a16-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="f3a16-102">Gdy <xref:System.Text.UTF8Encoding> klasa napotka źle sformułowaną sekwencję bajtów UTF-8 podczas operacji transkodowania bajt-znak, zastąpi tę sekwencję znakiem ' ' (U+ FFFD REPLACEMENT CHARACTER) w ciągu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="f3a16-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="f3a16-103">Program .NET Core 3.0 różni się od poprzednich wersji programu .NET Core i programu .NET Framework, postępując zgodnie z najlepszą praktyką unicode dla wykonywania tej wymiany podczas operacji transkodowania.</span><span class="sxs-lookup"><span data-stu-id="f3a16-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="f3a16-104">Jest to część większego wysiłku, aby poprawić utf-8 obsługi <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> w <xref:System.Text.Rune?displayProperty=nameWithType> całej .NET, w tym przez nowe i typy.</span><span class="sxs-lookup"><span data-stu-id="f3a16-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="f3a16-105">Typ <xref:System.Text.UTF8Encoding> został ulepszony mechanika obsługi błędów, tak aby produkować dane wyjściowe zgodne z nowo wprowadzonych typów.</span><span class="sxs-lookup"><span data-stu-id="f3a16-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f3a16-106">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="f3a16-106">Change description</span></span>

<span data-ttu-id="f3a16-107">Począwszy od .NET Core 3.0, podczas transkodowania bajtów do znaków, <xref:System.Text.UTF8Encoding> klasa wykonuje podstawienie znaków na podstawie najlepszych rozwiązań Unicode.</span><span class="sxs-lookup"><span data-stu-id="f3a16-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="f3a16-108">Stosowany mechanizm zastępowania jest opisany przez [Standard Unicode, wersja 12.0, sek.](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) _U+FFFD Substitution of Maximal Subparts_</span><span class="sxs-lookup"><span data-stu-id="f3a16-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="f3a16-109">To zachowanie ma zastosowanie _tylko_ wtedy, gdy sekwencja bajtów wejściowych zawiera źle sformułowane dane UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f3a16-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="f3a16-110"><xref:System.Text.UTF8Encoding> Ponadto jeśli wystąpienie zostało skonstruowane `throwOnInvalidBytes: true` za pomocą (zobacz [UTF8Wcoding<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>konstruktora dokumentacji]( , `UTF8Encoding` wystąpienie będzie nadal rzucać na nieprawidłowe dane wejściowe, a nie wykonać zastąpienie U + FFFD.</span><span class="sxs-lookup"><span data-stu-id="f3a16-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="f3a16-111">Poniżej przedstawiono wpływ tej zmiany z nieprawidłowym wejściem 3-bajtowym:</span><span class="sxs-lookup"><span data-stu-id="f3a16-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="f3a16-112">Źle sformułowane wejście 3-bajtowe</span><span class="sxs-lookup"><span data-stu-id="f3a16-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="f3a16-113">Wyjście przed .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f3a16-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="f3a16-114">Wyjście zaczynające się od .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f3a16-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="f3a16-115">`[ FFFD FFFD ]`(wyjście 2-znakowe)</span><span class="sxs-lookup"><span data-stu-id="f3a16-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="f3a16-116">`[ FFFD FFFD FFFD ]`(wyjście 3-znakowe)</span><span class="sxs-lookup"><span data-stu-id="f3a16-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="f3a16-117">To wyjście 3-char jest preferowanym wyjściem, zgodnie z _tabelą 3-9_ wcześniej połączonego standardu Unicode PDF.</span><span class="sxs-lookup"><span data-stu-id="f3a16-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f3a16-118">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="f3a16-118">Version introduced</span></span>

<span data-ttu-id="f3a16-119">3.0</span><span class="sxs-lookup"><span data-stu-id="f3a16-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f3a16-120">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="f3a16-120">Recommended action</span></span>

<span data-ttu-id="f3a16-121">Nie jest wymagana żadna akcja ze strony dewelopera.</span><span class="sxs-lookup"><span data-stu-id="f3a16-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="f3a16-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="f3a16-122">Category</span></span>

<span data-ttu-id="f3a16-123">Podstawowe biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="f3a16-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f3a16-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f3a16-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
