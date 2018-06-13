---
title: Jak tworzyć standardowe okno dialogowe interfejsu użytkownika przy użyciu siatki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: d0b24e320c2a341b069e1c9c3e8b6d5e93076733
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551885"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="fcc5b-102">Jak tworzyć standardowe okno dialogowe interfejsu użytkownika przy użyciu siatki</span><span class="sxs-lookup"><span data-stu-id="fcc5b-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="fcc5b-103">W tym przykładzie przedstawiono sposób tworzenia standardowego [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] okno dialogowe przy użyciu <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="fcc5b-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcc5b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="fcc5b-104">Example</span></span>  
 <span data-ttu-id="fcc5b-105">Poniższy przykład tworzy okno dialogowe podobne **Uruchom** okno dialogowe w [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="fcc5b-105">The following example creates a dialog box like the **Run** dialog box in the [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="fcc5b-106">W przykładzie jest tworzony <xref:System.Windows.Controls.Grid> i używa <xref:System.Windows.Controls.ColumnDefinition> i <xref:System.Windows.Controls.RowDefinition> klasy do definiowania pięć kolumn i wierszy cztery.</span><span class="sxs-lookup"><span data-stu-id="fcc5b-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="fcc5b-107">W przykładzie następnie dodaje i umieszcza <xref:System.Windows.Controls.Image>, `RunIcon.png`, do reprezentowania obrazu, który można znaleźć w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="fcc5b-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="fcc5b-108">Obraz jest umieszczany w pierwszej kolumnie i wiersza <xref:System.Windows.Controls.Grid> (lewego górnego rogu).</span><span class="sxs-lookup"><span data-stu-id="fcc5b-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="fcc5b-109">Następnie w przykładzie dodano <xref:System.Windows.Controls.TextBlock> element do pierwszej kolumny, która obejmuje pozostałych kolumnach pierwszego wiersza.</span><span class="sxs-lookup"><span data-stu-id="fcc5b-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="fcc5b-110">Dodaje innego <xref:System.Windows.Controls.TextBlock> elementu do drugiego wiersza w pierwszej kolumnie do reprezentowania **Otwórz** pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="fcc5b-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="fcc5b-111">A <xref:System.Windows.Controls.TextBlock> następujące, które reprezentuje obszaru wprowadzania danych.</span><span class="sxs-lookup"><span data-stu-id="fcc5b-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="fcc5b-112">Ponadto w przykładzie dodano trzy <xref:System.Windows.Controls.Button> elementy do wiersza końcowego, które reprezentują **OK**, **anulować**, i **Przeglądaj** zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fcc5b-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fcc5b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcc5b-113">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.GridUnitType>  
 [<span data-ttu-id="fcc5b-114">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="fcc5b-114">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="fcc5b-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="fcc5b-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)
