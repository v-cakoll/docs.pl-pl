---
title: 'Instrukcje: Zarejestruj dołączoną właściwość'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
ms.openlocfilehash: 3cbbc8a1ea8419df408cda76de3459be9464a100
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377719"
---
# <a name="how-to-register-an-attached-property"></a><span data-ttu-id="556fd-102">Instrukcje: Zarejestruj dołączoną właściwość</span><span class="sxs-lookup"><span data-stu-id="556fd-102">How to: Register an Attached Property</span></span>
<span data-ttu-id="556fd-103">W tym przykładzie pokazano, jak zarejestrować dołączoną właściwość i podaj publiczne metody dostępu, tak, aby można było używać właściwości w obu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i kod.</span><span class="sxs-lookup"><span data-stu-id="556fd-103">This example shows how to register an attached property and provide public accessors so that you can use the property in both [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span> <span data-ttu-id="556fd-104">Dołączone właściwości to pojęcie składni zdefiniowane przez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="556fd-104">Attached properties are a syntax concept defined by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="556fd-105">Najbardziej dołączonych właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typy również są implementowane jako właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="556fd-105">Most attached properties for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] types are also implemented as dependency properties.</span></span> <span data-ttu-id="556fd-106">Można użyć właściwości zależności na dowolnym <xref:System.Windows.DependencyObject> typów.</span><span class="sxs-lookup"><span data-stu-id="556fd-106">You can use dependency properties on any <xref:System.Windows.DependencyObject> types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="556fd-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="556fd-107">Example</span></span>  
 <span data-ttu-id="556fd-108">Poniższy przykład pokazuje, jak zarejestrować dołączoną właściwość jako właściwość zależności za pomocą <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="556fd-108">The following example shows how to register an attached property as a dependency property, by using the <xref:System.Windows.DependencyProperty.RegisterAttached%2A> method.</span></span> <span data-ttu-id="556fd-109">Klasa dostawcy ma możliwość związanych z udostępnianiem domyślne metadane dla właściwości, która ma zastosowanie, gdy jest używana w innej klasy, chyba że ta klasa zastępuje metadanych.</span><span class="sxs-lookup"><span data-stu-id="556fd-109">The provider class has the option of providing default metadata for the property that is applicable when the property is used on another class, unless that class overrides the metadata.</span></span> <span data-ttu-id="556fd-110">W tym przykładzie wartość domyślną `IsBubbleSource` właściwość jest ustawiona na `false`.</span><span class="sxs-lookup"><span data-stu-id="556fd-110">In this example, the default value of the `IsBubbleSource` property is set to `false`.</span></span>  
  
 <span data-ttu-id="556fd-111">Klasa dostawcy dołączone właściwości (nawet jeśli nie jest zarejestrowany jako właściwość zależności) należy podać get statycznych i metod dostępu set, które przestrzegać konwencji nazewnictwa `Set` *[AttachedPropertyName]* i `Get` *[AttachedPropertyName]*.</span><span class="sxs-lookup"><span data-stu-id="556fd-111">The provider class for an attached property (even if it is not registered as a dependency property) must provide static get and set accessors that follow the naming convention `Set`*[AttachedPropertyName]* and `Get`*[AttachedPropertyName]*.</span></span> <span data-ttu-id="556fd-112">Te metody dostępu są wymagane, aby działający [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] czytnika rozpoznać właściwości jako atrybut w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i rozwiąż odpowiednie typy.</span><span class="sxs-lookup"><span data-stu-id="556fd-112">These accessors are required so that the acting [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader can recognize the property as an attribute in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and resolve the appropriate types.</span></span>  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a><span data-ttu-id="556fd-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="556fd-113">See also</span></span>
- <xref:System.Windows.DependencyProperty>
- [<span data-ttu-id="556fd-114">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="556fd-114">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="556fd-115">Niestandardowe właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="556fd-115">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="556fd-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="556fd-116">How-to Topics</span></span>](properties-how-to-topics.md)
