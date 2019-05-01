---
title: 'Instrukcje: Tworzenie ekspandera za pomocą kontrolki ScrollViewer'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: ef0bc5d344f7d465de9209708430d3e61d40d4f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910796"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="0c8cd-102">Instrukcje: Tworzenie ekspandera za pomocą kontrolki ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="0c8cd-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="0c8cd-103">W tym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Controls.Expander> formant, który zawiera złożone zawartości, takiej jak tekstowych i obrazów.</span><span class="sxs-lookup"><span data-stu-id="0c8cd-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="0c8cd-104">Przykład również umieszcza treść <xref:System.Windows.Controls.Expander> w <xref:System.Windows.Controls.ScrollViewer> kontroli.</span><span class="sxs-lookup"><span data-stu-id="0c8cd-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c8cd-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c8cd-105">Example</span></span>  
 <span data-ttu-id="0c8cd-106">Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.Expander>.</span><span class="sxs-lookup"><span data-stu-id="0c8cd-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="0c8cd-107">W przykładzie użyto <xref:System.Windows.Controls.Primitives.BulletDecorator> formant, który zawiera obraz i tekst, aby zdefiniować <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span><span class="sxs-lookup"><span data-stu-id="0c8cd-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="0c8cd-108">A <xref:System.Windows.Controls.ScrollViewer> kontroli udostępnia metodę przewijanie zawartości rozwinięty.</span><span class="sxs-lookup"><span data-stu-id="0c8cd-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="0c8cd-109">Należy zauważyć, że w przykładzie <xref:System.Windows.FrameworkElement.Height%2A> właściwość <xref:System.Windows.Controls.ScrollViewer> zamiast zawartości.</span><span class="sxs-lookup"><span data-stu-id="0c8cd-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="0c8cd-110">Jeśli <xref:System.Windows.FrameworkElement.Height%2A> jest ustawiony na zawartości, <xref:System.Windows.Controls.ScrollViewer> nie zezwala użytkownikowi na przewijanie zawartości.</span><span class="sxs-lookup"><span data-stu-id="0c8cd-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="0c8cd-111"><xref:System.Windows.FrameworkElement.Width%2A> Właściwość jest ustawiona na <xref:System.Windows.Controls.Expander> kontroli i to ustawienie dotyczy <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> oraz zawartość, rozwinięty.</span><span class="sxs-lookup"><span data-stu-id="0c8cd-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="0c8cd-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c8cd-112">See also</span></span>

- <xref:System.Windows.Controls.Expander>
- [<span data-ttu-id="0c8cd-113">Ekspander — omówienie</span><span class="sxs-lookup"><span data-stu-id="0c8cd-113">Expander Overview</span></span>](expander-overview.md)
- [<span data-ttu-id="0c8cd-114">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="0c8cd-114">How-to Topics</span></span>](expander-how-to-topics.md)
