---
title: 'Porady: niestandardowy rysunek formantu ToolStrip'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 40a0d683a6b9b91233cf9a5c1d133540e47192cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a>Porady: niestandardowy rysunek formantu ToolStrip
<xref:System.Windows.Forms.ToolStrip> Kontrolki skojarzone renderowania klasy (związane z malowaniem) są następujące elementy:  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer>udostępnia wygląd i styl systemu operacyjnego.  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer>udostępnia wygląd i styl pakietu Microsoft Office.  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>jest abstrakcyjna klasa podstawowa dla innych klas dwóch renderowania.  
  
 Do rysowania niestandardowy (nazywana również Rysowanie przez właściciela) <xref:System.Windows.Forms.ToolStrip>, można zastąpić jedną z klas renderowania i zmienić aspekt logiki renderowania.  
  
 W poniższych procedurach opisano różne aspekty Rysowanie niestandardowe.  
  
### <a name="to-switch-between-the-provided-renderers"></a>Aby przełączyć między podane moduły renderowania  
  
-   Ustaw <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> właściwości <xref:System.Windows.Forms.ToolStripRenderMode> ma wartość.  
  
     Z <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, statycznych <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> określa renderowania dla aplikacji. Inne wartości <xref:System.Windows.Forms.ToolStripRenderMode> są <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, i <xref:System.Windows.Forms.ToolStripRenderMode.System>.  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>Aby zmienić Microsoft Office — styl obramowania proste  
  
-   Zastąpienie <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ale nie należy wywoływać klasy podstawowej.  
  
> [!NOTE]
>  Dostępna jest wersja tej metody dla <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, i <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.  
  
### <a name="to-change-the-professionalcolortable"></a>Aby zmienić professionalcolortable —  
  
-   Zastąpienie <xref:System.Windows.Forms.ProfessionalColorTable> i zmiana kolorów ma.  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a>Aby zmienić renderowania dla wszystkich kontrolek ToolStrip w aplikacji  
  
1.  Użyj <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> właściwości można wybrać jeden z dostarczonego renderowania.  
  
2.  Użyj <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> można przypisać niestandardowego modułu renderowania.  
  
3.  Upewnij się, że <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> ma ustawioną wartość domyślną <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>Aby wyłączyć kolorów Microsoft Office dla całej aplikacji  
  
-   Ustaw <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> do `false`.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>Aby wyłączyć kolorów Microsoft Office dla jednego formantu ToolStrip  
  
-   Użyj kodu podobne do poniższego przykładu kodu.  
  
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
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 [Kontrolki z wbudowaną obsługą rysowania przez właściciela](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [Instrukcje: tworzenie i ustawienie niestandardowego modułu renderowania dla kontrolki ToolStrip w formularzach Windows Forms](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
 [ToolStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
