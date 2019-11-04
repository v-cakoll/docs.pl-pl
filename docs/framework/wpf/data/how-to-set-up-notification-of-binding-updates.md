---
title: Jak ustawić powiadomienie o łączeniu aktualizacji
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: dfa0f9264247f7585c1743e40fd980906556efd0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454948"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a><span data-ttu-id="3e41f-102">Jak ustawić powiadomienie o łączeniu aktualizacji</span><span class="sxs-lookup"><span data-stu-id="3e41f-102">How to: Set Up Notification of Binding Updates</span></span>
<span data-ttu-id="3e41f-103">Ten przykład pokazuje, jak skonfigurować, aby otrzymywać powiadomienia o aktualizacji elementu docelowego powiązania (target) lub źródła powiązania (Źródło) powiązania.</span><span class="sxs-lookup"><span data-stu-id="3e41f-103">This example shows how to set up to be notified when the binding target (target) or the binding source (source) property of a binding has been updated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e41f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e41f-104">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="3e41f-105">zgłasza zdarzenie aktualizacji danych za każdym razem, gdy źródło lub cel powiązania zostały zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="3e41f-105">raises a data update event each time that the binding source or target has been updated.</span></span> <span data-ttu-id="3e41f-106">Wewnętrznie to zdarzenie służy do informowania [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], że powinna zostać zaktualizowana, ponieważ dane powiązane zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="3e41f-106">Internally, this event is used to inform the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] that it should update, because the bound data has changed.</span></span> <span data-ttu-id="3e41f-107">Należy pamiętać, że w celu poprawnego działania tych zdarzeń, a także dla jednokierunkowego lub dwukierunkowego powiązania, należy zaimplementować klasę danych przy użyciu interfejsu <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="3e41f-107">Note that for these events to work, and also for one-way or two-way binding to work properly, you need to implement your data class using the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="3e41f-108">Aby uzyskać więcej informacji, zobacz [implementacja powiadomienia o zmianie właściwości](how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="3e41f-108">For more information, see [Implement Property Change Notification](how-to-implement-property-change-notification.md).</span></span>  
  
 <span data-ttu-id="3e41f-109">Ustaw właściwość <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> lub <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> (lub obie) na `true` w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="3e41f-109">Set the <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> or <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> property (or both) to `true` in the binding.</span></span> <span data-ttu-id="3e41f-110">Program obsługi, który zapewniasz nasłuchiwanie tego zdarzenia, musi zostać dołączony bezpośrednio do elementu, w którym chcesz otrzymywać informacje o zmianach lub do ogólnego kontekstu danych, jeśli chcesz mieć świadomość, że wszystkie elementy w kontekście uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="3e41f-110">The handler you provide to listen for this event must be attached directly to the element where you want to be informed of changes, or to the overall data context if you want to be aware that anything in the context has changed.</span></span>  
  
 <span data-ttu-id="3e41f-111">Oto przykład, w którym pokazano, jak skonfigurować dla powiadomienia, kiedy Właściwość docelowa została zaktualizowana.</span><span class="sxs-lookup"><span data-stu-id="3e41f-111">Here is an example that shows how to set up for notification when a target property has been updated.</span></span>  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="3e41f-112">Następnie można przypisać procedurę obsługi na podstawie EventHandler\<T > delegata, *OnTargetUpdated* w tym przykładzie, aby obsłużyć zdarzenie:</span><span class="sxs-lookup"><span data-stu-id="3e41f-112">You can then assign a handler based on the EventHandler\<T> delegate, *OnTargetUpdated* in this example, to handle the event:</span></span>  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 <span data-ttu-id="3e41f-113">Parametry zdarzenia mogą służyć do określenia szczegółowych informacji o właściwości, która została zmieniona (na przykład typu lub konkretnego elementu, jeśli ta sama procedura obsługi jest dołączona do więcej niż jednego elementu), co może być przydatne, jeśli istnieje wiele właściwości powiązanych jednego elementu.</span><span class="sxs-lookup"><span data-stu-id="3e41f-113">Parameters of the event can be used to determine details about the property that changed (such as the type or the specific element if the same handler is attached to more than one element), which can be useful if there are multiple bound properties on a single element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e41f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e41f-114">See also</span></span>

- [<span data-ttu-id="3e41f-115">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="3e41f-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="3e41f-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="3e41f-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
