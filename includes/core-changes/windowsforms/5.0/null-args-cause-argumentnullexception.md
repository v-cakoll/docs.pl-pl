---
ms.openlocfilehash: 63959c240b2fe16e086b97881a5a1792035bb3f8
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888137"
---
### <a name="winforms-apis-now-throw-argumentnullexception"></a><span data-ttu-id="3032a-101">Interfejsy API WinForms teraz rzucać ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="3032a-101">WinForms APIs now throw ArgumentNullException</span></span>

<span data-ttu-id="3032a-102">Niektóre metody windows forms <xref:System.ArgumentNullException> teraz rzucać dla null <xref:System.NullReferenceException>argumenty, gdzie wcześniej wrzucili .</span><span class="sxs-lookup"><span data-stu-id="3032a-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3032a-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="3032a-103">Change description</span></span>

<span data-ttu-id="3032a-104">Wcześniej niektóre metody windows forms <xref:System.NullReferenceException> rzucił if przeszedł argument, który był null.</span><span class="sxs-lookup"><span data-stu-id="3032a-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="3032a-105">Począwszy od .NET 5.0, <xref:System.ArgumentNullException> te metody teraz rzut dla argumentów null zamiast.</span><span class="sxs-lookup"><span data-stu-id="3032a-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="3032a-106">Zgłaszanie <xref:System.ArgumentNullException> jest zgodne z zachowaniem środowiska wykonawczego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3032a-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="3032a-107">Poprawia również środowisko debugowania, wyraźnie informując, że argument jest null i który argument jest.</span><span class="sxs-lookup"><span data-stu-id="3032a-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3032a-108">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="3032a-108">Version introduced</span></span>

<span data-ttu-id="3032a-109">.NET 5.0 Wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="3032a-109">.NET 5.0 Preview 1</span></span>\
<span data-ttu-id="3032a-110">.NET 5.0 Wersja zapoznawcza 2</span><span class="sxs-lookup"><span data-stu-id="3032a-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3032a-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="3032a-111">Recommended action</span></span>

<span data-ttu-id="3032a-112">Jeśli wywołasz dowolną z tych metod, a <xref:System.NullReferenceException> kod obecnie połowy <xref:System.ArgumentNullException> dla argumentów null, złapać zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="3032a-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="3032a-113">Ponadto należy rozważyć zaktualizowanie kodu, aby zapobiec przekazywaniu argumentów null do wymienionych metod.</span><span class="sxs-lookup"><span data-stu-id="3032a-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="3032a-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="3032a-114">Category</span></span>

<span data-ttu-id="3032a-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3032a-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3032a-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3032a-116">Affected APIs</span></span>

<span data-ttu-id="3032a-117">Począwszy od wersji .NET 5.0 Wersja zapoznawcza 1:</span><span class="sxs-lookup"><span data-stu-id="3032a-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="3032a-118">Począwszy od wersji .NET 5.0 Preview 2:</span><span class="sxs-lookup"><span data-stu-id="3032a-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="3032a-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(tylko <xref:System.IO.Stream> dla parametru)</span><span class="sxs-lookup"><span data-stu-id="3032a-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`

-->
