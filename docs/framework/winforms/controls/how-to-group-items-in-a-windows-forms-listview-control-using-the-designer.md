---
title: Grupowanie elementów w kontrolce ListView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 935d8d75517e1028e686ca229f6ada656f58b01e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736680"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="d8203-102">Porady: grupowanie elementów w formancie ListView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="d8203-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="d8203-103">Funkcja grupowania kontrolki <xref:System.Windows.Forms.ListView> umożliwia wyświetlanie powiązanych zestawów elementów w grupach.</span><span class="sxs-lookup"><span data-stu-id="d8203-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="d8203-104">Te grupy są rozdzielane na ekranie przez nagłówki grup poziomych, które zawierają tytuły grup.</span><span class="sxs-lookup"><span data-stu-id="d8203-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="d8203-105">Korzystając z grup <xref:System.Windows.Forms.ListView>, można ułatwić nawigację dużych list, grupując elementy alfabetycznie według daty lub przez inne grupowanie logiczne.</span><span class="sxs-lookup"><span data-stu-id="d8203-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="d8203-106">Na poniższej ilustracji przedstawiono niektóre zgrupowane elementy:</span><span class="sxs-lookup"><span data-stu-id="d8203-106">The following image shows some grouped items:</span></span>

![Liczby rozdzielone na grupy nieparzyste i parzyste.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

<span data-ttu-id="d8203-108">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="d8203-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="d8203-109">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d8203-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

<span data-ttu-id="d8203-110">Aby włączyć grupowanie, należy najpierw utworzyć co najmniej jeden obiekt <xref:System.Windows.Forms.ListViewGroup> w projektancie lub programowo.</span><span class="sxs-lookup"><span data-stu-id="d8203-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="d8203-111">Po zdefiniowaniu grupy można przypisać do niej elementy.</span><span class="sxs-lookup"><span data-stu-id="d8203-111">Once a group has been defined, you can assign items to it.</span></span>

## <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="d8203-112">Aby dodać lub usunąć grupy w projektancie</span><span class="sxs-lookup"><span data-stu-id="d8203-112">To add or remove groups in the designer</span></span>

1. <span data-ttu-id="d8203-113">W oknie **Właściwości** kliknij przycisk **wielokropka** (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.ListView.Groups%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8203-113">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>

     <span data-ttu-id="d8203-114">Zostanie wyświetlony **Edytor kolekcji ListView** .</span><span class="sxs-lookup"><span data-stu-id="d8203-114">The **ListViewGroup Collection Editor** appears.</span></span>

2. <span data-ttu-id="d8203-115">Aby dodać grupę, kliknij przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="d8203-115">To add a group, click the **Add** button.</span></span> <span data-ttu-id="d8203-116">Następnie można ustawić właściwości nowej grupy, takie jak <xref:System.Windows.Forms.ListViewGroup.Header%2A> i <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d8203-116">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="d8203-117">Aby usunąć grupę, zaznacz ją i kliknij przycisk **Usuń** .</span><span class="sxs-lookup"><span data-stu-id="d8203-117">To remove a group, select it and click the **Remove** button.</span></span>

## <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="d8203-118">Aby przypisać elementy do grup w projektancie</span><span class="sxs-lookup"><span data-stu-id="d8203-118">To assign items to groups in the designer</span></span>

1. <span data-ttu-id="d8203-119">W oknie **Właściwości** kliknij przycisk **wielokropka** (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.ListView.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8203-119">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>

     <span data-ttu-id="d8203-120">Zostanie wyświetlony **Edytor kolekcji ListViewItem** .</span><span class="sxs-lookup"><span data-stu-id="d8203-120">The **ListViewItem Collection Editor** appears.</span></span>

2. <span data-ttu-id="d8203-121">Aby dodać nowy element, kliknij przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="d8203-121">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="d8203-122">Następnie można ustawić właściwości nowego elementu, takie jak <xref:System.Windows.Forms.ListViewItem.Text%2A> i <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d8203-122">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>

3. <span data-ttu-id="d8203-123">Wybierz właściwość <xref:System.Windows.Forms.ListViewItem.Group%2A> i wybierz grupę z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="d8203-123">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8203-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8203-124">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="d8203-125">ListView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="d8203-125">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="d8203-126">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="d8203-126">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="d8203-127">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d8203-127">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
