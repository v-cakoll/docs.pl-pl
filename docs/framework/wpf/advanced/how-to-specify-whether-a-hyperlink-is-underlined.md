---
title: 'Instrukcje: Określ czy hiperłącze jest podkreślone'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 1968e1b2730f08eb76670a477f1d2bdb0a9140bf
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408707"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a><span data-ttu-id="59f3d-102">Instrukcje: Określ czy hiperłącze jest podkreślone</span><span class="sxs-lookup"><span data-stu-id="59f3d-102">How to: Specify Whether a Hyperlink is Underlined</span></span>
<span data-ttu-id="59f3d-103"><xref:System.Windows.Documents.Hyperlink> Obiekt jest element zawartości śródwierszowy przepływ, który pozwala na hosta hiperlinki w dowolnej zawartości.</span><span class="sxs-lookup"><span data-stu-id="59f3d-103">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="59f3d-104">Domyślnie <xref:System.Windows.Documents.Hyperlink> używa <xref:System.Windows.TextDecoration> obiektu, aby wyświetlić podkreślenie.</span><span class="sxs-lookup"><span data-stu-id="59f3d-104">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="59f3d-105"><xref:System.Windows.TextDecoration> obiekty mogą być intensywnie do utworzenia wystąpienia, wydajność, zwłaszcza, jeśli dostępnych jest wiele <xref:System.Windows.Documents.Hyperlink> obiektów.</span><span class="sxs-lookup"><span data-stu-id="59f3d-105"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="59f3d-106">Jeśli wprowadzisz zwiększone użycie <xref:System.Windows.Documents.Hyperlink> elementów, warto wziąć pod uwagę przedstawiający podkreślenie, tylko wtedy, gdy wyzwalanie zdarzenia, takie jak <xref:System.Windows.ContentElement.MouseEnter> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="59f3d-106">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="59f3d-107">W poniższym przykładzie jest dynamiczny podkreślenie dla linku "Mój MSN", oznacza to, że pojawia się tylko, gdy <xref:System.Windows.ContentElement.MouseEnter> zdarzenie jest wyzwalane.</span><span class="sxs-lookup"><span data-stu-id="59f3d-107">In the following example, the underline for the "My MSN" link is dynamic, that is, it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
  ![Wyświetlanie właściwości TextDecorations hiperłącza](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)  
  
  
## <a name="example"></a><span data-ttu-id="59f3d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="59f3d-109">Example</span></span>  
 <span data-ttu-id="59f3d-110">Ilustruje poniższy przykład kodu znaczników <xref:System.Windows.Documents.Hyperlink> zdefiniowane z lub bez podkreślenie:</span><span class="sxs-lookup"><span data-stu-id="59f3d-110">The following markup sample shows a <xref:System.Windows.Documents.Hyperlink> defined with and without an underline:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 <span data-ttu-id="59f3d-111">Poniższy przykład kodu pokazuje, jak utworzyć podkreślenie dla <xref:System.Windows.Documents.Hyperlink> na <xref:System.Windows.ContentElement.MouseEnter> zdarzenia i usunąć go na <xref:System.Windows.ContentElement.MouseLeave> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="59f3d-111">The following code sample shows how to create an underline for the <xref:System.Windows.Documents.Hyperlink> on the <xref:System.Windows.ContentElement.MouseEnter> event, and remove it on the <xref:System.Windows.ContentElement.MouseLeave> event.</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a><span data-ttu-id="59f3d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59f3d-112">See also</span></span>
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="59f3d-113">Optymalizacja wydajności aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="59f3d-113">Optimizing WPF Application Performance</span></span>](optimizing-wpf-application-performance.md)
- [<span data-ttu-id="59f3d-114">Tworzenie dekoracji tekstu</span><span class="sxs-lookup"><span data-stu-id="59f3d-114">Create a Text Decoration</span></span>](how-to-create-a-text-decoration.md)
