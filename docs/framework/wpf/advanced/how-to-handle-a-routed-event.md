---
title: "Jak obsłużyć zdarzenie trasowane"
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
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c491ff4e231d932b3714d2d059b52bad2502368c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-a-routed-event"></a><span data-ttu-id="6607a-102">Jak obsłużyć zdarzenie trasowane</span><span class="sxs-lookup"><span data-stu-id="6607a-102">How to: Handle a Routed Event</span></span>
<span data-ttu-id="6607a-103">Ten przykład przedstawia sposób propagacji pracy zdarzenia i jak napisać programu obsługi, który może przetwarzać danych kierowanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6607a-103">This example shows how bubbling events work and how to write a handler that can process the routed event data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6607a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6607a-104">Example</span></span>  
 <span data-ttu-id="6607a-105">W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elementy są rozmieszczane w strukturze drzewa elementu.</span><span class="sxs-lookup"><span data-stu-id="6607a-105">In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elements are arranged in an element tree structure.</span></span> <span data-ttu-id="6607a-106">Element nadrzędny mogą uczestniczyć w obsłudze zdarzeń, które są początkowo zgłoszony przez elementy podrzędne w drzewie elementu.</span><span class="sxs-lookup"><span data-stu-id="6607a-106">The parent element can participate in the handling of events that are initially raised by child elements in the element tree.</span></span> <span data-ttu-id="6607a-107">Jest to możliwe z powodu zdarzenia routingu.</span><span class="sxs-lookup"><span data-stu-id="6607a-107">This is possible because of event routing.</span></span>  
  
 <span data-ttu-id="6607a-108">Zazwyczaj kierowane zdarzenia wykonaj jedną z dwóch strategii routingu propagacji lub tunelowania.</span><span class="sxs-lookup"><span data-stu-id="6607a-108">Routed events typically follow one of two routing strategies, bubbling or tunneling.</span></span> <span data-ttu-id="6607a-109">W tym przykładzie koncentruje się na zdarzeń propagacji i używa <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> zdarzeń do wyświetlenia działa jak routingu.</span><span class="sxs-lookup"><span data-stu-id="6607a-109">This example focuses on the bubbling event and uses the <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> event to show how routing works.</span></span>  
  
 <span data-ttu-id="6607a-110">Poniższy przykład tworzy dwa <xref:System.Windows.Controls.Button> formanty i używa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu dołączania program obsługi zdarzeń do wspólnego elementu nadrzędnego, który w tym przykładzie jest <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="6607a-110">The following example creates two <xref:System.Windows.Controls.Button> controls and uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax to attach an event handler to a common parent element, which in this example is <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="6607a-111">Zamiast dołączanie obsługi poszczególnych zdarzeń dla każdego <xref:System.Windows.Controls.Button> elementu podrzędnego w przykładzie użyto Składnia atrybutu można dołączyć do programu obsługi zdarzeń <xref:System.Windows.Controls.StackPanel> elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="6607a-111">Instead of attaching individual event handlers for each <xref:System.Windows.Controls.Button> child element, the example uses attribute syntax to attach the event handler to the <xref:System.Windows.Controls.StackPanel> parent element.</span></span> <span data-ttu-id="6607a-112">Ten wzorzec obsługi zdarzeń pokazano, jak używać zdarzeń routingu jako technika zmniejszenie liczby elementów, którego program obsługi jest podłączony.</span><span class="sxs-lookup"><span data-stu-id="6607a-112">This event-handling pattern shows how to use event routing as a technique for reducing the number of elements where a handler is attached.</span></span> <span data-ttu-id="6607a-113">Wszystkie zdarzenia propagacji dla każdego <xref:System.Windows.Controls.Button> Rozsyłanie za pomocą elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="6607a-113">All the bubbling events for each <xref:System.Windows.Controls.Button> route through the parent element.</span></span>  
  
 <span data-ttu-id="6607a-114">Należy pamiętać, że w nadrzędnej <xref:System.Windows.Controls.StackPanel> elementu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Nazwa zdarzenia określony jako atrybut częściowo jest kwalifikowany za pomocą nazw <xref:System.Windows.Controls.Button> klasy.</span><span class="sxs-lookup"><span data-stu-id="6607a-114">Note that on the parent <xref:System.Windows.Controls.StackPanel> element, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event name specified as the attribute is partially qualified by naming the <xref:System.Windows.Controls.Button> class.</span></span> <span data-ttu-id="6607a-115"><xref:System.Windows.Controls.Button> Jest klasa <xref:System.Windows.Controls.Primitives.ButtonBase> klasy, która ma <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia w jego elementów członkowskich wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="6607a-115">The <xref:System.Windows.Controls.Button> class is a <xref:System.Windows.Controls.Primitives.ButtonBase> derived class that has the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in its members listing.</span></span> <span data-ttu-id="6607a-116">Ta technika częściowe kwalifikacji dołączanie program obsługi zdarzeń jest niezbędne, jeśli nie istnieje zdarzenie, które jest obsługiwane w elementach członkowskich wyświetlania elementu, w którym jest umocowana Obsługa kierowanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6607a-116">This partial qualification technique for attaching an event handler is necessary if the event that is being handled does not exist in the members listing of the element where the routed event handler is attached.</span></span>  
  
 [!code-xaml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 <span data-ttu-id="6607a-117">Następujący przykład uchwytów <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6607a-117">The following example handles the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  <span data-ttu-id="6607a-118">Przykład raporty element, który obsługuje zdarzenie i który element wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="6607a-118">The example reports which element handles the event and which element raises the event.</span></span> <span data-ttu-id="6607a-119">Program obsługi zdarzeń jest wykonywany, gdy użytkownik kliknie przycisk albo.</span><span class="sxs-lookup"><span data-stu-id="6607a-119">The event handler is executed when the user clicks either button.</span></span>  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="6607a-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6607a-120">See Also</span></span>  
 <xref:System.Windows.RoutedEvent>  
 [<span data-ttu-id="6607a-121">Przegląd danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="6607a-121">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="6607a-122">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="6607a-122">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="6607a-123">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="6607a-123">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)  
 [<span data-ttu-id="6607a-124">Szczegóły składni XAML</span><span class="sxs-lookup"><span data-stu-id="6607a-124">XAML Syntax In Detail</span></span>](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
