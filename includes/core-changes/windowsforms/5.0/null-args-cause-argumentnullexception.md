---
ms.openlocfilehash: ab8d801f3cdcfbeb6de20146754b26e3713d7dd6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702462"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="c012a-101">Metody WinForms teraz generują ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="c012a-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="c012a-102">Niektóre metody Windows Forms teraz throw <xref:System.ArgumentNullException> dla argumentów o wartości null, w których wcześniej wywołały <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="c012a-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c012a-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="c012a-103">Change description</span></span>

<span data-ttu-id="c012a-104">Wcześniej niektóre metody Windows Forms zgłosiły, <xref:System.NullReferenceException> Jeśli przekazano argument, który miał wartość null.</span><span class="sxs-lookup"><span data-stu-id="c012a-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="c012a-105">Począwszy od platformy .NET 5,0, metody te teraz zgłaszają <xref:System.ArgumentNullException> zamiast argumentów wartości null.</span><span class="sxs-lookup"><span data-stu-id="c012a-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="c012a-106">Zgłaszanie jest <xref:System.ArgumentNullException> zgodne z zachowaniem środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="c012a-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="c012a-107">Usprawnia to również środowisko debugowania przez wyraźne poinformowanie, że argument ma wartość null i który argument jest.</span><span class="sxs-lookup"><span data-stu-id="c012a-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c012a-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="c012a-108">Version introduced</span></span>

<span data-ttu-id="c012a-109">.NET 5,0 — wersja zapoznawcza 1 </span><span class="sxs-lookup"><span data-stu-id="c012a-109">.NET 5.0 Preview 1</span></span>\
<span data-ttu-id="c012a-110">.NET 5,0 (wersja zapoznawcza 2)</span><span class="sxs-lookup"><span data-stu-id="c012a-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c012a-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="c012a-111">Recommended action</span></span>

<span data-ttu-id="c012a-112">Jeśli wywołasz dowolną z tych metod, a kod aktualnie przechwytuje <xref:System.NullReferenceException> dla argumentów o wartości null, Przechwyć <xref:System.ArgumentNullException> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c012a-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="c012a-113">Ponadto należy rozważyć zaktualizowanie kodu, aby uniemożliwić przekazywanie argumentów o wartości null do wymienionych metod.</span><span class="sxs-lookup"><span data-stu-id="c012a-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="c012a-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="c012a-114">Category</span></span>

<span data-ttu-id="c012a-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c012a-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c012a-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c012a-116">Affected APIs</span></span>

<span data-ttu-id="c012a-117">Począwszy od wersji zapoznawczej programu .NET 5,0 1:</span><span class="sxs-lookup"><span data-stu-id="c012a-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="c012a-118">Począwszy od programu .NET 5,0 w wersji zapoznawczej 2:</span><span class="sxs-lookup"><span data-stu-id="c012a-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="c012a-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(tylko dla <xref:System.IO.Stream> parametru)</span><span class="sxs-lookup"><span data-stu-id="c012a-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

<!-- 

#### Affected APIs

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
