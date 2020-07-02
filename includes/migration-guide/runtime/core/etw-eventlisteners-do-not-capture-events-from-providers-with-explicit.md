---
ms.openlocfilehash: 7d50962b518c15875a5f1a82f5b89ab87a1db02e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620237"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a><span data-ttu-id="b9434-101">EventListeners ETW nie przechwytuje zdarzeń z dostawców z jawnymi słowami kluczowymi (takimi jak dostawca TPL)</span><span class="sxs-lookup"><span data-stu-id="b9434-101">ETW EventListeners do not capture events from providers with explicit keywords (like the TPL provider)</span></span>

#### <a name="details"></a><span data-ttu-id="b9434-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b9434-102">Details</span></span>

<span data-ttu-id="b9434-103">EventListeners ETW z pustą maską słowa kluczowego niepoprawnie przechwytuje zdarzenia z dostawców z jawnymi słowami kluczowymi.</span><span class="sxs-lookup"><span data-stu-id="b9434-103">ETW EventListeners with a blank keyword mask do not properly capture events from providers with explicit keywords.</span></span> <span data-ttu-id="b9434-104">W .NET Framework 4,5 dostawca TPL rozpoczął dostarczanie jawnych słów kluczowych i wyzwolił ten problem.</span><span class="sxs-lookup"><span data-stu-id="b9434-104">In the .NET Framework 4.5, the TPL provider began providing explicit keywords and triggered this issue.</span></span> <span data-ttu-id="b9434-105">W .NET Framework 4,6 EventListeners zostały zaktualizowane, aby nie miały już tego problemu.</span><span class="sxs-lookup"><span data-stu-id="b9434-105">In the .NET Framework 4.6, EventListeners have been updated to no longer have this issue.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b9434-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="b9434-106">Suggestion</span></span>

<span data-ttu-id="b9434-107">Aby obejść ten problem, Zastąp wywołania wywołaniami <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> przeciążenia EnableEvents, które jawnie określa &quot; maskę słów kluczowych &quot; do użycia: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code> . Alternatywnie ten problem został rozwiązany w .NET Framework 4,6 i może zostać rozwiązany przez uaktualnienie do tej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b9434-107">To work around this problem, replace calls to <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> with calls to the EnableEvents overload that explicitly specifies the &quot;any keywords&quot; mask to use: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>.Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="b9434-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b9434-108">Name</span></span>    | <span data-ttu-id="b9434-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="b9434-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b9434-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="b9434-110">Scope</span></span>   |<span data-ttu-id="b9434-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="b9434-111">Edge</span></span>|
|<span data-ttu-id="b9434-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="b9434-112">Version</span></span>|<span data-ttu-id="b9434-113">4.5</span><span class="sxs-lookup"><span data-stu-id="b9434-113">4.5</span></span>|
|<span data-ttu-id="b9434-114">Typ</span><span class="sxs-lookup"><span data-stu-id="b9434-114">Type</span></span>|<span data-ttu-id="b9434-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b9434-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b9434-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b9434-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|
