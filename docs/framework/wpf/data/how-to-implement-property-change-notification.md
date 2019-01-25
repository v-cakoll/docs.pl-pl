---
title: 'Instrukcje: Implementuj powiadomienie o zmianie właściwości'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: 7a8ab232019f1266095091cd4e1ce6e7fec63207
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587816"
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="c52f0-102">Instrukcje: Implementuj powiadomienie o zmianie właściwości</span><span class="sxs-lookup"><span data-stu-id="c52f0-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="c52f0-103">Do obsługi <xref:System.Windows.Data.BindingMode.OneWay> lub <xref:System.Windows.Data.BindingMode.TwoWay> powiązanie umożliwiające powiązanie właściwości docelowej do automatycznie odzwierciedlają zmiany dynamicznej w źródle powiązania (na przykład, aby mieć okienko podglądu aktualizowane automatycznie, gdy użytkownik edytuje formularza), klasa wymaga do udostępniania powiadomień o odpowiednie zmiany właściwości.</span><span class="sxs-lookup"><span data-stu-id="c52f0-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="c52f0-104">W tym przykładzie pokazano, jak utworzyć klasę, która implementuje <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="c52f0-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c52f0-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c52f0-105">Example</span></span>  
 <span data-ttu-id="c52f0-106">Do zaimplementowania <xref:System.ComponentModel.INotifyPropertyChanged> trzeba zadeklarować <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzeń i utworzyć `OnPropertyChanged` metody.</span><span class="sxs-lookup"><span data-stu-id="c52f0-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="c52f0-107">Następnie dla każdej właściwości mają powiadomienia o zmianie dla wywołania `OnPropertyChanged` zawsze, gdy właściwość jest aktualizowana.</span><span class="sxs-lookup"><span data-stu-id="c52f0-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="c52f0-108">Aby zobaczyć przykładowy sposób, w jaki `Person` klasa może być używana do obsługi <xref:System.Windows.Data.BindingMode.TwoWay> powiązań, zobacz [kontrolować kiedy tekst TextBox aktualizuje źródło](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="c52f0-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52f0-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c52f0-109">See also</span></span>
- [<span data-ttu-id="c52f0-110">Wiązanie źródeł — omówienie</span><span class="sxs-lookup"><span data-stu-id="c52f0-110">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)
- [<span data-ttu-id="c52f0-111">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="c52f0-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c52f0-112">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="c52f0-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
