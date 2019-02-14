---
title: 'Instrukcje: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: bd796d241cbb910bc23d1df428f08f267a831dd7
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261443"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="98c4e-102">Instrukcje: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych</span><span class="sxs-lookup"><span data-stu-id="98c4e-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="98c4e-103">Dobre układ odpowiada również zmiany w wymiarach jego formularza nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="98c4e-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="98c4e-104">Możesz użyć <xref:System.Windows.Forms.TableLayoutPanel> kontroli do układu formularza w taki sposób, aby zmienić rozmiar i położenie formantów w spójny sposób zmianami Wymiary formularza.</span><span class="sxs-lookup"><span data-stu-id="98c4e-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="98c4e-105"><xref:System.Windows.Forms.TableLayoutPanel> Kontroli jest również przydatne w przypadku gdy zmienia się w zawartości kontrolki Przyczyna zmiany w układzie.</span><span class="sxs-lookup"><span data-stu-id="98c4e-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="98c4e-106">Proces omówione w tej procedurze, możesz to zrobić w środowisku Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98c4e-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="98c4e-107">Zobacz też [instruktażu: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="98c4e-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98c4e-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="98c4e-108">Example</span></span>  
 <span data-ttu-id="98c4e-109">Poniższy przykład pokazuje sposób użycia <xref:System.Windows.Forms.TableLayoutPanel> kontrolki do tworzenia układu, który odpowiada również, gdy użytkownik zmienia rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="98c4e-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="98c4e-110">Ilustruje też układ, dobrze reagującego na lokalizację.</span><span class="sxs-lookup"><span data-stu-id="98c4e-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98c4e-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="98c4e-111">Compiling the Code</span></span>  
 <span data-ttu-id="98c4e-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="98c4e-112">This example requires:</span></span>  
  
-   <span data-ttu-id="98c4e-113">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="98c4e-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="98c4e-114">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="98c4e-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="98c4e-115">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="98c4e-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98c4e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98c4e-116">See also</span></span>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="98c4e-117">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="98c4e-117">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="98c4e-118">Instrukcje: Projektowanie układu formularzy Windows dobrze reagującego na lokalizację</span><span class="sxs-lookup"><span data-stu-id="98c4e-118">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="98c4e-119">Środowisko użytkownika Microsoft Windows, oficjalnych wytycznych dotyczących projektanci i deweloperzy interfejsu użytkownika. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span><span class="sxs-lookup"><span data-stu-id="98c4e-119">Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span></span>](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
