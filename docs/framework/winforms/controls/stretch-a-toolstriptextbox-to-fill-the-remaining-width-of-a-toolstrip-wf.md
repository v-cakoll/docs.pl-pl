---
title: "Porady: rozciąganie ToolStripTextBox w celu uzupełnienia szerokości ToolStrip (Formularze systemu Windows)"
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
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 213929e52f08fff19eb7641092789501c31648e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="cd8f8-102">Porady: rozciąganie ToolStripTextBox w celu uzupełnienia szerokości ToolStrip (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="cd8f8-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="cd8f8-103">Podczas ustawiania <xref:System.Windows.Forms.ToolStrip.Stretch%2A> właściwość <xref:System.Windows.Forms.ToolStrip> formant `true`, formantu wypełnia jego kontenera od końca do końca i zmienia rozmiar w przypadku jego kontenera zmienia rozmiar.</span><span class="sxs-lookup"><span data-stu-id="cd8f8-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="cd8f8-104">Ta konfiguracja może być przydatne do rozciągania elementu w formancie, takich jak <xref:System.Windows.Forms.ToolStripTextBox>, w celu wypełnienia dostępnego miejsca, jak i rozmiaru, gdy zmienia rozmiar formantu.</span><span class="sxs-lookup"><span data-stu-id="cd8f8-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="cd8f8-105">Rozciąganie ten jest przydatne, na przykład, jeśli chcesz osiągnąć wygląd i zachowanie jest podobne do paska adresu w programie Microsoft® Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="cd8f8-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd8f8-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd8f8-106">Example</span></span>  
 <span data-ttu-id="cd8f8-107">W poniższym przykładzie kodu przedstawiono klasę pochodzącą od <xref:System.Windows.Forms.ToolStripTextBox> o nazwie `ToolStripSpringTextBox`.</span><span class="sxs-lookup"><span data-stu-id="cd8f8-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="cd8f8-108">Ta klasa zastępuje <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> metodę obliczania dostępności szerokość elementu nadrzędnego <xref:System.Windows.Forms.ToolStrip> kontrolować, po odjęciu łączna szerokość wszystkie inne elementy.</span><span class="sxs-lookup"><span data-stu-id="cd8f8-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="cd8f8-109">W tym przykładzie kodu udostępnia również <xref:System.Windows.Forms.Form> klasy i `Program` klasy, aby zademonstrować nowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="cd8f8-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cd8f8-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="cd8f8-110">Compiling the Code</span></span>  
 <span data-ttu-id="cd8f8-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="cd8f8-111">This example requires:</span></span>  
  
-   <span data-ttu-id="cd8f8-112">Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="cd8f8-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd8f8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd8f8-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripTextBox>  
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="cd8f8-114">ToolStrip — architektura formantu</span><span class="sxs-lookup"><span data-stu-id="cd8f8-114">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="cd8f8-115">Porady: użycie właściwości Spring interaktywnie w StatusStrip</span><span class="sxs-lookup"><span data-stu-id="cd8f8-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
