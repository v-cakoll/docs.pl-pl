---
title: Projektowanie układu przyjazny dla lokalizacji
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
ms.openlocfilehash: 36ffd532b9f539107307144d25c8d9d5f8ba634a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743284"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="ddcab-102">Porady: projektowanie układu formularzy systemu Windows dobrze reagującego na lokalizację</span><span class="sxs-lookup"><span data-stu-id="ddcab-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="ddcab-103">Tworzenie formularzy, które są gotowe do zlokalizowania znacznie przyspiesza rozwój dla rynków międzynarodowych.</span><span class="sxs-lookup"><span data-stu-id="ddcab-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="ddcab-104">Za pomocą kontrolki <xref:System.Windows.Forms.TableLayoutPanel> można zaimplementować układy, które reagują bezproblemowo w miarę zmieniania rozmiaru formantów ze względu na zmiany wartości właściwości <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="ddcab-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddcab-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ddcab-105">Example</span></span>  
 <span data-ttu-id="ddcab-106">Ten formularz pokazuje, jak utworzyć układ, który zmienia się proporcjonalnie w przypadku tłumaczenia wyświetlanych wartości ciągu na inne języki.</span><span class="sxs-lookup"><span data-stu-id="ddcab-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="ddcab-107">Ten proces tłumaczenia nazywa się *lokalizacją*.</span><span class="sxs-lookup"><span data-stu-id="ddcab-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="ddcab-108">Aby uzyskać więcej informacji, zobacz [Lokalizacja](../../../standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="ddcab-108">For more information, see [Localization](../../../standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="ddcab-109">W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.</span><span class="sxs-lookup"><span data-stu-id="ddcab-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="ddcab-110">Zobacz również [Przewodnik: tworzenie układu, który dostosowuje proporcje dla lokalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ddcab-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a><span data-ttu-id="ddcab-111">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="ddcab-111">Additional resources</span></span>

1. [<span data-ttu-id="ddcab-112">Instrukcje: wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ddcab-112">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="ddcab-113">Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ddcab-113">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [<span data-ttu-id="ddcab-114">Instrukcje: obejmowanie rzędów i kolumn w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ddcab-114">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="ddcab-115">Instrukcje: edytowanie rzędów i kolumn w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ddcab-115">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [<span data-ttu-id="ddcab-116">Przewodnik: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ddcab-116">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [<span data-ttu-id="ddcab-117">Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ddcab-117">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [<span data-ttu-id="ddcab-118">Przewodnik: tworzenie kontrolek formularzy Windows Forms z uzupełnieniem, marginesami oraz właściwościami AutoSize</span><span class="sxs-lookup"><span data-stu-id="ddcab-118">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)  
  
8. <span data-ttu-id="ddcab-119">[Instrukcje: obsługa lokalizacji na Windows Forms przy użyciu funkcji Autodopasowanie rozmiaru i formantu TableLayoutPanel](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ddcab-119">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span></span>  
  
9. <span data-ttu-id="ddcab-120">[Przewodnik: Tworzenie formularza systemu Windows o zmiennym rozmiarze na potrzeby wprowadzania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ddcab-120">[Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ddcab-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ddcab-121">Compiling the Code</span></span>  
 <span data-ttu-id="ddcab-122">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ddcab-122">This example requires:</span></span>  
  
- <span data-ttu-id="ddcab-123">Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="ddcab-123">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcab-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddcab-124">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="ddcab-125">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="ddcab-125">Localization</span></span>](../../../standard/globalization-localization/localization.md)
