---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217060"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="59670-101">Element ZipArchiveEntry nie obsługuje już archiwów z niespójnymi rozmiarami wpisów</span><span class="sxs-lookup"><span data-stu-id="59670-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="59670-102">Archiwa zip wyświetlają rozmiar skompresowany i nieskompresowany w katalogu centralnym i nagłówku lokalnym.</span><span class="sxs-lookup"><span data-stu-id="59670-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="59670-103">Dane wejściowe również wskazują jego rozmiar.</span><span class="sxs-lookup"><span data-stu-id="59670-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="59670-104">W programie .NET Core 2,2 i starszych wersjach te wartości nigdy nie były sprawdzane pod kątem spójności.</span><span class="sxs-lookup"><span data-stu-id="59670-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="59670-105">Począwszy od platformy .NET Core 3,0, są one teraz.</span><span class="sxs-lookup"><span data-stu-id="59670-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="59670-106">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="59670-106">Change description</span></span>

<span data-ttu-id="59670-107">W programie .NET Core 2,2 i starszych wersjach <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> program kończy się powodzeniem nawet wtedy, gdy nagłówek lokalny nie zgadza się z centralnym nagłówkiem pliku zip.</span><span class="sxs-lookup"><span data-stu-id="59670-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="59670-108">Dane są dekompresowane do momentu osiągnięcia końca skompresowanego strumienia, nawet jeśli jego długość przekracza rozmiar nieskompresowanych plików wymieniony w katalogu centralnym/nagłówku lokalnym.</span><span class="sxs-lookup"><span data-stu-id="59670-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="59670-109">Począwszy od platformy .NET Core 3,0, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> Metoda sprawdza, czy nagłówek lokalny i nagłówek centralny zgadzają się na skompresowane i nieskompresowane rozmiary wpisu.</span><span class="sxs-lookup"><span data-stu-id="59670-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="59670-110">Jeśli tak nie jest, metoda zgłasza <xref:System.IO.InvalidDataException> rozmiar i/lub listę deskryptorów danych w archiwum, które nie zgadzają się z katalogiem centralnym pliku zip.</span><span class="sxs-lookup"><span data-stu-id="59670-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="59670-111">Podczas odczytywania wpisu dekompresowane dane są obcinane do rozmiaru nieskompresowanego pliku wymienionego w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="59670-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="59670-112">Ta zmiana została wprowadzona w celu upewnienia <xref:System.IO.Compression.ZipArchiveEntry> się, że poprawnie reprezentuje rozmiar danych i że tylko ta ilość danych jest odczytywana.</span><span class="sxs-lookup"><span data-stu-id="59670-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="59670-113">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="59670-113">Version introduced</span></span>

<span data-ttu-id="59670-114">3.0</span><span class="sxs-lookup"><span data-stu-id="59670-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="59670-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="59670-115">Recommended action</span></span>

<span data-ttu-id="59670-116">Ponownie spakować wszystkie archiwum zip, które wykazuje te problemy.</span><span class="sxs-lookup"><span data-stu-id="59670-116">Repackage any zip archive that exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="59670-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="59670-117">Category</span></span>

<span data-ttu-id="59670-118">CoreFx</span><span class="sxs-lookup"><span data-stu-id="59670-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="59670-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="59670-119">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
