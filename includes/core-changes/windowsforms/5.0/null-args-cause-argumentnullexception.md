---
ms.openlocfilehash: fc0eec26073c299887b4748d0ad37e21c7294e84
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275498"
---
### <a name="winforms-apis-now-throw-argumentnullexception"></a>Interfejsy API WinForms teraz rzucać ArgumentNullException

Niektóre metody windows forms <xref:System.ArgumentNullException> teraz rzucać dla null <xref:System.NullReferenceException>argumenty, gdzie wcześniej wrzucili .

#### <a name="change-description"></a>Zmień opis

Wcześniej niektóre metody windows forms <xref:System.NullReferenceException> rzucił if przeszedł argument, który był null. Począwszy od .NET 5.0, <xref:System.ArgumentNullException> te metody teraz rzut dla argumentów null zamiast.

Zgłaszanie <xref:System.ArgumentNullException> jest zgodne z zachowaniem środowiska wykonawczego platformy .NET. Poprawia również środowisko debugowania, wyraźnie informując, że argument jest null i który argument jest.

#### <a name="version-introduced"></a>Wprowadzono wersję

.NET 5.0 Wersja zapoznawcza 1\
.NET 5.0 Wersja zapoznawcza 2

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli wywołasz dowolną z tych metod, a <xref:System.NullReferenceException> kod obecnie połowy <xref:System.ArgumentNullException> dla argumentów null, złapać zamiast tego. Ponadto należy rozważyć zaktualizowanie kodu, aby zapobiec przekazywaniu argumentów null do wymienionych metod.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Począwszy od wersji .NET 5.0 Wersja zapoznawcza 1:

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

Począwszy od wersji .NET 5.0 Preview 2:

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(tylko <xref:System.IO.Stream> dla parametru)

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
