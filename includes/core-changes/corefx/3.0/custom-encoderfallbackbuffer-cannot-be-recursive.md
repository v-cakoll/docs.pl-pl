---
ms.openlocfilehash: 820825f0545aa78729414c388385b339225b1235
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021669"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="f3b81-101">Niestandardowe enkoderFallbackBuffer wystąpienia nie mogą cofać się rekursywnie</span><span class="sxs-lookup"><span data-stu-id="f3b81-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="f3b81-102">Wystąpienia <xref:System.Text.EncoderFallbackBuffer> niestandardowe nie mogą cofać się rekursywnie.</span><span class="sxs-lookup"><span data-stu-id="f3b81-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="f3b81-103">Implementacja <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musi spowodować sekwencji znaków, który jest konwertowany na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="f3b81-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="f3b81-104">W przeciwnym razie wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f3b81-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f3b81-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="f3b81-105">Change description</span></span>

<span data-ttu-id="f3b81-106">Podczas operacji transkodowania typu znak-bajt środowisko wykonawcze wykrywa źle sformułowane lub nieprzekonalne sekwencje UTF-16 i udostępnia te znaki do <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f3b81-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f3b81-107">Metoda `Fallback` określa, które znaki powinny być zastępowane oryginalnymi danymi nieprzeszkłonowymi, a te znaki są opróżniane przez wywołanie <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> w pętli.</span><span class="sxs-lookup"><span data-stu-id="f3b81-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="f3b81-108">Środowisko wykonawcze następnie próbuje transkodować te znaki podstawienia do kodowania docelowego.</span><span class="sxs-lookup"><span data-stu-id="f3b81-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="f3b81-109">Jeśli ta operacja zakończy się pomyślnie, środowisko wykonawcze kontynuuje transkodowanie, z którego zostało przerwane w oryginalnym ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="f3b81-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="f3b81-110">W .NET Core Preview 7 i wcześniejszych <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> wersjach niestandardowe implementacje mogą zwracać sekwencje znaków, które nie są konwerteralne do kodowania docelowego.</span><span class="sxs-lookup"><span data-stu-id="f3b81-110">In .NET Core Preview 7 and earlier versions, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="f3b81-111">Jeśli zastąpione znaki nie mogą być transkodowane do kodowania <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> docelowego, środowisko wykonawcze wywołuje <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> metodę ponownie ze znakami podstawienia, oczekując, że metoda zwraca nową sekwencję podstawiania.</span><span class="sxs-lookup"><span data-stu-id="f3b81-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="f3b81-112">Ten proces jest kontynuowany, aż środowisko wykonawcze po pewnym czasie widzi dobrze sformułowane, konwersowane podstawienie lub do osiągnięcia maksymalnej liczby rekursji.</span><span class="sxs-lookup"><span data-stu-id="f3b81-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="f3b81-113">Począwszy od .NET Core 3.0, niestandardowe implementacje <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> musi zwracać sekwencje znaków, które są konwertowane do kodowania docelowego.</span><span class="sxs-lookup"><span data-stu-id="f3b81-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="f3b81-114">Jeśli podstawione znaki nie mogą być transkodowane <xref:System.ArgumentException> do kodowania docelowego, jest generowany.</span><span class="sxs-lookup"><span data-stu-id="f3b81-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="f3b81-115">Środowisko wykonawcze nie będzie już wykonywać wywołania cykliczne do <xref:System.Text.EncoderFallbackBuffer> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f3b81-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="f3b81-116">To zachowanie ma zastosowanie tylko wtedy, gdy spełnione są wszystkie trzy z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="f3b81-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="f3b81-117">Środowisko wykonawcze wykrywa źle sformułowaną sekwencję UTF-16 lub sekwencję UTF-16, których nie można przekonwertować na kodowanie docelowe.</span><span class="sxs-lookup"><span data-stu-id="f3b81-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="f3b81-118">Określono <xref:System.Text.EncoderFallback> niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="f3b81-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="f3b81-119">Niestandardowe <xref:System.Text.EncoderFallback> próby zastąpienia nowej źle utworzonej lub nieprzekonalnej sekwencji UTF-16.</span><span class="sxs-lookup"><span data-stu-id="f3b81-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f3b81-120">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="f3b81-120">Version introduced</span></span>

<span data-ttu-id="f3b81-121">3.0</span><span class="sxs-lookup"><span data-stu-id="f3b81-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f3b81-122">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="f3b81-122">Recommended action</span></span>

<span data-ttu-id="f3b81-123">Większość programistów nie musi podejmować żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="f3b81-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="f3b81-124">Jeśli aplikacja używa <xref:System.Text.EncoderFallback> niestandardowe <xref:System.Text.EncoderFallbackBuffer> i klasy, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> upewnij się, że implementacja wypełnia bufor rezerwowy z dobrze sformułowanych danych UTF-16, który jest bezpośrednio konwertowane do kodowania docelowego, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> gdy metoda jest po raz pierwszy wywoływana przez środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="f3b81-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="f3b81-125">Kategoria</span><span class="sxs-lookup"><span data-stu-id="f3b81-125">Category</span></span>

<span data-ttu-id="f3b81-126">Podstawowe biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="f3b81-126">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f3b81-127">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f3b81-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
