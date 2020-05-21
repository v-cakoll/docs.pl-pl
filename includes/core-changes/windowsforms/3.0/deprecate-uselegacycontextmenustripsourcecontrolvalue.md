---
ms.openlocfilehash: 3ada05a13ec7acde1d8374ed733d0d51cdfb408c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721539"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="d1fa6-101">Nieobsługiwany przełącznik zgodności UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="d1fa6-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="d1fa6-102">`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`Przełącznik zgodności, który został wprowadzony w .NET Framework 4.7.2, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="d1fa6-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d1fa6-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="d1fa6-103">Change description</span></span>

<span data-ttu-id="d1fa6-104">Począwszy od .NET Framework 4.7.2, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` przełącznik zgodności pozwala deweloperowi zrezygnować z nowego zachowania <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> właściwości, co teraz zwraca odwołanie do kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="d1fa6-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="d1fa6-105">Poprzednie zachowanie właściwości zostało zwrócone `null` .</span><span class="sxs-lookup"><span data-stu-id="d1fa6-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="d1fa6-106">Aby uzyskać więcej informacji, zobacz [ \< AppContextSwitchOverrides> elementu](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="d1fa6-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="d1fa6-107">W przypadku platformy .NET Core `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="d1fa6-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d1fa6-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="d1fa6-108">Version introduced</span></span>

<span data-ttu-id="d1fa6-109">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="d1fa6-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d1fa6-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="d1fa6-110">Recommended action</span></span>

<span data-ttu-id="d1fa6-111">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="d1fa6-111">Remove the switch.</span></span> <span data-ttu-id="d1fa6-112">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="d1fa6-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="d1fa6-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d1fa6-113">Category</span></span>

<span data-ttu-id="d1fa6-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1fa6-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d1fa6-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d1fa6-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
