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
ms.openlocfilehash: 4f9ff49a443577e119b0c1079abbe23bd7ede4c4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459747"
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="54f50-102">Jak implementować powiadomienie o zmianie właściwości</span><span class="sxs-lookup"><span data-stu-id="54f50-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="54f50-103">Aby obsłużyć <xref:System.Windows.Data.BindingMode.OneWay> lub <xref:System.Windows.Data.BindingMode.TwoWay> powiązania, aby właściwości celu powiązania automatycznie odzwierciedlały dynamiczne zmiany źródła powiązania (na przykład w celu automatycznego aktualizowania okienka podglądu podczas edytowania formularza przez użytkownika), Klasa musi podaj odpowiednie powiadomienia o zmianach właściwości.</span><span class="sxs-lookup"><span data-stu-id="54f50-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="54f50-104">Ten przykład pokazuje, jak utworzyć klasę, która implementuje <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="54f50-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54f50-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="54f50-105">Example</span></span>  
 <span data-ttu-id="54f50-106">Aby zaimplementować <xref:System.ComponentModel.INotifyPropertyChanged> należy zadeklarować zdarzenie <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> i utworzyć metodę `OnPropertyChanged`.</span><span class="sxs-lookup"><span data-stu-id="54f50-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="54f50-107">Następnie dla każdej właściwości, dla której chcesz zmienić powiadomienia, należy wywołać `OnPropertyChanged` przy każdej aktualizacji właściwości.</span><span class="sxs-lookup"><span data-stu-id="54f50-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="54f50-108">Aby zobaczyć przykład sposobu, w jaki Klasa `Person` może być używana do obsługi powiązań <xref:System.Windows.Data.BindingMode.TwoWay>, zobacz [kontrolowanie, kiedy tekst TextBox aktualizuje Źródło](how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="54f50-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54f50-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54f50-109">See also</span></span>

- [<span data-ttu-id="54f50-110">Wiązanie źródeł — omówienie</span><span class="sxs-lookup"><span data-stu-id="54f50-110">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="54f50-111">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="54f50-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="54f50-112">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="54f50-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
