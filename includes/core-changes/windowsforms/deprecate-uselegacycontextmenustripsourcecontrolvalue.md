---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181787"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="eb5d9-101">Przełącznik. System. Windows. Forms. UseLegacyContextMenuStripSourceControlValue nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="eb5d9-101">Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="eb5d9-102">Przełącznik `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` zgodności, który został wprowadzony w .NET Framework 4.7.2, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="eb5d9-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="eb5d9-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="eb5d9-103">Change description</span></span>

<span data-ttu-id="eb5d9-104">Począwszy od .NET Framework 4.7.2, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` przełącznik zgodności pozwala deweloperowi zrezygnować z nowego zachowania <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> właściwości, co teraz zwraca odwołanie do kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="eb5d9-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="eb5d9-105">Poprzednie zachowanie właściwości zostało zwrócone `null`.</span><span class="sxs-lookup"><span data-stu-id="eb5d9-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="eb5d9-106">Aby uzyskać więcej informacji, zobacz [ \<AppContextSwitchOverrides > elementu](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="eb5d9-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="eb5d9-107">W przypadku `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` platformy .NET Core przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="eb5d9-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eb5d9-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="eb5d9-108">Version introduced</span></span>

<span data-ttu-id="eb5d9-109">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="eb5d9-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eb5d9-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="eb5d9-110">Recommended action</span></span>

<span data-ttu-id="eb5d9-111">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="eb5d9-111">Remove the switch.</span></span> <span data-ttu-id="eb5d9-112">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="eb5d9-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="eb5d9-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="eb5d9-113">Category</span></span>

<span data-ttu-id="eb5d9-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eb5d9-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eb5d9-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="eb5d9-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
