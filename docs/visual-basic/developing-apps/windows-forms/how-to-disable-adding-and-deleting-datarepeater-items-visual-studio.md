---
title: 'Porady: wyłączanie dodawania i usuwania elementów DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
ms.openlocfilehash: e3d0d2a8d422054e269ee92df1fdfcb5acb96eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590812"
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a><span data-ttu-id="abc82-102">Porady: wyłączanie dodawania i usuwania elementów DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="abc82-102">How to: Disable Adding and Deleting DataRepeater Items (Visual Studio)</span></span>
<span data-ttu-id="abc82-103">Domyślnie użytkownicy mogą dodawać i usuwać elementy w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="abc82-103">By default, users can add and delete items in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="abc82-104">Użytkownicy mogą dodać nowy element przez naciśnięcie klawiszy CTRL + N podczas <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> ma fokus lub przez kliknięcie przycisku **AddNewItem** znajdującego się na <xref:System.Windows.Forms.BindingNavigator> formantu.</span><span class="sxs-lookup"><span data-stu-id="abc82-104">Users can add a new item by pressing CTRL+N when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **AddNewItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span> <span data-ttu-id="abc82-105">Użytkownicy mogą usuwać elementu przez naciśnięcie przycisku usuwania, kiedy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> ma fokus lub przez kliknięcie przycisku **DeleteItem** znajdującego się na <xref:System.Windows.Forms.BindingNavigator> formantu.</span><span class="sxs-lookup"><span data-stu-id="abc82-105">Users can delete an item by pressing DELETE when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **DeleteItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
 <span data-ttu-id="abc82-106">Można wyłączyć, dodawanie lub usuwanie w czasie projektowania lub w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="abc82-106">You can disable adding and/or deleting at design time or at run time.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a><span data-ttu-id="abc82-107">Aby wyłączyć dodawania i usuwania w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="abc82-107">To disable adding and deleting at design time</span></span>  
  
1.  <span data-ttu-id="abc82-108">W narzędziu Projektant dla formularzy systemu Windows wybierz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="abc82-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="abc82-109">Musisz wybrać dolnej części kontrolki.</span><span class="sxs-lookup"><span data-stu-id="abc82-109">You must select the lower section of the control.</span></span> <span data-ttu-id="abc82-110">W przypadku wybrania sekcji szablonu elementu pojawi się zestaw właściwości.</span><span class="sxs-lookup"><span data-stu-id="abc82-110">If you select the item template section, a different set of properties will be displayed.</span></span>  
  
2.  <span data-ttu-id="abc82-111">W oknie właściwości ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="abc82-111">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> property to **False**.</span></span>  
  
3.  <span data-ttu-id="abc82-112">Ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="abc82-112">Set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> property to **False**.</span></span>  
  
4.  <span data-ttu-id="abc82-113">W narzędziu Projektant dla formularzy systemu Windows wybierz <xref:System.Windows.Forms.BindingNavigator> kontroli, a następnie kliknij przycisk **AddNewItem** (przycisk ze znakiem plus na nim).</span><span class="sxs-lookup"><span data-stu-id="abc82-113">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **AddNewItem** button (the button with a plus sign on it).</span></span>  
  
5.  <span data-ttu-id="abc82-114">W oknie właściwości ustaw <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="abc82-114">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
6.  <span data-ttu-id="abc82-115">W narzędziu Projektant dla formularzy systemu Windows wybierz <xref:System.Windows.Forms.BindingNavigator> kontroli, a następnie kliknij przycisk **DeleteItem** (przycisk z czerwonym symbolem X w niej).</span><span class="sxs-lookup"><span data-stu-id="abc82-115">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **DeleteItem** button (the button with a red X on it).</span></span>  
  
7.  <span data-ttu-id="abc82-116">W oknie właściwości ustaw <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="abc82-116">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
8.  <span data-ttu-id="abc82-117">Na pasku składnika wybierz <xref:System.Windows.Forms.BindingSource> do którego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> jest powiązany.</span><span class="sxs-lookup"><span data-stu-id="abc82-117">In the Component Tray, select the <xref:System.Windows.Forms.BindingSource> to which the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is bound.</span></span>  
  
9. <span data-ttu-id="abc82-118">W oknie właściwości ustaw <xref:System.Windows.Forms.BindingSource.AllowNew%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="abc82-118">In the Properties window, set the <xref:System.Windows.Forms.BindingSource.AllowNew%2A> property to **False**.</span></span>  
  
10. <span data-ttu-id="abc82-119">W narzędziu Projektant dla formularzy systemu Windows, kliknij dwukrotnie **DeleteItem** przycisk, aby otworzyć edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="abc82-119">In the Windows Forms Designer, double-click the **DeleteItem** button to open the Code Editor.</span></span>  
  
11. <span data-ttu-id="abc82-120">Na liście rozwijanej zdarzenia wybierz `BindingNavigatorDeleteItem_EnabledChanged` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="abc82-120">In the Events drop-down list, select the `BindingNavigatorDeleteItem_EnabledChanged` event.</span></span>  
  
12. <span data-ttu-id="abc82-121">Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="abc82-121">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="abc82-122">Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> spowoduje włączenie **DeleteItem** przycisk zawsze zmiany bieżącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="abc82-122">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a><span data-ttu-id="abc82-123">Aby wyłączyć dodawania i usuwania w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="abc82-123">To disable adding and deleting at run time</span></span>  
  
1.  <span data-ttu-id="abc82-124">W narzędziu Projektant dla formularzy systemu Windows kliknij dwukrotnie formularza, aby otworzyć edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="abc82-124">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="abc82-125">Dodaj następujący kod do `Form_Load` zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="abc82-125">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  <span data-ttu-id="abc82-126">Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="abc82-126">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="abc82-127">Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> spowoduje włączenie **DeleteItem** przycisk zawsze zmiany bieżącego rekordu.</span><span class="sxs-lookup"><span data-stu-id="abc82-127">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc82-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abc82-128">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="abc82-129">Wprowadzenie do kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="abc82-129">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="abc82-130">Rozwiązywanie problemów z kontrolką DataRepeater</span><span class="sxs-lookup"><span data-stu-id="abc82-130">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
