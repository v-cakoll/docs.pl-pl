---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937112"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="1192c-101">Przełącznik zgodności AllowUpdateChildControlForTabControl nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="1192c-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="1192c-102">Przełącznik `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` zgodności jest obsługiwany w formularzach systemu Windows w wersji .NET Framework 4.6 i nowszej, ale nie jest obsługiwany w formularzach systemu Windows, począwszy od .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="1192c-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1192c-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="1192c-103">Change description</span></span>

<span data-ttu-id="1192c-104">W .NET Framework 4.6 i nowszych wersjach wybranie karty zmienia kolejność swojej kolekcji formantów.</span><span class="sxs-lookup"><span data-stu-id="1192c-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="1192c-105">Przełącznik `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` zgodności umożliwia aplikacji pominąć to ponowne zamawianie, gdy to zachowanie jest niepożądane.</span><span class="sxs-lookup"><span data-stu-id="1192c-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="1192c-106">W .NET Core `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="1192c-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1192c-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="1192c-107">Version introduced</span></span>

<span data-ttu-id="1192c-108">3.0 Podgląd 9</span><span class="sxs-lookup"><span data-stu-id="1192c-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1192c-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="1192c-109">Recommended action</span></span>

<span data-ttu-id="1192c-110">Wyjmij przełącznik.</span><span class="sxs-lookup"><span data-stu-id="1192c-110">Remove the switch.</span></span> <span data-ttu-id="1192c-111">Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="1192c-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="1192c-112">Kategoria</span><span class="sxs-lookup"><span data-stu-id="1192c-112">Category</span></span>

<span data-ttu-id="1192c-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1192c-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1192c-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="1192c-114">Affected APIs</span></span>

- <span data-ttu-id="1192c-115">Brak</span><span class="sxs-lookup"><span data-stu-id="1192c-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
