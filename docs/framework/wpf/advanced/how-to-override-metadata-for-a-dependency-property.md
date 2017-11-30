---
title: "Jak zastąpić metadane dla właściwości zależności"
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
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e7cb01c81b5fb24830cbe0cc39befbadaf4405e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a><span data-ttu-id="eddc1-102">Jak zastąpić metadane dla właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="eddc1-102">How to: Override Metadata for a Dependency Property</span></span>
<span data-ttu-id="eddc1-103">W tym przykładzie pokazano, jak zastąpić domyślny metadanych właściwości zależności, które pochodzi z klasy dziedziczonej, wywołując <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> — metoda i udostępnia metadane określonego typu.</span><span class="sxs-lookup"><span data-stu-id="eddc1-103">This example shows how to override default dependency property metadata that comes from an inherited class, by calling the <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> method and providing type-specific metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eddc1-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="eddc1-104">Example</span></span>  
 <span data-ttu-id="eddc1-105">Definiując jego <xref:System.Windows.PropertyMetadata>, klasy można zdefiniować właściwości zależności zachowania, takie jak jego domyślne wartości właściwości systemu wywołania zwrotne i.</span><span class="sxs-lookup"><span data-stu-id="eddc1-105">By defining its <xref:System.Windows.PropertyMetadata>, a class can define the dependency property's behaviors, such as its default value and property system callbacks.</span></span> <span data-ttu-id="eddc1-106">Wiele klas właściwość zależności jest już metadanych domyślne ustanowiony jako część procesu rejestracji.</span><span class="sxs-lookup"><span data-stu-id="eddc1-106">Many dependency property classes already have default metadata established as part of their registration process.</span></span> <span data-ttu-id="eddc1-107">Dotyczy to również właściwości zależności, które są częścią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eddc1-107">This includes the dependency properties that are part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)].</span></span> <span data-ttu-id="eddc1-108">Klasa, która dziedziczy właściwości zależności za pomocą jego dziedziczenia klas można zastąpić oryginalnych metadanych tak, aby właściwości właściwości, które można zmienić za pomocą metadanych będzie odpowiadała żadnych wymagań specyficznych dla podklasy.</span><span class="sxs-lookup"><span data-stu-id="eddc1-108">A class that inherits the dependency property through its class inheritance can override the original metadata so that the characteristics of the property that can be altered through metadata will match any subclass-specific requirements.</span></span>  
  
 <span data-ttu-id="eddc1-109">Zastępowanie metadanych dla właściwości zależności należy przeprowadzić przed tą właściwością zostanie umieszczona w użycia przez system właściwości (to jest równa godzinę, o której tworzone są określone wystąpienia obiektów, które rejestrują właściwości).</span><span class="sxs-lookup"><span data-stu-id="eddc1-109">Overriding metadata on a dependency property must be done prior to that property being placed in use by the property system (this equates to the time that specific instances of objects that register the property are instantiated).</span></span> <span data-ttu-id="eddc1-110">Wywołuje się <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> musi zostać wykonana konstruktorów statycznych typu, który udostępnia siebie jako `forType` parametr <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="eddc1-110">Calls to <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> must be performed within the static constructors of the type that provides itself as the `forType` parameter of <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>.</span></span> <span data-ttu-id="eddc1-111">Jeśli spróbujesz zmienić metadanych, gdy istnieje wystąpienie typu właściciela, to zostanie nie zgłaszaj wyjątków, ale spowoduje niespójność zachowania w systemie właściwości.</span><span class="sxs-lookup"><span data-stu-id="eddc1-111">If you attempt to change metadata once instances of the owner type exist, this will not raise exceptions, but will result in inconsistent behaviors in the property system.</span></span> <span data-ttu-id="eddc1-112">Ponadto metadane tylko można zastąpić raz dla typu.</span><span class="sxs-lookup"><span data-stu-id="eddc1-112">Also, metadata can only be overridden once per type.</span></span> <span data-ttu-id="eddc1-113">Kolejne próby na zastępowanie metadanych do tego samego typu zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="eddc1-113">Subsequent attempts to override metadata on the same type will raise an exception.</span></span>  
  
 <span data-ttu-id="eddc1-114">W poniższym przykładzie, niestandardowe klasy `MyAdvancedStateControl` zastępuje metadane podane dla `StateProperty` przez `MyAdvancedStateControl` o nowe metadane właściwości.</span><span class="sxs-lookup"><span data-stu-id="eddc1-114">In the following example, the custom class `MyAdvancedStateControl` overrides the metadata provided for `StateProperty` by `MyAdvancedStateControl` with new property metadata.</span></span> <span data-ttu-id="eddc1-115">Na przykład, wartość domyślna `StateProperty` jest teraz `true` gdy właściwość jest poddawany kwerendzie na nowo utworzone `MyAdvancedStateControl` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="eddc1-115">For instance, the default value of the `StateProperty` is now `true` when the property is queried on a newly constructed `MyAdvancedStateControl` instance.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="eddc1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eddc1-116">See Also</span></span>  
 <xref:System.Windows.DependencyProperty>  
 [<span data-ttu-id="eddc1-117">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="eddc1-117">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="eddc1-118">Właściwości niestandardowe zależności</span><span class="sxs-lookup"><span data-stu-id="eddc1-118">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="eddc1-119">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="eddc1-119">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
