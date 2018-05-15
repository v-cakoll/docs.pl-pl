---
title: Jak implementować powiadomienie o zmianie właściwości
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
ms.openlocfilehash: a9c0fb433e2fa65e28db3b793e038b49f9d6353b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="826e3-102">Jak implementować powiadomienie o zmianie właściwości</span><span class="sxs-lookup"><span data-stu-id="826e3-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="826e3-103">Do obsługi <xref:System.Windows.Data.BindingMode.OneWay> lub <xref:System.Windows.Data.BindingMode.TwoWay> powiązanie umożliwia powiązanie właściwości docelowej automatycznie zgodnie ze zmianami dynamiczne źródła powiązanie (na przykład okienko podglądu aktualizowane automatycznie, gdy użytkownik edytuje formularza), klasa należy podać powiadomienia odpowiednie zmiany właściwości.</span><span class="sxs-lookup"><span data-stu-id="826e3-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="826e3-104">W tym przykładzie pokazano, jak utworzyć klasę, która implementuje <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="826e3-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="826e3-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="826e3-105">Example</span></span>  
 <span data-ttu-id="826e3-106">Aby zaimplementować <xref:System.ComponentModel.INotifyPropertyChanged> należy zadeklarować <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenia i utworzyć `OnPropertyChanged` — metoda.</span><span class="sxs-lookup"><span data-stu-id="826e3-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="826e3-107">Następnie dla każdej właściwości mają powiadomienia o zmianie dla wywołania `OnPropertyChanged` zawsze, gdy właściwość jest aktualizowana.</span><span class="sxs-lookup"><span data-stu-id="826e3-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="826e3-108">Aby wyświetlić przykład przedstawia sposób `Person` klasa może być używana do obsługi <xref:System.Windows.Data.BindingMode.TwoWay> powiązanie, zobacz [kontroli, gdy tekst pola tekstowego aktualizuje źródła](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="826e3-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826e3-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="826e3-109">See Also</span></span>  
 [<span data-ttu-id="826e3-110">Wiązanie źródeł — omówienie</span><span class="sxs-lookup"><span data-stu-id="826e3-110">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="826e3-111">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="826e3-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="826e3-112">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="826e3-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
