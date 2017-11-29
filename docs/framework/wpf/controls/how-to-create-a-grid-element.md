---
title: "Jak utworzyć element siatki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd9614aee6e2bf7085b2fbee77993217439320a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="6fca7-102">Jak utworzyć element siatki</span><span class="sxs-lookup"><span data-stu-id="6fca7-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="6fca7-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fca7-103">Example</span></span>  
 <span data-ttu-id="6fca7-104">Poniższy przykład przedstawia sposób tworzenia i używania wystąpienia <xref:System.Windows.Controls.Grid> za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] lub kodu.</span><span class="sxs-lookup"><span data-stu-id="6fca7-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="6fca7-105">W tym przykładzie użyto trzy <xref:System.Windows.Controls.ColumnDefinition> obiektów i trzy <xref:System.Windows.Controls.RowDefinition> obiektów do tworzenia siatki z dziewięciu komórki, taki jak arkusza.</span><span class="sxs-lookup"><span data-stu-id="6fca7-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="6fca7-106">Każda komórka zawiera <xref:System.Windows.Controls.TextBlock> zawiera element, który reprezentuje dane i górnym wierszu <xref:System.Windows.Controls.TextBlock> z <xref:System.Windows.Controls.Grid.ColumnSpan%2A> właściwości stosowane.</span><span class="sxs-lookup"><span data-stu-id="6fca7-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="6fca7-107">Aby wyświetlić granice każdej komórki <xref:System.Windows.Controls.Grid.ShowGridLines%2A> właściwość jest włączona.</span><span class="sxs-lookup"><span data-stu-id="6fca7-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6fca7-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6fca7-108">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="6fca7-109">Omówienie paneli</span><span class="sxs-lookup"><span data-stu-id="6fca7-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
