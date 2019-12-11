---
title: 'Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 4f51d3a596bc3358942cdfd654b3e4515d96cd07
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960101"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="40553-102">Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="40553-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="40553-103">Funkcja widok kafelka kontrolki <xref:System.Windows.Forms.ListView> umożliwia zapewnienie równowagi wizualnej między informacjami graficznymi i tekstowymi.</span><span class="sxs-lookup"><span data-stu-id="40553-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="40553-104">Informacje tekstowe wyświetlane dla elementu w widoku kafelków są takie same, jak informacje o kolumnie zdefiniowane dla widoku szczegółów.</span><span class="sxs-lookup"><span data-stu-id="40553-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="40553-105">Funkcje widoku kafelków w połączeniu z funkcjami grupowania lub wstawiania znaczników w kontrolce <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="40553-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>

 <span data-ttu-id="40553-106">Widok kafelka używa ikony 32 x 32 i kilku wierszy tekstu, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="40553-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>

 <span data-ttu-id="40553-107">![Widok kafelka w kontrolce ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Wyświetlanie ikon i tekstu kafelków")</span><span class="sxs-lookup"><span data-stu-id="40553-107">![Tile View in a ListView Control](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>

 <span data-ttu-id="40553-108">Właściwości widoku kafelków i metody umożliwiają określenie pól kolumn, które mają być wyświetlane dla każdego elementu, oraz zbiorcze kontrolowanie rozmiaru i wyglądu wszystkich elementów w oknie widoku kafelków.</span><span class="sxs-lookup"><span data-stu-id="40553-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="40553-109">Dla jasności pierwszy wiersz tekstu na kafelku jest zawsze nazwą elementu; nie można go zmienić.</span><span class="sxs-lookup"><span data-stu-id="40553-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>

 <span data-ttu-id="40553-110">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="40553-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="40553-111">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="40553-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="40553-112">Aby ustawić widok kafelków w projektancie</span><span class="sxs-lookup"><span data-stu-id="40553-112">To set tile view in the designer</span></span>

1. <span data-ttu-id="40553-113">W programie Visual Studio Wybierz kontrolkę <xref:System.Windows.Forms.ListView> w formularzu.</span><span class="sxs-lookup"><span data-stu-id="40553-113">In Visual Studio, select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>

2. <span data-ttu-id="40553-114">W oknie **Właściwości** wybierz właściwość <xref:System.Windows.Forms.ListView.View%2A> i wybierz pozycję **kafelek**.</span><span class="sxs-lookup"><span data-stu-id="40553-114">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>

## <a name="see-also"></a><span data-ttu-id="40553-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40553-115">See also</span></span>

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="40553-116">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="40553-116">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
