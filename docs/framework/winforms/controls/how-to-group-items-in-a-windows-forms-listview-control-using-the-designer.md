---
title: 'Instrukcje: grupowanie elementów w kontrolce ListView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: b63bcd9e5e357db350cc2987e09af84eb58bdcff
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039398"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="0d4f1-102">Instrukcje: grupowanie elementów w kontrolce ListView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="0d4f1-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="0d4f1-103">Funkcja <xref:System.Windows.Forms.ListView> grupowania kontrolki umożliwia wyświetlanie powiązanych zestawów elementów w grupach.</span><span class="sxs-lookup"><span data-stu-id="0d4f1-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="0d4f1-104">Te grupy są rozdzielane na ekranie przez nagłówki grup poziomych, które zawierają tytuły grup.</span><span class="sxs-lookup"><span data-stu-id="0d4f1-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="0d4f1-105"><xref:System.Windows.Forms.ListView> Grupy umożliwiają łatwiejsze nawigowanie po dużych listach, grupując elementy alfabetycznie według daty lub przez inne grupowanie logiczne.</span><span class="sxs-lookup"><span data-stu-id="0d4f1-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="0d4f1-106">Na poniższej ilustracji przedstawiono niektóre zgrupowane elementy:</span><span class="sxs-lookup"><span data-stu-id="0d4f1-106">The following image shows some grouped items:</span></span>

![Liczby rozdzielone na grupy nieparzyste i parzyste.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

<span data-ttu-id="0d4f1-108">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.ListView> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="0d4f1-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="0d4f1-109">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0d4f1-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

<span data-ttu-id="0d4f1-110">Aby włączyć grupowanie, należy najpierw utworzyć jeden lub więcej <xref:System.Windows.Forms.ListViewGroup> obiektów w projektancie lub programowo.</span><span class="sxs-lookup"><span data-stu-id="0d4f1-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="0d4f1-111">Po zdefiniowaniu grupy można przypisać do niej elementy.</span><span class="sxs-lookup"><span data-stu-id="0d4f1-111">Once a group has been defined, you can assign items to it.</span></span>

> [!NOTE]
> <span data-ttu-id="0d4f1-112"><xref:System.Windows.Forms.ListView>grupy są dostępne tylko [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] wtedy, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> gdy aplikacja wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="0d4f1-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0d4f1-113">We wcześniejszych systemach operacyjnych każdy kod dotyczący grup nie ma wpływu, a grupy nie będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="0d4f1-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="0d4f1-114">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0d4f1-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>

## <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="0d4f1-115">Aby dodać lub usunąć grupy w projektancie</span><span class="sxs-lookup"><span data-stu-id="0d4f1-115">To add or remove groups in the designer</span></span>

1. <span data-ttu-id="0d4f1-116">W oknie **Właściwości** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio <xref:System.Windows.Forms.ListView.Groups%2A> .](./media/visual-studio-ellipsis-button.png)) obok właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d4f1-116">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>

     <span data-ttu-id="0d4f1-117">Zostanie wyświetlony **Edytor kolekcji ListView** .</span><span class="sxs-lookup"><span data-stu-id="0d4f1-117">The **ListViewGroup Collection Editor** appears.</span></span>

2. <span data-ttu-id="0d4f1-118">Aby dodać grupę, kliknij przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="0d4f1-118">To add a group, click the **Add** button.</span></span> <span data-ttu-id="0d4f1-119">Następnie można ustawić właściwości nowej grupy, takie jak <xref:System.Windows.Forms.ListViewGroup.Header%2A> właściwości i. <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A></span><span class="sxs-lookup"><span data-stu-id="0d4f1-119">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="0d4f1-120">Aby usunąć grupę, zaznacz ją i kliknij przycisk **Usuń** .</span><span class="sxs-lookup"><span data-stu-id="0d4f1-120">To remove a group, select it and click the **Remove** button.</span></span>

## <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="0d4f1-121">Aby przypisać elementy do grup w projektancie</span><span class="sxs-lookup"><span data-stu-id="0d4f1-121">To assign items to groups in the designer</span></span>

1. <span data-ttu-id="0d4f1-122">W oknie **Właściwości** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio <xref:System.Windows.Forms.ListView.Items%2A> .](./media/visual-studio-ellipsis-button.png)) obok właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d4f1-122">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="0d4f1-123">Zostanie wyświetlony **Edytor kolekcji ListViewItem** .</span><span class="sxs-lookup"><span data-stu-id="0d4f1-123">The **ListViewItem Collection Editor** appears.</span></span>

2. <span data-ttu-id="0d4f1-124">Aby dodać nowy element, kliknij przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="0d4f1-124">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="0d4f1-125">Następnie można ustawić właściwości nowego elementu, <xref:System.Windows.Forms.ListViewItem.Text%2A> na przykład właściwości i. <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A></span><span class="sxs-lookup"><span data-stu-id="0d4f1-125">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

3. <span data-ttu-id="0d4f1-126"><xref:System.Windows.Forms.ListViewItem.Group%2A> Wybierz właściwość i wybierz grupę z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="0d4f1-126">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d4f1-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d4f1-127">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="0d4f1-128">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="0d4f1-128">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="0d4f1-129">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="0d4f1-129">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="0d4f1-130">Instrukcje: Dodawanie i usuwanie elementów za pomocą kontrolki ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d4f1-130">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
