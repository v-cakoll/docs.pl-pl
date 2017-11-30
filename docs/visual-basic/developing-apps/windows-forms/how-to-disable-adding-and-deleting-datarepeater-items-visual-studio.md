---
title: "Porady: wyłączanie dodawania i usuwania elementów DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b15fe6fb5190855126ffa60ac488aaa74ad9b5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a><span data-ttu-id="5e45f-102">Porady: wyłączanie dodawania i usuwania elementów DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="5e45f-102">How to: Disable Adding and Deleting DataRepeater Items (Visual Studio)</span></span>
<span data-ttu-id="5e45f-103">Domyślnie użytkownicy mogą dodawać i usuwać elementy w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="5e45f-103">By default, users can add and delete items in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="5e45f-104">Użytkownicy mogą dodać nowy element przez naciśnięcie klawiszy CTRL + N podczas <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> ma fokus lub przez kliknięcie przycisku **AddNewItem** znajdującego się na <xref:System.Windows.Forms.BindingNavigator> formantu.</span><span class="sxs-lookup"><span data-stu-id="5e45f-104">Users can add a new item by pressing CTRL+N when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **AddNewItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span> <span data-ttu-id="5e45f-105">Użytkownicy mogą usuwać elementu przez naciśnięcie przycisku usuwania, kiedy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> ma fokus lub przez kliknięcie przycisku **DeleteItem** znajdującego się na <xref:System.Windows.Forms.BindingNavigator> formantu.</span><span class="sxs-lookup"><span data-stu-id="5e45f-105">Users can delete an item by pressing DELETE when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **DeleteItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
 <span data-ttu-id="5e45f-106">Można wyłączyć, dodawanie lub usuwanie w czasie projektowania lub w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5e45f-106">You can disable adding and/or deleting at design time or at run time.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a><span data-ttu-id="5e45f-107">Aby wyłączyć dodawania i usuwania w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="5e45f-107">To disable adding and deleting at design time</span></span>  
  
1.  <span data-ttu-id="5e45f-108">W narzędziu Projektant dla formularzy systemu Windows wybierz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="5e45f-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5e45f-109">Musisz wybrać dolnej części kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5e45f-109">You must select the lower section of the control.</span></span> <span data-ttu-id="5e45f-110">W przypadku wybrania sekcji szablonu elementu pojawi się zestaw właściwości.</span><span class="sxs-lookup"><span data-stu-id="5e45f-110">If you select the item template section, a different set of properties will be displayed.</span></span>  
  
2.  <span data-ttu-id="5e45f-111">W oknie właściwości ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="5e45f-111">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> property to **False**.</span></span>  
  
3.  <span data-ttu-id="5e45f-112">Ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="5e45f-112">Set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> property to **False**.</span></span>  
  
4.  <span data-ttu-id="5e45f-113">W narzędziu Projektant dla formularzy systemu Windows wybierz <xref:System.Windows.Forms.BindingNavigator> kontroli, a następnie kliknij przycisk **AddNewItem** (przycisk ze znakiem plus na nim).</span><span class="sxs-lookup"><span data-stu-id="5e45f-113">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **AddNewItem** button (the button with a plus sign on it).</span></span>  
  
5.  <span data-ttu-id="5e45f-114">W oknie właściwości ustaw <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="5e45f-114">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
6.  <span data-ttu-id="5e45f-115">W narzędziu Projektant dla formularzy systemu Windows wybierz <xref:System.Windows.Forms.BindingNavigator> kontroli, a następnie kliknij przycisk **DeleteItem** (przycisk z czerwonym symbolem X w niej).</span><span class="sxs-lookup"><span data-stu-id="5e45f-115">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **DeleteItem** button (the button with a red X on it).</span></span>  
  
7.  <span data-ttu-id="5e45f-116">W oknie właściwości ustaw <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="5e45f-116">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
8.  <span data-ttu-id="5e45f-117">Na pasku składnika wybierz <xref:System.Windows.Forms.BindingSource> do którego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> jest powiązany.</span><span class="sxs-lookup"><span data-stu-id="5e45f-117">In the Component Tray, select the <xref:System.Windows.Forms.BindingSource> to which the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is bound.</span></span>  
  
9. <span data-ttu-id="5e45f-118">W oknie właściwości ustaw <xref:System.Windows.Forms.BindingSource.AllowNew%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="5e45f-118">In the Properties window, set the <xref:System.Windows.Forms.BindingSource.AllowNew%2A> property to **False**.</span></span>  
  
10. <span data-ttu-id="5e45f-119">W narzędziu Projektant dla formularzy systemu Windows, kliknij dwukrotnie **DeleteItem** przycisk, aby otworzyć edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="5e45f-119">In the Windows Forms Designer, double-click the **DeleteItem** button to open the Code Editor.</span></span>  
  
11. <span data-ttu-id="5e45f-120">Na liście rozwijanej zdarzenia wybierz `BindingNavigatorDeleteItem_EnabledChanged` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5e45f-120">In the Events drop-down list, select the `BindingNavigatorDeleteItem_EnabledChanged` event.</span></span>  
  
12. <span data-ttu-id="5e45f-121">Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="5e45f-121">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="5e45f-122">Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> spowoduje włączenie **DeleteItem** przycisk zawsze zmiany bieżącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="5e45f-122">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a><span data-ttu-id="5e45f-123">Aby wyłączyć dodawania i usuwania w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="5e45f-123">To disable adding and deleting at run time</span></span>  
  
1.  <span data-ttu-id="5e45f-124">W narzędziu Projektant dla formularzy systemu Windows kliknij dwukrotnie formularza, aby otworzyć edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="5e45f-124">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="5e45f-125">Dodaj następujący kod do `Form_Load` zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="5e45f-125">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  <span data-ttu-id="5e45f-126">Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="5e45f-126">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="5e45f-127">Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> spowoduje włączenie **DeleteItem** przycisk zawsze zmiany bieżącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="5e45f-127">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e45f-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e45f-128">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="5e45f-129">Wprowadzenie do formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5e45f-129">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5e45f-130">Rozwiązywanie problemów z formantem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5e45f-130">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
