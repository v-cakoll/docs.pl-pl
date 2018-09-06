---
title: 'Porady: projektowanie układu formularzy systemu Windows dobrze reagującego na lokalizację'
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
ms.openlocfilehash: c72cae58e8486f1187fd27d200522a43dca328ca
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44032004"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="3fdc2-102">Porady: projektowanie układu formularzy systemu Windows dobrze reagującego na lokalizację</span><span class="sxs-lookup"><span data-stu-id="3fdc2-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="3fdc2-103">Tworzenie formularzy, które są gotowe do przeniesienia poza zlokalizowany znacznie rozwoju szybkości na rynki międzynarodowe.</span><span class="sxs-lookup"><span data-stu-id="3fdc2-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="3fdc2-104">Możesz użyć <xref:System.Windows.Forms.TableLayoutPanel> formantu do zaimplementowania układy odpowiadać bez problemu zmieniała jak formanty zmiany rozmiaru z powodu zmian w ich <xref:System.Windows.Forms.Control.Text%2A> wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="3fdc2-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fdc2-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fdc2-105">Example</span></span>  
 <span data-ttu-id="3fdc2-106">Ten formularz, pokazuje, jak utworzyć układ, który proporcjonalnie dostosowuje podczas translacji wartości ciągu wyświetlanego w innych językach.</span><span class="sxs-lookup"><span data-stu-id="3fdc2-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="3fdc2-107">Ten proces tłumaczenia jest nazywany *lokalizacji*.</span><span class="sxs-lookup"><span data-stu-id="3fdc2-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="3fdc2-108">Aby uzyskać więcej informacji, zobacz [lokalizacji](../../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="3fdc2-108">For more information, see [Localization](../../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="3fdc2-109">Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3fdc2-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="3fdc2-110">Zobacz też [wskazówki: tworzenie układu, który dostosowuje proporcje dla lokalizacji](https://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="3fdc2-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  [<span data-ttu-id="3fdc2-111">Instrukcje: wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="3fdc2-111">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  <span data-ttu-id="3fdc2-112">[Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3fdc2-112">[Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span></span>  
  
3.  [<span data-ttu-id="3fdc2-113">Instrukcje: obejmowanie rzędów i kolumn w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="3fdc2-113">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4.  [<span data-ttu-id="3fdc2-114">Instrukcje: edytowanie rzędów i kolumn w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="3fdc2-114">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5.  <span data-ttu-id="3fdc2-115">[Przewodnik: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy Windows Forms](https://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3fdc2-115">[Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](https://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span></span>  
  
6.  <span data-ttu-id="3fdc2-116">[Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3fdc2-116">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
7.  <span data-ttu-id="3fdc2-117">[Przewodnik: tworzenie kontrolek formularzy Windows Forms z uzupełnieniem, marginesami oraz właściwościami AutoSize](https://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3fdc2-117">[Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](https://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span></span>  
  
8.  <span data-ttu-id="3fdc2-118">[Porady: obsługiwanie lokalizacji na Windows Forms przy użyciu AutoSize i TableLayoutPanel](https://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3fdc2-118">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span></span>  
  
9. <span data-ttu-id="3fdc2-119">[Wskazówki: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych](https://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3fdc2-119">[Walkthrough: Creating a Resizable Windows Form for Data Entry](https://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3fdc2-120">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3fdc2-120">Compiling the Code</span></span>  
 <span data-ttu-id="3fdc2-121">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="3fdc2-121">This example requires:</span></span>  
  
-   <span data-ttu-id="3fdc2-122">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="3fdc2-122">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3fdc2-123">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3fdc2-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3fdc2-124">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="3fdc2-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="3fdc2-125">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="3fdc2-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fdc2-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3fdc2-126">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [<span data-ttu-id="3fdc2-127">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="3fdc2-127">Localization</span></span>](../../../../docs/standard/globalization-localization/localization.md)
