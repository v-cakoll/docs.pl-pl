---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393908"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a><span data-ttu-id="0e6e1-101">Kestrel: przeniesiono nagłówki przyczepki do nowej kolekcji</span><span class="sxs-lookup"><span data-stu-id="0e6e1-101">Kestrel: Request trailer headers moved to new collection</span></span>

<span data-ttu-id="0e6e1-102">We wcześniejszych wersjach Kestrel dodaliśmy nagłówki podzielonych punktów protokołu HTTP/1.1 do kolekcji nagłówków żądań, gdy treść żądania została odczytana na końcu.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-102">In prior versions, Kestrel added HTTP/1.1 chunked trailer headers into the request headers collection when the request body was read to the end.</span></span> <span data-ttu-id="0e6e1-103">Takie zachowanie powodowało obawy dotyczące niejednoznaczności między nagłówkami i przyczepami.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-103">This behavior caused concerns about ambiguity between headers and trailers.</span></span> <span data-ttu-id="0e6e1-104">Podjęto decyzję o przeniesieniu przyczep do nowej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-104">The decision was made to move the trailers to a new collection.</span></span>

<span data-ttu-id="0e6e1-105">W ASP.NET Core 2,2 są niedostępne Wszystkie przyczepy z żądaniami HTTP/2, ale są teraz również dostępne w tej nowej kolekcji w ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-105">HTTP/2 request trailers were unavailable in ASP.NET Core 2.2 but are now also available in this new collection in ASP.NET Core 3.0.</span></span>

<span data-ttu-id="0e6e1-106">Dodano nowe metody rozszerzenia żądania w celu uzyskania dostępu do tych przyczep.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-106">New request extension methods have been added to access these trailers.</span></span>

<span data-ttu-id="0e6e1-107">Przyczepy protokołu HTTP/1.1 są dostępne po odczytaniu całej treści żądania.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-107">HTTP/1.1 trailers are available once the entire request body has been read.</span></span>

<span data-ttu-id="0e6e1-108">Przyczepy protokołu HTTP/2 są dostępne po odebraniu ich od klienta.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-108">HTTP/2 trailers are available once they're received from the client.</span></span> <span data-ttu-id="0e6e1-109">Klient nie wyśle przyczep do momentu, gdy cała treść żądania nie będzie co najmniej buforowana przez serwer.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-109">The client won't send the trailers until the entire request body has been at least buffered by the server.</span></span> <span data-ttu-id="0e6e1-110">Może być konieczne odczytanie treści żądania w celu zwolnienia miejsca w buforze.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-110">You may need to read the request body to free up buffer space.</span></span> <span data-ttu-id="0e6e1-111">Przyczepy są zawsze dostępne w przypadku odczytywania treści żądania na końcu.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-111">Trailers are always available if you read the request body to the end.</span></span> <span data-ttu-id="0e6e1-112">Przyczepy oznaczają koniec treści.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-112">The trailers mark the end of the body.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0e6e1-113">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="0e6e1-113">Version introduced</span></span>

<span data-ttu-id="0e6e1-114">3.0</span><span class="sxs-lookup"><span data-stu-id="0e6e1-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0e6e1-115">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="0e6e1-115">Old behavior</span></span>

<span data-ttu-id="0e6e1-116">Nagłówki przyczepy z żądaniem zostaną dodane do `HttpRequest.Headers` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-116">Request trailer headers would be added to the `HttpRequest.Headers` collection.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0e6e1-117">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="0e6e1-117">New behavior</span></span>

<span data-ttu-id="0e6e1-118">Nagłówki przyczepy z żądaniem **nie znajdują** się w `HttpRequest.Headers` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-118">Request trailer headers **aren't present** in the `HttpRequest.Headers` collection.</span></span> <span data-ttu-id="0e6e1-119">Użyj następujących metod rozszerzenia w `HttpRequest` celu uzyskania dostępu do nich:</span><span class="sxs-lookup"><span data-stu-id="0e6e1-119">Use the following extension methods on `HttpRequest` to access them:</span></span>

- <span data-ttu-id="0e6e1-120">`GetDeclaredTrailers()`— Pobiera nagłówek "Przyczepka" z listą, do których przyczep powinien oczekiwać po treści.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-120">`GetDeclaredTrailers()` - Gets the request "Trailer" header that lists which trailers to expect after the body.</span></span>
- <span data-ttu-id="0e6e1-121">`SupportsTrailers()`-Wskazuje, czy żądanie obsługuje nagłówki przyczepy.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-121">`SupportsTrailers()` - Indicates if the request supports receiving trailer headers.</span></span>
- <span data-ttu-id="0e6e1-122">`CheckTrailersAvailable()`-Określa, czy żądanie obsługuje przyczepy i czy są dostępne do odczytu.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-122">`CheckTrailersAvailable()` - Determines if the request supports trailers and if they're available for reading.</span></span>
- <span data-ttu-id="0e6e1-123">`GetTrailer(string trailerName)`-Pobiera żądany końcowy nagłówek z odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-123">`GetTrailer(string trailerName)` - Gets the requested trailing header from the response.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0e6e1-124">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="0e6e1-124">Reason for change</span></span>

<span data-ttu-id="0e6e1-125">Przyczepy są kluczową funkcją w scenariuszach takich jak gRPC.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-125">Trailers are a key feature in scenarios like gRPC.</span></span> <span data-ttu-id="0e6e1-126">Scalanie przyczep w programie w celu utworzenia nagłówków żądań było mylące dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-126">Merging the trailers in to request headers was confusing to users.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0e6e1-127">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="0e6e1-127">Recommended action</span></span>

<span data-ttu-id="0e6e1-128">Użyj metod rozszerzenia związanych z przyczepą w `HttpRequest` celu uzyskania dostępu do przyczep.</span><span class="sxs-lookup"><span data-stu-id="0e6e1-128">Use the trailer-related extension methods on `HttpRequest` to access trailers.</span></span>

#### <a name="category"></a><span data-ttu-id="0e6e1-129">Kategoria</span><span class="sxs-lookup"><span data-stu-id="0e6e1-129">Category</span></span>

<span data-ttu-id="0e6e1-130">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0e6e1-130">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0e6e1-131">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="0e6e1-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
