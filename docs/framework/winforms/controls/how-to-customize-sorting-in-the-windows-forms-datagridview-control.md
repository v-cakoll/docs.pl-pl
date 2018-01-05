---
title: 'Porady: dostosowywanie sortowania w formancie DataGridView formularzy systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e1fd70aea1dec618a324d271d5bab34ac58ce85a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="0e49e-102">Porady: dostosowywanie sortowania w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0e49e-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0e49e-103"><xref:System.Windows.Forms.DataGridView> Kontrola zapewnia automatyczne sortowanie, ale w zależności od potrzeb, może być konieczne dostosowanie operacji sortowania.</span><span class="sxs-lookup"><span data-stu-id="0e49e-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="0e49e-104">Na przykład można sortowanie programowe tworzenie alternatywny interfejs użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="0e49e-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="0e49e-105">Alternatywnie można obsługiwać <xref:System.Windows.Forms.DataGridView.SortCompare> zdarzenia lub wywołanie `Sort(IComparer)` przeciążenia z <xref:System.Windows.Forms.DataGridView.Sort%2A> metodę większą elastyczność sortowania, takich jak sortowania wielu kolumn.</span><span class="sxs-lookup"><span data-stu-id="0e49e-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="0e49e-106">W poniższych przykładach kodu pokazano te trzy sposoby sortowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="0e49e-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="0e49e-107">Aby uzyskać więcej informacji, zobacz [Tryb sortowania kolumn w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="0e49e-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="0e49e-108">Sortowanie programowe</span><span class="sxs-lookup"><span data-stu-id="0e49e-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="0e49e-109">Poniższy przykład kodu pokazuje programowe sortowania za pomocą <xref:System.Windows.Forms.DataGridView.SortOrder%2A> i <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> właściwości, aby określić kierunek sortowania i <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> właściwości na ręczne ustawienie sortowania symbolu.</span><span class="sxs-lookup"><span data-stu-id="0e49e-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="0e49e-110">`Sort(DataGridViewColumn,ListSortDirection)` Przeciążenia z <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda jest używana do sortowania danych tylko w jednej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="0e49e-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="0e49e-111">Za pomocą tego zdarzenia SortCompare sortowanie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="0e49e-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="0e49e-112">Poniższy przykład kodu pokazuje sortowanie niestandardowe przy użyciu <xref:System.Windows.Forms.DataGridView.SortCompare> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0e49e-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="0e49e-113">Wybrane <xref:System.Windows.Forms.DataGridViewColumn> jest sortowana i, jeśli występują zduplikowane wartości w kolumnie, w kolumnie Identyfikator służy do określania kolejności końcowego.</span><span class="sxs-lookup"><span data-stu-id="0e49e-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="0e49e-114">Sortowanie niestandardowe przy użyciu interfejsu IComparer</span><span class="sxs-lookup"><span data-stu-id="0e49e-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="0e49e-115">Poniższy przykład kodu pokazuje sortowanie niestandardowe przy użyciu `Sort(IComparer)` przeciążenia z <xref:System.Windows.Forms.DataGridView.Sort%2A> metodę, która przyjmuje implementacja <xref:System.Collections.IComparer> interfejs do wykonania sortowania wiele kolumn.</span><span class="sxs-lookup"><span data-stu-id="0e49e-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0e49e-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0e49e-116">Compiling the Code</span></span>  
 <span data-ttu-id="0e49e-117">Wymagaj te przykłady:</span><span class="sxs-lookup"><span data-stu-id="0e49e-117">These examples require:</span></span>  
  
-   <span data-ttu-id="0e49e-118">Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="0e49e-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0e49e-119">Informacji dotyczących tworzenia tych przykładów z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0e49e-119">For information about building these examples from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0e49e-120">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="0e49e-120">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="0e49e-121">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="0e49e-121">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e49e-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e49e-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="0e49e-123">Sortowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0e49e-123">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0e49e-124">Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0e49e-124">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0e49e-125">Instrukcje: ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0e49e-125">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)
