---
title: Jak określić źródło wiążące
description: Dowiedz się, jak określić źródło powiązania za pomocą tego przykładu w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 02f27da007ebe8c5985f91b83adfba7d3d00219a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621668"
---
# <a name="how-to-specify-the-binding-source"></a><span data-ttu-id="3af59-103">Jak określić źródło wiążące</span><span class="sxs-lookup"><span data-stu-id="3af59-103">How to: Specify the Binding Source</span></span>
<span data-ttu-id="3af59-104">W powiązaniu danych obiekt źródłowy powiązania odwołuje się do obiektu, z którego uzyskujesz dane.</span><span class="sxs-lookup"><span data-stu-id="3af59-104">In data binding, the binding source object refers to the object you obtain your data from.</span></span> <span data-ttu-id="3af59-105">W tym temacie opisano różne sposoby określania źródła powiązania.</span><span class="sxs-lookup"><span data-stu-id="3af59-105">This topic describes the different ways of specifying the binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3af59-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="3af59-106">Example</span></span>  
 <span data-ttu-id="3af59-107">Jeśli powiążesz kilka właściwości ze wspólnym źródłem, chcesz użyć `DataContext` właściwości, która zapewnia wygodny sposób ustanowienia zakresu, w którym wszystkie właściwości powiązane z danymi dziedziczą wspólne źródło.</span><span class="sxs-lookup"><span data-stu-id="3af59-107">If you are binding several properties to a common source, you want to use the `DataContext` property, which provides a convenient way to establish a scope within which all data-bound properties inherit a common source.</span></span>  
  
 <span data-ttu-id="3af59-108">W poniższym przykładzie kontekst danych jest ustanowiony w elemencie głównym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3af59-108">In the following example, the data context is established on the root element of the application.</span></span> <span data-ttu-id="3af59-109">Dzięki temu wszystkie elementy podrzędne będą dziedziczyły ten kontekst danych.</span><span class="sxs-lookup"><span data-stu-id="3af59-109">This allows all child elements to inherit that data context.</span></span> <span data-ttu-id="3af59-110">Dane dla powiązania pochodzą z niestandardowej klasy danych, `NetIncome` do których odwołuje się bezpośrednio za pomocą mapowania i podanego klucza zasobu `incomeDataSource` .</span><span class="sxs-lookup"><span data-stu-id="3af59-110">Data for the binding comes from a custom data class, `NetIncome`, referenced directly through a mapping and given the resource key of `incomeDataSource`.</span></span>  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 <span data-ttu-id="3af59-111">W poniższym przykładzie przedstawiono definicję `NetIncome` klasy.</span><span class="sxs-lookup"><span data-stu-id="3af59-111">The following example shows the definition of the `NetIncome` class.</span></span>  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> <span data-ttu-id="3af59-112">Powyższy przykład tworzy wystąpienie obiektu w znaczniku i używa go jako zasobu.</span><span class="sxs-lookup"><span data-stu-id="3af59-112">The above example instantiates the object in markup and uses it as a resource.</span></span> <span data-ttu-id="3af59-113">Jeśli chcesz powiązać z obiektem, który został już utworzony w kodzie, należy ustawić `DataContext` właściwość programowo.</span><span class="sxs-lookup"><span data-stu-id="3af59-113">If you want to bind to an object that has already been instantiated in code, you need to set the `DataContext` property programmatically.</span></span> <span data-ttu-id="3af59-114">Aby zapoznać się z przykładem, zobacz [udostępnianie danych do powiązania w języku XAML](how-to-make-data-available-for-binding-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="3af59-114">For an example, see [Make Data Available for Binding in XAML](how-to-make-data-available-for-binding-in-xaml.md).</span></span>  
  
 <span data-ttu-id="3af59-115">Alternatywnie, jeśli chcesz jawnie określić źródło dla konkretnych powiązań, masz następujące opcje.</span><span class="sxs-lookup"><span data-stu-id="3af59-115">Alternatively, if you want to specify the source on your individual bindings explicitly, you have the following options.</span></span> <span data-ttu-id="3af59-116">Mają pierwszeństwo przed dziedziczonym kontekstem danych.</span><span class="sxs-lookup"><span data-stu-id="3af59-116">These take precedence over the inherited data context.</span></span>  
  
