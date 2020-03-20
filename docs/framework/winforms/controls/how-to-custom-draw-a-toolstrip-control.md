---
title: 'Porady: niestandardowy rysunek formantu ToolStrip'
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
ms.openlocfilehash: a9f603efdb4b4a5f68154da9c6a8bd05b55b8f46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182222"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a>Porady: niestandardowy rysunek formantu ToolStrip
Formanty <xref:System.Windows.Forms.ToolStrip> mają następujące skojarzone klasy renderowania (malowania):  
  
- <xref:System.Windows.Forms.ToolStripSystemRenderer>zapewnia wygląd i styl systemu operacyjnego.  
  
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>zapewnia wygląd i styl pakietu Microsoft Office.  
  
- <xref:System.Windows.Forms.ToolStripRenderer>jest abstrakcyjną klasą podstawową dla pozostałych dwóch klas renderowania.  
  
 Aby narysować niestandardowe (znane <xref:System.Windows.Forms.ToolStrip>również jako rysowanie właściciela) a , można zastąpić jedną z klas modułu renderowania i zmienić aspekt logiki renderowania.  
  
 W poniższych procedurach opisano różne aspekty rysunku niestandardowego.  
  
### <a name="to-switch-between-the-provided-renderers"></a>Aby przełączać się między dostarczonymi modułami renderowania  
  
- Ustaw <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> właściwość <xref:System.Windows.Forms.ToolStripRenderMode> na żądaną wartość.  
  
     Za <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>pomocą , <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> statyczne określa moduł renderowania dla aplikacji. Inne wartości <xref:System.Windows.Forms.ToolStripRenderMode> to <xref:System.Windows.Forms.ToolStripRenderMode.Custom> <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, <xref:System.Windows.Forms.ToolStripRenderMode.System>i .  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>Aby zmienić obramowania w stylu pakietu Microsoft Office na proste  
  
- Zastądić <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ale nie wywołać klasy podstawowej.  
  
> [!NOTE]
> Istnieje wersja tej metody <xref:System.Windows.Forms.ToolStripRenderer>dla <xref:System.Windows.Forms.ToolStripSystemRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>i .  
  
### <a name="to-change-the-professionalcolortable"></a>Aby zmienić tabelę ProfessionalColorTable  
  
- Zastąd w <xref:System.Windows.Forms.ProfessionalColorTable> odpowiedni sposób i zmień kolory.  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a>Aby zmienić renderowanie dla wszystkich formantów ToolStrip w aplikacji  
  
1. Użyj <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> właściwości, aby wybrać jeden z dostarczonych modułów renderowania.  
  
2. Służy <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> do przypisywania niestandardowego modułu renderowania.  
  
3. Upewnij <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> się, że jest <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>ustawiona wartość domyślna .  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>Aby wyłączyć kolory pakietu Microsoft Office dla całej aplikacji  
  
- Ustaw <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> `false`na .  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>Aby wyłączyć kolory pakietu Microsoft Office dla jednego formantu ToolStrip  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [Kontrolki z wbudowaną obsługą rysowania przez właściciela](controls-with-built-in-owner-drawing-support.md)
- [Instrukcje: tworzenie i ustawienie niestandardowego modułu renderowania dla kontrolki ToolStrip w formularzach Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [ToolStrip — Informacje o formancie](toolstrip-control-overview-windows-forms.md)
