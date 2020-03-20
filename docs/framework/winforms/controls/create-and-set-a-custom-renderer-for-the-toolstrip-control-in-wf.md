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
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="e5542-102">Porady: tworzenie i ustawienie niestandardowego modułu renderowania dla formantu ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e5542-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="e5542-103"><xref:System.Windows.Forms.ToolStrip>zapewniają łatwe wsparcie dla tematów i stylów.</span><span class="sxs-lookup"><span data-stu-id="e5542-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="e5542-104">Można osiągnąć całkowicie niestandardowy wygląd i zachowanie (wygląd <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> i działanie), ustawiając właściwość lub <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> właściwość do niestandardowego modułu renderowania.</span><span class="sxs-lookup"><span data-stu-id="e5542-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="e5542-105">Można przypisać moduły renderowania <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip>do <xref:System.Windows.Forms.StatusStrip> każdej osoby <xref:System.Windows.Forms.ToolStrip>, , <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> lub formantu, lub można użyć właściwości, aby wpłynąć na wszystkie obiekty, ustawiając <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> właściwość na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e5542-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5542-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A>zwraca <xref:System.Windows.Forms.ToolStripRenderMode.Custom> tylko wtedy, <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> gdy `null`wartość nie jest .</span><span class="sxs-lookup"><span data-stu-id="e5542-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="e5542-107">Aby utworzyć niestandardowy moduł renderowania</span><span class="sxs-lookup"><span data-stu-id="e5542-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="e5542-108">Rozszerz <xref:System.Windows.Forms.ToolStripRenderer> klasę.</span><span class="sxs-lookup"><span data-stu-id="e5542-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="e5542-109">Zaimplementuj żądane renderowanie niestandardowe, zastępując odpowiednie *włączone...*</span><span class="sxs-lookup"><span data-stu-id="e5542-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="e5542-110">elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e5542-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="e5542-111">Aby ustawić niestandardowy moduł renderowania jako bieżący moduł renderowania</span><span class="sxs-lookup"><span data-stu-id="e5542-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="e5542-112">Aby ustawić niestandardowy moduł <xref:System.Windows.Forms.ToolStrip>renderowania <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> dla jednego , ustaw właściwość na niestandardowy moduł renderowania.</span><span class="sxs-lookup"><span data-stu-id="e5542-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="e5542-113">Lub ustawić niestandardowy moduł <xref:System.Windows.Forms.ToolStrip> renderowania dla wszystkich klas <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> zawartych w aplikacji: Ustaw <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> właściwość na niestandardowy moduł renderowania i ustaw właściwość na <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="e5542-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e5542-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5542-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="e5542-115">ToolStrip — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="e5542-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="e5542-116">ToolStrip — Architektura formantu</span><span class="sxs-lookup"><span data-stu-id="e5542-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="e5542-117">Podsumowanie informacji o technologii formantów ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e5542-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