|<span data-ttu-id="3af59-117">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3af59-117">Property</span></span>|<span data-ttu-id="3af59-118">Opis</span><span class="sxs-lookup"><span data-stu-id="3af59-118">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|<span data-ttu-id="3af59-119">Ta właściwość służy do ustawiania źródła do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3af59-119">You use this property to set the source to an instance of an object.</span></span> <span data-ttu-id="3af59-120">Jeśli nie potrzebujesz funkcji ustanawiania zakresu, w którym kilka właściwości dziedziczy ten sam kontekst danych, możesz użyć <xref:System.Windows.Data.Binding.Source%2A> Właściwości zamiast `DataContext` właściwości.</span><span class="sxs-lookup"><span data-stu-id="3af59-120">If you do not need the functionality of establishing a scope in which several properties inherit the same data context, you can use the <xref:System.Windows.Data.Binding.Source%2A> property instead of the `DataContext` property.</span></span> <span data-ttu-id="3af59-121">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="3af59-121">For more information, see <xref:System.Windows.Data.Binding.Source%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|<span data-ttu-id="3af59-122">Jest to przydatne, gdy chcesz określić źródło względem lokalizacji docelowej powiązania.</span><span class="sxs-lookup"><span data-stu-id="3af59-122">This is useful when you want to specify the source relative to where your binding target is.</span></span> <span data-ttu-id="3af59-123">Niektóre typowe scenariusze, w których można użyć tej właściwości, można powiązać z jedną właściwością elementu z inną właściwością tego samego elementu lub w przypadku definiowania powiązania w stylu lub szablonie.</span><span class="sxs-lookup"><span data-stu-id="3af59-123">Some common scenarios where you may use this property is when you want to bind one property of your element to another property of the same element or if you are defining a binding in a style or a template.</span></span> <span data-ttu-id="3af59-124">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="3af59-124">For more information, see <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|<span data-ttu-id="3af59-125">Należy określić ciąg, który reprezentuje element, z którym ma zostać utworzone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="3af59-125">You specify a string that represents the element you want to bind to.</span></span> <span data-ttu-id="3af59-126">Jest to przydatne, gdy chcesz powiązać z właściwością innego elementu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3af59-126">This is useful when you want to bind to the property of another element on your application.</span></span> <span data-ttu-id="3af59-127">Na przykład, jeśli chcesz użyć elementu, <xref:System.Windows.Controls.Slider> Aby kontrolować wysokość innej kontrolki w aplikacji, lub jeśli chcesz powiązać <xref:System.Windows.Controls.ContentControl.Content%2A> formant z <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> właściwością <xref:System.Windows.Controls.ListBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="3af59-127">For example, if you want to use a <xref:System.Windows.Controls.Slider> to control the height of another control in your application, or if you want to bind the <xref:System.Windows.Controls.ContentControl.Content%2A> of your control to the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property of your <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="3af59-128">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="3af59-128">For more information, see <xref:System.Windows.Data.Binding.ElementName%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3af59-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3af59-129">See also</span></span>

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3af59-130">Przejęcie wartości właściwości</span><span class="sxs-lookup"><span data-stu-id="3af59-130">Property Value Inheritance</span></span>](../advanced/property-value-inheritance.md)
- [<span data-ttu-id="3af59-131">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="3af59-131">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="3af59-132">Przegląd Wiązanie deklaracji</span><span class="sxs-lookup"><span data-stu-id="3af59-132">Binding Declarations Overview</span></span>](binding-declarations-overview.md)
- [<span data-ttu-id="3af59-133">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="3af59-133">How-to Topics</span></span>](data-binding-how-to-topics.md)
