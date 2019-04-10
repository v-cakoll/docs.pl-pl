---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235564"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="7a44a-101">Właściwość CheckForOverflowUnderflow WinForm firmy to teraz System.Drawing</span><span class="sxs-lookup"><span data-stu-id="7a44a-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7a44a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7a44a-102">Details</span></span>|<span data-ttu-id="7a44a-103">Właściwość CheckForOverflowUnderflow dla zestawu System.Drawing.dll jest ustawiona na wartość true.</span><span class="sxs-lookup"><span data-stu-id="7a44a-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="7a44a-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7a44a-104">Suggestion</span></span>|<span data-ttu-id="7a44a-105">Poprzednio po wystąpieniu przepełnienia wynik zostałby dyskretnie obcięty.</span><span class="sxs-lookup"><span data-stu-id="7a44a-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="7a44a-106">Teraz <xref:System.OverflowException?displayProperty=name> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7a44a-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="7a44a-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="7a44a-107">Scope</span></span>|<span data-ttu-id="7a44a-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="7a44a-108">Edge</span></span>|
|<span data-ttu-id="7a44a-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="7a44a-109">Version</span></span>|<span data-ttu-id="7a44a-110">4.5</span><span class="sxs-lookup"><span data-stu-id="7a44a-110">4.5</span></span>|
|<span data-ttu-id="7a44a-111">Typ</span><span class="sxs-lookup"><span data-stu-id="7a44a-111">Type</span></span>|<span data-ttu-id="7a44a-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7a44a-112">Runtime</span></span>|
