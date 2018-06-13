---
title: 'Porady: zmienianie układu formantu DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
ms.openlocfilehash: fa780ee40171143c17b5bdbda4a97179ed5f2151
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590845"
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="239f2-102">Porady: zmienianie układu formantu DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="239f2-102">How to: Change the Layout of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="239f2-103"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Kontroli mogą być wyświetlane w pionie (przewijania elementów w pionie) lub pozioma (elementy przewijania w poziomie) orientacji.</span><span class="sxs-lookup"><span data-stu-id="239f2-103">The <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control can be displayed in either a vertical (items scroll vertically) or horizontal (items scroll horizontally) orientation.</span></span> <span data-ttu-id="239f2-104">Orientacja w czasie projektowania lub w czasie wykonywania można zmienić, zmieniając <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="239f2-104">You can change the orientation at design time or at run time by changing the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property.</span></span> <span data-ttu-id="239f2-105">Jeśli zmienisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwości w czasie wykonywania, może również chcesz zmienić <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> i położenia formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="239f2-105">If you change the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property at run time, you may also want to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and reposition the child controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="239f2-106">Jeśli zmiana położenia kontrolki na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> w czasie wykonywania, należy wywołać <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> i <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> metody na początku i na końcu bloku kodu, który zmienia położenie kontrolki.</span><span class="sxs-lookup"><span data-stu-id="239f2-106">If you reposition controls on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> at run time, you will need to call the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> and <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> methods at the beginning and end of the code block that repositions the controls.</span></span>  
  
### <a name="to-change-the-layout-at-design-time"></a><span data-ttu-id="239f2-107">Aby zmienić układ w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="239f2-107">To change the layout at design time</span></span>  
  
1.  <span data-ttu-id="239f2-108">W narzędziu Projektant dla formularzy systemu Windows wybierz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="239f2-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="239f2-109">Musisz wybrać zewnętrzną krawędzią <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania, klikając w region na dole formantu, nie znajduje się w prawym górnym <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> regionu.</span><span class="sxs-lookup"><span data-stu-id="239f2-109">You must select the outer border of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control by clicking in the lower region of the control, not in the upper <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> region.</span></span>  
  
2.  <span data-ttu-id="239f2-110">W oknie właściwości ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwości albo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> lub <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span><span class="sxs-lookup"><span data-stu-id="239f2-110">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property to either <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span></span>  
  
### <a name="to-change-the-layout-at-run-time"></a><span data-ttu-id="239f2-111">Aby zmienić układ w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="239f2-111">To change the layout at run time</span></span>  
  
1.  <span data-ttu-id="239f2-112">Dodaj następujący kod do menu lub przycisku `Click` obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="239f2-112">Add the following code to a button or menu `Click` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  <span data-ttu-id="239f2-113">W większości przypadków należy dodać kod, podobnie jak pokazano w sekcji przykład, aby zmienić rozmiar <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> i rozmieszczanie formantów w celu dopasowania nowej orientacji.</span><span class="sxs-lookup"><span data-stu-id="239f2-113">In most cases, you will want to add code similar to that shown in the Example section to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and rearrange controls to fit the new orientation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="239f2-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="239f2-114">Example</span></span>  
 <span data-ttu-id="239f2-115">Poniższy przykład pokazuje, jak odpowiedzieć na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> zdarzeń w obsłudze zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="239f2-115">The following example shows how to respond to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> event in an event handler.</span></span> <span data-ttu-id="239f2-116">W tym przykładzie wymaga <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu o nazwie `DataRepeater1` na formularzu oraz że jego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> zawierać dwa <xref:System.Windows.Forms.TextBox> formantów `TextBox1` i `TextBox2`.</span><span class="sxs-lookup"><span data-stu-id="239f2-116">This example requires that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control named `DataRepeater1` on a form and that its <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> contain two <xref:System.Windows.Forms.TextBox> controls named `TextBox1` and `TextBox2`.</span></span>  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="239f2-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="239f2-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>  
 [<span data-ttu-id="239f2-118">Wprowadzenie do kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="239f2-118">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="239f2-119">Rozwiązywanie problemów z kontrolką DataRepeater</span><span class="sxs-lookup"><span data-stu-id="239f2-119">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="239f2-120">Instrukcje: zmienianie wyglądu kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="239f2-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
