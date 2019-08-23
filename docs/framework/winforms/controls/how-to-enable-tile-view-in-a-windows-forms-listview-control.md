---
title: 'Instrukcje: włączanie widoku Tile w kontrolce ListView formularzy systemu Windows'
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
ms.openlocfilehash: 44d34ddb00005a0fb86b2d06c4c14e2a5b949819
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966677"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="233d9-102">Instrukcje: włączanie widoku Tile w kontrolce ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="233d9-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="233d9-103">Za pomocą funkcji <xref:System.Windows.Forms.ListView> widok kafelków formantu można zapewnić wizualną równowagę między informacjami graficznymi i tekstowymi.</span><span class="sxs-lookup"><span data-stu-id="233d9-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="233d9-104">Informacje tekstowe wyświetlane dla elementu w widoku kafelków są takie same, jak informacje o kolumnie zdefiniowane dla widoku szczegółów.</span><span class="sxs-lookup"><span data-stu-id="233d9-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="233d9-105">Widok kafelków działa w połączeniu z funkcjami grupowania lub wstawiania znaczników w <xref:System.Windows.Forms.ListView> formancie.</span><span class="sxs-lookup"><span data-stu-id="233d9-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="233d9-106">Widok kafelka używa ikony pikseli 32 x 32 i kilku wierszy tekstu, jak pokazano na poniższych ilustracjach.</span><span class="sxs-lookup"><span data-stu-id="233d9-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="233d9-107">![Widok kafelka w kontrolce ListView](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Wyświetlanie ikon i tekstu kafelków")</span><span class="sxs-lookup"><span data-stu-id="233d9-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  
 
 <span data-ttu-id="233d9-108">Aby włączyć widok kafelków, ustaw <xref:System.Windows.Forms.ListView.View%2A> właściwość na <xref:System.Windows.Forms.View.Tile>.</span><span class="sxs-lookup"><span data-stu-id="233d9-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="233d9-109">Można dostosować rozmiar kafelków, ustawiając <xref:System.Windows.Forms.ListView.TileSize%2A> Właściwość oraz liczbę linii tekstu wyświetlanych na kafelku przez <xref:System.Windows.Forms.ListView.Columns%2A> dostosowanie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="233d9-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="233d9-110">Widok kafelków jest dostępny tylko [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] wtedy, gdy aplikacja <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="233d9-110">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="233d9-111">We wcześniejszych systemach operacyjnych każdy kod związany z widokiem kafelka nie ma żadnego efektu, a <xref:System.Windows.Forms.ListView> kontrolka zostanie wyświetlona w widoku dużych ikon.</span><span class="sxs-lookup"><span data-stu-id="233d9-111">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="233d9-112">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="233d9-112">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="233d9-113">Aby programowo ustawić widok kafelków</span><span class="sxs-lookup"><span data-stu-id="233d9-113">To set tile view programmatically</span></span>  
  
1. <span data-ttu-id="233d9-114"><xref:System.Windows.Forms.View> Użyj wyliczenia<xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="233d9-114">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="233d9-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="233d9-115">Example</span></span>  
 <span data-ttu-id="233d9-116">Poniższy przykładowy kod ilustruje widok kafelków z kafelkami zmodyfikowanymi, aby pokazać trzy wiersze tekstu.</span><span class="sxs-lookup"><span data-stu-id="233d9-116">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="233d9-117">Rozmiar kafelka został dostosowany, aby zapobiec zawijaniu wierszy.</span><span class="sxs-lookup"><span data-stu-id="233d9-117">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="233d9-118">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="233d9-118">Compiling the Code</span></span>  
 <span data-ttu-id="233d9-119">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="233d9-119">This example requires:</span></span>  
  
- <span data-ttu-id="233d9-120">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="233d9-120">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="233d9-121">Plik ikony o nazwie Book. ico w tym samym katalogu, w którym znajduje się plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="233d9-121">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="233d9-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="233d9-122">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="233d9-123">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="233d9-123">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="233d9-124">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="233d9-124">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
