---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568157"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="9684a-101">Niestandardowe wystąpienia EncoderFallbackBuffer nie mogą podlegać rekursywnie</span><span class="sxs-lookup"><span data-stu-id="9684a-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="9684a-102">Niestandardowe wystąpienia <xref:System.Text.EncoderFallbackBuffer> nie mogą przeliczyć cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="9684a-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="9684a-103">Implementacja <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musi spowodować sekwencję znaków, która jest konwertowany na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="9684a-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="9684a-104">W przeciwnym razie wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9684a-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9684a-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="9684a-105">Change description</span></span>

<span data-ttu-id="9684a-106">Podczas operacji transkodowania typu "Character-to-Byte" środowisko uruchomieniowe wykrywa nieprawidłowo sformułowane lub niewymienialne sekwencje UTF-16 i dostarcza te znaki do metody <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9684a-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9684a-107">Metoda `Fallback` określa, które znaki powinny być zastępowane dla oryginalnych danych nieprzekonwertowanych. te znaki są opróżniane przez wywołanie <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> w pętli.</span><span class="sxs-lookup"><span data-stu-id="9684a-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="9684a-108">Środowisko uruchomieniowe następnie próbuje transkodowanie te znaki podstawiania do kodowania docelowego.</span><span class="sxs-lookup"><span data-stu-id="9684a-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="9684a-109">Jeśli ta operacja zakończy się pomyślnie, środowisko uruchomieniowe kontynuuje transkodowanie z miejsca, w którym jest pozostawione w oryginalnym ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="9684a-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="9684a-110">W programie .NET Core w wersji zapoznawczej 7 i starszych wersjach niestandardowe implementacje <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> mogą zwracać sekwencje znaków, które nie są konwertowane na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="9684a-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="9684a-111">Jeśli podstawiane znaki nie mogą być transkodowane do kodowania docelowego, środowisko uruchomieniowe wywołuje metodę <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> raz ponownie z znakami podstawiania, oczekiwanie metody <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> do zwrócenia nowej sekwencji podstawiania.</span><span class="sxs-lookup"><span data-stu-id="9684a-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="9684a-112">Ten proces jest kontynuowany do momentu, gdy środowisko uruchomieniowe ostatecznie zobaczy dobrze sformułowane, Zastępcze podstawienie lub dopóki nie zostanie osiągnięta maksymalna liczba rekursji.</span><span class="sxs-lookup"><span data-stu-id="9684a-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="9684a-113">Począwszy od platformy .NET Core 3,0, niestandardowe implementacje <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> muszą zwracać sekwencje znaków, które są konwertowane na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="9684a-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="9684a-114">Jeśli podstawiane znaki nie mogą być transkodowane do kodowania docelowego, zostanie zgłoszony <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="9684a-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="9684a-115">Środowisko wykonawcze nie będzie już powodowało wywołań cyklicznych do wystąpienia <xref:System.Text.EncoderFallbackBuffer>.</span><span class="sxs-lookup"><span data-stu-id="9684a-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="9684a-116">To zachowanie ma zastosowanie tylko wtedy, gdy spełnione są wszystkie trzy z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="9684a-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="9684a-117">Środowisko uruchomieniowe wykrywa źle sformułowaną sekwencję UTF-16 lub sekwencję UTF-16, której nie można przekonwertować na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="9684a-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="9684a-118">Określono niestandardową <xref:System.Text.EncoderFallback>.</span><span class="sxs-lookup"><span data-stu-id="9684a-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="9684a-119">Niestandardowy <xref:System.Text.EncoderFallback> próbuje zastąpić nową sekwencję UTF-16 źle sformułowaną lub nieprzekonwertowaną.</span><span class="sxs-lookup"><span data-stu-id="9684a-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9684a-120">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="9684a-120">Version introduced</span></span>

<span data-ttu-id="9684a-121">3.0</span><span class="sxs-lookup"><span data-stu-id="9684a-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9684a-122">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="9684a-122">Recommended action</span></span>

<span data-ttu-id="9684a-123">Większość deweloperów nie musi podejmować wszelkie działania.</span><span class="sxs-lookup"><span data-stu-id="9684a-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="9684a-124">Jeśli aplikacja używa niestandardowej klasy <xref:System.Text.EncoderFallback> i <xref:System.Text.EncoderFallbackBuffer>, upewnij się, że implementacja <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> wypełnia bufor rezerwowy przy użyciu poprawnie sformułowanych danych UTF-16, które są bezpośrednio konwertowane na kodowanie docelowe, gdy metoda <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> jest wywoływana po raz pierwszy przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="9684a-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="9684a-125">Kategoria</span><span class="sxs-lookup"><span data-stu-id="9684a-125">Category</span></span>

<span data-ttu-id="9684a-126">CoreFx</span><span class="sxs-lookup"><span data-stu-id="9684a-126">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9684a-127">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="9684a-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
