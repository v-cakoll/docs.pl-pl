---
title: 'Instrukcje: Projektowanie układu formularzy Windows dobrze reagującego na lokalizację'
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
ms.openlocfilehash: 15f290f7d076eede7a8092d7295df810e4e51bf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563525"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="6fd49-102">Instrukcje: Projektowanie układu formularzy Windows dobrze reagującego na lokalizację</span><span class="sxs-lookup"><span data-stu-id="6fd49-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="6fd49-103">Tworzenie formularzy, które są gotowe do przeniesienia poza zlokalizowany znacznie rozwoju szybkości na rynki międzynarodowe.</span><span class="sxs-lookup"><span data-stu-id="6fd49-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="6fd49-104">Możesz użyć <xref:System.Windows.Forms.TableLayoutPanel> formantu do zaimplementowania układy odpowiadać bez problemu zmieniała jak formanty zmiany rozmiaru z powodu zmian w ich <xref:System.Windows.Forms.Control.Text%2A> wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fd49-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fd49-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fd49-105">Example</span></span>  
 <span data-ttu-id="6fd49-106">Ten formularz, pokazuje, jak utworzyć układ, który proporcjonalnie dostosowuje podczas translacji wartości ciągu wyświetlanego w innych językach.</span><span class="sxs-lookup"><span data-stu-id="6fd49-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="6fd49-107">Ten proces tłumaczenia jest nazywany *lokalizacji*.</span><span class="sxs-lookup"><span data-stu-id="6fd49-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="6fd49-108">Aby uzyskać więcej informacji, zobacz [lokalizacji](../../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="6fd49-108">For more information, see [Localization](../../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="6fd49-109">Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6fd49-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="6fd49-110">Zobacz też [instruktażu: Tworzenie układu, który dostosowuje proporcje dla lokalizacji](https://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6fd49-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  [<span data-ttu-id="6fd49-111">Instrukcje: Wyrównaj i rozciągnij kontrolki w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6fd49-111">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  <span data-ttu-id="6fd49-112">[Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą FlowLayoutPanel](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6fd49-112">[Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span></span>  
  
3.  [<span data-ttu-id="6fd49-113">Instrukcje: Obejmowanie rzędów i kolumn w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6fd49-113">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4.  [<span data-ttu-id="6fd49-114">Instrukcje: Edytowanie rzędów i kolumn w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6fd49-114">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5.  <span data-ttu-id="6fd49-115">[Przewodnik: Wykonywania typowych zadań przy użyciu inteligentnych tagów w Windows Forms, formanty](https://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6fd49-115">[Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](https://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span></span>  
  
6.  <span data-ttu-id="6fd49-116">[Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6fd49-116">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
7.  <span data-ttu-id="6fd49-117">[Przewodnik: Układania Windows formantów formularzy przy użyciu dopełnienie, marginesy oraz właściwościami AutoSize](https://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6fd49-117">[Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](https://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span></span>  
  
8.  <span data-ttu-id="6fd49-118">[Instrukcje: Obsługiwanie lokalizacji na Windows Forms przy użyciu AutoSize i TableLayoutPanel](https://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6fd49-118">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span></span>  
  
9. <span data-ttu-id="6fd49-119">[Przewodnik: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych](https://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6fd49-119">[Walkthrough: Creating a Resizable Windows Form for Data Entry](https://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6fd49-120">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6fd49-120">Compiling the Code</span></span>  
 <span data-ttu-id="6fd49-121">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6fd49-121">This example requires:</span></span>  
  
-   <span data-ttu-id="6fd49-122">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6fd49-122">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6fd49-123">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6fd49-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6fd49-124">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="6fd49-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="6fd49-125">Zobacz też [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6fd49-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd49-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fd49-126">See also</span></span>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="6fd49-127">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="6fd49-127">Localization</span></span>](../../../../docs/standard/globalization-localization/localization.md)
