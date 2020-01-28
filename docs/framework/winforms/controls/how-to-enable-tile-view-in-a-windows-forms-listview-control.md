---
title: Włącz widok kafelków w formancie ListView
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
ms.openlocfilehash: 8ccbd42d870e44fc6fd80169327922409ea4f6e7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745465"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="ff8f1-102">Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ff8f1-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="ff8f1-103">Za pomocą funkcji Widok kafelka kontrolki <xref:System.Windows.Forms.ListView> można zapewnić balans wizualizacji między informacjami graficznymi i tekstowymi.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="ff8f1-104">Informacje tekstowe wyświetlane dla elementu w widoku kafelków są takie same, jak informacje o kolumnie zdefiniowane dla widoku szczegółów.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="ff8f1-105">Widok kafelków działa w połączeniu z funkcjami grupowania lub wstawiania znaczników w kontrolce <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="ff8f1-106">Widok kafelka używa ikony pikseli 32 x 32 i kilku wierszy tekstu, jak pokazano na poniższych ilustracjach.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="ff8f1-107">![Widok kafelka w kontrolce ListView](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Wyświetlanie ikon i tekstu kafelków")</span><span class="sxs-lookup"><span data-stu-id="ff8f1-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  
 
 <span data-ttu-id="ff8f1-108">Aby włączyć widok kafelków, ustaw właściwość <xref:System.Windows.Forms.ListView.View%2A> na <xref:System.Windows.Forms.View.Tile>.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="ff8f1-109">Można dostosować rozmiar kafelków, ustawiając właściwość <xref:System.Windows.Forms.ListView.TileSize%2A> i liczbę wierszy tekstu wyświetlanych na kafelku przez dostosowanie kolekcji <xref:System.Windows.Forms.ListView.Columns%2A>.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="ff8f1-110">Aby programowo ustawić widok kafelków</span><span class="sxs-lookup"><span data-stu-id="ff8f1-110">To set tile view programmatically</span></span>  
  
1. <span data-ttu-id="ff8f1-111">Użyj <xref:System.Windows.Forms.View> Wyliczenie <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-111">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="ff8f1-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff8f1-112">Example</span></span>  
 <span data-ttu-id="ff8f1-113">Poniższy przykładowy kod ilustruje widok kafelków z kafelkami zmodyfikowanymi, aby pokazać trzy wiersze tekstu.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-113">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="ff8f1-114">Rozmiar kafelka został dostosowany, aby zapobiec zawijaniu wierszy.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-114">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ff8f1-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ff8f1-115">Compiling the Code</span></span>  
 <span data-ttu-id="ff8f1-116">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ff8f1-116">This example requires:</span></span>  
  
- <span data-ttu-id="ff8f1-117">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-117">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="ff8f1-118">Plik ikony o nazwie Book. ico w tym samym katalogu, w którym znajduje się plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-118">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff8f1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff8f1-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="ff8f1-120">ListView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="ff8f1-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="ff8f1-121">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="ff8f1-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
