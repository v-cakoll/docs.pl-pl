---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644034"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="67b85-101">Przełącznik. System. Windows. Forms. UseLegacyImages nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="67b85-101">Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="67b85-102">Przełącznik zgodności `Switch.System.Windows.Forms.UseLegacyImages`, który został wprowadzony w .NET Framework 4,8, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="67b85-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="67b85-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="67b85-103">Change description</span></span>

<span data-ttu-id="67b85-104">Począwszy od .NET Framework 4,8, przełącznik zgodności `Switch.System.Windows.Forms.UseLegacyImages` zapoznajł możliwe problemy z skalowaniem obrazu w scenariuszach ClickOnce w środowiskach o wysokiej rozdzielczości DPI.</span><span class="sxs-lookup"><span data-stu-id="67b85-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="67b85-105">Gdy ustawiona na `true`, przełącznik zezwala użytkownikowi na przywracanie starszego skalowania obrazów na wyświetlaczach o wysokiej rozdzielczości DPI, których Skala jest ustawiona na wartość większą niż 100%.</span><span class="sxs-lookup"><span data-stu-id="67b85-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="67b85-106">Aby uzyskać więcej informacji, zobacz [Informacje o wersji .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="67b85-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="67b85-107">W programie .NET Core przełącznik `Switch.System.Windows.Forms.UseLegacyImages` nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="67b85-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="67b85-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="67b85-108">Version introduced</span></span>

<span data-ttu-id="67b85-109">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="67b85-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="67b85-110">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="67b85-110">Recommended action</span></span>

<span data-ttu-id="67b85-111">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="67b85-111">Remove the switch.</span></span> <span data-ttu-id="67b85-112">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="67b85-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="67b85-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="67b85-113">Category</span></span>

<span data-ttu-id="67b85-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67b85-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="67b85-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="67b85-115">Affected APIs</span></span>

- <span data-ttu-id="67b85-116">Brak</span><span class="sxs-lookup"><span data-stu-id="67b85-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
