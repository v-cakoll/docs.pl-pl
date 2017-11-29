---
title: "Jak implementować właściwość zależności"
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
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9bc4dee8f0b2eef76e5769ae7da3a13edf7c3300
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="da67e-102">Jak implementować właściwość zależności</span><span class="sxs-lookup"><span data-stu-id="da67e-102">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="da67e-103">W tym przykładzie pokazano, jak utworzyć kopię [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości o <xref:System.Windows.DependencyProperty> pola, w związku z tym Definiowanie właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="da67e-103">This example shows how to back a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="da67e-104">Podczas definiowania własnych właściwości i chcesz, aby obsługiwać wiele aspektów [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcje, w tym style, powiązanie danych dziedziczenia, animacji i wartości domyślne, należy je zaimplementować jako właściwość zależności.</span><span class="sxs-lookup"><span data-stu-id="da67e-104">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da67e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="da67e-105">Example</span></span>  
 <span data-ttu-id="da67e-106">Poniższy przykład najpierw rejestruje właściwości zależności przez wywołanie metody <xref:System.Windows.DependencyProperty.Register%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="da67e-106">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="da67e-107">Nazwa pola Identyfikator, który służy do przechowywania nazwy i właściwości właściwości zależności musi być <xref:System.Windows.DependencyProperty.Name%2A> wybrany dla właściwości zależności w ramach <xref:System.Windows.DependencyProperty.Register%2A> wywołanie przez ciąg literału `Property`.</span><span class="sxs-lookup"><span data-stu-id="da67e-107">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="da67e-108">Na przykład jeśli Zarejestruj właściwości zależności z <xref:System.Windows.DependencyProperty.Name%2A> z `Location`, następnie pole identyfikatora, dla właściwości zależności musi mieć nazwę `LocationProperty`.</span><span class="sxs-lookup"><span data-stu-id="da67e-108">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="da67e-109">W tym przykładzie nazwa właściwości zależności i jego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] akcesor jest `State`; to pole identyfikatora `StateProperty`; typ właściwości jest <xref:System.Boolean>; i typ, który rejestruje właściwość zależności jest `MyStateControl`.</span><span class="sxs-lookup"><span data-stu-id="da67e-109">In this example, the name of the dependency property and its [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="da67e-110">Jeśli nie należy wykonać ten wzorzec nazewnictwa, projektantów może nie raportować z właściwości prawidłowo i niektórych aspektów aplikacji styl systemu właściwość może nie działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="da67e-110">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="da67e-111">Można także określić domyślny metadane dla właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="da67e-111">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="da67e-112">W tym przykładzie rejestruje domyślną wartość `State` właściwości zależności, aby być `false`.</span><span class="sxs-lookup"><span data-stu-id="da67e-112">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="da67e-113">Aby uzyskać więcej informacji o tym, jak i dlaczego implementuje właściwości zależności, a nie tylko tworzenie kopii [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwość z polem prywatnych, zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da67e-113">For more information about how and why to implement a dependency property, as opposed to just backing a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property with a private field, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da67e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da67e-114">See Also</span></span>  
 [<span data-ttu-id="da67e-115">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="da67e-115">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="da67e-116">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="da67e-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
