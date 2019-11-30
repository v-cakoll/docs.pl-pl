---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644006"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="4445f-101">Przełącznik. System. Windows. Forms. DontSupportReentrantFilterMessage nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="4445f-101">Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="4445f-102">Przełącznik zgodności `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`, który został wprowadzony w .NET Framework 4.6.1, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="4445f-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4445f-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="4445f-103">Change description</span></span>

<span data-ttu-id="4445f-104">Począwszy od .NET Framework 4.6.1, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` <xref:System.IndexOutOfRangeException> wyjątki, gdy komunikat <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> jest wywoływany przy użyciu niestandardowej implementacji <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4445f-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="4445f-105">Aby uzyskać więcej informacji, zobacz Rozwiązywanie [problemów z niestandardowymi implementacjami IMessageFilter. PreFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span><span class="sxs-lookup"><span data-stu-id="4445f-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="4445f-106">W programie .NET Core przełącznik `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="4445f-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4445f-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="4445f-107">Version introduced</span></span>

<span data-ttu-id="4445f-108">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="4445f-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4445f-109">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="4445f-109">Recommended action</span></span>

<span data-ttu-id="4445f-110">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="4445f-110">Remove the switch.</span></span> <span data-ttu-id="4445f-111">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="4445f-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="4445f-112">Kategoria</span><span class="sxs-lookup"><span data-stu-id="4445f-112">Category</span></span>

<span data-ttu-id="4445f-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4445f-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4445f-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="4445f-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
