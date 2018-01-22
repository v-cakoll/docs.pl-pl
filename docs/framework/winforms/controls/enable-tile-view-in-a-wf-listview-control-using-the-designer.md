---
title: "Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72fc1212e6e154cf3459d9ae6b94b6a8965fb151
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="5dd3c-102">Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="5dd3c-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="5dd3c-103">Funkcja widoku kafelków <xref:System.Windows.Forms.ListView> kontroli umożliwia podanie visual równowagi między informacji graficznych i tekstowych.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="5dd3c-104">Wyświetlane dla elementu w widoku tile informacji tekstowych jest taka sama jak informacji o kolumnie zdefiniowanych w widoku szczegółów.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="5dd3c-105">Funkcje widoku kafelków w połączeniu z grupowania lub wstawiania oznaczyć funkcje <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="5dd3c-106">Widoku tile używa ikonę 32 x 32 i kilka wierszy tekstu, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>  
  
 <span data-ttu-id="5dd3c-107">![Widok sąsiadujący w formancie ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span><span class="sxs-lookup"><span data-stu-id="5dd3c-107">![Tile View in a ListView Control](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span></span>  
  
 <span data-ttu-id="5dd3c-108">Widok się, że właściwości i metody umożliwiają określenie pola, które kolumny do wyświetlenia dla każdego elementu i zbiorczo kontrolować rozmiar i wyglądu wszystkich elementów w obrębie kafelka okno widoku kafelków.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="5dd3c-109">Dla uzyskania przejrzystości pierwszy wiersz tekstu na kafelku jest zawsze nazwę elementu; Nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>  
  
 <span data-ttu-id="5dd3c-110">Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="5dd3c-111">Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5dd3c-111">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5dd3c-112">Jest dostępna tylko w widoku tile [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] podczas wywołania aplikacji <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-112">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5dd3c-113">W starszych systemach operacyjnych, dowolny kod związane z widoku tile nie obowiązuje, a <xref:System.Windows.Forms.ListView> kontrolka ma być wyświetlana w widoku dużych ikon.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-113">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="5dd3c-114">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-114">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
>   
>  <span data-ttu-id="5dd3c-115">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5dd3c-116">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5dd3c-117">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5dd3c-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="5dd3c-118">Aby ustawić widoku tile w Projektancie</span><span class="sxs-lookup"><span data-stu-id="5dd3c-118">To set tile view in the designer</span></span>  
  
1.  <span data-ttu-id="5dd3c-119">Wybierz <xref:System.Windows.Forms.ListView> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-119">Select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>  
  
2.  <span data-ttu-id="5dd3c-120">W **właściwości** wybierz <xref:System.Windows.Forms.ListView.View%2A> właściwości i wybierz polecenie **Kafelek**.</span><span class="sxs-lookup"><span data-stu-id="5dd3c-120">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd3c-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5dd3c-121">See Also</span></span>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [<span data-ttu-id="5dd3c-122">Funkcje systemu Windows XP i formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5dd3c-122">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="5dd3c-123">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="5dd3c-123">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
