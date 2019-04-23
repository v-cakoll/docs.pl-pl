---
title: 'Instrukcje: Używanie metod przewijania zawartości ScrollViewer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
ms.openlocfilehash: e81c63de16d09de8435d5ec49a013bf8dc5927cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142158"
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a><span data-ttu-id="519d7-102">Instrukcje: Używanie metod przewijania zawartości ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="519d7-102">How to: Use the Content-Scrolling Methods of ScrollViewer</span></span>
<span data-ttu-id="519d7-103">W tym przykładzie pokazano, jak używać metody przewijania <xref:System.Windows.Controls.ScrollViewer> elementu.</span><span class="sxs-lookup"><span data-stu-id="519d7-103">This example shows how to use the scrolling methods of the <xref:System.Windows.Controls.ScrollViewer> element.</span></span> <span data-ttu-id="519d7-104">Metody te zapewniają przyrostowe przewijanie zawartości przy użyciu wiersza lub przez stronę, <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="519d7-104">These methods provide incremental scrolling of content, either by line or by page, in a <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="519d7-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="519d7-105">Example</span></span>  
 <span data-ttu-id="519d7-106">Poniższy przykład tworzy <xref:System.Windows.Controls.ScrollViewer> o nazwie `sv1`, która hostuje element podrzędny <xref:System.Windows.Controls.TextBlock> elementu.</span><span class="sxs-lookup"><span data-stu-id="519d7-106">The following example creates a <xref:System.Windows.Controls.ScrollViewer> named `sv1`, which hosts a child <xref:System.Windows.Controls.TextBlock> element.</span></span> <span data-ttu-id="519d7-107">Ponieważ <xref:System.Windows.Controls.TextBlock> jest większy niż element nadrzędny <xref:System.Windows.Controls.ScrollViewer>, paski przewijania są wyświetlane w celu umożliwienia przewijania.</span><span class="sxs-lookup"><span data-stu-id="519d7-107">Because the <xref:System.Windows.Controls.TextBlock> is larger than the parent <xref:System.Windows.Controls.ScrollViewer>, scroll bars appear in order to enable scrolling.</span></span> <span data-ttu-id="519d7-108"><xref:System.Windows.Controls.Button> elementy, które reprezentują różne metody przewijania są zadokowane po lewej stronie w osobnym <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="519d7-108"><xref:System.Windows.Controls.Button> elements that represent the various scrolling methods are docked on the left in a separate <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="519d7-109">Każdy <xref:System.Windows.Controls.Button> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku wywołuje powiązanej metody niestandardowego, który kontroluje zachowanie przewijania w <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="519d7-109">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file calls a related custom method that controls scrolling behavior in <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
 [!code-xaml[ScrollViewerMethods#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="519d7-110">W poniższym przykładzie użyto <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> i <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="519d7-110">The following example uses the <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> and <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> methods.</span></span>  
  
 [!code-csharp[ScrollViewerMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="519d7-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="519d7-111">See also</span></span>

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.StackPanel>
