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
ms.openlocfilehash: ca1a7444c029632f83b1600e5855a13c83777594
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296384"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="97312-102">Instrukcje: tworzenie i ustawienie niestandardowego modułu renderowania dla kontrolki ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="97312-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<xref:System.Windows.Forms.ToolStrip> <span data-ttu-id="97312-103">kontrolki daj pomocy technicznej łatwe do kompozycje i style.</span><span class="sxs-lookup"><span data-stu-id="97312-103">controls give easy support to themes and styles.</span></span> <span data-ttu-id="97312-104">Można osiągnąć zupełnie niestandardowy wygląd i zachowanie (wygląd i działanie), ustawiając opcję <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> właściwości lub <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> właściwości do niestandardowego modułu renderowania.</span><span class="sxs-lookup"><span data-stu-id="97312-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="97312-105">Programy renderujące można przypisać do poszczególnych osób <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, lub <xref:System.Windows.Forms.StatusStrip> kontroli, lub użyć <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> mają wpływ na wszystkie obiekty, ustawiając właściwość <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> właściwość <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="97312-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> <span data-ttu-id="97312-106">Zwraca <xref:System.Windows.Forms.ToolStripRenderMode.Custom> tylko wtedy, gdy wartość <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> nie `null`.</span><span class="sxs-lookup"><span data-stu-id="97312-106">returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="97312-107">Aby utworzyć niestandardowego modułu renderowania</span><span class="sxs-lookup"><span data-stu-id="97312-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="97312-108">Rozszerzanie <xref:System.Windows.Forms.ToolStripRenderer> klasy.</span><span class="sxs-lookup"><span data-stu-id="97312-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="97312-109">Implementuj żądane niestandardowe renderowanie przez zastąpienie odpowiednie *na...*</span><span class="sxs-lookup"><span data-stu-id="97312-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="97312-110">elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="97312-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="97312-111">Aby ustawić niestandardowego modułu renderowania do bieżącego programu renderującego</span><span class="sxs-lookup"><span data-stu-id="97312-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="97312-112">Aby ustawić niestandardowego modułu renderowania dla jednego <xref:System.Windows.Forms.ToolStrip>ustaw <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> właściwości do niestandardowego modułu renderowania.</span><span class="sxs-lookup"><span data-stu-id="97312-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="97312-113">Lub ustawienie niestandardowego modułu renderowania dla wszystkich <xref:System.Windows.Forms.ToolStrip> klasy zawarte w Twojej aplikacji: Ustaw <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> właściwości do niestandardowego modułu renderowania, a zestaw <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> właściwość <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="97312-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="97312-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97312-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="97312-115">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="97312-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="97312-116">ToolStrip — Architektura formantu</span><span class="sxs-lookup"><span data-stu-id="97312-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="97312-117">Podsumowanie informacji o technologii formantów ToolStrip</span><span class="sxs-lookup"><span data-stu-id="97312-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
