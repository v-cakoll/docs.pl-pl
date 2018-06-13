---
title: Jak utworzyć ekspander za pomocą ScrollViewer
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: 6c014d4f6a12bfb58c2ae68f580f632c9478c82f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553065"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="34438-102">Jak utworzyć ekspander za pomocą ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="34438-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="34438-103">W tym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Controls.Expander> formant, który zawiera złożone zawartości, takich jak obraz i tekst.</span><span class="sxs-lookup"><span data-stu-id="34438-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="34438-104">Przykład obejmuje również zawartość <xref:System.Windows.Controls.Expander> w <xref:System.Windows.Controls.ScrollViewer> formantu.</span><span class="sxs-lookup"><span data-stu-id="34438-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34438-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="34438-105">Example</span></span>  
 <span data-ttu-id="34438-106">Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.Expander>.</span><span class="sxs-lookup"><span data-stu-id="34438-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="34438-107">W przykładzie użyto <xref:System.Windows.Controls.Primitives.BulletDecorator> formant, który zawiera obraz i tekst, aby zdefiniować <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span><span class="sxs-lookup"><span data-stu-id="34438-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="34438-108">A <xref:System.Windows.Controls.ScrollViewer> kontroli zapewnia metodę przewijanie zawartości rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="34438-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="34438-109">Należy pamiętać, że w przykładzie <xref:System.Windows.FrameworkElement.Height%2A> właściwość <xref:System.Windows.Controls.ScrollViewer> zamiast na zawartość.</span><span class="sxs-lookup"><span data-stu-id="34438-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="34438-110">Jeśli <xref:System.Windows.FrameworkElement.Height%2A> jest ustawiony dla zawartości, <xref:System.Windows.Controls.ScrollViewer> nie zezwala użytkownikowi na przewijanie zawartości.</span><span class="sxs-lookup"><span data-stu-id="34438-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="34438-111"><xref:System.Windows.FrameworkElement.Width%2A> Właściwość jest ustawiona na <xref:System.Windows.Controls.Expander> kontroli i to ustawienie dotyczy <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i rozszerzonej zawartości.</span><span class="sxs-lookup"><span data-stu-id="34438-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="34438-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34438-112">See Also</span></span>  
 <xref:System.Windows.Controls.Expander>  
 [<span data-ttu-id="34438-113">Ekspander — omówienie</span><span class="sxs-lookup"><span data-stu-id="34438-113">Expander Overview</span></span>](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [<span data-ttu-id="34438-114">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="34438-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
