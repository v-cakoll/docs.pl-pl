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
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="858d8-102">Porady: tworzenie i ustawienie niestandardowego modułu renderowania dla formantu ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="858d8-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="858d8-103">formanty <xref:System.Windows.Forms.ToolStrip> zapewniają łatwą obsługę motywów i stylów.</span><span class="sxs-lookup"><span data-stu-id="858d8-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="858d8-104">Możesz uzyskać zupełnie niestandardową wygląd i zachowanie (wygląd i działanie), ustawiając właściwość <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> lub właściwość <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> na moduł renderowania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="858d8-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="858d8-105">Można przypisać moduły renderowania do poszczególnych <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>lub kontrolki <xref:System.Windows.Forms.StatusStrip> lub użyć właściwości <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>, aby wpływać na wszystkie obiekty przez ustawienie właściwości <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="858d8-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="858d8-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> zwraca <xref:System.Windows.Forms.ToolStripRenderMode.Custom> tylko wtedy, gdy wartość <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> nie jest `null`.</span><span class="sxs-lookup"><span data-stu-id="858d8-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="858d8-107">Aby utworzyć niestandardowy moduł renderujący</span><span class="sxs-lookup"><span data-stu-id="858d8-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="858d8-108">Rozwiń klasę <xref:System.Windows.Forms.ToolStripRenderer>.</span><span class="sxs-lookup"><span data-stu-id="858d8-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="858d8-109">Zaimplementuj żądane renderowanie niestandardowe przez zastępowanie właściwych *w...*</span><span class="sxs-lookup"><span data-stu-id="858d8-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="858d8-110">elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="858d8-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="858d8-111">Aby ustawić moduł renderowania niestandardowego jako bieżący moduł renderowania</span><span class="sxs-lookup"><span data-stu-id="858d8-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="858d8-112">Aby ustawić niestandardowy moduł renderujący dla jednego <xref:System.Windows.Forms.ToolStrip>, ustaw właściwość <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> na renderowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="858d8-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="858d8-113">Lub w celu ustawienia modułu renderowania niestandardowego dla wszystkich <xref:System.Windows.Forms.ToolStrip> klas zawartych w aplikacji: Ustaw właściwość <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> na moduł renderowania niestandardowego i ustaw właściwość <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="858d8-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="858d8-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="858d8-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="858d8-115">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="858d8-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="858d8-116">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="858d8-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="858d8-117">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="858d8-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
