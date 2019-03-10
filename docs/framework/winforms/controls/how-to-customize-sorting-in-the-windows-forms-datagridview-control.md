---
title: 'Instrukcje: Dostosowywanie sortowania w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 18d3ec4aa2c8c4a9bfd769b8d922bc76e7dac4a5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718535"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a9ff9-102">Instrukcje: Dostosowywanie sortowania w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9ff9-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a9ff9-103"><xref:System.Windows.Forms.DataGridView> Control oferuje automatyczne sortowanie, ale w zależności od potrzeb, może być konieczne dostosowanie operacjach sortowania.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="a9ff9-104">Na przykład umożliwia sortowanie programowe tworzenie alternatywny interfejs użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="a9ff9-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="a9ff9-105">Alternatywnie, można obsługiwać <xref:System.Windows.Forms.DataGridView.SortCompare> zdarzenia lub wywołanie `Sort(IComparer)` przeciążenia <xref:System.Windows.Forms.DataGridView.Sort%2A> metody sortowania funkcje i elastyczność, takich jak sortowanie wielu kolumn.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="a9ff9-106">Poniższe przykłady kodu ilustrują te trzy sposoby sortowania niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="a9ff9-107">Aby uzyskać więcej informacji, zobacz [Tryb sortowania kolumn w formancie DataGridView formularzy Windows](column-sort-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="a9ff9-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="a9ff9-108">Programowe sortowanie</span><span class="sxs-lookup"><span data-stu-id="a9ff9-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="a9ff9-109">Poniższy przykład kodu demonstruje programowe sortowanie, za pomocą <xref:System.Windows.Forms.DataGridView.SortOrder%2A> i <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> właściwości, aby określić kierunek sortowania, a <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> właściwości, aby ręcznie ustawić symbol sortowania.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="a9ff9-110">`Sort(DataGridViewColumn,ListSortDirection)` Przeciążenia <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda jest używana do sortowania danych tylko w przypadku zaznaczenia jednej kolumny.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="a9ff9-111">Niestandardowe sortowanie, za pomocą zdarzenia SortCompare</span><span class="sxs-lookup"><span data-stu-id="a9ff9-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="a9ff9-112">Poniższy przykład kodu demonstruje, niestandardowe sortowanie, za pomocą <xref:System.Windows.Forms.DataGridView.SortCompare> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="a9ff9-113">Wybrane <xref:System.Windows.Forms.DataGridViewColumn> jest sortowana i, jeśli istnieją zduplikowane wartości w kolumnie, kolumna Identyfikatora służy do określenia końcowego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="a9ff9-114">Sortowanie niestandardowe przy użyciu interfejsu IComparer</span><span class="sxs-lookup"><span data-stu-id="a9ff9-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="a9ff9-115">Poniższy przykład kodu demonstruje, niestandardowe sortowanie, za pomocą `Sort(IComparer)` przeciążenia <xref:System.Windows.Forms.DataGridView.Sort%2A> metody, która przyjmuje implementację <xref:System.Collections.IComparer> interfejsu, aby wykonać sortowanie wielu kolumn.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a9ff9-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a9ff9-116">Compiling the Code</span></span>  
 <span data-ttu-id="a9ff9-117">Wymagaj tych przykładach:</span><span class="sxs-lookup"><span data-stu-id="a9ff9-117">These examples require:</span></span>  
  
-   <span data-ttu-id="a9ff9-118">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="a9ff9-119">Aby uzyskać informacje o tworzeniu tych przykładów z poziomu wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a9ff9-119">For information about building these examples from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a9ff9-120">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-120">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ff9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9ff9-121">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="a9ff9-122">Sortowanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9ff9-122">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a9ff9-123">Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9ff9-123">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a9ff9-124">Instrukcje: Ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a9ff9-124">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)
