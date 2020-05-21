---
ms.openlocfilehash: dd850e83540ffed4dc95b00f807f49b0dd3725e9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721295"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="a63ed-101">Przełącznik zgodności DomainUpDown. UseLegacyScrolling nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="a63ed-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="a63ed-102">`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`Przełącznik zgodności, który został wprowadzony w .NET Framework 4.7.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="a63ed-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a63ed-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="a63ed-103">Change description</span></span>

<span data-ttu-id="a63ed-104">Począwszy od .NET Framework 4.7.1, `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` przełącznik zgodności zezwala deweloperom na rezygnację z niezależnych i niezależnych <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcji.</span><span class="sxs-lookup"><span data-stu-id="a63ed-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="a63ed-105">Przełącznik przywrócił starsze zachowanie, w którym <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> jest ignorowany, jeśli jest obecny tekst kontekstu, a deweloper jest zobowiązany do używania <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akcji na formancie przed <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcją.</span><span class="sxs-lookup"><span data-stu-id="a63ed-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="a63ed-106">Aby uzyskać więcej informacji, zobacz [ \< AppContextSwitchOverrides> elementu](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="a63ed-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="a63ed-107">W przypadku platformy .NET Core `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="a63ed-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a63ed-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="a63ed-108">Version introduced</span></span>

<span data-ttu-id="a63ed-109">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="a63ed-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a63ed-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="a63ed-110">Recommended action</span></span>

<span data-ttu-id="a63ed-111">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="a63ed-111">Remove the switch.</span></span> <span data-ttu-id="a63ed-112">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="a63ed-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="a63ed-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="a63ed-113">Category</span></span>

<span data-ttu-id="a63ed-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a63ed-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a63ed-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a63ed-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
