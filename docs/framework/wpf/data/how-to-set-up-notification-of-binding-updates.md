---
title: "Jak ustawić powiadomienie o łączeniu aktualizacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a07337e99e985bfbc0a5dbc5f2d231ee36cf1422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-up-notification-of-binding-updates"></a><span data-ttu-id="99f98-102">Jak ustawić powiadomienie o łączeniu aktualizacji</span><span class="sxs-lookup"><span data-stu-id="99f98-102">How to: Set Up Notification of Binding Updates</span></span>
<span data-ttu-id="99f98-103">W tym przykładzie pokazano, jak można skonfigurować, aby otrzymać powiadomienie, gdy cel wiązania (docelowy) lub powiązanie właściwości source (źródło) powiązania został zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="99f98-103">This example shows how to set up to be notified when the binding target (target) or the binding source (source) property of a binding has been updated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99f98-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="99f98-104">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="99f98-105">zgłasza zdarzenie aktualizacji danych zawsze o zaktualizowaniu powiązanie źródłowa lub docelowa.</span><span class="sxs-lookup"><span data-stu-id="99f98-105"> raises a data update event each time that the binding source or target has been updated.</span></span> <span data-ttu-id="99f98-106">To zdarzenie jest używana wewnętrznie, informują o tym [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] którego on należy zaktualizować, ponieważ zmienił się powiązana z danymi.</span><span class="sxs-lookup"><span data-stu-id="99f98-106">Internally, this event is used to inform the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] that it should update, because the bound data has changed.</span></span> <span data-ttu-id="99f98-107">Należy pamiętać, że te zdarzenia do pracy, a także do- lub dwukierunkowo powiązanie działało poprawnie, musisz wdrożyć swoją danych klasy przy użyciu <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="99f98-107">Note that for these events to work, and also for one-way or two-way binding to work properly, you need to implement your data class using the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="99f98-108">Aby uzyskać więcej informacji, zobacz [powiadomienia o zmianie właściwości wdrożenie](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="99f98-108">For more information, see [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
 <span data-ttu-id="99f98-109">Ustaw <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> lub <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> właściwości (lub obie) do `true` w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="99f98-109">Set the <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> or <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> property (or both) to `true` in the binding.</span></span> <span data-ttu-id="99f98-110">Program obsługi podane przez użytkownika do nasłuchiwania dla tego zdarzenia musi być dołączony bezpośrednio do elementu, w którym ma być powiadamiane o zmianach lub ogólną kontekst danych Aby Pamiętaj, że w kontekście została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="99f98-110">The handler you provide to listen for this event must be attached directly to the element where you want to be informed of changes, or to the overall data context if you want to be aware that anything in the context has changed.</span></span>  
  
 <span data-ttu-id="99f98-111">Oto przykład pokazujący sposób skonfigurować powiadomienia, gdy właściwość docelowa została zaktualizowana.</span><span class="sxs-lookup"><span data-stu-id="99f98-111">Here is an example that shows how to set up for notification when a target property has been updated.</span></span>  
  
 [!code-xaml[DirectionalBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="99f98-112">Następnie można przypisać obsługi oparte na EventHandler\<T > delegować, *OnTargetUpdated* w tym przykładzie Obsługa zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="99f98-112">You can then assign a handler based on the EventHandler\<T> delegate, *OnTargetUpdated* in this example, to handle the event:</span></span>  
  
 [!code-csharp[DirectionalBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 <span data-ttu-id="99f98-113">Parametry zdarzenia może służyć do określenia szczegółowe informacje o właściwości zmianie (na przykład typ lub konkretny element w przypadku tej procedury obsługi jest podłączony do więcej niż jeden element), które mogą być przydatne, jeśli istnieje wiele właściwości powiązanej na pojedynczy element.</span><span class="sxs-lookup"><span data-stu-id="99f98-113">Parameters of the event can be used to determine details about the property that changed (such as the type or the specific element if the same handler is attached to more than one element), which can be useful if there are multiple bound properties on a single element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99f98-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99f98-114">See Also</span></span>  
 [<span data-ttu-id="99f98-115">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="99f98-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="99f98-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="99f98-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
