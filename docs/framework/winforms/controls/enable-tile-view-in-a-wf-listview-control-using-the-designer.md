---
title: 'Instrukcje: włączanie widoku Tile w kontrolce ListView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 8a45a8a484bd373f53585b1b113a51e59b30fca2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040364"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="31191-102">Instrukcje: włączanie widoku Tile w kontrolce ListView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="31191-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="31191-103">Funkcja widok kafelka <xref:System.Windows.Forms.ListView> kontrolki umożliwia zapewnienie balansu wizualnego między informacjami graficznymi i tekstowymi.</span><span class="sxs-lookup"><span data-stu-id="31191-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="31191-104">Informacje tekstowe wyświetlane dla elementu w widoku kafelków są takie same, jak informacje o kolumnie zdefiniowane dla widoku szczegółów.</span><span class="sxs-lookup"><span data-stu-id="31191-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="31191-105">Funkcje widoku kafelków w połączeniu z funkcjami grupowania lub wstawiania znaczników w <xref:System.Windows.Forms.ListView> formancie.</span><span class="sxs-lookup"><span data-stu-id="31191-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>

 <span data-ttu-id="31191-106">Widok kafelka używa ikony 32 x 32 i kilku wierszy tekstu, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="31191-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>

 <span data-ttu-id="31191-107">![Widok kafelka w kontrolce ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Wyświetlanie ikon i tekstu kafelków")</span><span class="sxs-lookup"><span data-stu-id="31191-107">![Tile View in a ListView Control](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>

 <span data-ttu-id="31191-108">Właściwości widoku kafelków i metody umożliwiają określenie pól kolumn, które mają być wyświetlane dla każdego elementu, oraz zbiorcze kontrolowanie rozmiaru i wyglądu wszystkich elementów w oknie widoku kafelków.</span><span class="sxs-lookup"><span data-stu-id="31191-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="31191-109">Dla jasności pierwszy wiersz tekstu na kafelku jest zawsze nazwą elementu; nie można go zmienić.</span><span class="sxs-lookup"><span data-stu-id="31191-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>

 <span data-ttu-id="31191-110">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.ListView> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="31191-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="31191-111">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="31191-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

> [!NOTE]
> <span data-ttu-id="31191-112">Widok kafelków jest dostępny tylko [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] wtedy, gdy aplikacja <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="31191-112">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="31191-113">We wcześniejszych systemach operacyjnych każdy kod związany z widokiem kafelka nie ma żadnego efektu, a <xref:System.Windows.Forms.ListView> kontrolka zostanie wyświetlona w widoku dużych ikon.</span><span class="sxs-lookup"><span data-stu-id="31191-113">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="31191-114">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="31191-114">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>

## <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="31191-115">Aby ustawić widok kafelków w projektancie</span><span class="sxs-lookup"><span data-stu-id="31191-115">To set tile view in the designer</span></span>

1. <span data-ttu-id="31191-116">W programie Visual Studio zaznacz <xref:System.Windows.Forms.ListView> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="31191-116">In Visual Studio, select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>

2. <span data-ttu-id="31191-117">W oknie **Właściwości** wybierz <xref:System.Windows.Forms.ListView.View%2A> właściwość, a następnie wybierz pozycję **kafelek**.</span><span class="sxs-lookup"><span data-stu-id="31191-117">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>

## <a name="see-also"></a><span data-ttu-id="31191-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31191-118">See also</span></span>

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="31191-119">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="31191-119">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
