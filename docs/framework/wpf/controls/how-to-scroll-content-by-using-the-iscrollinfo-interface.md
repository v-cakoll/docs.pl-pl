---
title: 'Instrukcje: Przewijanie zawartości przy użyciu interfejsu IScrollInfo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 6ebd8268e1358b45709885c07e6b096d5f806ebb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098549"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a><span data-ttu-id="a7849-102">Instrukcje: Przewijanie zawartości przy użyciu interfejsu IScrollInfo</span><span class="sxs-lookup"><span data-stu-id="a7849-102">How to: Scroll Content by Using the IScrollInfo Interface</span></span>
<span data-ttu-id="a7849-103">W tym przykładzie pokazano, jak przewijać zawartość przy użyciu <xref:System.Windows.Controls.Primitives.IScrollInfo> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a7849-103">This example shows how to scroll content by using the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7849-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7849-104">Example</span></span>  
 <span data-ttu-id="a7849-105">W poniższym przykładzie pokazano funkcje <xref:System.Windows.Controls.Primitives.IScrollInfo> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a7849-105">The following example demonstrates the features of the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span> <span data-ttu-id="a7849-106">W przykładzie jest tworzony <xref:System.Windows.Controls.StackPanel> element [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] zagnieżdżony w obiekcie nadrzędnym <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="a7849-106">The example creates a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that is nested in a parent <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="a7849-107">Elementy podrzędne <xref:System.Windows.Controls.StackPanel> mogą być przewijane logicznie za pomocą metod zdefiniowanych przez <xref:System.Windows.Controls.Primitives.IScrollInfo> interfejsu i Rzutowanie na wystąpienie <xref:System.Windows.Controls.StackPanel> (`sp1`) w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a7849-107">The child elements of the <xref:System.Windows.Controls.StackPanel> can be scrolled logically by using the methods defined by the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface and cast to the instance of <xref:System.Windows.Controls.StackPanel> (`sp1`) in code.</span></span>  
  
 [!code-xaml[IScrollInfoMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="a7849-108">Każdy <xref:System.Windows.Controls.Button> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku wyzwala skojarzone niestandardową metodę, która kontroluje zachowanie przewijania w <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="a7849-108">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file triggers an associated custom method that controls scrolling behavior in <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="a7849-109">Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> i <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> metod; również ogólną pokazuje sposób użycia metody pozycjonowania, <xref:System.Windows.Controls.Primitives.IScrollInfo> klasa definiuje.</span><span class="sxs-lookup"><span data-stu-id="a7849-109">The following example shows how to use the <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> and <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> methods; it also generically shows how to use all the positioning methods that the <xref:System.Windows.Controls.Primitives.IScrollInfo> class defines.</span></span>  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a7849-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7849-110">See also</span></span>

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- <xref:System.Windows.Controls.StackPanel>
- [<span data-ttu-id="a7849-111">ScrollViewer — Przegląd</span><span class="sxs-lookup"><span data-stu-id="a7849-111">ScrollViewer Overview</span></span>](scrollviewer-overview.md)
- [<span data-ttu-id="a7849-112">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="a7849-112">How-to Topics</span></span>](scrollviewer-how-to-topics.md)
- [<span data-ttu-id="a7849-113">Przegląd Panele</span><span class="sxs-lookup"><span data-stu-id="a7849-113">Panels Overview</span></span>](panels-overview.md)
