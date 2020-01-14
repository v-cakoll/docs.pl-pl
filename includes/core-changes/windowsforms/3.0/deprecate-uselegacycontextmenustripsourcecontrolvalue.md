---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937022"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="3e18e-101">Nieobsługiwany przełącznik zgodności UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="3e18e-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="3e18e-102">Przełącznik zgodności `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`, który został wprowadzony w .NET Framework 4.7.2, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="3e18e-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3e18e-103">Opis zmiany</span><span class="sxs-lookup"><span data-stu-id="3e18e-103">Change description</span></span>

<span data-ttu-id="3e18e-104">Począwszy od .NET Framework 4.7.2, przełącznik zgodności `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` pozwala deweloperowi zrezygnować z nowego zachowania właściwości <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>, która teraz zwraca odwołanie do kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="3e18e-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="3e18e-105">Poprzednie zachowanie właściwości miało zwrócić `null`.</span><span class="sxs-lookup"><span data-stu-id="3e18e-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="3e18e-106">Aby uzyskać więcej informacji, zobacz [\<AppContextSwitchOverrides > elementu](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="3e18e-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="3e18e-107">W programie .NET Core przełącznik `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="3e18e-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3e18e-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="3e18e-108">Version introduced</span></span>

<span data-ttu-id="3e18e-109">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="3e18e-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3e18e-110">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="3e18e-110">Recommended action</span></span>

<span data-ttu-id="3e18e-111">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="3e18e-111">Remove the switch.</span></span> <span data-ttu-id="3e18e-112">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="3e18e-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="3e18e-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="3e18e-113">Category</span></span>

<span data-ttu-id="3e18e-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e18e-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3e18e-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3e18e-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
