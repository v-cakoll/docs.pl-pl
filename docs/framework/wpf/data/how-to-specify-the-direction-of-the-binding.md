---
title: Jak określić kierunek łączenia
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 8f7d843382ee3409047d7cf9549267d582883984
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459094"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="2bd37-102">Instrukcje: Określanie kierunku powiązania</span><span class="sxs-lookup"><span data-stu-id="2bd37-102">How to: Specify the direction of the binding</span></span>

<span data-ttu-id="2bd37-103">W tym przykładzie pokazano, jak określić, czy powiązanie aktualizuje tylko Właściwość cel powiązania (target), właściwość Źródło powiązania (Źródło) lub właściwość target oraz Właściwość Source.</span><span class="sxs-lookup"><span data-stu-id="2bd37-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bd37-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2bd37-104">Example</span></span>  
 <span data-ttu-id="2bd37-105">Użyj właściwości <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType>, aby określić kierunek powiązania.</span><span class="sxs-lookup"><span data-stu-id="2bd37-105">You use the <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> property to specify the direction of the binding.</span></span> <span data-ttu-id="2bd37-106">Dostępne są następujące opcje dla aktualizacji powiązań:</span><span class="sxs-lookup"><span data-stu-id="2bd37-106">The following are the available options for binding updates:</span></span>  
  
- <span data-ttu-id="2bd37-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> aktualizuje właściwość docelową lub właściwość za każdym razem, gdy właściwość docelowa lub właściwość źródłowa ulegnie zmianie.</span><span class="sxs-lookup"><span data-stu-id="2bd37-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
- <span data-ttu-id="2bd37-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> aktualizuje właściwość docelową tylko wtedy, gdy właściwość źródłowa ulegnie zmianie.</span><span class="sxs-lookup"><span data-stu-id="2bd37-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> updates the target property only when the source property changes.</span></span>  
  
- <span data-ttu-id="2bd37-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> aktualizuje właściwość docelową tylko wtedy, gdy aplikacja zostanie uruchomiona lub gdy <xref:System.Windows.FrameworkElement.DataContext%2A> ulegnie zmianie.</span><span class="sxs-lookup"><span data-stu-id="2bd37-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
- <span data-ttu-id="2bd37-110"><xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> aktualizuje właściwość source po zmianie właściwości docelowej.</span><span class="sxs-lookup"><span data-stu-id="2bd37-110"><xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> updates the source property when the target property changes.</span></span>  
  
- <span data-ttu-id="2bd37-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> powoduje użycie domyślnej <xref:System.Windows.Data.Binding.Mode%2A> wartości właściwości docelowej.</span><span class="sxs-lookup"><span data-stu-id="2bd37-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="2bd37-112">Aby uzyskać więcej informacji, zobacz Wyliczenie <xref:System.Windows.Data.BindingMode>.</span><span class="sxs-lookup"><span data-stu-id="2bd37-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="2bd37-113">Poniższy przykład pokazuje, jak ustawić właściwość <xref:System.Windows.Data.Binding.Mode%2A>.</span><span class="sxs-lookup"><span data-stu-id="2bd37-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="2bd37-114">Aby wykrywać zmiany źródła (mające zastosowanie do <xref:System.Windows.Data.BindingMode.OneWay> i <xref:System.Windows.Data.BindingMode.TwoWay> powiązań), Źródło musi zaimplementować odpowiedni mechanizm powiadamiania o zmianach właściwości, taki jak <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="2bd37-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="2bd37-115">Zapoznaj się z tematem implementacja [powiadomienia o zmianie właściwości](how-to-implement-property-change-notification.md) dla przykładu implementacji <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="2bd37-115">See [Implement Property Change Notification](how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="2bd37-116">W przypadku powiązań <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> można kontrolować chronometraż aktualizacji źródłowych przez ustawienie właściwości <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="2bd37-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="2bd37-117">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="2bd37-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd37-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2bd37-118">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="2bd37-119">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="2bd37-119">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="2bd37-120">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="2bd37-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
