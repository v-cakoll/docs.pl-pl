---
title: 'Instrukcje: Użyj SystemFonts'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: bf99d716c5c41b7604244022d2e58423594a9cf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674875"
---
# <a name="how-to-use-systemfonts"></a><span data-ttu-id="9660c-102">Instrukcje: Użyj SystemFonts</span><span class="sxs-lookup"><span data-stu-id="9660c-102">How to: Use SystemFonts</span></span>
<span data-ttu-id="9660c-103">W tym przykładzie pokazano, jak korzystać z zasobów statycznych <xref:System.Windows.SystemFonts> klasy do nadawania stylu lub dostosować przycisku.</span><span class="sxs-lookup"><span data-stu-id="9660c-103">This example shows how to use the static resources of the <xref:System.Windows.SystemFonts> class in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9660c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9660c-104">Example</span></span>  
 <span data-ttu-id="9660c-105">Zasobów systemowych uwidocznić kilka wartości określić systemu jako zarówno z zasobów i właściwości, aby można było pomocne podczas tworzenia wizualizacji, które są zgodne z ustawieniami systemu.</span><span class="sxs-lookup"><span data-stu-id="9660c-105">System resources expose several system-determined values as both resources and properties in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="9660c-106"><xref:System.Windows.SystemFonts> jest to klasa, która zawiera obie wartości czcionki systemu jako właściwości statycznych i właściwości, które odwołują się klucze zasobów, których można użyć, aby uzyskać dostęp do tych wartości dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9660c-106"><xref:System.Windows.SystemFonts> is a class that contains both system font values as static properties, and properties that reference resource keys that can be used to access those values dynamically at run time.</span></span> <span data-ttu-id="9660c-107">Na przykład <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> jest <xref:System.Windows.SystemFonts> wartości, a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> jest odpowiedni klucz zasobu.</span><span class="sxs-lookup"><span data-stu-id="9660c-107">For example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> is a <xref:System.Windows.SystemFonts> value, and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> is a corresponding resource key.</span></span>  
  
 <span data-ttu-id="9660c-108">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można użyć elementów członkowskich <xref:System.Windows.SystemFonts> jako właściwości statyczne lub odwołania do zasobów dynamicznej (wartością właściwości statycznej jako klucz).</span><span class="sxs-lookup"><span data-stu-id="9660c-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemFonts> as either static properties or dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="9660c-109">Użyj odwołania zasób dynamiczny, jeśli chcesz, aby metryki czcionki do automatycznego aktualizowania podczas jej uruchomieniu; w przeciwnym razie użyj odwołania wartość statyczną.</span><span class="sxs-lookup"><span data-stu-id="9660c-109">Use a dynamic resource reference if you want the font metric to automatically update while the application runs; otherwise, use a static value reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9660c-110">Klucze zasobu ma sufiks "Key" dołączony do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="9660c-110">The resource keys have the suffix "Key" appended to the property name.</span></span>  
  
 <span data-ttu-id="9660c-111">Poniższy przykład pokazuje, jak uzyskać dostęp do właściwości <xref:System.Windows.SystemFonts> jako statyczne wartości do nadawania stylu lub dostosować przycisku.</span><span class="sxs-lookup"><span data-stu-id="9660c-111">The following example shows how to access and use the properties of <xref:System.Windows.SystemFonts> as static values in order to style or customize a button.</span></span> <span data-ttu-id="9660c-112">W tym przykładzie znaczników przypisuje <xref:System.Windows.SystemFonts> wartości do przycisku.</span><span class="sxs-lookup"><span data-stu-id="9660c-112">This markup example assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 <span data-ttu-id="9660c-113">Aby użyć wartości <xref:System.Windows.SystemFonts> w kodzie, nie trzeba użyć wartość statyczną lub odwołanie do zasobu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="9660c-113">To use the values of <xref:System.Windows.SystemFonts> in code, you do not have to use either a static value or a dynamic resource reference.</span></span> <span data-ttu-id="9660c-114">Zamiast tego należy użyć właściwości klucza <xref:System.Windows.SystemFonts> klasy.</span><span class="sxs-lookup"><span data-stu-id="9660c-114">Instead, use the non-key properties of the <xref:System.Windows.SystemFonts> class.</span></span> <span data-ttu-id="9660c-115">Mimo że niekluczowych właściwości najwyraźniej są definiowane jako właściwości statyczne zachowania w czasie wykonywania z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako hostowanej przez system spowoduje to ponowne ocenienie właściwości w czasie rzeczywistym i prawidłowo będzie uwzględniać zmiany wartości systemu oparte na użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9660c-115">Although the non-key properties are apparently defined as static properties, the run-time behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in real time and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="9660c-116">Poniższy przykład pokazuje, jak określić ustawienia czcionki przycisku.</span><span class="sxs-lookup"><span data-stu-id="9660c-116">The following example shows how to specify the font settings of a button.</span></span>  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="9660c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9660c-117">See also</span></span>
- <xref:System.Windows.SystemFonts>
- [<span data-ttu-id="9660c-118">Malowanie obszaru pędzlem systemowym</span><span class="sxs-lookup"><span data-stu-id="9660c-118">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="9660c-119">Używanie elementu SystemParameters</span><span class="sxs-lookup"><span data-stu-id="9660c-119">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
- [<span data-ttu-id="9660c-120">Używanie kluczy czcionek systemowych</span><span class="sxs-lookup"><span data-stu-id="9660c-120">Use System Fonts Keys</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-system-fonts-keys.md)
- [<span data-ttu-id="9660c-121">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="9660c-121">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
- [<span data-ttu-id="9660c-122">x:Static, rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="9660c-122">x:Static Markup Extension</span></span>](../../../../docs/framework/xaml-services/x-static-markup-extension.md)
- [<span data-ttu-id="9660c-123">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="9660c-123">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)
- [<span data-ttu-id="9660c-124">DynamicResource, rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="9660c-124">DynamicResource Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
