---
title: Jak implementować powiadomienie o zmianie właściwości
description: Włącz automatyczne powiadamianie źródła powiązania, gdy wartość właściwości zostanie zmieniona w Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 6c298930b7b1f812e94ea6add8f53c67d3453530
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620784"
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="6ec8a-103">Jak implementować powiadomienie o zmianie właściwości</span><span class="sxs-lookup"><span data-stu-id="6ec8a-103">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="6ec8a-104">Aby <xref:System.Windows.Data.BindingMode.OneWay> umożliwić obsługę lub <xref:System.Windows.Data.BindingMode.TwoWay> wiązanie w celu włączenia właściwości celu powiązania, aby automatycznie odzwierciedlały dynamiczne zmiany źródła powiązania (na przykład w celu automatycznego aktualizowania okienka podglądu podczas edytowania formularza przez użytkownika), Klasa musi podać odpowiednie powiadomienia o zmianach właściwości.</span><span class="sxs-lookup"><span data-stu-id="6ec8a-104">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="6ec8a-105">Ten przykład przedstawia sposób tworzenia klasy implementującej <xref:System.ComponentModel.INotifyPropertyChanged> .</span><span class="sxs-lookup"><span data-stu-id="6ec8a-105">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ec8a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ec8a-106">Example</span></span>  
 <span data-ttu-id="6ec8a-107">Aby zaimplementować, należy <xref:System.ComponentModel.INotifyPropertyChanged> zadeklarować <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenie i utworzyć `OnPropertyChanged` metodę.</span><span class="sxs-lookup"><span data-stu-id="6ec8a-107">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="6ec8a-108">Następnie dla każdej właściwości, dla której chcesz zmienić powiadomienia, `OnPropertyChanged` jest wywoływana za każdym razem, gdy właściwość zostanie zaktualizowana.</span><span class="sxs-lookup"><span data-stu-id="6ec8a-108">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="6ec8a-109">Aby zobaczyć przykład sposobu `Person` użycia klasy do obsługi <xref:System.Windows.Data.BindingMode.TwoWay> powiązań, zobacz [kontrolowanie, kiedy tekst TextBox aktualizuje Źródło](how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="6ec8a-109">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec8a-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ec8a-110">See also</span></span>

- [<span data-ttu-id="6ec8a-111">Wiązanie źródeł — omówienie</span><span class="sxs-lookup"><span data-stu-id="6ec8a-111">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="6ec8a-112">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="6ec8a-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="6ec8a-113">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="6ec8a-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
