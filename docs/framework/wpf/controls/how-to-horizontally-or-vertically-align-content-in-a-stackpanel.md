---
title: Jak wyrównać w poziomie lub w pionie zawartość w StackPanel
description: Dowiedz się, jak dostosować orientację zawartości w Windows Presentation Foundation StackPanel i HorizontalAlignment i VerticalAlignment zawartości podrzędnej.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: d3c7215d8193d1d8a72597c44cf265f5bd400ea1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167629"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a><span data-ttu-id="5104d-103">Jak wyrównać w poziomie lub w pionie zawartość w StackPanel</span><span class="sxs-lookup"><span data-stu-id="5104d-103">How to: Horizontally or Vertically Align Content in a StackPanel</span></span>
<span data-ttu-id="5104d-104">Ten przykład pokazuje, jak dostosować <xref:System.Windows.Controls.StackPanel.Orientation%2A> zawartość w obrębie <xref:System.Windows.Controls.StackPanel> elementu, a także dostosować <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> zawartość elementu <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5104d-104">This example shows how to adjust the <xref:System.Windows.Controls.StackPanel.Orientation%2A> of content within a <xref:System.Windows.Controls.StackPanel> element, and also how to adjust the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> of child content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5104d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="5104d-105">Example</span></span>  
 <span data-ttu-id="5104d-106">Poniższy przykład tworzy trzy <xref:System.Windows.Controls.ListBox> elementy w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5104d-106">The following example creates three <xref:System.Windows.Controls.ListBox> elements in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="5104d-107">Każdy <xref:System.Windows.Controls.ListBox> reprezentuje możliwe wartości <xref:System.Windows.Controls.StackPanel.Orientation%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości,, i <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.Controls.StackPanel> .</span><span class="sxs-lookup"><span data-stu-id="5104d-107">Each <xref:System.Windows.Controls.ListBox> represents the possible values of the <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> properties of a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="5104d-108">Gdy użytkownik wybierze wartość w którymkolwiek z <xref:System.Windows.Controls.ListBox> elementów, skojarzona właściwość <xref:System.Windows.Controls.StackPanel> i jego <xref:System.Windows.Controls.Button> elementy podrzędne zmienią się.</span><span class="sxs-lookup"><span data-stu-id="5104d-108">When a user selects a value in any of the <xref:System.Windows.Controls.ListBox> elements, the associated property of the <xref:System.Windows.Controls.StackPanel> and its child <xref:System.Windows.Controls.Button> elements change.</span></span>  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="5104d-109">Następujący plik związany z kodem definiuje zmiany w zdarzeniach, które są skojarzone z <xref:System.Windows.Controls.ListBox> zmianą zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="5104d-109">The following code-behind file defines the changes to the events that are associated with the <xref:System.Windows.Controls.ListBox> selection changes.</span></span> <span data-ttu-id="5104d-110"><xref:System.Windows.Controls.StackPanel>jest identyfikowany przez <xref:System.Windows.FrameworkElement.Name%2A> `sp1` .</span><span class="sxs-lookup"><span data-stu-id="5104d-110"><xref:System.Windows.Controls.StackPanel> is identified by the <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span></span>  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5104d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5104d-111">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [<span data-ttu-id="5104d-112">Przegląd Panele</span><span class="sxs-lookup"><span data-stu-id="5104d-112">Panels Overview</span></span>](panels-overview.md)
