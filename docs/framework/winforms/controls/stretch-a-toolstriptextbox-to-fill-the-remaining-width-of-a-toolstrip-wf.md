---
title: 'Porady: rozciąganie ToolStripTextBox w celu uzupełnienia szerokości ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: c60cc2a377f08a73159f25b2ab5f2812d41f0c10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742841"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="1439f-102">Porady: rozciąganie ToolStripTextBox w celu uzupełnienia szerokości ToolStrip (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="1439f-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="1439f-103">Po ustawieniu właściwości <xref:System.Windows.Forms.ToolStrip.Stretch%2A> kontrolki <xref:System.Windows.Forms.ToolStrip> na `true`, formant wypełni jego kontener od końca do końca i zmienia rozmiar, gdy rozmiar kontenera zostanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="1439f-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="1439f-104">W tej konfiguracji przydatne może być rozciągnięcie elementu w formancie, takiego jak <xref:System.Windows.Forms.ToolStripTextBox>, wypełnienie dostępnego miejsca i zmiana rozmiaru kontrolki.</span><span class="sxs-lookup"><span data-stu-id="1439f-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="1439f-105">To rozciąganie jest przydatne, jeśli na przykład chcesz uzyskać wygląd i zachowanie podobne do paska adresu w programie Microsoft® Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="1439f-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1439f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1439f-106">Example</span></span>  
 <span data-ttu-id="1439f-107">Poniższy przykład kodu udostępnia klasę pochodną <xref:System.Windows.Forms.ToolStripTextBox> o nazwie `ToolStripSpringTextBox`.</span><span class="sxs-lookup"><span data-stu-id="1439f-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="1439f-108">Ta klasa przesłania metodę <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A>, aby obliczyć dostępną szerokość kontrolki nadrzędnej <xref:System.Windows.Forms.ToolStrip> po odjęciu połączonej szerokości wszystkich innych elementów.</span><span class="sxs-lookup"><span data-stu-id="1439f-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="1439f-109">Ten przykład kodu dostarcza również klasy <xref:System.Windows.Forms.Form> i klasy `Program`, aby pokazać nowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="1439f-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1439f-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1439f-110">Compiling the Code</span></span>  
 <span data-ttu-id="1439f-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="1439f-111">This example requires:</span></span>  
  
- <span data-ttu-id="1439f-112">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="1439f-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1439f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1439f-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1439f-114">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="1439f-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="1439f-115">Instrukcje: użycie właściwości Spring interaktywnie w kontrolce StatusStrip</span><span class="sxs-lookup"><span data-stu-id="1439f-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
