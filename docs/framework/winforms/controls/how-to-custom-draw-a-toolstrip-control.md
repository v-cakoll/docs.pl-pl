---
title: 'Instrukcje: niestandardowy rysunek kontrolki ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], custom drawing
- drawing [Windows Forms], owner
- ProfessionalColorTable class [Windows Forms], overriding
- examples [Windows Forms], toolbars
- drawing [Windows Forms], custom
- toolbars [Windows Forms], changing colors
- ToolStrip control [Windows Forms], drawing
- ToolStrip control [Windows Forms], changing colors
- custom drawing
- owner drawing
ms.assetid: 94e7d7bd-a752-441c-b5b3-7acf98881163
ms.openlocfilehash: 810a680a1a9d9065e80ed87453a728fe628a953d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935368"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a>Instrukcje: niestandardowy rysunek kontrolki ToolStrip
<xref:System.Windows.Forms.ToolStrip> Formanty mają następujące skojarzone klasy renderowania (Painting):  
  
- <xref:System.Windows.Forms.ToolStripSystemRenderer>zapewnia wygląd i styl systemu operacyjnego.  
  
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>zapewnia wygląd i styl Microsoft Office.  
  
- <xref:System.Windows.Forms.ToolStripRenderer>jest abstrakcyjną klasą bazową dla pozostałych dwóch klas renderowania.  
  
 Do niestandardowego rysowania (nazywanego również rysowaniem przez właściciela <xref:System.Windows.Forms.ToolStrip>) a można przesłonić jedną z klas modułu renderowania i zmienić aspekt logiki renderowania.  
  
 Poniższe procedury opisują różne aspekty niestandardowego rysowania.  
  
### <a name="to-switch-between-the-provided-renderers"></a>Aby przełączać się między podanymi elementami renderowania  
  
- Ustaw właściwość na żądaną <xref:System.Windows.Forms.ToolStripRenderMode>wartość. <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>  
  
     W <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>programie statyczny <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> określa moduł renderujący dla aplikacji. Inne wartości <xref:System.Windows.Forms.ToolStripRenderMode> to <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, i <xref:System.Windows.Forms.ToolStripRenderMode.System>.  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>Aby zmienić obramowanie Microsoft Office — do stylu prostego  
  
- Przesłoń <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ale nie wywołuj klasy bazowej.  
  
> [!NOTE]
> Istnieje wersja tej metody dla <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>i <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.  
  
### <a name="to-change-the-professionalcolortable"></a>Aby zmienić ProfessionalColorTable  
  
- Zastąp <xref:System.Windows.Forms.ProfessionalColorTable> i zmień odpowiednie kolory.  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As _  
    System.EventArgs) Handles Me.Load  
        Dim t As MyColorTable = New MyColorTable  
        ToolStrip1.Renderer = New ToolStripProfessionalRenderer(t)  
    End Sub  
  
    Class MyColorTable   
    Inherits ProfessionalColorTable  
  
    Public Overrides ReadOnly Property ButtonPressedGradientBegin() As Color  
        Get  
            Return Color.Red  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientMiddle() _  
    As System.Drawing.Color  
        Get  
            Return Color.Blue  
        End Get  
            End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Green  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientBegin() _  
    As Color  
        Get  
            Return Color.Yellow  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientMiddle() As System.Drawing.Color  
        Get  
            Return Color.Orange  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Violet  
        End Get  
    End Property  
    End Class  
    ```  
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a>Aby zmienić renderowanie dla wszystkich kontrolek ToolStrip w aplikacji  
  
1. <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> Użyj właściwości, aby wybrać jeden z podanych elementów renderowania.  
  
2. Służy <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> do przypisywania niestandardowego modułu renderowania.  
  
3. Upewnij się <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> , że ustawiono <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>wartość domyślną.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>Aby wyłączyć Microsoft Office kolory dla całej aplikacji  
  
- <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> Ustaw wartość .`false`  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>Aby wyłączyć Microsoft Office kolory dla jednej kontrolki ToolStrip  
  
- Użyj kodu podobnego do poniższego przykładu kodu.  
  
    ```vb  
    Dim colorTable As ProfessionalColorTable()  
    colorTable.UseSystemColors = True  
    Dim toolStrip.Renderer As ToolStripProfessionalRenderer(colorTable)  
    ```  
  
    ```csharp  
    ProfessionalColorTable colorTable = new ProfessionalColorTable();  
    colorTable.UseSystemColors = true;  
    toolStrip.Renderer = new ToolStripProfessionalRenderer(colorTable);  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [Kontrolki z wbudowaną obsługą rysowania przez właściciela](controls-with-built-in-owner-drawing-support.md)
- [Instrukcje: Tworzenie i Ustawianie niestandardowego modułu renderowania dla formantu ToolStrip w Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [ToolStrip, kontrolka — omówienie](toolstrip-control-overview-windows-forms.md)
