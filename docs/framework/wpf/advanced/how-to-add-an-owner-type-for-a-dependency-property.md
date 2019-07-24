---
title: 'Instrukcje: Dodawanie typu właściciela dla właściwości zależności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: 5ddc85d159b4bf81751428c13c234c5e53be8ad4
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401135"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a><span data-ttu-id="47579-102">Instrukcje: Dodawanie typu właściciela dla właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="47579-102">How to: Add an Owner Type for a Dependency Property</span></span>
<span data-ttu-id="47579-103">Ten przykład pokazuje, jak dodać klasę jako właściciela właściwości zależności zarejestrowanej dla innego typu.</span><span class="sxs-lookup"><span data-stu-id="47579-103">This example shows how to add a class as an owner of a dependency property registered for a different type.</span></span> <span data-ttu-id="47579-104">W ten [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sposób czytnik i system właściwości mogą rozpoznać klasę jako dodatkowy właściciel właściwości.</span><span class="sxs-lookup"><span data-stu-id="47579-104">By doing this, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader and property system are both able to recognize the class as an additional owner of the property.</span></span> <span data-ttu-id="47579-105">Dodanie jako właściciela opcjonalnie zezwala na dodawanie metadanych specyficznych dla typu dla klasy.</span><span class="sxs-lookup"><span data-stu-id="47579-105">Adding as owner optionally allows the adding class to provide type-specific metadata.</span></span>  
  
 <span data-ttu-id="47579-106">W poniższym przykładzie `StateProperty` jest właściwością zarejestrowana `MyStateControl` przez klasę.</span><span class="sxs-lookup"><span data-stu-id="47579-106">In the following example, `StateProperty` is a property registered by the `MyStateControl` class.</span></span> <span data-ttu-id="47579-107">Klasa `UnrelatedStateControl` dodaje siebie jako właściciela `StateProperty` przy użyciu <xref:System.Windows.DependencyProperty.AddOwner%2A> metody, w odniesieniu do podpisu, który umożliwia nowe metadane dla właściwości zależności, która istnieje w typie Dodawanie.</span><span class="sxs-lookup"><span data-stu-id="47579-107">The class `UnrelatedStateControl` adds itself as an owner of the `StateProperty` using the <xref:System.Windows.DependencyProperty.AddOwner%2A> method, specifically using the signature that allows for new metadata for the dependency property as it exists on the adding type.</span></span> <span data-ttu-id="47579-108">Należy zauważyć, że należy zapewnić dostęp do środowiska uruchomieniowego języka wspólnego (CLR) dla właściwości, podobnie jak w przykładzie pokazanym w przykładowym [implementacji właściwości zależności](how-to-implement-a-dependency-property.md) , a także ponownego uwidocznić identyfikator właściwości zależności w klasie dodawanej jako właściciel.</span><span class="sxs-lookup"><span data-stu-id="47579-108">Notice that you should provide common language runtime (CLR) accessors for the property similar to the example shown in the [Implement a Dependency Property](how-to-implement-a-dependency-property.md) example, as well as re-expose the dependency property identifier on the class being added as owner.</span></span>  
  
 <span data-ttu-id="47579-109">Bez otok, właściwość zależności nadal będzie współpracować z perspektywą dostępu programistycznego przy użyciu <xref:System.Windows.DependencyObject.GetValue%2A> lub. <xref:System.Windows.DependencyObject.SetValue%2A></span><span class="sxs-lookup"><span data-stu-id="47579-109">Without wrappers, the dependency property would still work from the perspective of programmatic access using <xref:System.Windows.DependencyObject.GetValue%2A> or <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="47579-110">Zwykle jednak ma to na celu równoległe zachowanie systemu właściwości przy użyciu otok właściwości środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="47579-110">But you typically want to parallel this property-system behavior with the CLR property wrappers.</span></span> <span data-ttu-id="47579-111">Otoki ułatwiają programowo Ustawianie właściwości zależności i umożliwiają ustawianie właściwości jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutów.</span><span class="sxs-lookup"><span data-stu-id="47579-111">The wrappers make it easier to set the dependency property programmatically, and make it possible to set the properties as [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributes.</span></span>  
  
 <span data-ttu-id="47579-112">Aby dowiedzieć się, jak zastąpić domyślne metadane, zobacz [przesłanianie metadanych dla właściwości zależności](how-to-override-metadata-for-a-dependency-property.md).</span><span class="sxs-lookup"><span data-stu-id="47579-112">To find out how to override default metadata, see [Override Metadata for a Dependency Property](how-to-override-metadata-for-a-dependency-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="47579-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="47579-113">Example</span></span>  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="47579-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47579-114">See also</span></span>

- [<span data-ttu-id="47579-115">Niestandardowe właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="47579-115">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="47579-116">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="47579-116">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
