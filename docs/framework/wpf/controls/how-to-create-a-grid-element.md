---
title: Jak utworzyć element siatki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: b93bb859c4a0df50da2fa00587a28fda3776fd09
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185787"
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="2ca23-102">Jak utworzyć element siatki</span><span class="sxs-lookup"><span data-stu-id="2ca23-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="2ca23-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ca23-103">Example</span></span>  
 <span data-ttu-id="2ca23-104">Poniższy przykład pokazuje, jak utworzyć i używać wystąpienia <xref:System.Windows.Controls.Grid> przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] lub kodu.</span><span class="sxs-lookup"><span data-stu-id="2ca23-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="2ca23-105">W tym przykładzie użyto trzy <xref:System.Windows.Controls.ColumnDefinition> obiektów i trzy <xref:System.Windows.Controls.RowDefinition> obiekty, do tworzenia jest siatka z dziewięciu komórek, takich jak arkusz.</span><span class="sxs-lookup"><span data-stu-id="2ca23-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="2ca23-106">Każda komórka zawiera <xref:System.Windows.Controls.TextBlock> element, który reprezentuje dane i górny wiersz zawiera <xref:System.Windows.Controls.TextBlock> z <xref:System.Windows.Controls.Grid.ColumnSpan%2A> właściwości stosowane.</span><span class="sxs-lookup"><span data-stu-id="2ca23-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="2ca23-107">Aby wyświetlić granice każdej komórki <xref:System.Windows.Controls.Grid.ShowGridLines%2A> właściwość jest włączona.</span><span class="sxs-lookup"><span data-stu-id="2ca23-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
  <span data-ttu-id="2ca23-108">Każda z tych metod, spowoduje wygenerowanie interfejsu użytkownika, który znacznie wygląda tak samo, jak poniżej.</span><span class="sxs-lookup"><span data-stu-id="2ca23-108">Either approach will generate a user interface that looks much the same, like the one below.</span></span>

  ![Zrzut ekranu przedstawia interfejs użytkownika WPF, zawierającą podzielone na trzy kolumny siatki.](./media/how-to-create-a-grid-element/how-to-create-a-grid-element.png)
## <a name="see-also"></a><span data-ttu-id="2ca23-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ca23-112">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="2ca23-113">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="2ca23-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
