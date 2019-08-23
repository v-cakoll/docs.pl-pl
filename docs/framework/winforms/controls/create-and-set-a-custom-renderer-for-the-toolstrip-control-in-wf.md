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
ms.openlocfilehash: c354ace3a7d3ce43f549dd1295a85fbee004eb22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929738"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="c1db3-102">Instrukcje: tworzenie i ustawienie niestandardowego modułu renderowania dla kontrolki ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c1db3-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="c1db3-103"><xref:System.Windows.Forms.ToolStrip>kontrolki zapewniają łatwą obsługę motywów i stylów.</span><span class="sxs-lookup"><span data-stu-id="c1db3-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="c1db3-104">Możesz uzyskać całkowicie niestandardowy wygląd i zachowanie (wygląd i działanie), ustawiając <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> Właściwość <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> lub właściwość na niestandardowy moduł renderujący.</span><span class="sxs-lookup"><span data-stu-id="c1db3-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="c1db3-105">Można przypisać moduły <xref:System.Windows.Forms.ToolStrip>renderowania do poszczególnych osób <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> lub <xref:System.Windows.Forms.StatusStrip> kontrolki, lub użyć właściwości, aby wpływać na wszystkie obiekty przez ustawienie <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> właściwości na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c1db3-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1db3-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A>zwraca <xref:System.Windows.Forms.ToolStripRenderMode.Custom> tylko wtedy, gdy <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> wartość nie `null`jest.</span><span class="sxs-lookup"><span data-stu-id="c1db3-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="c1db3-107">Aby utworzyć niestandardowy moduł renderujący</span><span class="sxs-lookup"><span data-stu-id="c1db3-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="c1db3-108"><xref:System.Windows.Forms.ToolStripRenderer> Rozwiń klasę.</span><span class="sxs-lookup"><span data-stu-id="c1db3-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="c1db3-109">Zaimplementuj żądane renderowanie niestandardowe przez zastępowanie właściwych *w...*</span><span class="sxs-lookup"><span data-stu-id="c1db3-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="c1db3-110">elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c1db3-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="c1db3-111">Aby ustawić moduł renderowania niestandardowego jako bieżący moduł renderowania</span><span class="sxs-lookup"><span data-stu-id="c1db3-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="c1db3-112">Aby ustawić niestandardowy moduł renderujący dla <xref:System.Windows.Forms.ToolStrip>jednego, <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> ustaw właściwość na niestandardowy moduł renderowania.</span><span class="sxs-lookup"><span data-stu-id="c1db3-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="c1db3-113">Lub w celu ustawienia modułu renderowania niestandardowego dla <xref:System.Windows.Forms.ToolStrip> wszystkich klas zawartych w aplikacji: Ustaw właściwość na moduł renderowania niestandardowego i <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> ustaw właściwość na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>. <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c1db3-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c1db3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1db3-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="c1db3-115">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="c1db3-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="c1db3-116">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="c1db3-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="c1db3-117">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="c1db3-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
