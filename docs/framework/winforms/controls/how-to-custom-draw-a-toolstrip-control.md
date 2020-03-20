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
# <a name="how-to-custom-draw-a-toolstrip-control"></a><span data-ttu-id="a383e-102">Porady: niestandardowy rysunek formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a383e-102">How to: Custom Draw a ToolStrip Control</span></span>
<span data-ttu-id="a383e-103">Formanty <xref:System.Windows.Forms.ToolStrip> mają następujące skojarzone klasy renderowania (malowania):</span><span class="sxs-lookup"><span data-stu-id="a383e-103">The <xref:System.Windows.Forms.ToolStrip> controls have the following associated rendering (painting) classes:</span></span>  
  
- <span data-ttu-id="a383e-104"><xref:System.Windows.Forms.ToolStripSystemRenderer>zapewnia wygląd i styl systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a383e-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> provides the appearance and style of your operating system.</span></span>  
  
- <span data-ttu-id="a383e-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer>zapewnia wygląd i styl pakietu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="a383e-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> provides the appearance and style of Microsoft Office.</span></span>  
  
- <span data-ttu-id="a383e-106"><xref:System.Windows.Forms.ToolStripRenderer>jest abstrakcyjną klasą podstawową dla pozostałych dwóch klas renderowania.</span><span class="sxs-lookup"><span data-stu-id="a383e-106"><xref:System.Windows.Forms.ToolStripRenderer> is the abstract base class for the other two rendering classes.</span></span>  
  
 <span data-ttu-id="a383e-107">Aby narysować niestandardowe (znane <xref:System.Windows.Forms.ToolStrip>również jako rysowanie właściciela) a , można zastąpić jedną z klas modułu renderowania i zmienić aspekt logiki renderowania.</span><span class="sxs-lookup"><span data-stu-id="a383e-107">To custom draw (also known as owner draw) a <xref:System.Windows.Forms.ToolStrip>, you can override one of the renderer classes and change an aspect of the rendering logic.</span></span>  
  
 <span data-ttu-id="a383e-108">W poniższych procedurach opisano różne aspekty rysunku niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="a383e-108">The following procedures describe various aspects of custom drawing.</span></span>  
  
### <a name="to-switch-between-the-provided-renderers"></a><span data-ttu-id="a383e-109">Aby przełączać się między dostarczonymi modułami renderowania</span><span class="sxs-lookup"><span data-stu-id="a383e-109">To switch between the provided renderers</span></span>  
  
- <span data-ttu-id="a383e-110">Ustaw <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> właściwość <xref:System.Windows.Forms.ToolStripRenderMode> na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="a383e-110">Set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to the <xref:System.Windows.Forms.ToolStripRenderMode> value you want.</span></span>  
  
     <span data-ttu-id="a383e-111">Za <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>pomocą , <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> statyczne określa moduł renderowania dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a383e-111">With <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, the static <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determines the renderer for your application.</span></span> <span data-ttu-id="a383e-112">Inne wartości <xref:System.Windows.Forms.ToolStripRenderMode> to <xref:System.Windows.Forms.ToolStripRenderMode.Custom> <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, <xref:System.Windows.Forms.ToolStripRenderMode.System>i .</span><span class="sxs-lookup"><span data-stu-id="a383e-112">The other values of <xref:System.Windows.Forms.ToolStripRenderMode> are <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, and <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span></span>  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a><span data-ttu-id="a383e-113">Aby zmienić obramowania w stylu pakietu Microsoft Office na proste</span><span class="sxs-lookup"><span data-stu-id="a383e-113">To change the Microsoft Office–style borders to straight</span></span>  
  
- <span data-ttu-id="a383e-114">Zastądić <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ale nie wywołać klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="a383e-114">Override <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, but do not call the base class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a383e-115">Istnieje wersja tej metody <xref:System.Windows.Forms.ToolStripRenderer>dla <xref:System.Windows.Forms.ToolStripSystemRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>i .</span><span class="sxs-lookup"><span data-stu-id="a383e-115">There is a version of this method for <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, and <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span></span>  
  
### <a name="to-change-the-professionalcolortable"></a><span data-ttu-id="a383e-116">Aby zmienić tabelę ProfessionalColorTable</span><span class="sxs-lookup"><span data-stu-id="a383e-116">To change the ProfessionalColorTable</span></span>  
  
- <span data-ttu-id="a383e-117">Zastąd w <xref:System.Windows.Forms.ProfessionalColorTable> odpowiedni sposób i zmień kolory.</span><span class="sxs-lookup"><span data-stu-id="a383e-117">Override <xref:System.Windows.Forms.ProfessionalColorTable> and change the colors you want.</span></span>  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a><span data-ttu-id="a383e-118">Aby zmienić renderowanie dla wszystkich formantów ToolStrip w aplikacji</span><span class="sxs-lookup"><span data-stu-id="a383e-118">To change the rendering for all ToolStrip controls in your application</span></span>  
  
1. <span data-ttu-id="a383e-119">Użyj <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> właściwości, aby wybrać jeden z dostarczonych modułów renderowania.</span><span class="sxs-lookup"><span data-stu-id="a383e-119">Use the <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> property to choose one of the provided renderers.</span></span>  
  
2. <span data-ttu-id="a383e-120">Służy <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> do przypisywania niestandardowego modułu renderowania.</span><span class="sxs-lookup"><span data-stu-id="a383e-120">Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> to assign a custom renderer.</span></span>  
  
3. <span data-ttu-id="a383e-121">Upewnij <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> się, że jest <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>ustawiona wartość domyślna .</span><span class="sxs-lookup"><span data-stu-id="a383e-121">Ensure that <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> is set to the default value of <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a><span data-ttu-id="a383e-122">Aby wyłączyć kolory pakietu Microsoft Office dla całej aplikacji</span><span class="sxs-lookup"><span data-stu-id="a383e-122">To turn off the Microsoft Office colors for the entire application</span></span>  
  
- <span data-ttu-id="a383e-123">Ustaw <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> `false`na .</span><span class="sxs-lookup"><span data-stu-id="a383e-123">Set <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> to `false`.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a><span data-ttu-id="a383e-124">Aby wyłączyć kolory pakietu Microsoft Office dla jednego formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a383e-124">To turn off the Microsoft Office colors for one ToolStrip control</span></span>  
  
- <span data-ttu-id="a383e-125">Użyj kodu podobnego do poniższego przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="a383e-125">Use code similar to the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a383e-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a383e-126">See also</span></span>

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [<span data-ttu-id="a383e-127">Kontrolki z wbudowaną obsługą rysowania przez właściciela</span><span class="sxs-lookup"><span data-stu-id="a383e-127">Controls with Built-In Owner-Drawing Support</span></span>](controls-with-built-in-owner-drawing-support.md)
- [<span data-ttu-id="a383e-128">Instrukcje: tworzenie i ustawienie niestandardowego modułu renderowania dla kontrolki ToolStrip w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a383e-128">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [<span data-ttu-id="a383e-129">ToolStrip — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="a383e-129">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
