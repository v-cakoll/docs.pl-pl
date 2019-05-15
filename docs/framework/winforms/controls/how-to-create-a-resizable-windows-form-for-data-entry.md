---
title: 'Instrukcje: tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych'
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
ms.openlocfilehash: 1b27c0e67aae1935c4216654d9f3ddf557719572
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588940"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="75ce1-102">Instrukcje: tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych</span><span class="sxs-lookup"><span data-stu-id="75ce1-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="75ce1-103">Dobre układ odpowiada również zmiany w wymiarach jego formularza nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="75ce1-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="75ce1-104">Możesz użyć <xref:System.Windows.Forms.TableLayoutPanel> kontroli do układu formularza w taki sposób, aby zmienić rozmiar i położenie formantów w spójny sposób zmianami Wymiary formularza.</span><span class="sxs-lookup"><span data-stu-id="75ce1-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="75ce1-105"><xref:System.Windows.Forms.TableLayoutPanel> Kontroli jest również przydatne w przypadku gdy zmienia się w zawartości kontrolki Przyczyna zmiany w układzie.</span><span class="sxs-lookup"><span data-stu-id="75ce1-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="75ce1-106">Proces omówione w tej procedurze, możesz to zrobić w środowisku Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75ce1-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="75ce1-107">Zobacz też [instruktażu: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="75ce1-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75ce1-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="75ce1-108">Example</span></span>  
 <span data-ttu-id="75ce1-109">Poniższy przykład pokazuje sposób użycia <xref:System.Windows.Forms.TableLayoutPanel> kontrolki do tworzenia układu, który odpowiada również, gdy użytkownik zmienia rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="75ce1-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="75ce1-110">Ilustruje też układ, dobrze reagującego na lokalizację.</span><span class="sxs-lookup"><span data-stu-id="75ce1-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="75ce1-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="75ce1-111">Compiling the Code</span></span>  
 <span data-ttu-id="75ce1-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="75ce1-112">This example requires:</span></span>  
  
- <span data-ttu-id="75ce1-113">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="75ce1-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75ce1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75ce1-114">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="75ce1-115">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="75ce1-115">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="75ce1-116">Instrukcje: Projektowanie układu formularzy Windows dobrze reagującego na lokalizację</span><span class="sxs-lookup"><span data-stu-id="75ce1-116">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="75ce1-117">Środowisko użytkownika Microsoft Windows, oficjalnych wytycznych dotyczących projektanci i deweloperzy interfejsu użytkownika. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span><span class="sxs-lookup"><span data-stu-id="75ce1-117">Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span></span>](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
