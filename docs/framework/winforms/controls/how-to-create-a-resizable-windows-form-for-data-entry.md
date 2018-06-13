---
title: 'Porady: tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych'
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
ms.openlocfilehash: a7768b3c6be10373e742cbeea0028d1aee0b261d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531794"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="e30d5-102">Porady: tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych</span><span class="sxs-lookup"><span data-stu-id="e30d5-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="e30d5-103">Dobrym układu odpowiada również zmiany w wymiarach jego formularza nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="e30d5-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="e30d5-104">Można użyć <xref:System.Windows.Forms.TableLayoutPanel> formant układu formularza do zmiany rozmiaru i umieść formanty w spójny sposób, jak zmiany wymiarów formularza.</span><span class="sxs-lookup"><span data-stu-id="e30d5-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="e30d5-105"><xref:System.Windows.Forms.TableLayoutPanel> Formant jest również przydatne w przypadku gdy zmienia się zawartość formantów Przyczyna zmiany w układzie.</span><span class="sxs-lookup"><span data-stu-id="e30d5-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="e30d5-106">Proces omówione w tej procedurze można zrobić w środowisku Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e30d5-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="e30d5-107">Zobacz też [wskazówki: Tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych](http://msdn.microsoft.com/library/991eahec\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e30d5-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](http://msdn.microsoft.com/library/991eahec\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e30d5-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="e30d5-108">Example</span></span>  
 <span data-ttu-id="e30d5-109">W poniższym przykładzie pokazano sposób użycia <xref:System.Windows.Forms.TableLayoutPanel> formantu do tworzenia układu, który reaguje także, gdy użytkownik zmienia rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="e30d5-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="e30d5-110">Ilustruje też dobrze reagującego na układ.</span><span class="sxs-lookup"><span data-stu-id="e30d5-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e30d5-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e30d5-111">Compiling the Code</span></span>  
 <span data-ttu-id="e30d5-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e30d5-112">This example requires:</span></span>  
  
-   <span data-ttu-id="e30d5-113">Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e30d5-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e30d5-114">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e30d5-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e30d5-115">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="e30d5-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e30d5-116">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e30d5-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e30d5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e30d5-117">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="e30d5-118">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e30d5-118">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="e30d5-119">Instrukcje: projektowanie układu formularzy Windows Forms dobrze reagującego na lokalizację</span><span class="sxs-lookup"><span data-stu-id="e30d5-119">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [<span data-ttu-id="e30d5-120">Środowisko użytkownika systemu Windows firmy Microsoft, oficjalnego wskazówki dla deweloperów interfejsu użytkownika i projektantów. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span><span class="sxs-lookup"><span data-stu-id="e30d5-120">Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span></span>](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)
