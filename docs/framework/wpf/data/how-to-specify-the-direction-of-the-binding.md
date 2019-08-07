---
title: 'Instrukcje: Określanie kierunku powiązania'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 023cd42ad5fb321e7ffa65f08673cb4145f49af4
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817910"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="6f328-102">Instrukcje: Określ kierunek powiązania</span><span class="sxs-lookup"><span data-stu-id="6f328-102">How to: Specify the direction of the binding</span></span>

<span data-ttu-id="6f328-103">W tym przykładzie pokazano, jak określić, czy powiązanie aktualizuje tylko Właściwość cel powiązania (target), właściwość Źródło powiązania (Źródło) lub właściwość target oraz Właściwość Source.</span><span class="sxs-lookup"><span data-stu-id="6f328-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f328-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6f328-104">Example</span></span>  
 <span data-ttu-id="6f328-105">Użyj właściwości, <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> aby określić kierunek powiązania.</span><span class="sxs-lookup"><span data-stu-id="6f328-105">You use the <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> property to specify the direction of the binding.</span></span> <span data-ttu-id="6f328-106">Dostępne są następujące opcje dla aktualizacji powiązań:</span><span class="sxs-lookup"><span data-stu-id="6f328-106">The following are the available options for binding updates:</span></span>  
  
- <span data-ttu-id="6f328-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>aktualizuje właściwość docelową lub właściwość za każdym razem, gdy właściwość docelowa lub właściwość źródłowa ulegnie zmianie.</span><span class="sxs-lookup"><span data-stu-id="6f328-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
- <span data-ttu-id="6f328-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType>aktualizuje właściwość docelową tylko wtedy, gdy właściwość źródłowa ulegnie zmianie.</span><span class="sxs-lookup"><span data-stu-id="6f328-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> updates the target property only when the source property changes.</span></span>  
  
- <span data-ttu-id="6f328-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType>aktualizuje właściwość docelową tylko wtedy, gdy aplikacja jest uruchamiana lub gdy <xref:System.Windows.FrameworkElement.DataContext%2A> zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="6f328-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
- <span data-ttu-id="6f328-110"><xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType>aktualizuje właściwość source po zmianie właściwości docelowej.</span><span class="sxs-lookup"><span data-stu-id="6f328-110"><xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> updates the source property when the target property changes.</span></span>  
  
- <span data-ttu-id="6f328-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType>powoduje użycie domyślnej <xref:System.Windows.Data.Binding.Mode%2A> wartości właściwości docelowej.</span><span class="sxs-lookup"><span data-stu-id="6f328-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="6f328-112">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.BindingMode> Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="6f328-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="6f328-113">Poniższy przykład pokazuje, <xref:System.Windows.Data.Binding.Mode%2A> jak ustawić właściwość.</span><span class="sxs-lookup"><span data-stu-id="6f328-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="6f328-114">Aby wykryć zmiany źródła (odpowiednie dla <xref:System.Windows.Data.BindingMode.OneWay> i <xref:System.Windows.Data.BindingMode.TwoWay> powiązania), Źródło musi zaimplementować odpowiedni mechanizm powiadamiania o zmianach właściwości, <xref:System.ComponentModel.INotifyPropertyChanged>taki jak.</span><span class="sxs-lookup"><span data-stu-id="6f328-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="6f328-115">Aby zapoznać się z <xref:System.ComponentModel.INotifyPropertyChanged> przykładem implementacji, zobacz [implementacja powiadomienia o zmianie właściwości](how-to-implement-property-change-notification.md) .</span><span class="sxs-lookup"><span data-stu-id="6f328-115">See [Implement Property Change Notification](how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="6f328-116">W <xref:System.Windows.Data.BindingMode.TwoWay> przypadku <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązań lub można kontrolować chronometraż aktualizacji <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> źródłowych przez ustawienie właściwości.</span><span class="sxs-lookup"><span data-stu-id="6f328-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="6f328-117">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f328-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f328-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f328-118">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="6f328-119">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="6f328-119">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="6f328-120">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="6f328-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
