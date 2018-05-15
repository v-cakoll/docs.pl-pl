---
title: Jak określić kierunek łączenia
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 100130f3dc099d1cf1f216c841e7e1dc1d083f39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="5d8f2-102">Jak określić kierunek łączenia</span><span class="sxs-lookup"><span data-stu-id="5d8f2-102">How to: Specify the Direction of the Binding</span></span>
<span data-ttu-id="5d8f2-103">Ten przykład przedstawia sposób określić, czy powiązanie aktualizować tylko właściwość target (docelowy) powiązania powiązania właściwości source (źródło), lub zarówno właściwość target właściwości oraz źródła.</span><span class="sxs-lookup"><span data-stu-id="5d8f2-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d8f2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d8f2-104">Example</span></span>  
 <span data-ttu-id="5d8f2-105">Możesz użyć <xref:System.Windows.Data.Binding.Mode%2A> właściwości do określania kierunku powiązania.</span><span class="sxs-lookup"><span data-stu-id="5d8f2-105">You use the <xref:System.Windows.Data.Binding.Mode%2A> property to specify the direction of the binding.</span></span> <span data-ttu-id="5d8f2-106">Na poniższej liście wyliczenia przedstawia dostępne opcje aktualizacji powiązania:</span><span class="sxs-lookup"><span data-stu-id="5d8f2-106">The following enumeration list shows the available options for binding updates:</span></span>  
  
-   <span data-ttu-id="5d8f2-107"><xref:System.Windows.Data.BindingMode.TwoWay> aktualizuje właściwość docelowego lub zmianie właściwości target lub właściwości source.</span><span class="sxs-lookup"><span data-stu-id="5d8f2-107"><xref:System.Windows.Data.BindingMode.TwoWay> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
-   <span data-ttu-id="5d8f2-108"><xref:System.Windows.Data.BindingMode.OneWay> Właściwość target aktualizacji, tylko wtedy, gdy zmienia się właściwości source.</span><span class="sxs-lookup"><span data-stu-id="5d8f2-108"><xref:System.Windows.Data.BindingMode.OneWay> updates the target property only when the source property changes.</span></span>  
  
-   <span data-ttu-id="5d8f2-109"><xref:System.Windows.Data.BindingMode.OneTime> aktualizuje właściwość target tylko podczas uruchamiania aplikacji lub <xref:System.Windows.FrameworkElement.DataContext%2A> ulega zmianie.</span><span class="sxs-lookup"><span data-stu-id="5d8f2-109"><xref:System.Windows.Data.BindingMode.OneTime> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
-   <span data-ttu-id="5d8f2-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> Aktualizuje właściwości source po zmianie właściwości target.</span><span class="sxs-lookup"><span data-stu-id="5d8f2-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> updates the source property when the target property changes.</span></span>  
  
-   <span data-ttu-id="5d8f2-111"><xref:System.Windows.Data.BindingMode.Default> powoduje, że wartość domyślna <xref:System.Windows.Data.Binding.Mode%2A> wartości właściwości docelowej do użycia.</span><span class="sxs-lookup"><span data-stu-id="5d8f2-111"><xref:System.Windows.Data.BindingMode.Default> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="5d8f2-112">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.BindingMode> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5d8f2-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="5d8f2-113">Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.Data.Binding.Mode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5d8f2-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="5d8f2-114">Aby wykryć zmiany źródła (dotyczy <xref:System.Windows.Data.BindingMode.OneWay> i <xref:System.Windows.Data.BindingMode.TwoWay> powiązań), źródło musi implementować mechanizm powiadamiania Zmień odpowiednie właściwości takich jak <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="5d8f2-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="5d8f2-115">Zobacz [powiadomienia o zmianie właściwości wdrożenie](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) przykład <xref:System.ComponentModel.INotifyPropertyChanged> implementacji.</span><span class="sxs-lookup"><span data-stu-id="5d8f2-115">See [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="5d8f2-116">Dla <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązań, można kontrolować czas aktualizacji źródła przez ustawienie <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5d8f2-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="5d8f2-117">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="5d8f2-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d8f2-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d8f2-118">See Also</span></span>  
 <xref:System.Windows.Data.Binding>  
 [<span data-ttu-id="5d8f2-119">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="5d8f2-119">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="5d8f2-120">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="5d8f2-120">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
