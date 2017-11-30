---
title: "Porady: zmienianie wyglądu formantu DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 585ff4c942185f3199fe6e9e47a4ebd9f1f0a478
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="b53ca-102">Porady: zmienianie wyglądu formantu DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="b53ca-102">How to: Change the Appearance of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="b53ca-103">Można zmienić wygląd <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie projektowania, ustawiając właściwości lub w czasie wykonywania Obsługa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b53ca-103">You can change the appearance of a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time by setting properties or at run time by handling the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event.</span></span>  
  
 <span data-ttu-id="b53ca-104">Właściwości, które można ustawić w czasie projektowania, po wybraniu elementu sekcji szablonu formantu zostanie należy powtórzyć dla każdego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b53ca-104">Properties that you set at design time when the item template section of the control is selected will be repeated for each <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> at run time.</span></span> <span data-ttu-id="b53ca-105">Właściwości związane z wygląd <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolki będą widoczne w czasie wykonywania, pozostało tylko wtedy, gdy w ramach kontenera niewykrytych (na przykład, jeśli <xref:System.Windows.Forms.Control.Padding%2A> właściwości jest ustawiona na wartość duże).</span><span class="sxs-lookup"><span data-stu-id="b53ca-105">Appearance-related properties of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control itself will be visible at run time only if a part of the container is left uncovered (for example, if the <xref:System.Windows.Forms.Control.Padding%2A> property is set to a large value).</span></span>  
  
 <span data-ttu-id="b53ca-106">W czasie wykonywania powiązane z wyglądem właściwości można ustawiona na podstawie warunków.</span><span class="sxs-lookup"><span data-stu-id="b53ca-106">At run time, appearance-related properties can be set based on conditions.</span></span> <span data-ttu-id="b53ca-107">Na przykład w harmonogramie aplikacji, można zmienić kolor tła elementu, aby ostrzec użytkowników, gdy element jest zaległa.</span><span class="sxs-lookup"><span data-stu-id="b53ca-107">For example, in a scheduling application, you might change the background color of an item to warn users when an item is past due.</span></span> <span data-ttu-id="b53ca-108">W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> program obsługi zdarzeń, jeśli zostanie ustawiona właściwość w instrukcji warunkowej takich jak `If…Then`, należy również użyć `Else` klauzuli, aby określić wygląd, jeśli nie jest spełniony warunek.</span><span class="sxs-lookup"><span data-stu-id="b53ca-108">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, if you set a property in a conditional statement such as `If…Then`, you must also use an `Else` clause to specify the appearance when the condition is not met.</span></span>  
  
### <a name="to-change-the-appearance-at-design-time"></a><span data-ttu-id="b53ca-109">Zmiana wyglądu w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="b53ca-109">To change the appearance at design time</span></span>  
  
1.  <span data-ttu-id="b53ca-110">W narzędziu Projektant dla formularzy systemu Windows wybierz region szablonu (wielkich) elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="b53ca-110">In the Windows Forms Designer, select the item template (upper) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="b53ca-111">W oknie właściwości wybierz właściwość, a następnie zmień wartość.</span><span class="sxs-lookup"><span data-stu-id="b53ca-111">In the Properties window, select a property and change the value.</span></span> <span data-ttu-id="b53ca-112">Wspólne właściwości, które mają wpływ na wygląd obejmują <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, i <xref:System.Windows.Forms.Control.ForeColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="b53ca-112">Common properties that affect appearance include <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, and <xref:System.Windows.Forms.Control.ForeColor%2A>.</span></span>  
  
### <a name="to-change-the-appearance-at-run-time"></a><span data-ttu-id="b53ca-113">Zmiana wyglądu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="b53ca-113">To change the appearance at run time</span></span>  
  
1.  <span data-ttu-id="b53ca-114">W edytorze kodu, w przypadku menu rozwijanego, kliknij przycisk **DrawItem**.</span><span class="sxs-lookup"><span data-stu-id="b53ca-114">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
2.  <span data-ttu-id="b53ca-115">W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> program obsługi zdarzeń, Dodaj kod, aby ustawić właściwości:</span><span class="sxs-lookup"><span data-stu-id="b53ca-115">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add code to set the properties:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="b53ca-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="b53ca-116">Example</span></span>  
 <span data-ttu-id="b53ca-117">Niektóre typowe dostosowania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli obejmują wyświetlanie wiersze w naprzemiennych kolorów i zmiana koloru pole na podstawie warunku.</span><span class="sxs-lookup"><span data-stu-id="b53ca-117">Some common customizations for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control include displaying the rows in alternating colors and changing the color of a field based on a condition.</span></span> <span data-ttu-id="b53ca-118">Poniższy przykład przedstawia sposób wykonywania tych dostosowań.</span><span class="sxs-lookup"><span data-stu-id="b53ca-118">The following example shows how to perform these customizations.</span></span> <span data-ttu-id="b53ca-119">W tym przykładzie przyjęto założenie, że masz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formant, który jest powiązany z tabeli Produkty bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="b53ca-119">This example assumes that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that is bound to the Products table in the Northwind database.</span></span>  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 <span data-ttu-id="b53ca-120">Należy pamiętać, że dla obu tych dostosowań, należy podać kod, aby ustawić właściwości po obu stronach warunku.</span><span class="sxs-lookup"><span data-stu-id="b53ca-120">Note that for both of these customizations, you must provide code to set the properties for both sides of the condition.</span></span> <span data-ttu-id="b53ca-121">Jeśli nie określisz `Else` warunku, zobaczysz nieoczekiwane wyniki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b53ca-121">If you do not specify the `Else` condition, you will see unexpected results at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b53ca-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b53ca-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
 [<span data-ttu-id="b53ca-123">Wprowadzenie do formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="b53ca-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="b53ca-124">Rozwiązywanie problemów z formantem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="b53ca-124">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="b53ca-125">Porady: wyświetlanie powiązanych danych w formancie Datarepeater</span><span class="sxs-lookup"><span data-stu-id="b53ca-125">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="b53ca-126">Porady: wyświetlanie formantów niepowiązanych w formancie DataRepeater</span><span class="sxs-lookup"><span data-stu-id="b53ca-126">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="b53ca-127">Porady: wyświetlanie nagłówków elementów w formancie Datarepeater</span><span class="sxs-lookup"><span data-stu-id="b53ca-127">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
