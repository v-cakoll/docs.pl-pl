---
title: 'Instrukcje: Tworzenie i ustawienie niestandardowego modułu renderowania dla formantu ToolStrip w formularzach Windows Forms'
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
ms.openlocfilehash: a70503dd4def19dd303a7362c9ca4d92f1419ff6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538508"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Instrukcje: Tworzenie i ustawienie niestandardowego modułu renderowania dla formantu ToolStrip w formularzach Windows Forms
<xref:System.Windows.Forms.ToolStrip> kontrolki daj pomocy technicznej łatwe do kompozycje i style. Można osiągnąć zupełnie niestandardowy wygląd i zachowanie (wygląd i działanie), ustawiając opcję <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> właściwości lub <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> właściwości do niestandardowego modułu renderowania.  
  
 Programy renderujące można przypisać do poszczególnych osób <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, lub <xref:System.Windows.Forms.StatusStrip> kontroli, lub użyć <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> mają wpływ na wszystkie obiekty, ustawiając właściwość <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> właściwość <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> Zwraca <xref:System.Windows.Forms.ToolStripRenderMode.Custom> tylko wtedy, gdy wartość <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> nie `null`.  
  
### <a name="to-create-a-custom-renderer"></a>Aby utworzyć niestandardowego modułu renderowania  
  
1.  Rozszerzanie <xref:System.Windows.Forms.ToolStripRenderer> klasy.  
  
2.  Implementuj żądane niestandardowe renderowanie przez zastąpienie odpowiednie *na...* elementy członkowskie  
  
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
  
1.  Aby ustawić niestandardowego modułu renderowania dla jednego <xref:System.Windows.Forms.ToolStrip>ustaw <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> właściwości do niestandardowego modułu renderowania.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2.  Lub ustawienie niestandardowego modułu renderowania dla wszystkich <xref:System.Windows.Forms.ToolStrip> klasy zawarte w Twojej aplikacji: Ustaw <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> właściwości do niestandardowego modułu renderowania, a zestaw <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> właściwość <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
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
- [ToolStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
- [ToolStrip, kontrolka — architektura](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [ToolStrip — podsumowanie informacji o technologii](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
