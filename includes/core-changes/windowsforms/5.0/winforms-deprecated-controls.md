---
ms.openlocfilehash: 27bd38edd81abb5ce5893021bcc96e7eeae7ae2c
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140893"
---
### <a name="removed-status-bar-controls"></a><span data-ttu-id="7488c-101">Usunięto kontrolki paska stanu</span><span class="sxs-lookup"><span data-stu-id="7488c-101">Removed status bar controls</span></span>

<span data-ttu-id="7488c-102">Począwszy od programu .NET 5,0 w wersji zapoznawczej 1, niektóre kontrolki Windows Forms nie są już dostępne.</span><span class="sxs-lookup"><span data-stu-id="7488c-102">Starting in .NET 5.0 Preview 1, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7488c-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="7488c-103">Change description</span></span>

<span data-ttu-id="7488c-104">Począwszy od programu .NET 5,0 w wersji zapoznawczej 1, niektóre kontrolki Windows Forms powiązane z paskiem stanu nie są już dostępne.</span><span class="sxs-lookup"><span data-stu-id="7488c-104">Starting with .NET 5.0 Preview 1, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="7488c-105">Kontrolki zamiany, które mają lepszy projekt i pomoc techniczną, zostały wprowadzone w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="7488c-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="7488c-106">Przestarzałe formanty zostały wcześniej usunięte z przyborników projektanta, ale były nadal dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="7488c-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="7488c-107">Teraz zostały całkowicie usunięte.</span><span class="sxs-lookup"><span data-stu-id="7488c-107">Now, they have been completely removed.</span></span>

<span data-ttu-id="7488c-108">Następujące typy nie są już dostępne:</span><span class="sxs-lookup"><span data-stu-id="7488c-108">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

#### <a name="version-introduced"></a><span data-ttu-id="7488c-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="7488c-109">Version introduced</span></span>

<span data-ttu-id="7488c-110">5,0 wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="7488c-110">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7488c-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="7488c-111">Recommended action</span></span>

<span data-ttu-id="7488c-112">Przejdź do zastępczych interfejsów API dla tych formantów i ich scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="7488c-112">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="7488c-113">Stara kontrolka (API)</span><span class="sxs-lookup"><span data-stu-id="7488c-113">Old Control (API)</span></span> | <span data-ttu-id="7488c-114">Zalecane zastąpienie</span><span class="sxs-lookup"><span data-stu-id="7488c-114">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="7488c-115">StatusBar</span><span class="sxs-lookup"><span data-stu-id="7488c-115">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="7488c-116">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="7488c-116">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

#### <a name="category"></a><span data-ttu-id="7488c-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="7488c-117">Category</span></span>

<span data-ttu-id="7488c-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7488c-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7488c-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7488c-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.StatusBar?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanel?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelAutoSize?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelBorderStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelStyle?displayProperty=fullName>

<!-- 

### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle` 

-->
