---
title: 'Instrukcje: Implementowanie właściwości zależności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: e2f18cb3941be2ebf4315a844c05b91ff49c6aa2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223804"
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="24dc2-102">Instrukcje: Implementowanie właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="24dc2-102">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="24dc2-103">W tym przykładzie pokazano, jak utworzyć kopię [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwość o <xref:System.Windows.DependencyProperty> pola, w związku z tym Definiowanie właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="24dc2-103">This example shows how to back a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="24dc2-104">Podczas definiowania własnych właściwości i chcesz, aby obsługiwać wiele aspektów [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcje, w tym stylów, powiązań danych, dziedziczenie, animacji i wartości domyślne należy go wdrożyć jako właściwość zależności.</span><span class="sxs-lookup"><span data-stu-id="24dc2-104">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24dc2-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="24dc2-105">Example</span></span>  
 <span data-ttu-id="24dc2-106">Poniższy przykład najpierw rejestruje właściwości zależności, wywołując <xref:System.Windows.DependencyProperty.Register%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="24dc2-106">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="24dc2-107">Nazwa pola identyfikatora, które umożliwiają przechowywanie nazwy i właściwości właściwość zależności musi być <xref:System.Windows.DependencyProperty.Name%2A> został wybrany dla właściwości zależności w ramach <xref:System.Windows.DependencyProperty.Register%2A> wywołanie, uzupełnione przez ciąg literału `Property`.</span><span class="sxs-lookup"><span data-stu-id="24dc2-107">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="24dc2-108">Na przykład jeśli Zarejestruj właściwości zależności za pomocą <xref:System.Windows.DependencyProperty.Name%2A> z `Location`, muszą być nazwane pole identyfikatora, który zdefiniujesz dla właściwości zależności, a następnie `LocationProperty`.</span><span class="sxs-lookup"><span data-stu-id="24dc2-108">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="24dc2-109">W tym przykładzie nazwa właściwości zależności i jego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] akcesor jest `State`; to pole identyfikatora `StateProperty`; typ właściwości to <xref:System.Boolean>; i typ, który rejestruje właściwość zależności jest `MyStateControl`.</span><span class="sxs-lookup"><span data-stu-id="24dc2-109">In this example, the name of the dependency property and its [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="24dc2-110">Jeśli nie korzystać z tego wzoru nazewnictwa, projektantów może nie raportować Twoja własność prawidłowo i niektóre aspekty stosowanie stylu systemu właściwości mogą nie zachowywać się zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="24dc2-110">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="24dc2-111">Można również określić domyślne metadane dla właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="24dc2-111">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="24dc2-112">W tym przykładzie rejestruje wartość domyślną `State` właściwości zależności `false`.</span><span class="sxs-lookup"><span data-stu-id="24dc2-112">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="24dc2-113">Aby uzyskać więcej informacji o tym, jak i dlaczego implementować właściwość zależności, a nie tylko tworzenie kopii [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Zobacz właściwość z polem prywatnej [Przegląd właściwości zależności](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="24dc2-113">For more information about how and why to implement a dependency property, as opposed to just backing a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property with a private field, see [Dependency Properties Overview](dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24dc2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24dc2-114">See also</span></span>

- [<span data-ttu-id="24dc2-115">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="24dc2-115">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="24dc2-116">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="24dc2-116">How-to Topics</span></span>](properties-how-to-topics.md)
