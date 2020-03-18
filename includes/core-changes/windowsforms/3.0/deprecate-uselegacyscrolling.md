---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937085"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="dc347-101">Przełącznik zgodności DomainUpDown.UseLegacyScrolling nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="dc347-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="dc347-102">Przełącznik `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` zgodności, który został wprowadzony w programie .NET Framework 4.7.1, nie jest obsługiwany w formularzach systemu Windows w programie .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="dc347-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="dc347-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="dc347-103">Change description</span></span>

<span data-ttu-id="dc347-104">Począwszy od .NET Framework 4.7.1, przełącznik `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` zgodności pozwolił <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> deweloperom zrezygnować z niezależnych i <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcji.</span><span class="sxs-lookup"><span data-stu-id="dc347-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="dc347-105">Przełącznik przywrócił starsze zachowanie, w <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> którym jest ignorowany, jeśli tekst kontekstu jest <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> obecny, a deweloper <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> jest wymagany do użycia akcji w forsce przed akcją.</span><span class="sxs-lookup"><span data-stu-id="dc347-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="dc347-106">Aby uzyskać więcej informacji, zobacz [ \<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="dc347-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="dc347-107">W .NET Core `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="dc347-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dc347-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="dc347-108">Version introduced</span></span>

<span data-ttu-id="dc347-109">3.0 Podgląd 9</span><span class="sxs-lookup"><span data-stu-id="dc347-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dc347-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="dc347-110">Recommended action</span></span>

<span data-ttu-id="dc347-111">Wyjmij przełącznik.</span><span class="sxs-lookup"><span data-stu-id="dc347-111">Remove the switch.</span></span> <span data-ttu-id="dc347-112">Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="dc347-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="dc347-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="dc347-113">Category</span></span>

<span data-ttu-id="dc347-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dc347-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dc347-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="dc347-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
