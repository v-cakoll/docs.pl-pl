---
title: Włącz widok kafelków w kontrolce widoku listview
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: 1478ba5e4f175cd7d9ec7ab5c3c4bc9050ce02fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182150"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="b42be-102">Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b42be-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="b42be-103">Dzięki funkcji widoku kafelków <xref:System.Windows.Forms.ListView> formantu można zapewnić wizualną równowagę między informacjami graficznymi i tekstowymi.</span><span class="sxs-lookup"><span data-stu-id="b42be-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="b42be-104">Informacje tekstowe wyświetlane dla elementu w widoku kafelków są takie same jak informacje o kolumnach zdefiniowane dla widoku szczegółów.</span><span class="sxs-lookup"><span data-stu-id="b42be-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="b42be-105">Widok kafelków działa w połączeniu z elementami grupowania <xref:System.Windows.Forms.ListView> lub wstawiania w formancie.</span><span class="sxs-lookup"><span data-stu-id="b42be-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="b42be-106">Widok kafelka używa ikony 32 x 32 pikseli i kilku wierszy tekstu, jak pokazano na poniższych obrazach.</span><span class="sxs-lookup"><span data-stu-id="b42be-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="b42be-107">![Widok kafli w formancie widoku listy](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Ikony widoku kafelków i tekst")</span><span class="sxs-lookup"><span data-stu-id="b42be-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  

 <span data-ttu-id="b42be-108">Aby włączyć widok kafelka, <xref:System.Windows.Forms.View.Tile>ustaw właściwość na <xref:System.Windows.Forms.ListView.View%2A> .</span><span class="sxs-lookup"><span data-stu-id="b42be-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="b42be-109">Rozmiar kafelków można dostosować, ustawiając <xref:System.Windows.Forms.ListView.TileSize%2A> właściwość oraz liczbę linii tekstowych wyświetlanych na <xref:System.Windows.Forms.ListView.Columns%2A> kafelku, dostosowując kolekcję.</span><span class="sxs-lookup"><span data-stu-id="b42be-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="b42be-110">Aby programowo ustawić widok kafelków</span><span class="sxs-lookup"><span data-stu-id="b42be-110">To set tile view programmatically</span></span>  
  
1. <span data-ttu-id="b42be-111">Użyj <xref:System.Windows.Forms.View> wyliczenia <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="b42be-111">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="b42be-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="b42be-112">Example</span></span>  
 <span data-ttu-id="b42be-113">W poniższym przykładzie pełnego kodu przedstawiono widok kafelków z zmodyfikowanymi kafelkami, aby wyświetlić trzy wiersze tekstu.</span><span class="sxs-lookup"><span data-stu-id="b42be-113">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="b42be-114">Rozmiar kafelka został dostosowany, aby zapobiec zawijania linii.</span><span class="sxs-lookup"><span data-stu-id="b42be-114">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b42be-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b42be-115">Compiling the Code</span></span>  
 <span data-ttu-id="b42be-116">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b42be-116">This example requires:</span></span>  
  
- <span data-ttu-id="b42be-117">Odwołania do zestawów System i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b42be-117">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="b42be-118">Plik ikony o nazwie book.ico w tym samym katalogu co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="b42be-118">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b42be-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b42be-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="b42be-120">ListView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="b42be-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="b42be-121">ListView — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="b42be-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
