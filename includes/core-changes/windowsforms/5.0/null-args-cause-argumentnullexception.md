---
ms.openlocfilehash: ab8d801f3cdcfbeb6de20146754b26e3713d7dd6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702462"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a>Metody WinForms teraz generują ArgumentNullException

Niektóre metody Windows Forms teraz throw <xref:System.ArgumentNullException> dla argumentów o wartości null, w których wcześniej wywołały <xref:System.NullReferenceException> .

#### <a name="change-description"></a>Zmień opis

Wcześniej niektóre metody Windows Forms zgłosiły, <xref:System.NullReferenceException> Jeśli przekazano argument, który miał wartość null. Począwszy od platformy .NET 5,0, metody te teraz zgłaszają <xref:System.ArgumentNullException> zamiast argumentów wartości null.

Zgłaszanie jest <xref:System.ArgumentNullException> zgodne z zachowaniem środowiska uruchomieniowego .NET. Usprawnia to również środowisko debugowania przez wyraźne poinformowanie, że argument ma wartość null i który argument jest.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET 5,0 — wersja zapoznawcza 1 \
.NET 5,0 (wersja zapoznawcza 2)

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli wywołasz dowolną z tych metod, a kod aktualnie przechwytuje <xref:System.NullReferenceException> dla argumentów o wartości null, Przechwyć <xref:System.ArgumentNullException> zamiast tego. Ponadto należy rozważyć zaktualizowanie kodu, aby uniemożliwić przekazywanie argumentów o wartości null do wymienionych metod.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Począwszy od wersji zapoznawczej programu .NET 5,0 1:

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

Począwszy od programu .NET 5,0 w wersji zapoznawczej 2:

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(tylko dla <xref:System.IO.Stream> parametru)

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
