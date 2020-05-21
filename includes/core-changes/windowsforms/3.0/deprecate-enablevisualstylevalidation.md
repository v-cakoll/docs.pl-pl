---
ms.openlocfilehash: 97e38685777c7c418c0ccd91f4c433501ecf3aaa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720941"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="2aeac-101">Nieobsługiwany przełącznik zgodności EnableVisualStyleValidation</span><span class="sxs-lookup"><span data-stu-id="2aeac-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="2aeac-102">`Switch.System.Windows.Forms.EnableVisualStyleValidation`Przełącznik zgodności nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="2aeac-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2aeac-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="2aeac-103">Change description</span></span>

<span data-ttu-id="2aeac-104">W .NET Framework `Switch.System.Windows.Forms.EnableVisualStyleValidation` przełącznik zgodności zezwala aplikacji na rezygnację z walidacji stylów wizualnych dostarczonych w postaci liczbowej.</span><span class="sxs-lookup"><span data-stu-id="2aeac-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="2aeac-105">W przypadku platformy .NET Core `Switch.System.Windows.Forms.EnableVisualStyleValidation` przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="2aeac-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2aeac-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2aeac-106">Version introduced</span></span>

<span data-ttu-id="2aeac-107">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="2aeac-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2aeac-108">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="2aeac-108">Recommended action</span></span>

<span data-ttu-id="2aeac-109">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="2aeac-109">Remove the switch.</span></span> <span data-ttu-id="2aeac-110">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="2aeac-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="2aeac-111">Kategoria</span><span class="sxs-lookup"><span data-stu-id="2aeac-111">Category</span></span>

<span data-ttu-id="2aeac-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2aeac-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2aeac-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="2aeac-113">Affected APIs</span></span>

- <span data-ttu-id="2aeac-114">Brak</span><span class="sxs-lookup"><span data-stu-id="2aeac-114">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
