---
ms.openlocfilehash: e4d9efe7d2a06a1e501b070c23184dcd913dba71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621286"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a><span data-ttu-id="329eb-101">W kalendarzu Perski jest teraz używany algorytm słoneczny Hijri</span><span class="sxs-lookup"><span data-stu-id="329eb-101">Persian calendar now uses the Hijri solar algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="329eb-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="329eb-102">Details</span></span>

<span data-ttu-id="329eb-103">Począwszy od .NET Framework 4,6, <xref:System.Globalization.PersianCalendar?displayProperty=fullName> Klasa używa algorytmu słonecznego kalendarza Hidżry.</span><span class="sxs-lookup"><span data-stu-id="329eb-103">Starting with the .NET Framework 4.6, the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> class uses the Hijri solar algorithm.</span></span> <span data-ttu-id="329eb-104">Konwertowanie dat między <xref:System.Globalization.PersianCalendar?displayProperty=fullName> i innymi kalendarzami może spowodować nieco inne wyniki zaczynające się od .NET Framework 4,6 dla dat wcześniejszych niż 1800 lub późniejsze niż 2023 (gregoriański). Ponadto <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> jest teraz <code>March 22, 0622</code> zamiast <code>March 21, 0622</code> .</span><span class="sxs-lookup"><span data-stu-id="329eb-104">Converting dates between the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> and other calendars may produce a slightly different result beginning with the .NET Framework 4.6 for dates earlier than 1800 or later than 2023 (Gregorian).Also, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> is now <code>March 22, 0622</code> instead of <code>March 21, 0622</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="329eb-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="329eb-105">Suggestion</span></span>

<span data-ttu-id="329eb-106">Należy pamiętać, że niektóre wczesne lub późne daty mogą być nieco inne podczas korzystania z PersianCalendar w .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="329eb-106">Be aware that some early or late dates may be slightly different when using the PersianCalendar in .NET Framework 4.6.</span></span> <span data-ttu-id="329eb-107">Ponadto podczas serializowania dat między procesami, które mogą być uruchamiane w różnych wersjach .NET Framework, nie należy przechowywać ich jako ciągów dat PersianCalendar (ponieważ te wartości mogą być różne).</span><span class="sxs-lookup"><span data-stu-id="329eb-107">Also, when serializing dates between processes which may run on different .NET Framework versions, do not store them as PersianCalendar date strings (since those values may be different).</span></span>

| <span data-ttu-id="329eb-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="329eb-108">Name</span></span>    | <span data-ttu-id="329eb-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="329eb-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="329eb-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="329eb-110">Scope</span></span>   |<span data-ttu-id="329eb-111">Mały</span><span class="sxs-lookup"><span data-stu-id="329eb-111">Minor</span></span>|
|<span data-ttu-id="329eb-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="329eb-112">Version</span></span>|<span data-ttu-id="329eb-113">4.6</span><span class="sxs-lookup"><span data-stu-id="329eb-113">4.6</span></span>|
|<span data-ttu-id="329eb-114">Typ</span><span class="sxs-lookup"><span data-stu-id="329eb-114">Type</span></span>|<span data-ttu-id="329eb-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="329eb-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="329eb-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="329eb-116">Affected APIs</span></span>

-<xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
