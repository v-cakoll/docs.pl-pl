---
title: 'Instrukcje: Tworzenie i Ustawianie niestandardowego modułu renderowania dla formantu ToolStrip'
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
ms.openlocfilehash: ad5ced42754fba6a714452220dd824c4f54fb5e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743412"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Porady: tworzenie i ustawienie niestandardowego modułu renderowania dla formantu ToolStrip w formularzach systemu Windows
formanty <xref:System.Windows.Forms.ToolStrip> zapewniają łatwą obsługę motywów i stylów. Możesz uzyskać zupełnie niestandardową wygląd i zachowanie (wygląd i działanie), ustawiając właściwość <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> lub właściwość <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> na moduł renderowania niestandardowego.  
  
 Można przypisać moduły renderowania do poszczególnych <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>lub kontrolki <xref:System.Windows.Forms.StatusStrip> lub użyć właściwości <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>, aby wpływać na wszystkie obiekty przez ustawienie właściwości <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> zwraca <xref:System.Windows.Forms.ToolStripRenderMode.Custom> tylko wtedy, gdy wartość <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> nie jest `null`.  
  
### <a name="to-create-a-custom-renderer"></a>Aby utworzyć niestandardowy moduł renderujący  
  
1. Rozwiń klasę <xref:System.Windows.Forms.ToolStripRenderer>.  
  
2. Zaimplementuj żądane renderowanie niestandardowe przez zastępowanie właściwych *w...* elementy członkowskie  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>Aby ustawić moduł renderowania niestandardowego jako bieżący moduł renderowania  
  
1. Aby ustawić niestandardowy moduł renderujący dla jednego <xref:System.Windows.Forms.ToolStrip>, ustaw właściwość <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> na renderowanie niestandardowe.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Lub w celu ustawienia modułu renderowania niestandardowego dla wszystkich <xref:System.Windows.Forms.ToolStrip> klas zawartych w aplikacji: Ustaw właściwość <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> na moduł renderowania niestandardowego i ustaw właściwość <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
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
