---
ms.openlocfilehash: 00c32c10f77995284264e795d386f699082dcb84
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721257"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="82cab-101">Niestandardowe wystąpienia EncoderFallbackBuffer nie mogą podlegać rekursywnie</span><span class="sxs-lookup"><span data-stu-id="82cab-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="82cab-102"><xref:System.Text.EncoderFallbackBuffer>Wystąpienia niestandardowe nie mogą podlegać rekursywnie.</span><span class="sxs-lookup"><span data-stu-id="82cab-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="82cab-103">Implementacja <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musi skutkować sekwencją znaków, która umożliwia konwersję na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="82cab-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="82cab-104">W przeciwnym razie wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="82cab-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="82cab-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="82cab-105">Change description</span></span>

<span data-ttu-id="82cab-106">Podczas operacji transkodowania typu "Character-to-Byte" środowisko uruchomieniowe wykrywa nieprawidłowo uformowane lub niewymienialne sekwencje UTF-16 i dostarcza te znaki do <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="82cab-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="82cab-107">`Fallback`Metoda określa, które znaki mają być zastępowane dla oryginalnych danych nieprzekonwertowanych. te znaki są opróżniane przez wywołanie <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> pętli.</span><span class="sxs-lookup"><span data-stu-id="82cab-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="82cab-108">Środowisko uruchomieniowe następnie próbuje transkodowanie te znaki podstawiania do kodowania docelowego.</span><span class="sxs-lookup"><span data-stu-id="82cab-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="82cab-109">Jeśli ta operacja zakończy się pomyślnie, środowisko uruchomieniowe kontynuuje transkodowanie z miejsca, w którym jest pozostawione w oryginalnym ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="82cab-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="82cab-110">W programie .NET Core w wersji zapoznawczej 7 i starszych wersjach niestandardowe implementacje <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> mogą zwracać sekwencje znaków, które nie są konwertowane na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="82cab-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="82cab-111">Jeśli podstawiane znaki nie mogą być transkodowane do kodowania docelowego, środowisko uruchomieniowe wywołuje <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metodę raz ponownie z znakami podstawiania, oczekiwanie <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> metody do zwrócenia nowej sekwencji podstawiania.</span><span class="sxs-lookup"><span data-stu-id="82cab-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="82cab-112">Ten proces jest kontynuowany do momentu, gdy środowisko uruchomieniowe ostatecznie zobaczy dobrze sformułowane, Zastępcze podstawienie lub dopóki nie zostanie osiągnięta maksymalna liczba rekursji.</span><span class="sxs-lookup"><span data-stu-id="82cab-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="82cab-113">Począwszy od platformy .NET Core 3,0, niestandardowe implementacje programu <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> muszą zwracać sekwencje znaków, które są konwertowane na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="82cab-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="82cab-114">Jeśli podstawiane znaki nie mogą być transkodowane do kodowania docelowego, <xref:System.ArgumentException> zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="82cab-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="82cab-115">Środowisko wykonawcze nie będzie już powodowało wywołań cyklicznych do <xref:System.Text.EncoderFallbackBuffer> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="82cab-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="82cab-116">To zachowanie ma zastosowanie tylko wtedy, gdy spełnione są wszystkie trzy z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="82cab-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="82cab-117">Środowisko uruchomieniowe wykrywa źle sformułowaną sekwencję UTF-16 lub sekwencję UTF-16, której nie można przekonwertować na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="82cab-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="82cab-118">Określono niestandardową <xref:System.Text.EncoderFallback> .</span><span class="sxs-lookup"><span data-stu-id="82cab-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="82cab-119">Niestandardowa <xref:System.Text.EncoderFallback> próbuje zastąpić nową sekwencję UTF-16 źle sformułowaną lub nieprzekonwertowaną.</span><span class="sxs-lookup"><span data-stu-id="82cab-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="82cab-120">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="82cab-120">Version introduced</span></span>

<span data-ttu-id="82cab-121">3.0</span><span class="sxs-lookup"><span data-stu-id="82cab-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="82cab-122">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="82cab-122">Recommended action</span></span>

<span data-ttu-id="82cab-123">Większość deweloperów nie musi podejmować wszelkie działania.</span><span class="sxs-lookup"><span data-stu-id="82cab-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="82cab-124">Jeśli aplikacja używa <xref:System.Text.EncoderFallback> klas niestandardowych i <xref:System.Text.EncoderFallbackBuffer> , należy upewnić się, że implementacja <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> wypełnia bufor rezerwowy przy użyciu poprawnie sformułowanych danych UTF-16, które są bezpośrednio konwertowane na kodowanie docelowe, gdy <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> Metoda jest wywoływana po raz pierwszy przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="82cab-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="82cab-125">Kategoria</span><span class="sxs-lookup"><span data-stu-id="82cab-125">Category</span></span>

<span data-ttu-id="82cab-126">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="82cab-126">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="82cab-127">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="82cab-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
