---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568109"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="a106f-101">ZipArchiveEntry nie obsługuje już archiwów z niespójnymi rozmiarami wejść</span><span class="sxs-lookup"><span data-stu-id="a106f-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="a106f-102">Archiwa zip wyświetlają zarówno skompresowany rozmiar, jak i nieskompresowany rozmiar w katalogu centralnym i nagłówku lokalnym.</span><span class="sxs-lookup"><span data-stu-id="a106f-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="a106f-103">Dane wpisu również wskazuje jego rozmiar.</span><span class="sxs-lookup"><span data-stu-id="a106f-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="a106f-104">W .NET Core 2.2 i wcześniejszych wersjach te wartości nigdy nie zostały sprawdzone pod kątem spójności.</span><span class="sxs-lookup"><span data-stu-id="a106f-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="a106f-105">Począwszy od .NET Core 3.0, są teraz.</span><span class="sxs-lookup"><span data-stu-id="a106f-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a106f-106">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="a106f-106">Change description</span></span>

<span data-ttu-id="a106f-107">W .NET Core 2.2 i <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> wcześniejszych wersjach, nawet jeśli nagłówek lokalny nie zgadza się z centralnym nagłówkiem pliku zip.</span><span class="sxs-lookup"><span data-stu-id="a106f-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="a106f-108">Dane są dekompresowane do momentu osiągnięcia końca skompresowanego strumienia, nawet jeśli jego długość przekracza rozmiar nieskompresowanego pliku wymieniony w centralnym katalogu/nagłówku lokalnym.</span><span class="sxs-lookup"><span data-stu-id="a106f-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="a106f-109">Począwszy od .NET Core <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> 3.0, metoda sprawdza, czy nagłówek lokalny i nagłówek centralny zgadzają się na skompresowane i nieskompresowane rozmiary wpisu.</span><span class="sxs-lookup"><span data-stu-id="a106f-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="a106f-110">Jeśli nie, metoda <xref:System.IO.InvalidDataException> zgłasza, jeśli w lokalnym nagłówku archiwum i/lub rozmiarze listy deskryptora danych, które nie zgadzają się z centralnym katalogiem pliku zip.</span><span class="sxs-lookup"><span data-stu-id="a106f-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="a106f-111">Podczas odczytywania wpisu dekompresowane dane są obcinane do rozmiaru nieskompresowanego pliku wymienionego w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="a106f-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="a106f-112">Ta zmiana została wmazana w celu zapewnienia, że <xref:System.IO.Compression.ZipArchiveEntry> poprawnie reprezentuje rozmiar swoich danych i że tylko ta ilość danych jest odczytywana.</span><span class="sxs-lookup"><span data-stu-id="a106f-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a106f-113">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="a106f-113">Version introduced</span></span>

<span data-ttu-id="a106f-114">3.0</span><span class="sxs-lookup"><span data-stu-id="a106f-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a106f-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="a106f-115">Recommended action</span></span>

<span data-ttu-id="a106f-116">Przepakuj dowolne archiwum zip, które wykazuje te problemy.</span><span class="sxs-lookup"><span data-stu-id="a106f-116">Repackage any zip archive that exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="a106f-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="a106f-117">Category</span></span>

<span data-ttu-id="a106f-118">CoreFx</span><span class="sxs-lookup"><span data-stu-id="a106f-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a106f-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a106f-119">Affected APIs</span></span>

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
