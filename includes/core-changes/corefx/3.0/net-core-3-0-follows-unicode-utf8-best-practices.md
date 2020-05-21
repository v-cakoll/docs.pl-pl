---
ms.openlocfilehash: 298cb441bf9fe7daddb30c85f9d7366dc972628c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721713"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a><span data-ttu-id="4f9c7-101">Zastępowanie źle sformułowanych sekwencji bajtów w formacie UTF-8 następuje po wskazówkach dotyczących standardu Unicode</span><span class="sxs-lookup"><span data-stu-id="4f9c7-101">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>

<span data-ttu-id="4f9c7-102">Gdy <xref:System.Text.UTF8Encoding> Klasa napotka niewłaściwie sformułowaną sekwencję bajtów UTF-8 podczas operacji transkodowania typu "Byte do znaku", zastępuje tę sekwencję znakiem "" (U + znak zastępczy FFFD) w ciągu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4f9c7-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it replaces that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="4f9c7-103">Program .NET Core 3,0 różni się od poprzednich wersji programu .NET Core i .NET Framework, zgodnie z najlepszymi rozwiązaniami Unicode dotyczącymi wykonywania tego zastąpienia podczas operacji transkodowania.</span><span class="sxs-lookup"><span data-stu-id="4f9c7-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="4f9c7-104">Jest to część większego nakładu pracy w celu poprawienia obsługi UTF-8 w całym środowisku .NET, w tym w przypadku nowych <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> i <xref:System.Text.Rune?displayProperty=nameWithType> typów.</span><span class="sxs-lookup"><span data-stu-id="4f9c7-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="4f9c7-105"><xref:System.Text.UTF8Encoding>Typ został osiągnięty Ulepszona obsługa błędów Mechanics, tak aby dane wyjściowe były spójne z nowo wprowadzonymi typami.</span><span class="sxs-lookup"><span data-stu-id="4f9c7-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4f9c7-106">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="4f9c7-106">Change description</span></span>

<span data-ttu-id="4f9c7-107">Począwszy od platformy .NET Core 3,0, podczas transkodowania bajtów do znaków, <xref:System.Text.UTF8Encoding> Klasa wykonuje podstawienie znaków na podstawie najlepszych rozwiązań w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="4f9c7-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="4f9c7-108">Używany mechanizm podstawiania jest opisany w [standardzie Unicode, w wersji 12,0, sek. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) w nagłówku zatytułowanym _U + FFFD podstawianie z maksymalną częścią_.</span><span class="sxs-lookup"><span data-stu-id="4f9c7-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="4f9c7-109">To zachowanie ma zastosowanie _tylko_ wtedy, gdy sekwencja bajtów wejściowych zawiera źle sformułowane dane UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4f9c7-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="4f9c7-110">Ponadto jeśli wystąpienie zostało <xref:System.Text.UTF8Encoding> skonstruowane z `throwOnInvalidBytes: true` , `UTF8Encoding` wystąpienie będzie nadal zgłaszać nieprawidłowe dane wejściowe zamiast wykonywać zamianę U + FFFD.</span><span class="sxs-lookup"><span data-stu-id="4f9c7-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true`, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span> <span data-ttu-id="4f9c7-111">Aby uzyskać więcej informacji na temat `UTF8Encoding` konstruktora, zobacz <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)> .</span><span class="sxs-lookup"><span data-stu-id="4f9c7-111">For more information about the `UTF8Encoding` constructor, see <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>.</span></span>

<span data-ttu-id="4f9c7-112">W poniższej tabeli przedstawiono wpływ tej zmiany z nieprawidłowymi danymi wejściowymi 3-bajtowymi:</span><span class="sxs-lookup"><span data-stu-id="4f9c7-112">The following table illustrates the impact of this change with an invalid 3-byte input:</span></span>

| <span data-ttu-id="4f9c7-113">Niewłaściwie sformułowane dane wejściowe 3-bajtowe</span><span class="sxs-lookup"><span data-stu-id="4f9c7-113">Ill-formed 3-byte input</span></span> | <span data-ttu-id="4f9c7-114">Dane wyjściowe przed platformą .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="4f9c7-114">Output before .NET Core 3.0</span></span>          | <span data-ttu-id="4f9c7-115">Dane wyjściowe rozpoczynające się od platformy .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="4f9c7-115">Output starting with .NET Core 3.0</span></span>        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | <span data-ttu-id="4f9c7-116">`[ FFFD FFFD ]`(2-znakowe dane wyjściowe)</span><span class="sxs-lookup"><span data-stu-id="4f9c7-116">`[ FFFD FFFD ]` (2-character output)</span></span> | <span data-ttu-id="4f9c7-117">`[ FFFD FFFD FFFD ]`(3 znaki wyjściowe)</span><span class="sxs-lookup"><span data-stu-id="4f9c7-117">`[ FFFD FFFD FFFD ]` (3-character output)</span></span> |

<span data-ttu-id="4f9c7-118">3-znakowe dane wyjściowe to preferowane dane wyjściowe, zgodnie z _tabelą 3-9_ poprzednio połączonego pliku PDF w standardzie Unicode.</span><span class="sxs-lookup"><span data-stu-id="4f9c7-118">The 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4f9c7-119">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="4f9c7-119">Version introduced</span></span>

<span data-ttu-id="4f9c7-120">3.0</span><span class="sxs-lookup"><span data-stu-id="4f9c7-120">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4f9c7-121">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="4f9c7-121">Recommended action</span></span>

<span data-ttu-id="4f9c7-122">W części dewelopera nie jest wymagana żadna akcja.</span><span class="sxs-lookup"><span data-stu-id="4f9c7-122">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="4f9c7-123">Kategoria</span><span class="sxs-lookup"><span data-stu-id="4f9c7-123">Category</span></span>

<span data-ttu-id="4f9c7-124">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="4f9c7-124">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4f9c7-125">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="4f9c7-125">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
