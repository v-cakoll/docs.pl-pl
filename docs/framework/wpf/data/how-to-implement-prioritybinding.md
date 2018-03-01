---
title: 'Porady: implementowanie PriorityBinding'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e6ab8826f2298a8660a85d739fbe3456374b476
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-implement-prioritybinding"></a><span data-ttu-id="52e51-102">Porady: implementowanie PriorityBinding</span><span class="sxs-lookup"><span data-stu-id="52e51-102">How to: Implement PriorityBinding</span></span>
<span data-ttu-id="52e51-103"><xref:System.Windows.Data.PriorityBinding>w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] działa przez określenie listy powiązań.</span><span class="sxs-lookup"><span data-stu-id="52e51-103"><xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] works by specifying a list of bindings.</span></span> <span data-ttu-id="52e51-104">Lista powiązań porządkowania z najwyższym priorytetem do najniższego priorytetu.</span><span class="sxs-lookup"><span data-stu-id="52e51-104">The list of bindings is ordered from highest priority to lowest priority.</span></span> <span data-ttu-id="52e51-105">Jeśli powiązanie najwyższy priorytet zwróci wartość pomyślnie podczas przetwarzania oznacza to, że nigdy nie potrzeba przetworzyć pozostałych powiązaniach na liście.</span><span class="sxs-lookup"><span data-stu-id="52e51-105">If the highest priority binding returns a value successfully when it is processed then there is never a need to process the other bindings in the list.</span></span> <span data-ttu-id="52e51-106">Może to być to powiązanie najwyższy priorytet trwa długo ma zostać obliczone, dalej najwyższy priorytet, która zwraca wartość pomyślnie zostanie użyty, dopóki powiązanie o wyższym priorytecie zwraca wartość pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="52e51-106">It could be the case that the highest priority binding takes a long time to be evaluated, the next highest priority that returns a value successfully will be used until a binding of a higher priority returns a value successfully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52e51-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="52e51-107">Example</span></span>  
 <span data-ttu-id="52e51-108">Aby zademonstrować sposób <xref:System.Windows.Data.PriorityBinding> działa, `AsyncDataSource` obiekt został utworzony z następujących trzech właściwości: `FastDP`, `SlowerDP`, i `SlowestDP`.</span><span class="sxs-lookup"><span data-stu-id="52e51-108">To demonstrate how <xref:System.Windows.Data.PriorityBinding> works, the `AsyncDataSource` object has been created with the following three properties: `FastDP`, `SlowerDP`, and `SlowestDP`.</span></span>  
  
 <span data-ttu-id="52e51-109">Metody dostępu get `FastDP` zwraca wartość `_fastDP` elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="52e51-109">The get accessor of `FastDP` returns the value of the `_fastDP` data member.</span></span>  
  
 <span data-ttu-id="52e51-110">Metody dostępu get `SlowerDP` czeka na 3 sekundy przed zwróceniem wartość `_slowerDP` elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="52e51-110">The get accessor of `SlowerDP` waits for 3 seconds before returning the value of the `_slowerDP` data member.</span></span>  
  
 <span data-ttu-id="52e51-111">Metody dostępu get `SlowestDP` czeka na 5 sekund przed zwróceniem wartość `_slowestDP` elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="52e51-111">The get accessor of `SlowestDP` waits for 5 seconds before returning the value of the `_slowestDP` data member.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52e51-112">W tym przykładzie jest tylko w celach demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="52e51-112">This example is for demonstration purposes only.</span></span> <span data-ttu-id="52e51-113">[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] Wytyczne zaleca się definiowania właściwości, które są rzędów wolniej niż zestaw pól.</span><span class="sxs-lookup"><span data-stu-id="52e51-113">The [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] guidelines recommend against defining properties that are orders of magnitude slower than a field set would be.</span></span> <span data-ttu-id="52e51-114">Aby uzyskać więcej informacji, zobacz [NIB: Wybieranie między właściwości i metody](http://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af).</span><span class="sxs-lookup"><span data-stu-id="52e51-114">For more information, see [NIB: Choosing Between Properties and Methods](http://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af).</span></span>  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <span data-ttu-id="52e51-115"><xref:System.Windows.Controls.TextBlock.Text%2A> Właściwość jest powiązana z powyższych `AsyncDS` przy użyciu <xref:System.Windows.Data.PriorityBinding>:</span><span class="sxs-lookup"><span data-stu-id="52e51-115">The <xref:System.Windows.Controls.TextBlock.Text%2A> property binds to the above `AsyncDS` using <xref:System.Windows.Data.PriorityBinding>:</span></span>  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="52e51-116">Gdy aparat wiązania przetwarza <xref:System.Windows.Data.Binding> obiekty, rozpoczyna się pierwszego <xref:System.Windows.Data.Binding>, która jest powiązana `SlowestDP` właściwości.</span><span class="sxs-lookup"><span data-stu-id="52e51-116">When the binding engine processes the <xref:System.Windows.Data.Binding> objects, it starts with the first <xref:System.Windows.Data.Binding>, which is bound to the `SlowestDP` property.</span></span> <span data-ttu-id="52e51-117">Gdy to <xref:System.Windows.Data.Binding> jest przetwarzane, nie zwraca wartości pomyślnie, ponieważ jego jest uśpiony 5 sekund, więc następnej <xref:System.Windows.Data.Binding> element jest przetwarzany.</span><span class="sxs-lookup"><span data-stu-id="52e51-117">When this <xref:System.Windows.Data.Binding> is processed, it does not return a value successfully because it is sleeping for 5 seconds, so the next <xref:System.Windows.Data.Binding> element is processed.</span></span> <span data-ttu-id="52e51-118">Następne <xref:System.Windows.Data.Binding> nie zwraca wartości pomyślnie, ponieważ jest uśpiony przez 3 sekundy.</span><span class="sxs-lookup"><span data-stu-id="52e51-118">The next <xref:System.Windows.Data.Binding> does not return a value successfully because it is sleeping for 3 seconds.</span></span> <span data-ttu-id="52e51-119">Aparat wiązania następnie przechodzi do następnego <xref:System.Windows.Data.Binding> element, który jest powiązany z `FastDP` właściwości.</span><span class="sxs-lookup"><span data-stu-id="52e51-119">The binding engine then moves onto the next <xref:System.Windows.Data.Binding> element, which is bound to the `FastDP` property.</span></span> <span data-ttu-id="52e51-120">To <xref:System.Windows.Data.Binding> zwraca wartość "Fast Value".</span><span class="sxs-lookup"><span data-stu-id="52e51-120">This <xref:System.Windows.Data.Binding> returns the value "Fast Value".</span></span> <span data-ttu-id="52e51-121"><xref:System.Windows.Controls.TextBlock> Wartość "Fast wartość" są obecnie wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="52e51-121">The <xref:System.Windows.Controls.TextBlock> now displays the value "Fast Value".</span></span>  
  
 <span data-ttu-id="52e51-122">Po upłynięciu tego 3 sekundy `SlowerDP` zwraca wartość "Wolniejsze Value".</span><span class="sxs-lookup"><span data-stu-id="52e51-122">After 3 seconds elapses, the `SlowerDP` property returns the value "Slower Value".</span></span> <span data-ttu-id="52e51-123"><xref:System.Windows.Controls.TextBlock> Następnie wyświetla wartość "Wolniejsze wartość".</span><span class="sxs-lookup"><span data-stu-id="52e51-123">The <xref:System.Windows.Controls.TextBlock> then displays the value "Slower Value".</span></span>  
  
 <span data-ttu-id="52e51-124">Po upłynięciu tego 5 sekund `SlowestDP` właściwość zwraca wartość "Najmniejszą wartość".</span><span class="sxs-lookup"><span data-stu-id="52e51-124">After 5 seconds elapses, the `SlowestDP` property returns the value "Slowest Value".</span></span> <span data-ttu-id="52e51-125">Czy powiązania ma najwyższy priorytet, ponieważ znajduje się najpierw.</span><span class="sxs-lookup"><span data-stu-id="52e51-125">That binding has the highest priority because it is listed first.</span></span> <span data-ttu-id="52e51-126"><xref:System.Windows.Controls.TextBlock> Wartość "Najmniejszą wartość" są obecnie wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="52e51-126">The <xref:System.Windows.Controls.TextBlock> now displays the value "Slowest Value".</span></span>  
  
 <span data-ttu-id="52e51-127">Zobacz <xref:System.Windows.Data.PriorityBinding> informacji o co to jest uznawany za pomyślnie wartość zwrotną z elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="52e51-127">See <xref:System.Windows.Data.PriorityBinding> for information about what is considered a successful return value from a binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e51-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52e51-128">See Also</span></span>  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="52e51-129">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="52e51-129">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="52e51-130">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="52e51-130">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
