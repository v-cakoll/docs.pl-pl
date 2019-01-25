---
title: 'Instrukcje: Zmienianie układu formantu DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
ms.openlocfilehash: 3389daa6383444b48faab4c5383b281e44349bce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625604"
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="b6aaa-102">Instrukcje: Zmienianie układu formantu DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="b6aaa-102">How to: Change the Layout of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="b6aaa-103"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Kontrolki mogą być wyświetlane w pionie (elementy przewijania w pionie) lub w poziomie (elementy przewijania w poziomie) orientacji.</span><span class="sxs-lookup"><span data-stu-id="b6aaa-103">The <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control can be displayed in either a vertical (items scroll vertically) or horizontal (items scroll horizontally) orientation.</span></span> <span data-ttu-id="b6aaa-104">Można zmienić orientację w czasie projektowania lub w czasie wykonywania, zmieniając <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b6aaa-104">You can change the orientation at design time or at run time by changing the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property.</span></span> <span data-ttu-id="b6aaa-105">Jeśli zmienisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwość w czasie wykonywania, możesz zmienić rozmiar <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> i zmienić położenie formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b6aaa-105">If you change the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property at run time, you may also want to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and reposition the child controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6aaa-106">Jeśli zmiana położenia kontrolki na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> w czasie wykonywania, musisz wywołać <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> i <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> metody na początku i końca bloku kodu, który zmienia położenie kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b6aaa-106">If you reposition controls on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> at run time, you will need to call the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> and <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> methods at the beginning and end of the code block that repositions the controls.</span></span>  
  
### <a name="to-change-the-layout-at-design-time"></a><span data-ttu-id="b6aaa-107">Aby zmienić układ w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="b6aaa-107">To change the layout at design time</span></span>  
  
1.  <span data-ttu-id="b6aaa-108">W programie Windows Forms Designer wybierz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="b6aaa-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b6aaa-109">Musisz wybrać zewnętrznymi krawędziami <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania, klikając w dolnego regionu formantu nie znajduje się w prawym górnym <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> regionu.</span><span class="sxs-lookup"><span data-stu-id="b6aaa-109">You must select the outer border of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control by clicking in the lower region of the control, not in the upper <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> region.</span></span>  
  
2.  <span data-ttu-id="b6aaa-110">W oknie właściwości ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwości albo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> lub <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span><span class="sxs-lookup"><span data-stu-id="b6aaa-110">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property to either <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span></span>  
  
### <a name="to-change-the-layout-at-run-time"></a><span data-ttu-id="b6aaa-111">Aby zmienić układ w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="b6aaa-111">To change the layout at run time</span></span>  
  
1.  <span data-ttu-id="b6aaa-112">Dodaj następujący kod do przycisku lub menu `Click` program obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="b6aaa-112">Add the following code to a button or menu `Click` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  <span data-ttu-id="b6aaa-113">W większości przypadków należy dodać kod, podobnie jak pokazano w sekcji z przykładowym, aby zmienić rozmiar <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> i rozmieszczanie formantów w celu dopasowania nowej orientacji.</span><span class="sxs-lookup"><span data-stu-id="b6aaa-113">In most cases, you will want to add code similar to that shown in the Example section to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and rearrange controls to fit the new orientation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6aaa-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6aaa-114">Example</span></span>  
 <span data-ttu-id="b6aaa-115">Poniższy przykład pokazuje, jak reagować na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> zdarzeń w obsłudze zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b6aaa-115">The following example shows how to respond to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> event in an event handler.</span></span> <span data-ttu-id="b6aaa-116">W tym przykładzie wymaga, że masz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu o nazwie `DataRepeater1` na formularzu oraz że jego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> zawierać dwa <xref:System.Windows.Forms.TextBox> kontrolki o nazwie `TextBox1` i `TextBox2`.</span><span class="sxs-lookup"><span data-stu-id="b6aaa-116">This example requires that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control named `DataRepeater1` on a form and that its <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> contain two <xref:System.Windows.Forms.TextBox> controls named `TextBox1` and `TextBox2`.</span></span>  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b6aaa-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6aaa-117">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>
- [<span data-ttu-id="b6aaa-118">Wprowadzenie do kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="b6aaa-118">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="b6aaa-119">Rozwiązywanie problemów z kontrolką DataRepeater</span><span class="sxs-lookup"><span data-stu-id="b6aaa-119">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="b6aaa-120">Instrukcje: Zmienianie wyglądu formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="b6aaa-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
