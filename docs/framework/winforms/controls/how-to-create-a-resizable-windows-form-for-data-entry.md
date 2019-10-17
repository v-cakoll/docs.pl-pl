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
ms.openlocfilehash: aeab1b506b9ded4c3c2ab527f07a8655a44cad2b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396028"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="9bc17-102">Porady: tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych</span><span class="sxs-lookup"><span data-stu-id="9bc17-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="9bc17-103">Dobry układ reaguje na zmiany w wymiarach jego formularza nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="9bc17-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="9bc17-104">Za pomocą kontrolki <xref:System.Windows.Forms.TableLayoutPanel> można rozmieścić układ formularza w celu zmiany rozmiaru i położenia kontrolek w spójny sposób.</span><span class="sxs-lookup"><span data-stu-id="9bc17-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="9bc17-105">Formant <xref:System.Windows.Forms.TableLayoutPanel> jest również przydatny, gdy zmiany w zawartości formantów powodują zmiany w układzie.</span><span class="sxs-lookup"><span data-stu-id="9bc17-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="9bc17-106">Proces objęty tą procedurą można wykonać w środowisku programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9bc17-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="9bc17-107">Zobacz też [Przewodnik: Tworzenie formularza systemu Windows o zmiennym rozmiarze do wprowadzania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9bc17-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bc17-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="9bc17-108">Example</span></span>  
 <span data-ttu-id="9bc17-109">Poniższy przykład ilustruje sposób używania kontrolki <xref:System.Windows.Forms.TableLayoutPanel> do kompilowania układu, który reaguje, gdy użytkownik zmienia rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="9bc17-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="9bc17-110">Przedstawiono w nim również układ, który reaguje na lokalizację.</span><span class="sxs-lookup"><span data-stu-id="9bc17-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9bc17-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9bc17-111">Compiling the Code</span></span>  
 <span data-ttu-id="9bc17-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="9bc17-112">This example requires:</span></span>  
  
- <span data-ttu-id="9bc17-113">Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="9bc17-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc17-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bc17-114">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="9bc17-115">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="9bc17-115">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="9bc17-116">Instrukcje: projektowanie układu formularzy Windows Forms dobrze reagującego na lokalizację</span><span class="sxs-lookup"><span data-stu-id="9bc17-116">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
