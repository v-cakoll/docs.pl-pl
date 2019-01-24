---
title: 'Instrukcje: Rozciąganie elementu ToolStripTextBox w celu wypełnienia pozostałego szerokości ToolStrip (formularze Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: 411c00743f0a02bdd498211d03b195aaaf023ecb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612271"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="719ff-102">Instrukcje: Rozciąganie elementu ToolStripTextBox w celu wypełnienia pozostałego szerokości ToolStrip (formularze Windows)</span><span class="sxs-lookup"><span data-stu-id="719ff-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="719ff-103">Po ustawieniu <xref:System.Windows.Forms.ToolStrip.Stretch%2A> właściwość <xref:System.Windows.Forms.ToolStrip> kontrolę `true`, formant wypełnienia jego kontenera od końca do końca i zmienia rozmiar, gdy jego kontenera zmienia rozmiar.</span><span class="sxs-lookup"><span data-stu-id="719ff-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="719ff-104">W tej konfiguracji, może okazać się przydatne do rozciągania element w kontrolce, takich jak <xref:System.Windows.Forms.ToolStripTextBox>, w celu wypełnienia dostępnego miejsca, jak i rozmiaru, gdy zmienia rozmiar kontrolki.</span><span class="sxs-lookup"><span data-stu-id="719ff-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="719ff-105">Rozciąganie ten jest przydatne na przykład, jeśli chcesz osiągnąć wygląd i zachowanie podobne do paska adresu w programie Microsoft® Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="719ff-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="719ff-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="719ff-106">Example</span></span>  
 <span data-ttu-id="719ff-107">Poniższy przykład kodu zawiera klasę pochodną <xref:System.Windows.Forms.ToolStripTextBox> o nazwie `ToolStripSpringTextBox`.</span><span class="sxs-lookup"><span data-stu-id="719ff-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="719ff-108">Ta klasa zastępuje <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> metodę obliczania dostępności szerokość elementu nadrzędnego <xref:System.Windows.Forms.ToolStrip> sterowania po odjęciu łączna szerokość wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="719ff-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="719ff-109">Ten przykład kodu udostępnia również <xref:System.Windows.Forms.Form> klasy i `Program` klasę wykazać nowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="719ff-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="719ff-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="719ff-110">Compiling the Code</span></span>  
 <span data-ttu-id="719ff-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="719ff-111">This example requires:</span></span>  
  
-   <span data-ttu-id="719ff-112">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="719ff-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="719ff-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="719ff-113">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [<span data-ttu-id="719ff-114">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="719ff-114">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [<span data-ttu-id="719ff-115">Instrukcje: Użycie właściwości Spring interaktywnie w StatusStrip</span><span class="sxs-lookup"><span data-stu-id="719ff-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
