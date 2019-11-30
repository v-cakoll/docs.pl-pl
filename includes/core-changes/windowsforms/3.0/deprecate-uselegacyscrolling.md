---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643971"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="0b978-101">Switch. System. Windows. Forms. DomainUpDown. UseLegacyScrolling nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="0b978-101">Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="0b978-102">Przełącznik zgodności `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`, który został wprowadzony w .NET Framework 4.7.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="0b978-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0b978-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="0b978-103">Change description</span></span>

<span data-ttu-id="0b978-104">Począwszy od .NET Framework 4.7.1, `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` przełączenia zgodności zezwala deweloperom na rezygnację z niezależnych <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> i <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcji.</span><span class="sxs-lookup"><span data-stu-id="0b978-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="0b978-105">Przełącznik przywrócił starsze zachowanie, w którym <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> jest ignorowany, jeśli jest obecny tekst kontekstu, a deweloper jest zobowiązany do użycia akcji <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> na formancie przed akcją <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0b978-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="0b978-106">Aby uzyskać więcej informacji, zobacz [\<AppContextSwitchOverrides > elementu](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="0b978-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="0b978-107">W programie .NET Core przełącznik `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="0b978-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0b978-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="0b978-108">Version introduced</span></span>

<span data-ttu-id="0b978-109">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="0b978-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0b978-110">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="0b978-110">Recommended action</span></span>

<span data-ttu-id="0b978-111">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="0b978-111">Remove the switch.</span></span> <span data-ttu-id="0b978-112">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="0b978-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="0b978-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="0b978-113">Category</span></span>

<span data-ttu-id="0b978-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b978-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0b978-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="0b978-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
