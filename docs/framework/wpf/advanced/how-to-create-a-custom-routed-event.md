---
title: "Jak utworzyć niestandardowe zdarzenie trasowane"
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
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecd335cb08056cb8b7c696555d666f54cad81b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-routed-event"></a><span data-ttu-id="ea8fb-102">Jak utworzyć niestandardowe zdarzenie trasowane</span><span class="sxs-lookup"><span data-stu-id="ea8fb-102">How to: Create a Custom Routed Event</span></span>
<span data-ttu-id="ea8fb-103">Niestandardowe zdarzenie w celu obsługi zdarzeń routingu, należy zarejestrować <xref:System.Windows.RoutedEvent> przy użyciu <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ea8fb-103">For your custom event to support event routing, you need to register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="ea8fb-104">W tym przykładzie pokazano tworzenie niestandardowych kierowanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ea8fb-104">This example demonstrates the basics of creating a custom routed event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea8fb-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea8fb-105">Example</span></span>  
 <span data-ttu-id="ea8fb-106">Jak pokazano w poniższym przykładzie, musisz najpierw zarejestrować <xref:System.Windows.RoutedEvent> przy użyciu <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ea8fb-106">As shown in the following example, you first register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="ea8fb-107">Według konwencji <xref:System.Windows.RoutedEvent> Nazwa pola statyczne powinny kończyć się sufiksem ***zdarzeń***.</span><span class="sxs-lookup"><span data-stu-id="ea8fb-107">By convention, the <xref:System.Windows.RoutedEvent> static field name should end with the suffix ***Event***.</span></span> <span data-ttu-id="ea8fb-108">W tym przykładzie nazwa zdarzenia jest `Tap` i strategii routingu zdarzenia jest <xref:System.Windows.RoutingStrategy.Bubble>.</span><span class="sxs-lookup"><span data-stu-id="ea8fb-108">In this example, the name of the event is `Tap` and the routing strategy of the event is <xref:System.Windows.RoutingStrategy.Bubble>.</span></span> <span data-ttu-id="ea8fb-109">Po wywołaniu metody rejestracji, możesz podać dodawania i usuwania [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] metod dostępu zdarzeń dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ea8fb-109">After the registration call, you can provide add-and-remove [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event accessors for the event.</span></span>  
  
 <span data-ttu-id="ea8fb-110">Należy pamiętać, że mimo, że zdarzenie jest wywoływane za pośrednictwem `OnTap` wirtualnej metody w tym przykładzie, jak wywołać zdarzenie lub sposób odpowiadania przez zdarzenie zmiany zależy od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="ea8fb-110">Note that even though the event is raised through the `OnTap` virtual method in this particular example, how you raise your event or how your event responds to changes depends on your needs.</span></span>  
  
 <span data-ttu-id="ea8fb-111">Należy też zauważyć, że w tym przykładzie zasadniczo implementuje całą podklasą klasy <xref:System.Windows.Controls.Button>; jest następnie utworzyć jako niestandardowej klasy na osobnym i utworzone jako osobny zestaw tego podklasy [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strony.</span><span class="sxs-lookup"><span data-stu-id="ea8fb-111">Note also that this example basically implements an entire subclass of <xref:System.Windows.Controls.Button>; that subclass is built as a separate assembly and then instantiated as a custom class on a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="ea8fb-112">Jest to w celu zilustrowania koncepcji, czy formanty będące podklasami można wstawiać do drzewa zawierający inne kontrolki, i czy w takiej sytuacji zdarzenia niestandardowe tych kontrolek mają bardzo takie same możliwości routingu zdarzeń jako dowolny native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest element.</span><span class="sxs-lookup"><span data-stu-id="ea8fb-112">This is to illustrate the concept that subclassed controls can be inserted into trees composed of other controls, and that in this situation, custom events on these controls have the very same event routing capabilities as any native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] element does.</span></span>  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 <span data-ttu-id="ea8fb-113">Tunelowania powstają zdarzenia taki sam sposób, ale z <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> ustawioną <xref:System.Windows.RoutingStrategy.Tunnel> w wywołaniu rejestracji.</span><span class="sxs-lookup"><span data-stu-id="ea8fb-113">Tunneling events are created the same way, but with <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> set to <xref:System.Windows.RoutingStrategy.Tunnel> in the registration call.</span></span> <span data-ttu-id="ea8fb-114">Według Konwencji tunelowania zdarzeń w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są poprzedzane prefiksem słowo "W wersji zapoznawczej".</span><span class="sxs-lookup"><span data-stu-id="ea8fb-114">By convention, tunneling events in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] are prefixed with the word "Preview".</span></span>  
  
 <span data-ttu-id="ea8fb-115">Aby zapoznać się przykładem sposobu propagacji pracy zdarzeń, zobacz [obsługi zdarzenia rozsyłane](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).</span><span class="sxs-lookup"><span data-stu-id="ea8fb-115">To see an example of how bubbling events work, see [Handle a Routed Event](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea8fb-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea8fb-116">See Also</span></span>  
 [<span data-ttu-id="ea8fb-117">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="ea8fb-117">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="ea8fb-118">Przegląd danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="ea8fb-118">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="ea8fb-119">Tworzenie kontrolek — omówienie</span><span class="sxs-lookup"><span data-stu-id="ea8fb-119">Control Authoring Overview</span></span>](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
