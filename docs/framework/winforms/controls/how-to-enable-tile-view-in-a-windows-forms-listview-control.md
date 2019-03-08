---
title: 'Instrukcje: Włączanie widoku Tile w formancie ListView formularzy Windows'
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
ms.openlocfilehash: 4bc5a9dfc17acc453030c6213b9c76572d21c474
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675813"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="8eb71-102">Instrukcje: Włączanie widoku Tile w formancie ListView formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="8eb71-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="8eb71-103">Korzystając z funkcji widoku kafelków <xref:System.Windows.Forms.ListView> kontrolki, możesz podać visual równowagi między informacje graficzne i tekstowe.</span><span class="sxs-lookup"><span data-stu-id="8eb71-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="8eb71-104">Tekstowe informacje wyświetlane dla elementu w widoku kafelków jest taka sama jak informacji o kolumnie zdefiniowane dla widoku szczegółów.</span><span class="sxs-lookup"><span data-stu-id="8eb71-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="8eb71-105">Widoku kafelków działa w połączeniu z grupowania lub wstawiania funkcji znaku w <xref:System.Windows.Forms.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8eb71-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="8eb71-106">Wyświetlanie kafelka używa ikonę 32 x 32 piksele i kilka wierszy tekstu, jak pokazano na poniższych ilustracjach.</span><span class="sxs-lookup"><span data-stu-id="8eb71-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="8eb71-107">![Widok w kontrolce ListView kafelków](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Kafelek widoku ikon i tekstu")</span><span class="sxs-lookup"><span data-stu-id="8eb71-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  
  
  
 <span data-ttu-id="8eb71-108">Aby włączyć widoku kafelków, ustaw <xref:System.Windows.Forms.ListView.View%2A> właściwość <xref:System.Windows.Forms.View.Tile>.</span><span class="sxs-lookup"><span data-stu-id="8eb71-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="8eb71-109">Można dostosować rozmiar kafelków, ustawiając <xref:System.Windows.Forms.ListView.TileSize%2A> właściwość i liczbę wierszy tekstu, wyświetlane na kafelku, dostosowując <xref:System.Windows.Forms.ListView.Columns%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8eb71-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8eb71-110">Widoku kafelków jest dostępna tylko na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] gdy Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8eb71-110">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8eb71-111">W starszych systemach operacyjnych, dowolnego kodu, powiązany z widoku kafelków nie obowiązuje oraz <xref:System.Windows.Forms.ListView> kontrolka wyświetla się w Widok dużych ikon.</span><span class="sxs-lookup"><span data-stu-id="8eb71-111">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="8eb71-112">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8eb71-112">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="8eb71-113">Aby programowo ustawić widoku kafelków</span><span class="sxs-lookup"><span data-stu-id="8eb71-113">To set tile view programmatically</span></span>  
  
1.  <span data-ttu-id="8eb71-114">Użyj <xref:System.Windows.Forms.View> wyliczenie <xref:System.Windows.Forms.ListView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8eb71-114">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="8eb71-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="8eb71-115">Example</span></span>  
 <span data-ttu-id="8eb71-116">Poniższy przykład kompletny kod pokazuje widoku kafelków z kafelkami zmodyfikowany do wyświetlania trzy wiersze tekstu.</span><span class="sxs-lookup"><span data-stu-id="8eb71-116">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="8eb71-117">Rozmiar fragmentu został dostosowany tak, aby zapobiec zawijania wierszy.</span><span class="sxs-lookup"><span data-stu-id="8eb71-117">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8eb71-118">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8eb71-118">Compiling the Code</span></span>  
 <span data-ttu-id="8eb71-119">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="8eb71-119">This example requires:</span></span>  
  
-   <span data-ttu-id="8eb71-120">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="8eb71-120">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="8eb71-121">Plik ikony o nazwie book.ico w tym samym katalogu co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="8eb71-121">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
 <span data-ttu-id="8eb71-122">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8eb71-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8eb71-123">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="8eb71-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb71-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8eb71-124">See also</span></span>
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="8eb71-125">Kontrolka ListView</span><span class="sxs-lookup"><span data-stu-id="8eb71-125">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [<span data-ttu-id="8eb71-126">ListView, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="8eb71-126">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
