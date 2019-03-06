---
title: 'Instrukcje: Określ kierunek łączenia'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 265271cee16d203d7652281c5416b93759e66d4b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378226"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="9b394-102">Instrukcje: Określ kierunek łączenia</span><span class="sxs-lookup"><span data-stu-id="9b394-102">How to: Specify the Direction of the Binding</span></span>
<span data-ttu-id="9b394-103">Ten przykład przedstawia sposób określania, czy powiązanie aktualizuje właściwość target (docelowy) powiązania, powiązania właściwość source (źródło), lub zarówno właściwość docelowa, jak i właściwość source.</span><span class="sxs-lookup"><span data-stu-id="9b394-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b394-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9b394-104">Example</span></span>  
 <span data-ttu-id="9b394-105">Możesz użyć <xref:System.Windows.Data.Binding.Mode%2A> właściwość, aby określić kierunek łączenia.</span><span class="sxs-lookup"><span data-stu-id="9b394-105">You use the <xref:System.Windows.Data.Binding.Mode%2A> property to specify the direction of the binding.</span></span> <span data-ttu-id="9b394-106">Na poniższej liście wyliczenia przedstawiono dostępne opcje powiązanie aktualizacji:</span><span class="sxs-lookup"><span data-stu-id="9b394-106">The following enumeration list shows the available options for binding updates:</span></span>  
  
-   <span data-ttu-id="9b394-107"><xref:System.Windows.Data.BindingMode.TwoWay> aktualizuje właściwość target lub zawsze wtedy, gdy zmieni się właściwość docelowa lub właściwość source.</span><span class="sxs-lookup"><span data-stu-id="9b394-107"><xref:System.Windows.Data.BindingMode.TwoWay> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
-   <span data-ttu-id="9b394-108"><xref:System.Windows.Data.BindingMode.OneWay> Aktualizuje właściwości docelowych, tylko wtedy, gdy zmieni się właściwość source.</span><span class="sxs-lookup"><span data-stu-id="9b394-108"><xref:System.Windows.Data.BindingMode.OneWay> updates the target property only when the source property changes.</span></span>  
  
-   <span data-ttu-id="9b394-109"><xref:System.Windows.Data.BindingMode.OneTime> Aktualizuje właściwości docelowych, tylko wtedy, gdy aplikacja jest uruchamiana, lub gdy <xref:System.Windows.FrameworkElement.DataContext%2A> ulega zmianie.</span><span class="sxs-lookup"><span data-stu-id="9b394-109"><xref:System.Windows.Data.BindingMode.OneTime> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
-   <span data-ttu-id="9b394-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> Aktualizuje właściwości source, gdy zmieni się właściwość docelowa.</span><span class="sxs-lookup"><span data-stu-id="9b394-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> updates the source property when the target property changes.</span></span>  
  
-   <span data-ttu-id="9b394-111"><xref:System.Windows.Data.BindingMode.Default> powoduje, że wartość domyślna <xref:System.Windows.Data.Binding.Mode%2A> wartość właściwości docelowym ma być używany.</span><span class="sxs-lookup"><span data-stu-id="9b394-111"><xref:System.Windows.Data.BindingMode.Default> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="9b394-112">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.BindingMode> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9b394-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="9b394-113">Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Data.Binding.Mode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9b394-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="9b394-114">Aby wykryć zmiany źródła (dotyczy <xref:System.Windows.Data.BindingMode.OneWay> i <xref:System.Windows.Data.BindingMode.TwoWay> powiązania), źródło musi zaimplementować mechanizm powiadamiania Zmień odpowiednie właściwości takich jak <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="9b394-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="9b394-115">Zobacz [powiadomienie o zmianie właściwości Implementowanie](how-to-implement-property-change-notification.md) przykład <xref:System.ComponentModel.INotifyPropertyChanged> implementacji.</span><span class="sxs-lookup"><span data-stu-id="9b394-115">See [Implement Property Change Notification](how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="9b394-116">Aby uzyskać <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązań chronometraż aktualizacji źródła można kontrolować przez ustawienie <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9b394-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="9b394-117">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="9b394-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b394-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b394-118">See also</span></span>
- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="9b394-119">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="9b394-119">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="9b394-120">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="9b394-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
