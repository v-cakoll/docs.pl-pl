---
ms.openlocfilehash: 0795ee244bf3d1261bbe61dc0c67c3936f427f04
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216347"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="a1dc6-101">Środowisko .NET Core 3,0 jest zgodne z najlepszymi rozwiązaniami Unicode podczas zamiany niepoprawnie sformułowanych sekwencji bajtów UTF-8</span><span class="sxs-lookup"><span data-stu-id="a1dc6-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="a1dc6-102"><xref:System.Text.UTF8Encoding> Gdy Klasa napotka niewłaściwie sformułowaną sekwencję bajtów UTF-8 podczas operacji transkodowania typu "Byte-to-Character", zastąpi tę sekwencję znakiem "" (U + znak zastępczy FFFD) w ciągu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a1dc6-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="a1dc6-103">Program .NET Core 3,0 różni się od poprzednich wersji programu .NET Core i .NET Framework, zgodnie z najlepszymi rozwiązaniami Unicode dotyczącymi wykonywania tego zastąpienia podczas operacji transkodowania.</span><span class="sxs-lookup"><span data-stu-id="a1dc6-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="a1dc6-104">Jest to część większego nakładu pracy w celu poprawienia obsługi UTF-8 w całym środowisku .NET <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> , <xref:System.Text.Rune?displayProperty=nameWithType> w tym w przypadku nowych i typów.</span><span class="sxs-lookup"><span data-stu-id="a1dc6-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="a1dc6-105"><xref:System.Text.UTF8Encoding> Typ został osiągnięty Ulepszona obsługa błędów Mechanics, tak aby dane wyjściowe były spójne z nowo wprowadzonymi typami.</span><span class="sxs-lookup"><span data-stu-id="a1dc6-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="details"></a><span data-ttu-id="a1dc6-106">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a1dc6-106">Details</span></span>

<span data-ttu-id="a1dc6-107">Począwszy od platformy .NET Core 3,0, podczas transkodowania bajtów do znaków, <xref:System.Text.UTF8Encoding> Klasa wykonuje podstawienie znaków na podstawie najlepszych rozwiązań w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="a1dc6-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="a1dc6-108">Używany mechanizm podstawiania jest opisany w [standardzie Unicode, w wersji 12,0, sek. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) w nagłówku zatytułowanym _U + FFFD podstawianie z maksymalną częścią_.</span><span class="sxs-lookup"><span data-stu-id="a1dc6-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="a1dc6-109">To zachowanie ma zastosowanie _tylko_ wtedy, gdy sekwencja bajtów wejściowych zawiera źle sformułowane dane UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a1dc6-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="a1dc6-110">Ponadto, jeśli <xref:System.Text.UTF8Encoding> wystąpienie zostało skonstruowane przy użyciu `throwOnInvalidBytes: true` (zobacz `UTF8Encoding` dokumentację konstruktora UTF8Encoding] (<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, wystąpienie będzie nadal zgłaszać nieprawidłowe dane wejściowe zamiast wykonywać U + FFFD zastępc.</span><span class="sxs-lookup"><span data-stu-id="a1dc6-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="a1dc6-111">Poniżej przedstawiono wpływ tej zmiany na nieprawidłowe dane wejściowe 3-bajtowe:</span><span class="sxs-lookup"><span data-stu-id="a1dc6-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="a1dc6-112">Niewłaściwie sformułowane dane wejściowe 3-bajtowe</span><span class="sxs-lookup"><span data-stu-id="a1dc6-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="a1dc6-113">Dane wyjściowe przed platformą .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="a1dc6-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="a1dc6-114">Dane wyjściowe rozpoczynające się od platformy .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="a1dc6-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="a1dc6-115">`[ FFFD FFFD ]`(2-znakowe dane wyjściowe)</span><span class="sxs-lookup"><span data-stu-id="a1dc6-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="a1dc6-116">`[ FFFD FFFD FFFD ]`(3 znaki wyjściowe)</span><span class="sxs-lookup"><span data-stu-id="a1dc6-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="a1dc6-117">Ten 3-znakowy wynik jest preferowanym wyjściem, zgodnie z _tabelą 3-9_ poprzednio połączonego pliku PDF w standardzie Unicode.</span><span class="sxs-lookup"><span data-stu-id="a1dc6-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a1dc6-118">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="a1dc6-118">Version introduced</span></span>

<span data-ttu-id="a1dc6-119">3.0</span><span class="sxs-lookup"><span data-stu-id="a1dc6-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a1dc6-120">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="a1dc6-120">Recommended action</span></span>

<span data-ttu-id="a1dc6-121">W części dewelopera nie jest wymagana żadna akcja.</span><span class="sxs-lookup"><span data-stu-id="a1dc6-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="a1dc6-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="a1dc6-122">Category</span></span>

<span data-ttu-id="a1dc6-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="a1dc6-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a1dc6-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a1dc6-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
