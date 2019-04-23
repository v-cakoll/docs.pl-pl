---
title: 'Instrukcje: Konfigurowanie powiadomienia o aktualizacji powiązań'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: 4185198312ed98f9aaa1388626600d9f21abae55
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213965"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a><span data-ttu-id="19fe3-102">Instrukcje: Konfigurowanie powiadomienia o aktualizacji powiązań</span><span class="sxs-lookup"><span data-stu-id="19fe3-102">How to: Set Up Notification of Binding Updates</span></span>
<span data-ttu-id="19fe3-103">Ten przykład pokazuje, jak ustawić, aby otrzymywać powiadomienia, gdy cel wiążący (docelowy) lub właściwość source (źródło) powiązania powiązania został zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="19fe3-103">This example shows how to set up to be notified when the binding target (target) or the binding source (source) property of a binding has been updated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19fe3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="19fe3-104">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="19fe3-105">zgłasza zdarzenie aktualizacji danych każdorazowo o zaktualizowaniu powiązania źródłowych lub docelowych.</span><span class="sxs-lookup"><span data-stu-id="19fe3-105">raises a data update event each time that the binding source or target has been updated.</span></span> <span data-ttu-id="19fe3-106">Wewnętrznie, to zdarzenie służy do informowania [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] który go zaktualizować, ponieważ została zmieniona powiązane dane.</span><span class="sxs-lookup"><span data-stu-id="19fe3-106">Internally, this event is used to inform the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] that it should update, because the bound data has changed.</span></span> <span data-ttu-id="19fe3-107">Uwaga dla tych zdarzeń do pracy, a także dla- lub dwukierunkowo powiązanie działało poprawnie, należy zaimplementować klasy dane przy użyciu <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="19fe3-107">Note that for these events to work, and also for one-way or two-way binding to work properly, you need to implement your data class using the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="19fe3-108">Aby uzyskać więcej informacji, zobacz [powiadomienie o zmianie właściwości Implementowanie](how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="19fe3-108">For more information, see [Implement Property Change Notification](how-to-implement-property-change-notification.md).</span></span>  
  
 <span data-ttu-id="19fe3-109">Ustaw <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> lub <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> właściwości (lub obie) `true` w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="19fe3-109">Set the <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> or <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> property (or both) to `true` in the binding.</span></span> <span data-ttu-id="19fe3-110">Program obsługi, podane do nasłuchiwania pod kątem tego zdarzenia musi być dołączony bezpośrednio do elementu, którego powiadamiane o zmianach, lub ogólny kontekst danych, aby należy pamiętać, że niczego w kontekście zmieniła się.</span><span class="sxs-lookup"><span data-stu-id="19fe3-110">The handler you provide to listen for this event must be attached directly to the element where you want to be informed of changes, or to the overall data context if you want to be aware that anything in the context has changed.</span></span>  
  
 <span data-ttu-id="19fe3-111">Oto przykład pokazujący sposób konfigurowania powiadomienia, gdy właściwość docelowa została zaktualizowana.</span><span class="sxs-lookup"><span data-stu-id="19fe3-111">Here is an example that shows how to set up for notification when a target property has been updated.</span></span>  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="19fe3-112">Następnie można przypisać obsługi, w oparciu o EventHandler\<T > delegować, *OnTargetUpdated* w tym przykładzie, aby obsłużyć zdarzenie:</span><span class="sxs-lookup"><span data-stu-id="19fe3-112">You can then assign a handler based on the EventHandler\<T> delegate, *OnTargetUpdated* in this example, to handle the event:</span></span>  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 <span data-ttu-id="19fe3-113">Aby określić szczegóły dotyczące właściwości, która się zmieniła (na przykład typ lub określony element, jeśli ten sam program obsługi jest podłączony do więcej niż jeden element), można użyć parametrów zdarzenia, które mogą być przydatne, jeśli ma wiele powiązanych właściwości na pojedynczy element.</span><span class="sxs-lookup"><span data-stu-id="19fe3-113">Parameters of the event can be used to determine details about the property that changed (such as the type or the specific element if the same handler is attached to more than one element), which can be useful if there are multiple bound properties on a single element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19fe3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19fe3-114">See also</span></span>

- [<span data-ttu-id="19fe3-115">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="19fe3-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="19fe3-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="19fe3-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
