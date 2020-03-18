---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937119"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="5c4b7-101">Przełącznik zgodności EnableVisualStyleValidation nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="5c4b7-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="5c4b7-102">Przełącznik `Switch.System.Windows.Forms.EnableVisualStyleValidation` zgodności nie jest obsługiwany w formularzach systemu Windows w programie .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="5c4b7-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5c4b7-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="5c4b7-103">Change description</span></span>

<span data-ttu-id="5c4b7-104">W programie .NET `Switch.System.Windows.Forms.EnableVisualStyleValidation` Framework przełącznik zgodności umożliwił aplikacji rezygnację z sprawdzania poprawności stylów wizualnych dostarczanych w formie liczbowej.</span><span class="sxs-lookup"><span data-stu-id="5c4b7-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="5c4b7-105">W .NET Core `Switch.System.Windows.Forms.EnableVisualStyleValidation` przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="5c4b7-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5c4b7-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="5c4b7-106">Version introduced</span></span>

<span data-ttu-id="5c4b7-107">3.0 Podgląd 9</span><span class="sxs-lookup"><span data-stu-id="5c4b7-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5c4b7-108">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="5c4b7-108">Recommended action</span></span>

<span data-ttu-id="5c4b7-109">Wyjmij przełącznik.</span><span class="sxs-lookup"><span data-stu-id="5c4b7-109">Remove the switch.</span></span> <span data-ttu-id="5c4b7-110">Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="5c4b7-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="5c4b7-111">Kategoria</span><span class="sxs-lookup"><span data-stu-id="5c4b7-111">Category</span></span>

<span data-ttu-id="5c4b7-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c4b7-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5c4b7-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="5c4b7-113">Affected APIs</span></span>

- <span data-ttu-id="5c4b7-114">Brak</span><span class="sxs-lookup"><span data-stu-id="5c4b7-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
