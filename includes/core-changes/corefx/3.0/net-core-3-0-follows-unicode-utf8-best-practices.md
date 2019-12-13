---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568087"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="31748-101">Środowisko .NET Core 3,0 jest zgodne z najlepszymi rozwiązaniami Unicode podczas zamiany niepoprawnie sformułowanych sekwencji bajtów UTF-8</span><span class="sxs-lookup"><span data-stu-id="31748-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="31748-102">Gdy Klasa <xref:System.Text.UTF8Encoding> napotka niewłaściwie sformułowaną sekwencję bajtów UTF-8 w trakcie operacji transkodowania typu "Byte do znaków", zastąpi tę sekwencję znakiem "" (U + znak ZASTĘPCZy FFFD) w ciągu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="31748-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="31748-103">Program .NET Core 3,0 różni się od poprzednich wersji programu .NET Core i .NET Framework, zgodnie z najlepszymi rozwiązaniami Unicode dotyczącymi wykonywania tego zastąpienia podczas operacji transkodowania.</span><span class="sxs-lookup"><span data-stu-id="31748-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="31748-104">Jest to część większego nakładu pracy w celu poprawienia obsługi UTF-8 w całym środowisku .NET, w tym w przypadku nowych typów <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> i <xref:System.Text.Rune?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="31748-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="31748-105"><xref:System.Text.UTF8Encoding> typ został osiągnięty Ulepszona obsługa błędów Mechanics, dzięki czemu generowanie danych wyjściowych jest spójne z nowo wprowadzonymi typami.</span><span class="sxs-lookup"><span data-stu-id="31748-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="31748-106">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="31748-106">Change description</span></span>

<span data-ttu-id="31748-107">Począwszy od platformy .NET Core 3,0, podczas transkodowania bajtów do znaków, Klasa <xref:System.Text.UTF8Encoding> wykonuje podstawienie znaków na podstawie najlepszych rozwiązań w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="31748-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="31748-108">Używany mechanizm podstawiania jest opisany w [standardzie Unicode, w wersji 12,0, sek. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) w nagłówku zatytułowanym _U + FFFD podstawianie z maksymalną częścią_.</span><span class="sxs-lookup"><span data-stu-id="31748-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="31748-109">To zachowanie ma zastosowanie _tylko_ wtedy, gdy sekwencja bajtów wejściowych zawiera źle sformułowane dane UTF-8.</span><span class="sxs-lookup"><span data-stu-id="31748-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="31748-110">Ponadto jeśli wystąpienie <xref:System.Text.UTF8Encoding> zostało skonstruowane z `throwOnInvalidBytes: true` (patrz [dokumentacja konstruktora UTF8Encoding] (<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, wystąpienie `UTF8Encoding` będzie nadal zgłaszać na nieprawidłowym wejściu, zamiast wykonywać zamianę U + FFFD.</span><span class="sxs-lookup"><span data-stu-id="31748-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="31748-111">Poniżej przedstawiono wpływ tej zmiany na nieprawidłowe dane wejściowe 3-bajtowe:</span><span class="sxs-lookup"><span data-stu-id="31748-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="31748-112">Niewłaściwie sformułowane dane wejściowe 3-bajtowe</span><span class="sxs-lookup"><span data-stu-id="31748-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="31748-113">Dane wyjściowe przed platformą .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="31748-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="31748-114">Dane wyjściowe rozpoczynające się od platformy .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="31748-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="31748-115">`[ FFFD FFFD ]` (2-znakowe dane wyjściowe)</span><span class="sxs-lookup"><span data-stu-id="31748-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="31748-116">`[ FFFD FFFD FFFD ]` (3-znakowe wyjście)</span><span class="sxs-lookup"><span data-stu-id="31748-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="31748-117">Ten 3-znakowy wynik jest preferowanym wyjściem, zgodnie z _tabelą 3-9_ poprzednio połączonego pliku PDF w standardzie Unicode.</span><span class="sxs-lookup"><span data-stu-id="31748-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="31748-118">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="31748-118">Version introduced</span></span>

<span data-ttu-id="31748-119">3.0</span><span class="sxs-lookup"><span data-stu-id="31748-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="31748-120">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="31748-120">Recommended action</span></span>

<span data-ttu-id="31748-121">W części dewelopera nie jest wymagana żadna akcja.</span><span class="sxs-lookup"><span data-stu-id="31748-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="31748-122">Category</span><span class="sxs-lookup"><span data-stu-id="31748-122">Category</span></span>

<span data-ttu-id="31748-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="31748-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="31748-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="31748-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
