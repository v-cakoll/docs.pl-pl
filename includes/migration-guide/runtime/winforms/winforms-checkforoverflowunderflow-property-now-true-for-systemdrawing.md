---
ms.openlocfilehash: 4cd06fd02fadbaa9f74e40f850e688ee883454ed
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620442"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="274e8-101">Właściwość CheckForOverflowUnderflow kontrolki WinForm jest teraz prawdziwa dla elementu System. Drawing</span><span class="sxs-lookup"><span data-stu-id="274e8-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

#### <a name="details"></a><span data-ttu-id="274e8-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="274e8-102">Details</span></span>

<span data-ttu-id="274e8-103">Właściwość CheckForOverflowUnderflow zestawu System.Drawing.dll ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="274e8-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="274e8-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="274e8-104">Suggestion</span></span>

<span data-ttu-id="274e8-105">Poprzednio po wystąpieniu przepełnienia wynik zostałby dyskretnie obcięty.</span><span class="sxs-lookup"><span data-stu-id="274e8-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="274e8-106">Zostanie <xref:System.OverflowException?displayProperty=fullName> zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="274e8-106">Now an <xref:System.OverflowException?displayProperty=fullName> exception is thrown.</span></span>

| <span data-ttu-id="274e8-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="274e8-107">Name</span></span>    | <span data-ttu-id="274e8-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="274e8-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="274e8-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="274e8-109">Scope</span></span>   |<span data-ttu-id="274e8-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="274e8-110">Edge</span></span>|
|<span data-ttu-id="274e8-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="274e8-111">Version</span></span>|<span data-ttu-id="274e8-112">4.5</span><span class="sxs-lookup"><span data-stu-id="274e8-112">4.5</span></span>|
|<span data-ttu-id="274e8-113">Typ</span><span class="sxs-lookup"><span data-stu-id="274e8-113">Type</span></span>|<span data-ttu-id="274e8-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="274e8-114">Runtime</span></span>|
