---
title: "Jak zarejestrować dołączoną właściwość"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37c727eee7b56473808fec06ea42044fc742f7f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-an-attached-property"></a><span data-ttu-id="28a30-102">Jak zarejestrować dołączoną właściwość</span><span class="sxs-lookup"><span data-stu-id="28a30-102">How to: Register an Attached Property</span></span>
<span data-ttu-id="28a30-103">W tym przykładzie pokazano, jak zarejestrować dołączona właściwość i zapewnia metody dostępu publicznego, dzięki czemu można użyć właściwości zarówno [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i kod.</span><span class="sxs-lookup"><span data-stu-id="28a30-103">This example shows how to register an attached property and provide public accessors so that you can use the property in both [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span> <span data-ttu-id="28a30-104">Dołączone właściwości są koncepcji składni zdefiniowane przez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="28a30-104">Attached properties are a syntax concept defined by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="28a30-105">Najbardziej dołączonych właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typy również są zaimplementowane jako właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="28a30-105">Most attached properties for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] types are also implemented as dependency properties.</span></span> <span data-ttu-id="28a30-106">Można użyć właściwości zależności na dowolnym <xref:System.Windows.DependencyObject> typów.</span><span class="sxs-lookup"><span data-stu-id="28a30-106">You can use dependency properties on any <xref:System.Windows.DependencyObject> types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28a30-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="28a30-107">Example</span></span>  
 <span data-ttu-id="28a30-108">Poniższy przykład pokazuje, jak zarejestrować dołączona właściwość jako właściwość zależności, przy użyciu <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="28a30-108">The following example shows how to register an attached property as a dependency property, by using the <xref:System.Windows.DependencyProperty.RegisterAttached%2A> method.</span></span> <span data-ttu-id="28a30-109">Klasa dostawcy ma możliwość zapewnienia domyślne metadane dla właściwości, która ma zastosowanie, gdy jest używana w innej klasy, chyba że tej klasy zastępuje metadane.</span><span class="sxs-lookup"><span data-stu-id="28a30-109">The provider class has the option of providing default metadata for the property that is applicable when the property is used on another class, unless that class overrides the metadata.</span></span> <span data-ttu-id="28a30-110">W tym przykładzie wartość domyślną `IsBubbleSource` właściwość jest ustawiona na `false`.</span><span class="sxs-lookup"><span data-stu-id="28a30-110">In this example, the default value of the `IsBubbleSource` property is set to `false`.</span></span>  
  
 <span data-ttu-id="28a30-111">Klasa dostawcy dla właściwości dołączonej (nawet jeśli nie jest zarejestrowany jako właściwość zależności), należy podać statyczne get i metody dostępu set, które postępuj zgodnie z konwencją nazewnictwa `Set` *[AttachedPropertyName]* i `Get` *[AttachedPropertyName]*.</span><span class="sxs-lookup"><span data-stu-id="28a30-111">The provider class for an attached property (even if it is not registered as a dependency property) must provide static get and set accessors that follow the naming convention `Set`*[AttachedPropertyName]* and `Get`*[AttachedPropertyName]*.</span></span> <span data-ttu-id="28a30-112">Te metody dostępu są wymagane, aby działający [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] czytnika rozpoznać właściwości jako atrybut w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i rozwiąż odpowiednie typy.</span><span class="sxs-lookup"><span data-stu-id="28a30-112">These accessors are required so that the acting [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader can recognize the property as an attribute in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and resolve the appropriate types.</span></span>  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a><span data-ttu-id="28a30-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28a30-113">See Also</span></span>  
 <xref:System.Windows.DependencyProperty>  
 [<span data-ttu-id="28a30-114">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="28a30-114">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="28a30-115">Niestandardowe właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="28a30-115">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="28a30-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="28a30-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
