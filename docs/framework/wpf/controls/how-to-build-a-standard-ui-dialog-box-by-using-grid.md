---
title: 'Instrukcje: Tworzenie standardowego okna dialogowego interfejsu użytkownika przy użyciu siatki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 68c9653e616388374aad2ad33ac7dab68446241d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923423"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="06f58-102">Instrukcje: Tworzenie standardowego okna dialogowego interfejsu użytkownika przy użyciu siatki</span><span class="sxs-lookup"><span data-stu-id="06f58-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="06f58-103">Ten przykład pokazuje, jak utworzyć standardowe [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] okno dialogowe przy <xref:System.Windows.Controls.Grid> użyciu elementu.</span><span class="sxs-lookup"><span data-stu-id="06f58-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06f58-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="06f58-104">Example</span></span>  
 <span data-ttu-id="06f58-105">Poniższy przykład tworzy okno dialogowe, takie jak okno dialogowe **uruchamiania** w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="06f58-105">The following example creates a dialog box like the **Run** dialog box in the Windows operating system.</span></span>  
  
 <span data-ttu-id="06f58-106">Przykład tworzy <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Controls.ColumnDefinition> używa klas i <xref:System.Windows.Controls.RowDefinition> , aby zdefiniować pięć kolumn i cztery wiersze.</span><span class="sxs-lookup"><span data-stu-id="06f58-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="06f58-107">Przykład dodaje i ustawia położenie <xref:System.Windows.Controls.Image>, `RunIcon.png`,,,, aby reprezentować obraz znaleziony w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="06f58-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="06f58-108">Obraz zostanie umieszczony w pierwszej kolumnie i wierszu <xref:System.Windows.Controls.Grid> (w lewym górnym rogu).</span><span class="sxs-lookup"><span data-stu-id="06f58-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="06f58-109">Następnie przykład dodaje <xref:System.Windows.Controls.TextBlock> element do pierwszej kolumny, który obejmuje pozostałe kolumny pierwszego wiersza.</span><span class="sxs-lookup"><span data-stu-id="06f58-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="06f58-110">Dodaje kolejny <xref:System.Windows.Controls.TextBlock> element do drugiego wiersza w pierwszej kolumnie, aby reprezentować **otwarte** pole tekstowe.</span><span class="sxs-lookup"><span data-stu-id="06f58-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="06f58-111"><xref:System.Windows.Controls.TextBlock> Poniżej, który reprezentuje obszar wprowadzania danych.</span><span class="sxs-lookup"><span data-stu-id="06f58-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="06f58-112">Na koniec <xref:System.Windows.Controls.Button> przykład dodaje trzy elementy do ostatniego wiersza, które reprezentują zdarzenia **OK**, **Anuluj**i **Przeglądaj** .</span><span class="sxs-lookup"><span data-stu-id="06f58-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="06f58-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06f58-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [<span data-ttu-id="06f58-114">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="06f58-114">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="06f58-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="06f58-115">How-to Topics</span></span>](grid-how-to-topics.md)
