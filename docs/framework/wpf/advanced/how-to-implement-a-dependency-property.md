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
ms.openlocfilehash: 6f2fb9b0824feb6253527de063f58da2427d0c06
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400359"
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="de163-102">Instrukcje: Implementowanie właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="de163-102">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="de163-103">Ten przykład pokazuje, jak wykonać kopię zapasową właściwości środowiska uruchomieniowego języka wspólnego <xref:System.Windows.DependencyProperty> (CLR) za pomocą pola, w ten sposób definiując właściwość zależności.</span><span class="sxs-lookup"><span data-stu-id="de163-103">This example shows how to back a common language runtime (CLR) property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="de163-104">Podczas definiowania własnych właściwości i chcą one obsługiwać wiele aspektów [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcjonalności, w tym style, powiązanie danych, dziedziczenie, animację i wartości domyślne, należy zaimplementować je jako właściwość zależności.</span><span class="sxs-lookup"><span data-stu-id="de163-104">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de163-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="de163-105">Example</span></span>  
 <span data-ttu-id="de163-106">Poniższy przykład najpierw rejestruje właściwość zależności przez wywołanie <xref:System.Windows.DependencyProperty.Register%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="de163-106">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="de163-107">Nazwa pola identyfikatora służącego do przechowywania nazwy i właściwości zależności musi być <xref:System.Windows.DependencyProperty.Name%2A> wybrana dla właściwości zależności jako część <xref:System.Windows.DependencyProperty.Register%2A> wywołania, dołączona przez ciąg `Property`literału.</span><span class="sxs-lookup"><span data-stu-id="de163-107">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="de163-108">Na przykład jeśli zostanie zarejestrowana właściwość zależności z <xref:System.Windows.DependencyProperty.Name%2A> `Location`, wówczas pole identyfikatora zdefiniowane dla właściwości zależności musi mieć nazwę `LocationProperty`.</span><span class="sxs-lookup"><span data-stu-id="de163-108">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="de163-109">W tym przykładzie nazwa właściwości Dependency i jej metoda dostępu CLR `State`to; pole identyfikatora to `StateProperty`; typ właściwości to <xref:System.Boolean>;, a typ, który rejestruje właściwość zależności, to `MyStateControl`.</span><span class="sxs-lookup"><span data-stu-id="de163-109">In this example, the name of the dependency property and its CLR accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="de163-110">Jeśli ten wzorzec nazewnictwa nie zostanie zgodny, projektanci mogą nie zgłosić swojej właściwości prawidłowo, a niektóre aspekty aplikacji stylu systemu właściwości mogą nie zachowywać się zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="de163-110">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="de163-111">Można również określić domyślne metadane dla właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="de163-111">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="de163-112">Ten przykład rejestruje wartość `State` domyślną właściwości `false`zależności.</span><span class="sxs-lookup"><span data-stu-id="de163-112">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="de163-113">Aby uzyskać więcej informacji o tym, jak i dlaczego zaimplementować właściwość zależności, w przeciwieństwie do tylko wykonywania kopii zapasowej właściwości CLR z polem prywatnym, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="de163-113">For more information about how and why to implement a dependency property, as opposed to just backing a CLR property with a private field, see [Dependency Properties Overview](dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de163-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de163-114">See also</span></span>

- [<span data-ttu-id="de163-115">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="de163-115">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="de163-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="de163-116">How-to Topics</span></span>](properties-how-to-topics.md)
