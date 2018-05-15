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
ms.openlocfilehash: 09d9654bf1a2670c77a4a3db2eae2ed7ab6dbfec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a><span data-ttu-id="9b83c-102">Porady: niestandardowy rysunek formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9b83c-102">How to: Custom Draw a ToolStrip Control</span></span>
<span data-ttu-id="9b83c-103"><xref:System.Windows.Forms.ToolStrip> Kontrolki skojarzone renderowania klasy (związane z malowaniem) są następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="9b83c-103">The <xref:System.Windows.Forms.ToolStrip> controls have the following associated rendering (painting) classes:</span></span>  
  
-   <span data-ttu-id="9b83c-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> udostępnia wygląd i styl systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="9b83c-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> provides the appearance and style of your operating system.</span></span>  
  
-   <span data-ttu-id="9b83c-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> udostępnia wygląd i styl pakietu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="9b83c-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> provides the appearance and style of Microsoft Office.</span></span>  
  
-   <span data-ttu-id="9b83c-106"><xref:System.Windows.Forms.ToolStripRenderer> jest abstrakcyjna klasa podstawowa dla innych klas dwóch renderowania.</span><span class="sxs-lookup"><span data-stu-id="9b83c-106"><xref:System.Windows.Forms.ToolStripRenderer> is the abstract base class for the other two rendering classes.</span></span>  
  
 <span data-ttu-id="9b83c-107">Do rysowania niestandardowy (nazywana również Rysowanie przez właściciela) <xref:System.Windows.Forms.ToolStrip>, można zastąpić jedną z klas renderowania i zmienić aspekt logiki renderowania.</span><span class="sxs-lookup"><span data-stu-id="9b83c-107">To custom draw (also known as owner draw) a <xref:System.Windows.Forms.ToolStrip>, you can override one of the renderer classes and change an aspect of the rendering logic.</span></span>  
  
 <span data-ttu-id="9b83c-108">W poniższych procedurach opisano różne aspekty Rysowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="9b83c-108">The following procedures describe various aspects of custom drawing.</span></span>  
  
### <a name="to-switch-between-the-provided-renderers"></a><span data-ttu-id="9b83c-109">Aby przełączyć między podane moduły renderowania</span><span class="sxs-lookup"><span data-stu-id="9b83c-109">To switch between the provided renderers</span></span>  
  
-   <span data-ttu-id="9b83c-110">Ustaw <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> właściwości <xref:System.Windows.Forms.ToolStripRenderMode> ma wartość.</span><span class="sxs-lookup"><span data-stu-id="9b83c-110">Set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to the <xref:System.Windows.Forms.ToolStripRenderMode> value you want.</span></span>  
  
     <span data-ttu-id="9b83c-111">Z <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, statycznych <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> określa renderowania dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b83c-111">With <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, the static <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determines the renderer for your application.</span></span> <span data-ttu-id="9b83c-112">Inne wartości <xref:System.Windows.Forms.ToolStripRenderMode> są <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, i <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span><span class="sxs-lookup"><span data-stu-id="9b83c-112">The other values of <xref:System.Windows.Forms.ToolStripRenderMode> are <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, and <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span></span>  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a><span data-ttu-id="9b83c-113">Aby zmienić Microsoft Office — styl obramowania proste</span><span class="sxs-lookup"><span data-stu-id="9b83c-113">To change the Microsoft Office–style borders to straight</span></span>  
  
-   <span data-ttu-id="9b83c-114">Zastąpienie <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ale nie należy wywoływać klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="9b83c-114">Override <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, but do not call the base class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b83c-115">Dostępna jest wersja tej metody dla <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, i <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span><span class="sxs-lookup"><span data-stu-id="9b83c-115">There is a version of this method for <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, and <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span></span>  
  
### <a name="to-change-the-professionalcolortable"></a><span data-ttu-id="9b83c-116">Aby zmienić professionalcolortable —</span><span class="sxs-lookup"><span data-stu-id="9b83c-116">To change the ProfessionalColorTable</span></span>  
  
-   <span data-ttu-id="9b83c-117">Zastąpienie <xref:System.Windows.Forms.ProfessionalColorTable> i zmiana kolorów ma.</span><span class="sxs-lookup"><span data-stu-id="9b83c-117">Override <xref:System.Windows.Forms.ProfessionalColorTable> and change the colors you want.</span></span>  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a><span data-ttu-id="9b83c-118">Aby zmienić renderowania dla wszystkich kontrolek ToolStrip w aplikacji</span><span class="sxs-lookup"><span data-stu-id="9b83c-118">To change the rendering for all ToolStrip controls in your application</span></span>  
  
1.  <span data-ttu-id="9b83c-119">Użyj <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> właściwości można wybrać jeden z dostarczonego renderowania.</span><span class="sxs-lookup"><span data-stu-id="9b83c-119">Use the <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> property to choose one of the provided renderers.</span></span>  
  
2.  <span data-ttu-id="9b83c-120">Użyj <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> można przypisać niestandardowego modułu renderowania.</span><span class="sxs-lookup"><span data-stu-id="9b83c-120">Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> to assign a custom renderer.</span></span>  
  
3.  <span data-ttu-id="9b83c-121">Upewnij się, że <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> ma ustawioną wartość domyślną <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="9b83c-121">Ensure that <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> is set to the default value of <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a><span data-ttu-id="9b83c-122">Aby wyłączyć kolorów Microsoft Office dla całej aplikacji</span><span class="sxs-lookup"><span data-stu-id="9b83c-122">To turn off the Microsoft Office colors for the entire application</span></span>  
  
-   <span data-ttu-id="9b83c-123">Ustaw <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> do `false`.</span><span class="sxs-lookup"><span data-stu-id="9b83c-123">Set <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> to `false`.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a><span data-ttu-id="9b83c-124">Aby wyłączyć kolorów Microsoft Office dla jednego formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9b83c-124">To turn off the Microsoft Office colors for one ToolStrip control</span></span>  
  
-   <span data-ttu-id="9b83c-125">Użyj kodu podobne do poniższego przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="9b83c-125">Use code similar to the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9b83c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b83c-126">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 [<span data-ttu-id="9b83c-127">Kontrolki z wbudowaną obsługą rysowania przez właściciela</span><span class="sxs-lookup"><span data-stu-id="9b83c-127">Controls with Built-In Owner-Drawing Support</span></span>](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [<span data-ttu-id="9b83c-128">Instrukcje: tworzenie i ustawienie niestandardowego modułu renderowania dla kontrolki ToolStrip w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9b83c-128">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
 [<span data-ttu-id="9b83c-129">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="9b83c-129">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
