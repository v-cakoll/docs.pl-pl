---
title: 'Instrukcje: projektowanie układu formularzy systemu Windows dobrze reagującego na lokalizację'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
ms.openlocfilehash: 131dc688d2a742fa7a0d99ec7858d4e280c9882f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310762"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="73d1b-102">Instrukcje: projektowanie układu formularzy systemu Windows dobrze reagującego na lokalizację</span><span class="sxs-lookup"><span data-stu-id="73d1b-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="73d1b-103">Tworzenie formularzy, które są gotowe do przeniesienia poza zlokalizowany znacznie rozwoju szybkości na rynki międzynarodowe.</span><span class="sxs-lookup"><span data-stu-id="73d1b-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="73d1b-104">Możesz użyć <xref:System.Windows.Forms.TableLayoutPanel> formantu do zaimplementowania układy odpowiadać bez problemu zmieniała jak formanty zmiany rozmiaru z powodu zmian w ich <xref:System.Windows.Forms.Control.Text%2A> wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="73d1b-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73d1b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="73d1b-105">Example</span></span>  
 <span data-ttu-id="73d1b-106">Ten formularz, pokazuje, jak utworzyć układ, który proporcjonalnie dostosowuje podczas translacji wartości ciągu wyświetlanego w innych językach.</span><span class="sxs-lookup"><span data-stu-id="73d1b-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="73d1b-107">Ten proces tłumaczenia jest nazywany *lokalizacji*.</span><span class="sxs-lookup"><span data-stu-id="73d1b-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="73d1b-108">Aby uzyskać więcej informacji, zobacz [lokalizacji](../../../standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="73d1b-108">For more information, see [Localization](../../../standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="73d1b-109">Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="73d1b-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="73d1b-110">Zobacz też [instruktażu: Tworzenie układu, który dostosowuje proporcje dla lokalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="73d1b-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a><span data-ttu-id="73d1b-111">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="73d1b-111">Additional resources</span></span>
1. [<span data-ttu-id="73d1b-112">Instrukcje: wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="73d1b-112">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="73d1b-113">Przewodnik: rozmieszczanie kontrolek w aplikacji formularzy systemu Windows za pomocą FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="73d1b-113">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [<span data-ttu-id="73d1b-114">Instrukcje: obejmowanie rzędów i kolumn w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="73d1b-114">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="73d1b-115">Instrukcje: edytowanie rzędów i kolumn w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="73d1b-115">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [<span data-ttu-id="73d1b-116">Przewodnik: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="73d1b-116">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [<span data-ttu-id="73d1b-117">Przewodnik: rozmieszczanie kontrolek w aplikacji formularzy systemu Windows za pomocą TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="73d1b-117">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [<span data-ttu-id="73d1b-118">Przewodnik: tworzenie kontrolek formularzy systemu Windows z uzupełnieniem, marginesami oraz właściwościami AutoSize</span><span class="sxs-lookup"><span data-stu-id="73d1b-118">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)  
  
8. [<span data-ttu-id="73d1b-119">Instrukcje: Obsługiwanie lokalizacji na Windows Forms przy użyciu AutoSize i TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="73d1b-119">How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [<span data-ttu-id="73d1b-120">Przewodnik: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych</span><span class="sxs-lookup"><span data-stu-id="73d1b-120">Walkthrough: Creating a Resizable Windows Form for Data Entry</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a><span data-ttu-id="73d1b-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="73d1b-121">Compiling the Code</span></span>  
 <span data-ttu-id="73d1b-122">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="73d1b-122">This example requires:</span></span>  
  
-   <span data-ttu-id="73d1b-123">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="73d1b-123">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="73d1b-124">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="73d1b-124">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="73d1b-125">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="73d1b-125">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73d1b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73d1b-126">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="73d1b-127">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="73d1b-127">Localization</span></span>](../../../standard/globalization-localization/localization.md)
