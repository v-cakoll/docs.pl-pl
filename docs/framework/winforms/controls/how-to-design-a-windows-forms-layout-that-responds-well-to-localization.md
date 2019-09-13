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
ms.openlocfilehash: c1aa62413e1c9cc29507b7b0ed5cbf1c5fcea26a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928568"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="38716-102">Instrukcje: projektowanie układu formularzy systemu Windows dobrze reagującego na lokalizację</span><span class="sxs-lookup"><span data-stu-id="38716-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="38716-103">Tworzenie formularzy, które są gotowe do zlokalizowania znacznie przyspiesza rozwój dla rynków międzynarodowych.</span><span class="sxs-lookup"><span data-stu-id="38716-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="38716-104">Można użyć <xref:System.Windows.Forms.TableLayoutPanel> kontrolki do implementacji układów, które reagują bezproblemowo w miarę zmieniania rozmiaru, <xref:System.Windows.Forms.Control.Text%2A> ze względu na zmiany wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="38716-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38716-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="38716-105">Example</span></span>  
 <span data-ttu-id="38716-106">Ten formularz pokazuje, jak utworzyć układ, który zmienia się proporcjonalnie w przypadku tłumaczenia wyświetlanych wartości ciągu na inne języki.</span><span class="sxs-lookup"><span data-stu-id="38716-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="38716-107">Ten proces tłumaczenia nazywa się *lokalizacją*.</span><span class="sxs-lookup"><span data-stu-id="38716-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="38716-108">Aby uzyskać więcej informacji, zobacz [Lokalizacja](../../../standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="38716-108">For more information, see [Localization](../../../standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="38716-109">W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.</span><span class="sxs-lookup"><span data-stu-id="38716-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="38716-110">Zobacz również [Przewodnik: Tworzenie układu dostosowującego proporcję lokalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="38716-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a><span data-ttu-id="38716-111">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="38716-111">Additional resources</span></span>

1. [<span data-ttu-id="38716-112">Instrukcje: Wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="38716-112">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="38716-113">Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="38716-113">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [<span data-ttu-id="38716-114">Instrukcje: Rozciągaj wiersze i kolumny w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="38716-114">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="38716-115">Instrukcje: Edytowanie kolumn i wierszy w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="38716-115">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [<span data-ttu-id="38716-116">Przewodnik: Wykonywanie typowych zadań przy użyciu tagów inteligentnych w kontrolkach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="38716-116">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [<span data-ttu-id="38716-117">Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="38716-117">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [<span data-ttu-id="38716-118">Przewodnik: Określanie układu formantów Windows Forms z dopełnieniem, marginesami i właściwością AutoSize</span><span class="sxs-lookup"><span data-stu-id="38716-118">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)  
  
8. <span data-ttu-id="38716-119">[Instrukcje: Obsługa lokalizacji na Windows Forms przy użyciu funkcji AutoSize i kontrolki TableLayoutPanel](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="38716-119">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span></span>  
  
9. <span data-ttu-id="38716-120">[Przewodnik: Tworzenie formularza systemu Windows o zmiennym rozmiarze na potrzeby wprowadzania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="38716-120">[Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="38716-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="38716-121">Compiling the Code</span></span>  
 <span data-ttu-id="38716-122">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="38716-122">This example requires:</span></span>  
  
- <span data-ttu-id="38716-123">Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="38716-123">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38716-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38716-124">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="38716-125">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="38716-125">Localization</span></span>](../../../standard/globalization-localization/localization.md)
