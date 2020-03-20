---
title: 'Jak: Tworzenie i ustawianie niestandardowego modułu renderowania dla formantu ToolStrip'
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
ms.openlocfilehash: 49db0d785155f19b7220ac64011eaf4253aaa7e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182404"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Porady: tworzenie i ustawienie niestandardowego modułu renderowania dla formantu ToolStrip w formularzach systemu Windows
<xref:System.Windows.Forms.ToolStrip>zapewniają łatwe wsparcie dla tematów i stylów. Można osiągnąć całkowicie niestandardowy wygląd i zachowanie (wygląd <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> i działanie), ustawiając właściwość lub <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> właściwość do niestandardowego modułu renderowania.  
  
 Można przypisać moduły renderowania <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip>do <xref:System.Windows.Forms.StatusStrip> każdej osoby <xref:System.Windows.Forms.ToolStrip>, , <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> lub formantu, lub można użyć właściwości, aby wpłynąć na wszystkie obiekty, ustawiając <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> właściwość na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>zwraca <xref:System.Windows.Forms.ToolStripRenderMode.Custom> tylko wtedy, <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> gdy `null`wartość nie jest .  
  
### <a name="to-create-a-custom-renderer"></a>Aby utworzyć niestandardowy moduł renderowania  
  
1. Rozszerz <xref:System.Windows.Forms.ToolStripRenderer> klasę.  
  
2. Zaimplementuj żądane renderowanie niestandardowe, zastępując odpowiednie *włączone...* elementy członkowskie  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>Aby ustawić niestandardowy moduł renderowania jako bieżący moduł renderowania  
  
1. Aby ustawić niestandardowy moduł <xref:System.Windows.Forms.ToolStrip>renderowania <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> dla jednego , ustaw właściwość na niestandardowy moduł renderowania.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Lub ustawić niestandardowy moduł <xref:System.Windows.Forms.ToolStrip> renderowania dla wszystkich klas <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> zawartych w aplikacji: Ustaw <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> właściwość na niestandardowy moduł renderowania i ustaw właściwość na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [ToolStrip — Informacje o formancie](toolstrip-control-overview-windows-forms.md)
- [ToolStrip — Architektura formantu](toolstrip-control-architecture.md)
- [Podsumowanie informacji o technologii formantów ToolStrip](toolstrip-technology-summary.md)
