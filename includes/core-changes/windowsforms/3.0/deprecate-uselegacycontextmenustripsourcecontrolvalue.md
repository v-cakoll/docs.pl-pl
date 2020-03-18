---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937022"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="702a2-101">UseLegacyContextMenuStripSourceControlValue przełącznik zgodności nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="702a2-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="702a2-102">Przełącznik `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` zgodności, który został wprowadzony w programie .NET Framework 4.7.2, nie jest obsługiwany w formularzach systemu Windows w programie .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="702a2-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="702a2-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="702a2-103">Change description</span></span>

<span data-ttu-id="702a2-104">Począwszy od .NET Framework 4.7.2, przełącznik `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` zgodności umożliwia deweloperowi zrezygnować z nowego zachowania <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> właściwości, która teraz zwraca odwołanie do kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="702a2-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="702a2-105">Poprzednie zachowanie właściwości było powrót `null`.</span><span class="sxs-lookup"><span data-stu-id="702a2-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="702a2-106">Aby uzyskać więcej informacji, zobacz [ \<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="702a2-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="702a2-107">W .NET Core `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="702a2-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="702a2-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="702a2-108">Version introduced</span></span>

<span data-ttu-id="702a2-109">3.0 Podgląd 9</span><span class="sxs-lookup"><span data-stu-id="702a2-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="702a2-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="702a2-110">Recommended action</span></span>

<span data-ttu-id="702a2-111">Wyjmij przełącznik.</span><span class="sxs-lookup"><span data-stu-id="702a2-111">Remove the switch.</span></span> <span data-ttu-id="702a2-112">Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="702a2-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="702a2-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="702a2-113">Category</span></span>

<span data-ttu-id="702a2-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="702a2-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="702a2-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="702a2-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
