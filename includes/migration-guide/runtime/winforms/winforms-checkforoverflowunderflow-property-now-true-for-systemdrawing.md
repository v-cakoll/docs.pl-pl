---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804763"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="38f75-101">Właściwość CheckForOverflowUnderflow WinForm firmy to teraz System.Drawing</span><span class="sxs-lookup"><span data-stu-id="38f75-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="38f75-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="38f75-102">Details</span></span>|<span data-ttu-id="38f75-103">Właściwość CheckForOverflowUnderflow dla zestawu System.Drawing.dll jest ustawiona na wartość true.</span><span class="sxs-lookup"><span data-stu-id="38f75-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="38f75-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="38f75-104">Suggestion</span></span>|<span data-ttu-id="38f75-105">Poprzednio po wystąpieniu przepełnienia wynik zostałby dyskretnie obcięty.</span><span class="sxs-lookup"><span data-stu-id="38f75-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="38f75-106">Teraz <xref:System.OverflowException?displayProperty=name> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="38f75-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="38f75-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="38f75-107">Scope</span></span>|<span data-ttu-id="38f75-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="38f75-108">Edge</span></span>|
|<span data-ttu-id="38f75-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="38f75-109">Version</span></span>|<span data-ttu-id="38f75-110">4.5</span><span class="sxs-lookup"><span data-stu-id="38f75-110">4.5</span></span>|
|<span data-ttu-id="38f75-111">Typ</span><span class="sxs-lookup"><span data-stu-id="38f75-111">Type</span></span>|<span data-ttu-id="38f75-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="38f75-112">Runtime</span></span>|
