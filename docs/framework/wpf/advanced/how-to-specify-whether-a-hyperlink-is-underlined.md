---
title: "Jak określić czy hiperłącze jest podkreślone"
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
helpviewer_keywords: Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7914b3b3332b7ea0abe05b3048b5016888e2d93e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a><span data-ttu-id="0a93a-102">Jak określić czy hiperłącze jest podkreślone</span><span class="sxs-lookup"><span data-stu-id="0a93a-102">How to: Specify Whether a Hyperlink is Underlined</span></span>
<span data-ttu-id="0a93a-103"><xref:System.Windows.Documents.Hyperlink> Obiekt jest element zawartości śródwierszowy przepływu, który umożliwia hiperłącza hosta w zawartości przepływu.</span><span class="sxs-lookup"><span data-stu-id="0a93a-103">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="0a93a-104">Domyślnie <xref:System.Windows.Documents.Hyperlink> używa <xref:System.Windows.TextDecoration> obiektu do wyświetlenia podkreślenie.</span><span class="sxs-lookup"><span data-stu-id="0a93a-104">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="0a93a-105"><xref:System.Windows.TextDecoration>obiekty mogą być znacznym można utworzyć wystąpienia, wydajność, szczególnie w przypadku wielu <xref:System.Windows.Documents.Hyperlink> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0a93a-105"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="0a93a-106">Jeśli wprowadzisz zwiększone użycie <xref:System.Windows.Documents.Hyperlink> elementów, warto rozważyć przedstawiający podkreślenie tylko wtedy, gdy wyzwolenie zdarzenia, takie jak <xref:System.Windows.ContentElement.MouseEnter> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0a93a-106">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="0a93a-107">W poniższym przykładzie jest dynamiczny podkreślenia łącza "Mój MSN" — tylko wygląda na to, kiedy <xref:System.Windows.ContentElement.MouseEnter> zdarzenie zostanie wyzwolone.</span><span class="sxs-lookup"><span data-stu-id="0a93a-107">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="0a93a-108">![Wyświetlanie właściwości TextDecorations hiperłącza](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="0a93a-108">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="0a93a-109">Zdefiniowane za pomocą właściwości TextDecorations hiperłącza</span><span class="sxs-lookup"><span data-stu-id="0a93a-109">Hyperlinks defined with TextDecorations</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a93a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a93a-110">Example</span></span>  
 <span data-ttu-id="0a93a-111">Poniżej przedstawiono przykładowy kod znaczników <xref:System.Windows.Documents.Hyperlink> zdefiniowane z włączonymi i wyłączonymi podkreślenie:</span><span class="sxs-lookup"><span data-stu-id="0a93a-111">The following markup sample shows a <xref:System.Windows.Documents.Hyperlink> defined with and without an underline:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 <span data-ttu-id="0a93a-112">Poniższy przykładowy kod przedstawia sposób tworzenia podkreślenie dla <xref:System.Windows.Documents.Hyperlink> na <xref:System.Windows.ContentElement.MouseEnter> zdarzenia i usunąć go na <xref:System.Windows.ContentElement.MouseLeave> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0a93a-112">The following code sample shows how to create an underline for the <xref:System.Windows.Documents.Hyperlink> on the <xref:System.Windows.ContentElement.MouseEnter> event, and remove it on the <xref:System.Windows.ContentElement.MouseLeave> event.</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a><span data-ttu-id="0a93a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a93a-113">See Also</span></span>  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [<span data-ttu-id="0a93a-114">Optymalizacja wydajności aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="0a93a-114">Optimizing WPF Application Performance</span></span>](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [<span data-ttu-id="0a93a-115">Tworzenie dekoracji tekstu</span><span class="sxs-lookup"><span data-stu-id="0a93a-115">Create a Text Decoration</span></span>](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)
