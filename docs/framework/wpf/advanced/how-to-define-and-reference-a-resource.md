---
title: "Jak definiować i tworzyć odwołanie do zasobu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 173be3048f7bf082db2eef2ea21eb1e0319f9a43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-and-reference-a-resource"></a><span data-ttu-id="bb251-102">Jak definiować i tworzyć odwołanie do zasobu</span><span class="sxs-lookup"><span data-stu-id="bb251-102">How to: Define and Reference a Resource</span></span>
<span data-ttu-id="bb251-103">W tym przykładzie pokazano, jak zdefiniować zasobu i odwołaj się przy użyciu atrybutu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb251-103">This example shows how to define a resource and reference it by using an attribute in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb251-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb251-104">Example</span></span>  
 <span data-ttu-id="bb251-105">W poniższym przykładzie zdefiniowano dwa typy zasobów: <xref:System.Windows.Media.SolidColorBrush> zasobów i kilka <xref:System.Windows.Style> zasobów.</span><span class="sxs-lookup"><span data-stu-id="bb251-105">The following example defines two types of resources: a <xref:System.Windows.Media.SolidColorBrush> resource, and several <xref:System.Windows.Style> resources.</span></span> <span data-ttu-id="bb251-106"><xref:System.Windows.Media.SolidColorBrush> Zasobów `MyBrush` służy do zapewnienia wartość kilka właściwości każdego zająć <xref:System.Windows.Media.Brush> wpisz wartość.</span><span class="sxs-lookup"><span data-stu-id="bb251-106">The <xref:System.Windows.Media.SolidColorBrush> resource `MyBrush` is used to provide the value of several properties that each take a <xref:System.Windows.Media.Brush> type value.</span></span> <span data-ttu-id="bb251-107"><xref:System.Windows.Style> Zasobów `PageBackground`, `TitleText` i `Label` każdego docelowego typu określonego formantu.</span><span class="sxs-lookup"><span data-stu-id="bb251-107">The <xref:System.Windows.Style> resources `PageBackground`, `TitleText` and `Label` each target a particular control type.</span></span> <span data-ttu-id="bb251-108">Style ustawić szereg różnych właściwości zawarte w formantach docelowej, gdy ten zasób stylu odwołuje się do niego klucz zasobu i jest używany do ustawiania <xref:System.Windows.FrameworkElement.Style%2A> właściwości zdefiniowanych w kilku elementów określonego formantu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb251-108">The styles set a variety of different properties on the targeted controls, when that style resource is referenced by resource key and is used to set the <xref:System.Windows.FrameworkElement.Style%2A> property of several specific control elements defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="bb251-109">Uwaga, że jedna z właściwości w ramach metod ustawiających `Label` odwołujący się styl `MyBrush` zasobów zdefiniowanego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="bb251-109">Note that one of the properties within the setters of the `Label` style also references the `MyBrush` resource defined earlier.</span></span> <span data-ttu-id="bb251-110">To jest typowe techniki, ale należy pamiętać, że zasoby są analizowane i wprowadzany do słownika zasobów w kolejności, czy są one.</span><span class="sxs-lookup"><span data-stu-id="bb251-110">This is a common technique, but it is important to remember that resources are parsed and entered into a resource dictionary in the order that they are given.</span></span> <span data-ttu-id="bb251-111">Zasoby wymagane są także według kolejności znaleziony w słowniku, jeśli używasz [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) do odwołania je z wewnątrz innego zasobu.</span><span class="sxs-lookup"><span data-stu-id="bb251-111">Resources are also requested by the order found within the dictionary if you use the [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) to reference them from within another resource.</span></span> <span data-ttu-id="bb251-112">Upewnij się, że wszystkich zasobów, do której odwołuje się zdefiniowano wcześniej w kolekcji zasobów niż gdzie jest następnie żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="bb251-112">Make sure that any resource that you reference is defined earlier within the resources collection than where that resource is then requested.</span></span> <span data-ttu-id="bb251-113">Jeśli to konieczne, można obejść, kolejność tworzenia strict refererences zasobów za pomocą [DynamicResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) można odwoływać się do zasobu w czasie wykonywania, ale pamiętaj, który to DynamicResource Metoda ma wpływ wydajności.</span><span class="sxs-lookup"><span data-stu-id="bb251-113">If necessary, you can work around the strict creation order of resource refererences by using a [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) to reference the resource at runtime instead, but you should be aware that this DynamicResource technique has performance consequences.</span></span> <span data-ttu-id="bb251-114">Aby uzyskać więcej informacji, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="bb251-114">For details, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a><span data-ttu-id="bb251-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb251-115">See Also</span></span>  
 [<span data-ttu-id="bb251-116">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="bb251-116">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="bb251-117">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="bb251-117">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
