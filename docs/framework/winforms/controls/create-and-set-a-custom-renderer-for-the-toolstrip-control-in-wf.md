---
title: 'Instrukcje: tworzenie i ustawienie niestandardowego modułu renderowania dla kontrolki ToolStrip w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
ms.openlocfilehash: ca1a7444c029632f83b1600e5855a13c83777594
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296384"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Instrukcje: tworzenie i ustawienie niestandardowego modułu renderowania dla kontrolki ToolStrip w formularzach systemu Windows
<xref:System.Windows.Forms.ToolStrip> kontrolki daj pomocy technicznej łatwe do kompozycje i style. Można osiągnąć zupełnie niestandardowy wygląd i zachowanie (wygląd i działanie), ustawiając opcję <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> właściwości lub <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> właściwości do niestandardowego modułu renderowania.  
  
 Programy renderujące można przypisać do poszczególnych osób <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, lub <xref:System.Windows.Forms.StatusStrip> kontroli, lub użyć <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> mają wpływ na wszystkie obiekty, ustawiając właściwość <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> właściwość <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> Zwraca <xref:System.Windows.Forms.ToolStripRenderMode.Custom> tylko wtedy, gdy wartość <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> nie `null`.  
  
### <a name="to-create-a-custom-renderer"></a>Aby utworzyć niestandardowego modułu renderowania  
  
1. Rozszerzanie <xref:System.Windows.Forms.ToolStripRenderer> klasy.  
  
2. Implementuj żądane niestandardowe renderowanie przez zastąpienie odpowiednie *na...* elementy członkowskie  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
    ```  
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>Aby ustawić niestandardowego modułu renderowania do bieżącego programu renderującego  
  
1. Aby ustawić niestandardowego modułu renderowania dla jednego <xref:System.Windows.Forms.ToolStrip>ustaw <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> właściwości do niestandardowego modułu renderowania.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Lub ustawienie niestandardowego modułu renderowania dla wszystkich <xref:System.Windows.Forms.ToolStrip> klasy zawarte w Twojej aplikacji: Ustaw <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> właściwości do niestandardowego modułu renderowania, a zestaw <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> właściwość <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [ToolStrip, kontrolka — omówienie](toolstrip-control-overview-windows-forms.md)
- [ToolStrip, kontrolka — architektura](toolstrip-control-architecture.md)
- [ToolStrip — podsumowanie informacji o technologii](toolstrip-technology-summary.md)
