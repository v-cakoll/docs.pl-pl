---
title: Jak utworzyć element siatki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: 9fc70b8f15c4ecb4844c9c2ff4f7eeab94e7b906
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="b7957-102">Jak utworzyć element siatki</span><span class="sxs-lookup"><span data-stu-id="b7957-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="b7957-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7957-103">Example</span></span>  
 <span data-ttu-id="b7957-104">Poniższy przykład przedstawia sposób tworzenia i używania wystąpienia <xref:System.Windows.Controls.Grid> za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] lub kodu.</span><span class="sxs-lookup"><span data-stu-id="b7957-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="b7957-105">W tym przykładzie użyto trzy <xref:System.Windows.Controls.ColumnDefinition> obiektów i trzy <xref:System.Windows.Controls.RowDefinition> obiektów do tworzenia siatki z dziewięciu komórki, taki jak arkusza.</span><span class="sxs-lookup"><span data-stu-id="b7957-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="b7957-106">Każda komórka zawiera <xref:System.Windows.Controls.TextBlock> zawiera element, który reprezentuje dane i górnym wierszu <xref:System.Windows.Controls.TextBlock> z <xref:System.Windows.Controls.Grid.ColumnSpan%2A> właściwości stosowane.</span><span class="sxs-lookup"><span data-stu-id="b7957-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="b7957-107">Aby wyświetlić granice każdej komórki <xref:System.Windows.Controls.Grid.ShowGridLines%2A> właściwość jest włączona.</span><span class="sxs-lookup"><span data-stu-id="b7957-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b7957-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7957-108">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="b7957-109">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="b7957-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
