---
title: "Porady: wyświetlanie nagłówków elementów w formancie DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da02f9374471a581a58131e26d618f91d7cbb7af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="385ee-102">Porady: wyświetlanie nagłówków elementów w formancie DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="385ee-102">How to: Display Item Headers in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="385ee-103">Nagłówek elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrola zapewnia wizualne wskaźnika podczas <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="385ee-103">The item header in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control provides a visual indicator when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> is selected.</span></span> <span data-ttu-id="385ee-104">Gdy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (domyślnie), nagłówek elementu jest wyświetlany z lewej strony każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="385ee-104">When the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (the default), the item header is displayed to the left of each item.</span></span> <span data-ttu-id="385ee-105">Gdy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, nagłówek elementu jest wyświetlany w górnej części każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="385ee-105">When the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, the item header is displayed at the top of each item.</span></span>  
  
 <span data-ttu-id="385ee-106">Gdy pierwszy jest zaznaczona, nagłówek elementu jest wyświetlane w kolorze określonym przez <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> właściwości i ikonę strzałki białe są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="385ee-106">When it is first selected, the item header is displayed in the color that is specified by the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> property, and a white arrow icon is displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="385ee-107">Jeśli ustawisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> do <xref:System.Drawing.Color.White%2A>, symbol zaznaczenia nie będą widoczne, gdy najpierw jest zaznaczony element.</span><span class="sxs-lookup"><span data-stu-id="385ee-107">If you set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> to <xref:System.Drawing.Color.White%2A>, the selection symbol will not be visible when the item is first selected.</span></span>  
  
 <span data-ttu-id="385ee-108">Pola w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> ma fokus, kolor zmiany nagłówka elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> koloru i zmiany ikonę strzałki na kolor czarny w tle.</span><span class="sxs-lookup"><span data-stu-id="385ee-108">When a field in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> has focus, the color of the item header changes to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> background color and the arrow icon changes to black.</span></span> <span data-ttu-id="385ee-109">Jeśli dane są zmieniane, symbol ołówka jest wyświetlany w nagłówku elementu.</span><span class="sxs-lookup"><span data-stu-id="385ee-109">If data is changed, a pencil symbol is displayed in the item header.</span></span>  
  
 <span data-ttu-id="385ee-110">Domyślna szerokość (lub wysokość podczas <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> właściwość jest ustawiona na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) elementu nagłówek jest 15 pikseli.</span><span class="sxs-lookup"><span data-stu-id="385ee-110">The default width (or height when the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) of the item header is 15 pixels.</span></span> <span data-ttu-id="385ee-111">Szerokość można zmienić, określając <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="385ee-111">You can change the width by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="385ee-112">Jeśli <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwość jest ustawiona na wartość, która jest mniejsza niż 11, symbole wskaźnika nagłówka elementu nie będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="385ee-112">If the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property is set to a value that is less than 11, the indicator symbols in the item header will not be displayed.</span></span>  
  
 <span data-ttu-id="385ee-113">Nagłówki elementów można ukryć, ustawiając <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="385ee-113">You can hide the item headers by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> property to **False**.</span></span> <span data-ttu-id="385ee-114">Gdy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> ustawiono **False**, jedyną reakcją, że element jest zaznaczony jest przerywana linia na obwodzie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span><span class="sxs-lookup"><span data-stu-id="385ee-114">When <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> is set to **False**, the only indication that an item is selected is a dotted line around the perimeter of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="385ee-115">Można też podać wskaźnika zaznaczenia przez monitorowanie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> właściwość <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzenie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="385ee-115">You can also provide your own selection indicator by monitoring the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> property of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="385ee-116">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.</span><span class="sxs-lookup"><span data-stu-id="385ee-116">For more information, see <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.</span></span>  
  
### <a name="to-change-the-appearance-of-item-headers"></a><span data-ttu-id="385ee-117">Aby zmienić wygląd nagłówków elementów</span><span class="sxs-lookup"><span data-stu-id="385ee-117">To change the appearance of item headers</span></span>  
  
1.  <span data-ttu-id="385ee-118">W narzędziu Projektant dla formularzy systemu Windows wybierz region niższe <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="385ee-118">In the Windows Forms Designer, select the lower region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="385ee-119">Należy wybrać region na dole formantu.</span><span class="sxs-lookup"><span data-stu-id="385ee-119">You must select the lower region of the control.</span></span> <span data-ttu-id="385ee-120">W przypadku wybrania sekcji szablonu elementu inny zestaw właściwości zostaną wyświetlone w oknie właściwości.</span><span class="sxs-lookup"><span data-stu-id="385ee-120">If you select the item template section, a different set of properties will appear in the Properties window.</span></span>  
  
2.  <span data-ttu-id="385ee-121">W oknie właściwości użyj <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> właściwości, aby zmienić kolor nagłówków elementów.</span><span class="sxs-lookup"><span data-stu-id="385ee-121">In the Properties window, use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> property to change the color of the item headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="385ee-122">Jeśli ustawisz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> do <xref:System.Drawing.Color.White%2A>, symbol zaznaczenia nie będą widoczne, gdy najpierw jest zaznaczony element.</span><span class="sxs-lookup"><span data-stu-id="385ee-122">If you set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> to <xref:System.Drawing.Color.White%2A>, the selection symbol will not be visible when the item is first selected.</span></span>  
  
3.  <span data-ttu-id="385ee-123">Użyj <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwości do zmiany szerokości (lub wysokości) nagłówków elementów.</span><span class="sxs-lookup"><span data-stu-id="385ee-123">Use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property to change the width (or height) of the item headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="385ee-124">Jeśli <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> właściwość jest ustawiona na wartość, która jest mniejsza niż 11, symbole wskaźnika nagłówka elementu nie będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="385ee-124">If the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property is set to a value that is less than 11, the indicator symbols in the item header will not be displayed.</span></span>  
  
### <a name="to-hide-item-headers"></a><span data-ttu-id="385ee-125">Aby ukryć nagłówków elementów</span><span class="sxs-lookup"><span data-stu-id="385ee-125">To hide item headers</span></span>  
  
1.  <span data-ttu-id="385ee-126">W narzędziu Projektant dla formularzy systemu Windows wybierz region niższe <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.</span><span class="sxs-lookup"><span data-stu-id="385ee-126">In the Windows Forms Designer, select the lower region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="385ee-127">Należy wybrać region na dole formantu.</span><span class="sxs-lookup"><span data-stu-id="385ee-127">You must select the lower region of the control.</span></span> <span data-ttu-id="385ee-128">W przypadku wybrania sekcji szablonu elementu inny zestaw właściwości zostaną wyświetlone w oknie właściwości.</span><span class="sxs-lookup"><span data-stu-id="385ee-128">If you select the item template section, a different set of properties will appear in the Properties window.</span></span>  
  
2.  <span data-ttu-id="385ee-129">W oknie właściwości ustaw <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="385ee-129">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> property to **False**.</span></span>  
  
     <span data-ttu-id="385ee-130">Gdy element <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> jest zaznaczone, jedyną reakcją będzie przerywana linia na obwodzie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span><span class="sxs-lookup"><span data-stu-id="385ee-130">When an item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is selected, the only indication will be a dotted line around the perimeter of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="385ee-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="385ee-131">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="385ee-132">Wprowadzenie do formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="385ee-132">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="385ee-133">Porady: Zmienianie wyglądu formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="385ee-133">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="385ee-134">Porady: Zmienianie układu formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="385ee-134">How to: Change the Layout of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="385ee-135">Rozwiązywanie problemów z formantem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="385ee-135">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
