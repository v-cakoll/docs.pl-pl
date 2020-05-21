---
ms.openlocfilehash: e1c55eab0b968daab7322350e201b49149e63215
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721254"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="621c6-101">Nieobsługiwany przełącznik zgodności AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="621c6-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="621c6-102">`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Przełącznik zgodności jest obsługiwany w Windows Forms na .NET Framework 4,6 i nowszych wersjach, ale nie jest obsługiwany w Windows Forms począwszy od platformy .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="621c6-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="621c6-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="621c6-103">Change description</span></span>

<span data-ttu-id="621c6-104">W .NET Framework 4,6 i nowszych wersjach, wybranie karty zmienia kolejność kolekcji kontrolek.</span><span class="sxs-lookup"><span data-stu-id="621c6-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="621c6-105">`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Przełącznik zgodności pozwala aplikacji pominąć tę zmianę kolejności, jeśli to zachowanie jest niepożądane.</span><span class="sxs-lookup"><span data-stu-id="621c6-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="621c6-106">W przypadku platformy .NET Core `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="621c6-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="621c6-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="621c6-107">Version introduced</span></span>

<span data-ttu-id="621c6-108">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="621c6-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="621c6-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="621c6-109">Recommended action</span></span>

<span data-ttu-id="621c6-110">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="621c6-110">Remove the switch.</span></span> <span data-ttu-id="621c6-111">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="621c6-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="621c6-112">Kategoria</span><span class="sxs-lookup"><span data-stu-id="621c6-112">Category</span></span>

<span data-ttu-id="621c6-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="621c6-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="621c6-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="621c6-114">Affected APIs</span></span>

- <span data-ttu-id="621c6-115">Brak</span><span class="sxs-lookup"><span data-stu-id="621c6-115">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
