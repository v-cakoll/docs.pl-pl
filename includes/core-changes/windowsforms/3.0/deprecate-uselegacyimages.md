---
ms.openlocfilehash: c980b0c0be9f4d6a529baa0743dec9ac16ca0d7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721753"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="182d4-101">Nieobsługiwany przełącznik zgodności UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="182d4-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="182d4-102">`Switch.System.Windows.Forms.UseLegacyImages`Przełącznik zgodności, który został wprowadzony w .NET Framework 4,8, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="182d4-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="182d4-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="182d4-103">Change description</span></span>

<span data-ttu-id="182d4-104">Począwszy od .NET Framework 4,8, przełącznik zgodności zapoznajł `Switch.System.Windows.Forms.UseLegacyImages` możliwe problemy z skalowaniem obrazu w scenariuszach ClickOnce w środowiskach o wysokiej rozdzielczości DPI.</span><span class="sxs-lookup"><span data-stu-id="182d4-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="182d4-105">Gdy ustawiona `true` jest wartość, przełącznik umożliwia użytkownikowi przywrócenie starszego skalowania obrazu na wyświetlaczach o wysokiej rozdzielczości DPI, których Skala jest ustawiona na wartość większą niż 100%.</span><span class="sxs-lookup"><span data-stu-id="182d4-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="182d4-106">Aby uzyskać więcej informacji, zobacz [Informacje o wersji .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="182d4-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="182d4-107">W przypadku platformy .NET Core `Switch.System.Windows.Forms.UseLegacyImages` przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="182d4-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="182d4-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="182d4-108">Version introduced</span></span>

<span data-ttu-id="182d4-109">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="182d4-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="182d4-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="182d4-110">Recommended action</span></span>

<span data-ttu-id="182d4-111">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="182d4-111">Remove the switch.</span></span> <span data-ttu-id="182d4-112">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="182d4-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="182d4-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="182d4-113">Category</span></span>

<span data-ttu-id="182d4-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="182d4-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="182d4-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="182d4-115">Affected APIs</span></span>

- <span data-ttu-id="182d4-116">Brak</span><span class="sxs-lookup"><span data-stu-id="182d4-116">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
