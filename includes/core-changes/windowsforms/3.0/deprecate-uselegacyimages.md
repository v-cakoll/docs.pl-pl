---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937120"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="8b861-101">Przełącznik zgodności UseLegacyImages nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="8b861-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="8b861-102">Przełącznik `Switch.System.Windows.Forms.UseLegacyImages` zgodności, który został wprowadzony w programie .NET Framework 4.8, nie jest obsługiwany w formularzach systemu Windows w programie .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="8b861-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8b861-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="8b861-103">Change description</span></span>

<span data-ttu-id="8b861-104">Począwszy od .NET Framework 4.8, przełącznik `Switch.System.Windows.Forms.UseLegacyImages` zgodności rozwiązać możliwe problemy ze skalowaniem obrazu w scenariuszach ClickOnce w środowiskach o wysokiej dpi.</span><span class="sxs-lookup"><span data-stu-id="8b861-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="8b861-105">Po ustawieniu przełącznik `true`umożliwia użytkownikowi przywrócenie starszego skalowania obrazu na wyświetlaczach o wysokiej jakości dpi, których skala jest ustawiona na więcej niż 100%.</span><span class="sxs-lookup"><span data-stu-id="8b861-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="8b861-106">Aby uzyskać więcej informacji, zobacz [.NET Framework 4.8 Informacje o wersji](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) w usiulach usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="8b861-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="8b861-107">W .NET Core `Switch.System.Windows.Forms.UseLegacyImages` przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="8b861-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8b861-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="8b861-108">Version introduced</span></span>

<span data-ttu-id="8b861-109">3.0 Podgląd 9</span><span class="sxs-lookup"><span data-stu-id="8b861-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8b861-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="8b861-110">Recommended action</span></span>

<span data-ttu-id="8b861-111">Wyjmij przełącznik.</span><span class="sxs-lookup"><span data-stu-id="8b861-111">Remove the switch.</span></span> <span data-ttu-id="8b861-112">Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="8b861-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="8b861-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="8b861-113">Category</span></span>

<span data-ttu-id="8b861-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b861-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8b861-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="8b861-115">Affected APIs</span></span>

- <span data-ttu-id="8b861-116">Brak</span><span class="sxs-lookup"><span data-stu-id="8b861-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
