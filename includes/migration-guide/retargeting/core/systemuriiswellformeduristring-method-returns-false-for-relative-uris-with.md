---
ms.openlocfilehash: f7dcf9c4c3dc7ea536ddc847769a1a30f1298bb2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617281"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a><span data-ttu-id="20d0a-101">Metoda System. URI. IsWellFormedUriString zwraca wartość false dla względnych identyfikatorów URI z dwukropkiem w pierwszym segmencie</span><span class="sxs-lookup"><span data-stu-id="20d0a-101">System.Uri.IsWellFormedUriString method returns false for relative URIs with a colon char in first segment</span></span>

#### <a name="details"></a><span data-ttu-id="20d0a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="20d0a-102">Details</span></span>

<span data-ttu-id="20d0a-103">Począwszy od .NET Framework 4,5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> traktuje względne identyfikatory URI z `:` w pierwszym segmencie jako niewłaściwie sformułowane.</span><span class="sxs-lookup"><span data-stu-id="20d0a-103">Beginning with the .NET Framework 4.5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> will treat relative URIs with a `:` in their first segment as not well formed.</span></span> <span data-ttu-id="20d0a-104">Jest to zmiana z <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> zachowania w .NET Framework 4,0, która była zgodna z RFC3986.</span><span class="sxs-lookup"><span data-stu-id="20d0a-104">This is a change from <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> behavior in the .NET Framework 4.0 that was made to conform to RFC3986.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="20d0a-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="20d0a-105">Suggestion</span></span>

<span data-ttu-id="20d0a-106">Ta zmiana (taka jak wiele innych zmian identyfikatorów URI) będzie mieć wpływ tylko na aplikacje ukierunkowane na .NET Framework 4,5 (lub nowsze).</span><span class="sxs-lookup"><span data-stu-id="20d0a-106">This change (like many other URI changes) will only affect applications targeting the .NET Framework 4.5 (or later).</span></span> <span data-ttu-id="20d0a-107">Aby nadal korzystać z starego zachowania, wybierz aplikację jako docelową do .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="20d0a-107">To keep using the old behavior, target the app against the .NET Framework 4.0.</span></span> <span data-ttu-id="20d0a-108">Alternatywnie możesz skanować identyfikator URI przed wywołaniem <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> wyszukiwania `:` znaków, które można usunąć w celu weryfikacji, jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="20d0a-108">Alternatively, scan URI's prior to calling <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> looking for `:` characters that you may want to remove for validation purposes, if the old behavior is desirable.</span></span>

| <span data-ttu-id="20d0a-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="20d0a-109">Name</span></span>    | <span data-ttu-id="20d0a-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="20d0a-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="20d0a-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="20d0a-111">Scope</span></span>   | <span data-ttu-id="20d0a-112">Mały</span><span class="sxs-lookup"><span data-stu-id="20d0a-112">Minor</span></span>       |
| <span data-ttu-id="20d0a-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="20d0a-113">Version</span></span> | <span data-ttu-id="20d0a-114">4.5</span><span class="sxs-lookup"><span data-stu-id="20d0a-114">4.5</span></span>         |
| <span data-ttu-id="20d0a-115">Typ</span><span class="sxs-lookup"><span data-stu-id="20d0a-115">Type</span></span>    | <span data-ttu-id="20d0a-116">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="20d0a-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="20d0a-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="20d0a-117">Affected APIs</span></span>

- <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType>
