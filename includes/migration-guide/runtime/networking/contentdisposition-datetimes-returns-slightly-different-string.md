---
ms.openlocfilehash: c103dff320ae30d02c12ea5c585a47b589da8237
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621310"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a><span data-ttu-id="937bb-101">ContentDisposition DateTimes zwraca nieco inny ciąg</span><span class="sxs-lookup"><span data-stu-id="937bb-101">ContentDisposition DateTimes returns slightly different string</span></span>

#### <a name="details"></a><span data-ttu-id="937bb-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="937bb-102">Details</span></span>

<span data-ttu-id="937bb-103">Reprezentacje ciągów dla <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> zostały zaktualizowane, począwszy od 4,6, do zawsze reprezentujące składnik godziny z <xref:System.DateTime?displayProperty=fullName> dwoma cyframi.</span><span class="sxs-lookup"><span data-stu-id="937bb-103">String representations of <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>'s have been updated, beginning in 4.6, to always represent the hour component of a <xref:System.DateTime?displayProperty=fullName> with two digits.</span></span> <span data-ttu-id="937bb-104">Jest to zgodne z [RFC822](https://www.ietf.org/rfc/rfc0822.txt) i [RFC2822](https://www.ietf.org/rfc/rfc2822.txt).</span><span class="sxs-lookup"><span data-stu-id="937bb-104">This is to comply with [RFC822](https://www.ietf.org/rfc/rfc0822.txt) and [RFC2822](https://www.ietf.org/rfc/rfc2822.txt).</span></span> <span data-ttu-id="937bb-105">Powoduje to <xref:System.Net.Mime.ContentDisposition.ToString> zwrócenie nieco innego ciągu w 4,6 w scenariuszach, w których jeden z elementów czasu dyspozycji był wcześniejszy niż 10:00 am.</span><span class="sxs-lookup"><span data-stu-id="937bb-105">This causes <xref:System.Net.Mime.ContentDisposition.ToString> to return a slightly different string in 4.6 in scenarios where one of the disposition's time elements was before 10:00 AM.</span></span> <span data-ttu-id="937bb-106">Należy zauważyć, że ContentDispositions są czasami serializowane przez konwersję do ciągów, więc <xref:System.Net.Mime.ContentDisposition.ToString> należy przejrzeć wszystkie wywołania operacji, serializacji lub GetHashCode.</span><span class="sxs-lookup"><span data-stu-id="937bb-106">Note that ContentDispositions are sometimes serialized via converting them to strings, so any <xref:System.Net.Mime.ContentDisposition.ToString> operations, serialization, or GetHashCode calls should be reviewed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="937bb-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="937bb-107">Suggestion</span></span>

<span data-ttu-id="937bb-108">Nie należy oczekiwać, że reprezentacje ciągów ContentDispositions z różnych wersji .NET Framework będą prawidłowo porównywane ze sobą.</span><span class="sxs-lookup"><span data-stu-id="937bb-108">Do not expect that string representations of ContentDispositions from different .NET Framework versions will correctly compare to one another.</span></span> <span data-ttu-id="937bb-109">Przed przeprowadzeniem porównania przekonwertuj ciągi z powrotem do ContentDispositions, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="937bb-109">Convert the strings back to ContentDispositions, if possible, before conducting a comparison.</span></span>

| <span data-ttu-id="937bb-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="937bb-110">Name</span></span>    | <span data-ttu-id="937bb-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="937bb-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="937bb-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="937bb-112">Scope</span></span>   |<span data-ttu-id="937bb-113">Mały</span><span class="sxs-lookup"><span data-stu-id="937bb-113">Minor</span></span>|
|<span data-ttu-id="937bb-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="937bb-114">Version</span></span>|<span data-ttu-id="937bb-115">4.6</span><span class="sxs-lookup"><span data-stu-id="937bb-115">4.6</span></span>|
|<span data-ttu-id="937bb-116">Typ</span><span class="sxs-lookup"><span data-stu-id="937bb-116">Type</span></span>|<span data-ttu-id="937bb-117">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="937bb-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="937bb-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="937bb-118">Affected APIs</span></span>

-<xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|
