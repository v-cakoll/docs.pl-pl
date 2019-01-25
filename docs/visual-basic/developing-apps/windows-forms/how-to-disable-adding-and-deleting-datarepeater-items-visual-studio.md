---
title: 'Instrukcje: Wyłączanie dodawania i usuwania elementów DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
ms.openlocfilehash: 3a304132d0514da4c19811be2536c9516e2838f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618545"
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a><span data-ttu-id="6c1f5-102">Instrukcje: Wyłączanie dodawania i usuwania elementów DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="6c1f5-102">How to: Disable Adding and Deleting DataRepeater Items (Visual Studio)</span></span>
<span data-ttu-id="6c1f5-103">Domyślnie użytkownicy mogą dodawać i usuwać elementy w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-103">By default, users can add and delete items in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="6c1f5-104">Użytkownicy mogą dodawać nowych elementów, naciskając klawisze CTRL + N przy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> fokusie lub klikając **AddNewItem** znajdujący się na <xref:System.Windows.Forms.BindingNavigator> kontroli.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-104">Users can add a new item by pressing CTRL+N when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **AddNewItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span> <span data-ttu-id="6c1f5-105">Użytkownicy mogą usunąć element, naciskając klawisz usunięcia, kiedy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> fokusie lub klikając **DeleteItem** znajdujący się na <xref:System.Windows.Forms.BindingNavigator> kontroli.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-105">Users can delete an item by pressing DELETE when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **DeleteItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
 <span data-ttu-id="6c1f5-106">Można wyłączyć, dodawania i/lub usuwania w czasie projektowania lub w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-106">You can disable adding and/or deleting at design time or at run time.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a><span data-ttu-id="6c1f5-107">Aby wyłączyć, dodawania i usuwania w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="6c1f5-107">To disable adding and deleting at design time</span></span>  
  
1.  <span data-ttu-id="6c1f5-108">W programie Windows Forms Designer wybierz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c1f5-109">Musisz wybrać dolnej części kontrolki.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-109">You must select the lower section of the control.</span></span> <span data-ttu-id="6c1f5-110">Jeśli wybierzesz element sekcji szablonu, pojawi się inny zbiór właściwości.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-110">If you select the item template section, a different set of properties will be displayed.</span></span>  
  
2.  <span data-ttu-id="6c1f5-111">W oknie właściwości ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-111">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> property to **False**.</span></span>  
  
3.  <span data-ttu-id="6c1f5-112">Ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-112">Set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> property to **False**.</span></span>  
  
4.  <span data-ttu-id="6c1f5-113">W programie Windows Forms Designer wybierz <xref:System.Windows.Forms.BindingNavigator> sterowania, a następnie kliknij przycisk **AddNewItem** (przycisk ze znakiem plus na nim).</span><span class="sxs-lookup"><span data-stu-id="6c1f5-113">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **AddNewItem** button (the button with a plus sign on it).</span></span>  
  
5.  <span data-ttu-id="6c1f5-114">W oknie właściwości ustaw <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-114">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
6.  <span data-ttu-id="6c1f5-115">W programie Windows Forms Designer wybierz <xref:System.Windows.Forms.BindingNavigator> sterowania, a następnie kliknij przycisk **DeleteItem** (przycisk z czerwonym symbolem X na nim).</span><span class="sxs-lookup"><span data-stu-id="6c1f5-115">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **DeleteItem** button (the button with a red X on it).</span></span>  
  
7.  <span data-ttu-id="6c1f5-116">W oknie właściwości ustaw <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-116">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
8.  <span data-ttu-id="6c1f5-117">W zasobniku składnika wybierz <xref:System.Windows.Forms.BindingSource> do której <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> jest powiązany.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-117">In the Component Tray, select the <xref:System.Windows.Forms.BindingSource> to which the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is bound.</span></span>  
  
9. <span data-ttu-id="6c1f5-118">W oknie właściwości ustaw <xref:System.Windows.Forms.BindingSource.AllowNew%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-118">In the Properties window, set the <xref:System.Windows.Forms.BindingSource.AllowNew%2A> property to **False**.</span></span>  
  
10. <span data-ttu-id="6c1f5-119">W Windows Forms Designer, kliknij dwukrotnie **DeleteItem** przycisk, aby otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-119">In the Windows Forms Designer, double-click the **DeleteItem** button to open the Code Editor.</span></span>  
  
11. <span data-ttu-id="6c1f5-120">Na liście rozwijanej zdarzenia wybierz `BindingNavigatorDeleteItem_EnabledChanged` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-120">In the Events drop-down list, select the `BindingNavigatorDeleteItem_EnabledChanged` event.</span></span>  
  
12. <span data-ttu-id="6c1f5-121">Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` program obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="6c1f5-121">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="6c1f5-122">Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> umożliwi **DeleteItem** przycisk ilekroć dany zmiany bieżącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-122">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a><span data-ttu-id="6c1f5-123">Aby wyłączyć, dodawania i usuwania w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="6c1f5-123">To disable adding and deleting at run time</span></span>  
  
1.  <span data-ttu-id="6c1f5-124">W Windows Forms Designer kliknij dwukrotnie formularza, aby otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-124">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="6c1f5-125">Dodaj następujący kod do `Form_Load` zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="6c1f5-125">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  <span data-ttu-id="6c1f5-126">Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` program obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="6c1f5-126">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="6c1f5-127">Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> umożliwi **DeleteItem** przycisk ilekroć dany zmiany bieżącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-127">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c1f5-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c1f5-128">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [<span data-ttu-id="6c1f5-129">Wprowadzenie do kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="6c1f5-129">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="6c1f5-130">Rozwiązywanie problemów z kontrolką DataRepeater</span><span class="sxs-lookup"><span data-stu-id="6c1f5-130">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
