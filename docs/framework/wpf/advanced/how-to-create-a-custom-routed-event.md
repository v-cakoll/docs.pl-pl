---
title: 'Instrukcje: Tworzenie niestandardowego zdarzenia trasowanego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: a3850875c8ca747f8709b55f8fe721d25be24304
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776691"
---
# <a name="how-to-create-a-custom-routed-event"></a><span data-ttu-id="819be-102">Instrukcje: Tworzenie niestandardowego zdarzenia trasowanego</span><span class="sxs-lookup"><span data-stu-id="819be-102">How to: Create a Custom Routed Event</span></span>
<span data-ttu-id="819be-103">Do zdarzenia niestandardowe do obsługi routingu zdarzeń, należy zarejestrować <xref:System.Windows.RoutedEvent> przy użyciu <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="819be-103">For your custom event to support event routing, you need to register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="819be-104">W tym przykładzie pokazano tworzenie niestandardowe zdarzenie trasowane.</span><span class="sxs-lookup"><span data-stu-id="819be-104">This example demonstrates the basics of creating a custom routed event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="819be-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="819be-105">Example</span></span>  
 <span data-ttu-id="819be-106">Jak pokazano w poniższym przykładzie, należy najpierw zarejestrować <xref:System.Windows.RoutedEvent> przy użyciu <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="819be-106">As shown in the following example, you first register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="819be-107">Zgodnie z Konwencją <xref:System.Windows.RoutedEvent> nazwę pola statyczne powinny kończyć się sufiksem ***zdarzeń***.</span><span class="sxs-lookup"><span data-stu-id="819be-107">By convention, the <xref:System.Windows.RoutedEvent> static field name should end with the suffix ***Event***.</span></span> <span data-ttu-id="819be-108">W tym przykładzie nazwa zdarzenia jest `Tap` i strategii routingu zdarzenia <xref:System.Windows.RoutingStrategy.Bubble>.</span><span class="sxs-lookup"><span data-stu-id="819be-108">In this example, the name of the event is `Tap` and the routing strategy of the event is <xref:System.Windows.RoutingStrategy.Bubble>.</span></span> <span data-ttu-id="819be-109">Po wywołaniu rejestracji umożliwia dodawanie i usuwanie [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] metod dostępu zdarzeń dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="819be-109">After the registration call, you can provide add-and-remove [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event accessors for the event.</span></span>  
  
 <span data-ttu-id="819be-110">Należy pamiętać, że nawet jeśli zdarzenie jest wywoływane za pośrednictwem `OnTap` metodę wirtualną, w tym przykładzie, jak zgłaszać zdarzenia lub sposób reagowania zdarzenia zmiany zależy od Twoich potrzeb.</span><span class="sxs-lookup"><span data-stu-id="819be-110">Note that even though the event is raised through the `OnTap` virtual method in this particular example, how you raise your event or how your event responds to changes depends on your needs.</span></span>  
  
 <span data-ttu-id="819be-111">Należy zauważyć, że w tym przykładzie po prostu implementuje całą podklasą <xref:System.Windows.Controls.Button>; tej podklasy jest kompilowany jako osobny zestaw, a następnie uruchomiony jako niestandardowej klasy na oddzielnym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strony.</span><span class="sxs-lookup"><span data-stu-id="819be-111">Note also that this example basically implements an entire subclass of <xref:System.Windows.Controls.Button>; that subclass is built as a separate assembly and then instantiated as a custom class on a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="819be-112">Ma to na celu zilustrowania koncepcji, że formanty będące podklasami mogą być wstawiane do drzewa zawierający inne formanty, i że w takiej sytuacji zdarzenia niestandardowe tych kontrolek mają bardzo te same możliwości routingu zdarzeń wszelkie native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest element.</span><span class="sxs-lookup"><span data-stu-id="819be-112">This is to illustrate the concept that subclassed controls can be inserted into trees composed of other controls, and that in this situation, custom events on these controls have the very same event routing capabilities as any native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] element does.</span></span>  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 <span data-ttu-id="819be-113">Tunelowania powstają zdarzenia taki sam sposób, ale z <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> równa <xref:System.Windows.RoutingStrategy.Tunnel> w wywołaniu rejestracji.</span><span class="sxs-lookup"><span data-stu-id="819be-113">Tunneling events are created the same way, but with <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> set to <xref:System.Windows.RoutingStrategy.Tunnel> in the registration call.</span></span> <span data-ttu-id="819be-114">Zgodnie z Konwencją, tunelowanie zdarzeń w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są poprzedzone wyrazem "Podgląd".</span><span class="sxs-lookup"><span data-stu-id="819be-114">By convention, tunneling events in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] are prefixed with the word "Preview".</span></span>  
  
 <span data-ttu-id="819be-115">Aby zobaczyć przykład sposobu propagacji pracy zdarzeń, zobacz [obsłużyć zdarzenie kierowane](how-to-handle-a-routed-event.md).</span><span class="sxs-lookup"><span data-stu-id="819be-115">To see an example of how bubbling events work, see [Handle a Routed Event](how-to-handle-a-routed-event.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="819be-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="819be-116">See also</span></span>

- [<span data-ttu-id="819be-117">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="819be-117">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="819be-118">Przegląd danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="819be-118">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="819be-119">Tworzenie kontrolek — omówienie</span><span class="sxs-lookup"><span data-stu-id="819be-119">Control Authoring Overview</span></span>](../controls/control-authoring-overview.md)
