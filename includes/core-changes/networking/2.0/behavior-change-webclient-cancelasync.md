---
ms.openlocfilehash: 80d4bbbfe52ab9685d7ca54f21b80d4b1773da22
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859618"
---
### <a name="webclientcancelasync-doesnt-always-cancel-immediately"></a><span data-ttu-id="4e847-101">Klient WebClient. CancelAsync nie zawsze anuluje natychmiast</span><span class="sxs-lookup"><span data-stu-id="4e847-101">WebClient.CancelAsync doesn't always cancel immediately</span></span>

<span data-ttu-id="4e847-102">Począwszy od platformy .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> wywołanie nie anuluje żądania natychmiast, jeśli odpowiedź została rozpoczęta do pobrania.</span><span class="sxs-lookup"><span data-stu-id="4e847-102">Starting in .NET Core 2.0, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> doesn't cancel the request immediately if the response has started to fetch.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4e847-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="4e847-103">Change description</span></span>

<span data-ttu-id="4e847-104">Wcześniej wywołanie <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="4e847-104">Previously, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> canceled the request immediately.</span></span> <span data-ttu-id="4e847-105">Począwszy od platformy .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> wywołanie anuluje żądanie natychmiast tylko wtedy, gdy odpowiedź nie rozpoczęła pobierania.</span><span class="sxs-lookup"><span data-stu-id="4e847-105">Starting in .NET Core 2.0, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> cancels the request immediately only if the response hasn't started fetching.</span></span> <span data-ttu-id="4e847-106">Jeśli odpowiedź została rozpoczęta do pobrania, żądanie zostanie anulowane tylko po odczytaniu kompletnej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="4e847-106">If the response has started to fetch, the request is cancelled only after a complete response is read.</span></span>

<span data-ttu-id="4e847-107">Ta zmiana została zaimplementowana <xref:System.Net.WebClient> , ponieważ interfejs API jest przestarzały <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="4e847-107">This change was implemented because the <xref:System.Net.WebClient> API is deprecated in favor of <xref:System.Net.Http.HttpClient>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4e847-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="4e847-108">Version introduced</span></span>

<span data-ttu-id="4e847-109">2.0</span><span class="sxs-lookup"><span data-stu-id="4e847-109">2.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4e847-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="4e847-110">Recommended action</span></span>

<span data-ttu-id="4e847-111">Użyj <xref:System.Net.Http.HttpClient?displayProperty=fullName> klasy zamiast <xref:System.Net.WebClient?displayProperty=fullName>, która jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="4e847-111">Use the <xref:System.Net.Http.HttpClient?displayProperty=fullName> class instead of <xref:System.Net.WebClient?displayProperty=fullName>, which is deprecated.</span></span>

#### <a name="category"></a><span data-ttu-id="4e847-112">Kategoria</span><span class="sxs-lookup"><span data-stu-id="4e847-112">Category</span></span>

<span data-ttu-id="4e847-113">Networking</span><span class="sxs-lookup"><span data-stu-id="4e847-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4e847-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="4e847-114">Affected APIs</span></span>

- <xref:System.Net.WebClient.CancelAsync?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.WebClient.CancelAsync`

-->
