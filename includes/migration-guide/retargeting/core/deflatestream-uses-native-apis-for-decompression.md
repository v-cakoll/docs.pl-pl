---
ms.openlocfilehash: 7e42a294b151d07a6fdc61308cdf92df7a31a1d6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614723"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a><span data-ttu-id="7737f-101">DeflateStream używa natywnych interfejsów API do dekompresji</span><span class="sxs-lookup"><span data-stu-id="7737f-101">DeflateStream uses native APIs for decompression</span></span>

#### <a name="details"></a><span data-ttu-id="7737f-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7737f-102">Details</span></span>

<span data-ttu-id="7737f-103">Począwszy od .NET Framework 4.7.2, implementacja dekompresji w `T:System.IO.Compression.DeflateStream` klasie została zmieniona tak, aby domyślnie używała natywnych interfejsów API systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7737f-103">Starting with the .NET Framework 4.7.2, the implementation of decompression in the `T:System.IO.Compression.DeflateStream` class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="7737f-104">Zwykle powoduje to znaczne zwiększenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="7737f-104">Typically, this results in a substantial performance improvement.</span></span> <span data-ttu-id="7737f-105">Wszystkie aplikacje .NET ukierunkowane na .NET Framework w wersji 4.7.2 lub nowszej używają natywnej implementacji. Ta zmiana może spowodować pewne różnice w działaniu, takie jak:</span><span class="sxs-lookup"><span data-stu-id="7737f-105">All .NET applications targeting the .NET Framework version 4.7.2 or higher use the native implementation.This change might result in some differences in behavior, which include:</span></span>

- <span data-ttu-id="7737f-106">Komunikaty o wyjątkach mogą się różnić.</span><span class="sxs-lookup"><span data-stu-id="7737f-106">Exception messages may be different.</span></span> <span data-ttu-id="7737f-107">Jednak typ zgłoszonego wyjątku pozostaje taki sam.</span><span class="sxs-lookup"><span data-stu-id="7737f-107">However, the type of exception thrown remains the same.</span></span>
- <span data-ttu-id="7737f-108">Niektóre specjalne sytuacje, takie jak brak wystarczającej ilości pamięci do ukończenia operacji, mogą być obsługiwane inaczej.</span><span class="sxs-lookup"><span data-stu-id="7737f-108">Some special situations, such as not having enough memory to complete an operation, may be handled differently.</span></span>
- <span data-ttu-id="7737f-109">Istnieją znane różnice dotyczące analizowania nagłówka gzip (Uwaga: dotyczy tylko `GZipStream` zestawu dla dekompresji):</span><span class="sxs-lookup"><span data-stu-id="7737f-109">There are known differences for parsing gzip header (note: only `GZipStream` set for decompression is affected):</span></span>
- <span data-ttu-id="7737f-110">Wyjątki podczas analizowania nieprawidłowych nagłówków można zgłaszać w różnym czasie.</span><span class="sxs-lookup"><span data-stu-id="7737f-110">Exceptions when parsing invalid headers may be thrown at different times.</span></span>
- <span data-ttu-id="7737f-111">Implementacja natywna wymusza, że wartości niektórych zarezerwowanych flag wewnątrz nagłówka gzip (tj. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) są ustawiane zgodnie ze specyfikacją, co może spowodować zgłoszenie wyjątku w przypadku zignorowania poprzednio nieprawidłowych wartości.</span><span class="sxs-lookup"><span data-stu-id="7737f-111">The native implementation enforces that values for some reserved flags inside the gzip header (i.e. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) are set according to the specification, which may cause it to throw an exception where previously invalid values were ignored.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7737f-112">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7737f-112">Suggestion</span></span>

<span data-ttu-id="7737f-113">Jeśli dekompresja z natywnymi interfejsami API ma negatywny wpływ na zachowanie aplikacji, możesz zrezygnować z tej funkcji, dodając `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` przełącznik do `runtime` sekcji pliku app.config i ustawiając go na `true` :</span><span class="sxs-lookup"><span data-stu-id="7737f-113">If decompression with native APIs has adversely affected the behavior of your app, you can opt out of this feature by adding the `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` switch to the `runtime` section of your app.config file and setting it to `true`:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="7737f-114">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7737f-114">Name</span></span>    | <span data-ttu-id="7737f-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="7737f-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7737f-116">Zakres</span><span class="sxs-lookup"><span data-stu-id="7737f-116">Scope</span></span>   | <span data-ttu-id="7737f-117">Mały</span><span class="sxs-lookup"><span data-stu-id="7737f-117">Minor</span></span>       |
| <span data-ttu-id="7737f-118">Wersja</span><span class="sxs-lookup"><span data-stu-id="7737f-118">Version</span></span> | <span data-ttu-id="7737f-119">4.7.2</span><span class="sxs-lookup"><span data-stu-id="7737f-119">4.7.2</span></span>       |
| <span data-ttu-id="7737f-120">Typ</span><span class="sxs-lookup"><span data-stu-id="7737f-120">Type</span></span>    | <span data-ttu-id="7737f-121">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="7737f-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="7737f-122">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7737f-122">Affected APIs</span></span>

- <xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType>
- <xref:System.IO.Compression.GZipStream?displayProperty=nameWithType>
