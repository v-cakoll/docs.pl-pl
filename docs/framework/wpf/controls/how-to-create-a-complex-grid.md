---
title: "Jak utworzyć siatkę złożoną"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9dfb913407622f3cbd9a067a94cc6400b501e2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-complex-grid"></a><span data-ttu-id="0df79-102">Jak utworzyć siatkę złożoną</span><span class="sxs-lookup"><span data-stu-id="0df79-102">How to: Create a Complex Grid</span></span>
<span data-ttu-id="0df79-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.Grid> do tworzenia układu, która wygląda jak kalendarza miesięcznego.</span><span class="sxs-lookup"><span data-stu-id="0df79-103">This example shows how to use a <xref:System.Windows.Controls.Grid> to create layout that looks like a monthly calendar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0df79-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0df79-104">Example</span></span>  
 <span data-ttu-id="0df79-105">W poniższym przykładzie zdefiniowano osiem wierszy i kolumn osiem przy użyciu <xref:System.Windows.Controls.RowDefinition> i <xref:System.Windows.Controls.ColumnDefinition> klasy.</span><span class="sxs-lookup"><span data-stu-id="0df79-105">The following example defines eight rows and eight columns by using the <xref:System.Windows.Controls.RowDefinition> and <xref:System.Windows.Controls.ColumnDefinition> classes.</span></span> <span data-ttu-id="0df79-106">Używa <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> dołączone właściwości, wraz z <xref:System.Windows.Shapes.Rectangle> elementów, które wypełnienia tła różnych kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="0df79-106">It uses the <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> attached properties, together with <xref:System.Windows.Shapes.Rectangle> elements, which fill the backgrounds of various columns and rows.</span></span> <span data-ttu-id="0df79-107">Ten projekt jest możliwa, ponieważ w każdej komórki w może istnieć więcej niż jeden element <xref:System.Windows.Controls.Grid>, zasady różnicę między <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Documents.Table>.</span><span class="sxs-lookup"><span data-stu-id="0df79-107">This design is possible because more than one element can exist in each cell in a <xref:System.Windows.Controls.Grid>, a principle difference between <xref:System.Windows.Controls.Grid> and <xref:System.Windows.Documents.Table>.</span></span>  
  
 <span data-ttu-id="0df79-108">W przykładzie użyto pionowy gradientów do <xref:System.Windows.Shapes.Shape.Fill%2A> kolumn i wierszy w celu ulepszania wizualną prezentację i czytelność kalendarza.</span><span class="sxs-lookup"><span data-stu-id="0df79-108">The example uses vertical gradients to <xref:System.Windows.Shapes.Shape.Fill%2A> the columns and rows in order to improve the visual presentation and readability of the calendar.</span></span> <span data-ttu-id="0df79-109">Styl <xref:System.Windows.Controls.TextBlock> elementy reprezentują dat i dni tygodnia.</span><span class="sxs-lookup"><span data-stu-id="0df79-109">Styled <xref:System.Windows.Controls.TextBlock> elements represent the dates and days of the week.</span></span> <span data-ttu-id="0df79-110"><xref:System.Windows.Controls.TextBlock>elementy są bezwzględnego w komórkach ich przy użyciu <xref:System.Windows.FrameworkElement.Margin%2A> właściwości i wyrównanie właściwości, które są zdefiniowane w stylu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0df79-110"><xref:System.Windows.Controls.TextBlock> elements are absolutely positioned within their cells by using the <xref:System.Windows.FrameworkElement.Margin%2A> property and alignment properties that are defined within the style for the application.</span></span>  
  
 [!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0df79-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0df79-111">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Documents.TableCell>  
 [<span data-ttu-id="0df79-112">Malowanie jednolitymi kolorami i gradientami — przegląd</span><span class="sxs-lookup"><span data-stu-id="0df79-112">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="0df79-113">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="0df79-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="0df79-114">Przegląd tabeli</span><span class="sxs-lookup"><span data-stu-id="0df79-114">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
