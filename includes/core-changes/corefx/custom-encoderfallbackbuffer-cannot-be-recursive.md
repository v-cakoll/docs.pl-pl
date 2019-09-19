---
ms.openlocfilehash: b4b49b55cda26ac9d9760f93e9758aab940ad135
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117165"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="36963-101">Niestandardowe wystąpienia EncoderFallbackBuffer nie mogą podlegać rekursywnie</span><span class="sxs-lookup"><span data-stu-id="36963-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="36963-102">Wystąpienia <xref:System.Text.EncoderFallbackBuffer> niestandardowe nie mogą podlegać rekursywnie.</span><span class="sxs-lookup"><span data-stu-id="36963-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="36963-103">Implementacja <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musi skutkować sekwencją znaków, która umożliwia konwersję na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="36963-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="36963-104">W przeciwnym razie wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="36963-104">Otherwise, an exception occurs.</span></span> 

#### <a name="details"></a><span data-ttu-id="36963-105">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="36963-105">Details</span></span>

<span data-ttu-id="36963-106">Podczas operacji transkodowania typu "Character-to-Byte" środowisko uruchomieniowe wykrywa nieprawidłowo uformowane lub niewymienialne sekwencje UTF-16 i dostarcza te <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> znaki do metody.</span><span class="sxs-lookup"><span data-stu-id="36963-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="36963-107">Metoda określa, które znaki mają być zastępowane dla oryginalnych danych nieprzekonwertowanych. te znaki są opróżniane przez wywołanie <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> pętli. `Fallback`</span><span class="sxs-lookup"><span data-stu-id="36963-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="36963-108">Środowisko uruchomieniowe następnie próbuje transkodowanie te znaki podstawiania do kodowania docelowego.</span><span class="sxs-lookup"><span data-stu-id="36963-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="36963-109">Jeśli ta operacja zakończy się pomyślnie, środowisko uruchomieniowe kontynuuje transkodowanie z miejsca, w którym jest pozostawione w oryginalnym ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="36963-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span> 

<span data-ttu-id="36963-110">W programie .NET Core w wersji zapoznawczej 7 i starszych <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> wersjach niestandardowe implementacje mogą zwracać sekwencje znaków, które nie są konwertowane na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="36963-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="36963-111">Jeśli podstawiane znaki nie mogą być transkodowane do kodowania docelowego, środowisko uruchomieniowe wywołuje <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metodę raz ponownie z znakami podstawiania, oczekiwanie <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> metody do zwrócenia nowej sekwencji podstawiania.</span><span class="sxs-lookup"><span data-stu-id="36963-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="36963-112">Ten proces jest kontynuowany do momentu, gdy środowisko uruchomieniowe ostatecznie zobaczy dobrze sformułowane, Zastępcze podstawienie lub dopóki nie zostanie osiągnięta maksymalna liczba rekursji.</span><span class="sxs-lookup"><span data-stu-id="36963-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="36963-113">Począwszy od platformy .NET Core 3,0, niestandardowe implementacje programu <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> muszą zwracać sekwencje znaków, które są konwertowane na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="36963-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="36963-114">Jeśli podstawiane znaki nie mogą być transkodowane do kodowania docelowego, <xref:System.ArgumentException> zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="36963-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="36963-115">Środowisko wykonawcze nie będzie już powodowało wywołań cyklicznych do <xref:System.Text.EncoderFallbackBuffer> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="36963-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span> 

<span data-ttu-id="36963-116">To zachowanie ma zastosowanie tylko wtedy, gdy spełnione są wszystkie trzy z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="36963-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="36963-117">Środowisko uruchomieniowe wykrywa źle sformułowaną sekwencję UTF-16 lub sekwencję UTF-16, której nie można przekonwertować na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="36963-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="36963-118">Określono niestandardową <xref:System.Text.EncoderFallback> .</span><span class="sxs-lookup"><span data-stu-id="36963-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="36963-119">Niestandardowa <xref:System.Text.EncoderFallback> próbuje zastąpić nową sekwencję UTF-16 źle sformułowaną lub nieprzekonwertowaną.</span><span class="sxs-lookup"><span data-stu-id="36963-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="36963-120">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="36963-120">Version introduced</span></span>

<span data-ttu-id="36963-121">3.0</span><span class="sxs-lookup"><span data-stu-id="36963-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="36963-122">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="36963-122">Recommended action</span></span>

<span data-ttu-id="36963-123">Większość deweloperów nie musi podejmować wszelkie działania.</span><span class="sxs-lookup"><span data-stu-id="36963-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="36963-124">Jeśli aplikacja używa klas <xref:System.Text.EncoderFallback> niestandardowych i <xref:System.Text.EncoderFallbackBuffer> <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> , należy upewnić się, że implementacja wypełnia bufor rezerwowy przy użyciu poprawnie sformułowanych danych UTF-16, które są <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> bezpośrednio konwertowane na kodowanie docelowe, gdy metoda jest najpierw wywoływany przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="36963-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="36963-125">Kategoria</span><span class="sxs-lookup"><span data-stu-id="36963-125">Category</span></span>

<span data-ttu-id="36963-126">CoreFx</span><span class="sxs-lookup"><span data-stu-id="36963-126">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="36963-127">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="36963-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->