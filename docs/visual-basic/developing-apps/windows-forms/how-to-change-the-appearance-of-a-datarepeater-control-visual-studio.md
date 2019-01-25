---
title: 'Instrukcje: Zmienianie wyglądu formantu DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
ms.openlocfilehash: e5508329ba716b53eff0c9e1bfe13e190fa1fd85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716638"
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="ab4b2-102">Instrukcje: Zmienianie wyglądu formantu DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="ab4b2-102">How to: Change the Appearance of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="ab4b2-103">Możesz zmienić wygląd <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie projektowania, ustawiając właściwości lub w czasie wykonywania, obsługując <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-103">You can change the appearance of a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time by setting properties or at run time by handling the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event.</span></span>  
  
 <span data-ttu-id="ab4b2-104">Właściwości ustawione w czasie projektowania, po wybraniu sekcji szablon elementu kontrolka będzie należy powtórzyć dla każdego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-104">Properties that you set at design time when the item template section of the control is selected will be repeated for each <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> at run time.</span></span> <span data-ttu-id="ab4b2-105">Właściwości powiązane z wyglądem <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolkę będą widoczne w czasie wykonywania, pozostało tylko wtedy, gdy części kontenera odkryte (na przykład, jeśli <xref:System.Windows.Forms.Control.Padding%2A> ustawioną na wartość duże).</span><span class="sxs-lookup"><span data-stu-id="ab4b2-105">Appearance-related properties of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control itself will be visible at run time only if a part of the container is left uncovered (for example, if the <xref:System.Windows.Forms.Control.Padding%2A> property is set to a large value).</span></span>  
  
 <span data-ttu-id="ab4b2-106">W czasie wykonywania właściwości dotyczące wygląd można ustawiona na podstawie warunków.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-106">At run time, appearance-related properties can be set based on conditions.</span></span> <span data-ttu-id="ab4b2-107">Na przykład w przypadku planowania aplikacji możesz zmienić kolor tła elementu, aby ostrzec użytkowników, gdy element jest zaległa.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-107">For example, in a scheduling application, you might change the background color of an item to warn users when an item is past due.</span></span> <span data-ttu-id="ab4b2-108">W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> programu obsługi zdarzeń, jeśli zostanie ustawiona właściwość w instrukcji warunkowej takie jak `If…Then`, musisz również użyć `Else` klauzulę, aby określić wygląd, gdy warunek nie jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-108">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, if you set a property in a conditional statement such as `If…Then`, you must also use an `Else` clause to specify the appearance when the condition is not met.</span></span>  
  
### <a name="to-change-the-appearance-at-design-time"></a><span data-ttu-id="ab4b2-109">Aby zmienić wygląd w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="ab4b2-109">To change the appearance at design time</span></span>  
  
1.  <span data-ttu-id="ab4b2-110">W programie Windows Forms Designer wybierz region szablonu (w prawym górnym) elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-110">In the Windows Forms Designer, select the item template (upper) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="ab4b2-111">W oknie dialogowym właściwości wybierz właściwość, a następnie zmień wartość.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-111">In the Properties window, select a property and change the value.</span></span> <span data-ttu-id="ab4b2-112">Obejmują typowe właściwości, które wpływają na wygląd <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, i <xref:System.Windows.Forms.Control.ForeColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-112">Common properties that affect appearance include <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, and <xref:System.Windows.Forms.Control.ForeColor%2A>.</span></span>  
  
### <a name="to-change-the-appearance-at-run-time"></a><span data-ttu-id="ab4b2-113">Aby zmienić wygląd w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="ab4b2-113">To change the appearance at run time</span></span>  
  
1.  <span data-ttu-id="ab4b2-114">W edytorze kodu, w przypadku menu rozwijanego, kliknij przycisk **drawitem —**.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-114">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
2.  <span data-ttu-id="ab4b2-115">W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> procedura obsługi zdarzeń, Dodaj kod, aby ustawić właściwości:</span><span class="sxs-lookup"><span data-stu-id="ab4b2-115">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add code to set the properties:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="ab4b2-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab4b2-116">Example</span></span>  
 <span data-ttu-id="ab4b2-117">Niektóre typowe dostosowania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli obejmują wyświetlanie wierszy w naprzemiennych kolorów i zmieniając kolor pola na podstawie warunku.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-117">Some common customizations for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control include displaying the rows in alternating colors and changing the color of a field based on a condition.</span></span> <span data-ttu-id="ab4b2-118">Poniższy przykład pokazuje, jak wykonywać te dostosowania.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-118">The following example shows how to perform these customizations.</span></span> <span data-ttu-id="ab4b2-119">W tym przykładzie przyjęto założenie, iż <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formant, który jest powiązany z tabeli Produkty w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-119">This example assumes that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that is bound to the Products table in the Northwind database.</span></span>  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 <span data-ttu-id="ab4b2-120">Należy pamiętać, że oba te dostosowania należy podać kod, aby ustawić właściwości dla obu stron warunku.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-120">Note that for both of these customizations, you must provide code to set the properties for both sides of the condition.</span></span> <span data-ttu-id="ab4b2-121">Jeśli nie określisz `Else` warunek, zostanie wyświetlony nieoczekiwane wyniki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ab4b2-121">If you do not specify the `Else` condition, you will see unexpected results at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab4b2-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab4b2-122">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>
- [<span data-ttu-id="ab4b2-123">Wprowadzenie do kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ab4b2-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="ab4b2-124">Rozwiązywanie problemów z kontrolką DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ab4b2-124">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="ab4b2-125">Instrukcje: Wyświetlanie powiązanych danych w formancie DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ab4b2-125">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="ab4b2-126">Instrukcje: Wyświetlanie formantów niepowiązanych w formancie DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ab4b2-126">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="ab4b2-127">Instrukcje: Wyświetlanie nagłówków elementów w formancie DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ab4b2-127">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
