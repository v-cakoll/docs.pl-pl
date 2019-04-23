---
title: 'Instrukcje: Używanie elementu SystemFonts'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 5976bc0cb8b34e68d5e89dd70a608d7e52ded332
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216785"
---
# <a name="how-to-use-systemfonts"></a><span data-ttu-id="dab59-102">Instrukcje: Używanie elementu SystemFonts</span><span class="sxs-lookup"><span data-stu-id="dab59-102">How to: Use SystemFonts</span></span>
<span data-ttu-id="dab59-103">W tym przykładzie pokazano, jak korzystać z zasobów statycznych <xref:System.Windows.SystemFonts> klasy do nadawania stylu lub dostosować przycisku.</span><span class="sxs-lookup"><span data-stu-id="dab59-103">This example shows how to use the static resources of the <xref:System.Windows.SystemFonts> class in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dab59-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="dab59-104">Example</span></span>  
 <span data-ttu-id="dab59-105">Zasobów systemowych uwidocznić kilka wartości określić systemu jako zarówno z zasobów i właściwości, aby można było pomocne podczas tworzenia wizualizacji, które są zgodne z ustawieniami systemu.</span><span class="sxs-lookup"><span data-stu-id="dab59-105">System resources expose several system-determined values as both resources and properties in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="dab59-106"><xref:System.Windows.SystemFonts> jest to klasa, która zawiera obie wartości czcionki systemu jako właściwości statycznych i właściwości, które odwołują się klucze zasobów, których można użyć, aby uzyskać dostęp do tych wartości dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dab59-106"><xref:System.Windows.SystemFonts> is a class that contains both system font values as static properties, and properties that reference resource keys that can be used to access those values dynamically at run time.</span></span> <span data-ttu-id="dab59-107">Na przykład <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> jest <xref:System.Windows.SystemFonts> wartości, a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> jest odpowiedni klucz zasobu.</span><span class="sxs-lookup"><span data-stu-id="dab59-107">For example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> is a <xref:System.Windows.SystemFonts> value, and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> is a corresponding resource key.</span></span>  
  
 <span data-ttu-id="dab59-108">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można użyć elementów członkowskich <xref:System.Windows.SystemFonts> jako właściwości statyczne lub odwołania do zasobów dynamicznej (wartością właściwości statycznej jako klucz).</span><span class="sxs-lookup"><span data-stu-id="dab59-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemFonts> as either static properties or dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="dab59-109">Użyj odwołania zasób dynamiczny, jeśli chcesz, aby metryki czcionki do automatycznego aktualizowania podczas jej uruchomieniu; w przeciwnym razie użyj odwołania wartość statyczną.</span><span class="sxs-lookup"><span data-stu-id="dab59-109">Use a dynamic resource reference if you want the font metric to automatically update while the application runs; otherwise, use a static value reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dab59-110">Klucze zasobu ma sufiks "Key" dołączony do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="dab59-110">The resource keys have the suffix "Key" appended to the property name.</span></span>  
  
 <span data-ttu-id="dab59-111">Poniższy przykład pokazuje, jak uzyskać dostęp do właściwości <xref:System.Windows.SystemFonts> jako statyczne wartości do nadawania stylu lub dostosować przycisku.</span><span class="sxs-lookup"><span data-stu-id="dab59-111">The following example shows how to access and use the properties of <xref:System.Windows.SystemFonts> as static values in order to style or customize a button.</span></span> <span data-ttu-id="dab59-112">W tym przykładzie znaczników przypisuje <xref:System.Windows.SystemFonts> wartości do przycisku.</span><span class="sxs-lookup"><span data-stu-id="dab59-112">This markup example assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 <span data-ttu-id="dab59-113">Aby użyć wartości <xref:System.Windows.SystemFonts> w kodzie, nie trzeba użyć wartość statyczną lub odwołanie do zasobu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="dab59-113">To use the values of <xref:System.Windows.SystemFonts> in code, you do not have to use either a static value or a dynamic resource reference.</span></span> <span data-ttu-id="dab59-114">Zamiast tego należy użyć właściwości klucza <xref:System.Windows.SystemFonts> klasy.</span><span class="sxs-lookup"><span data-stu-id="dab59-114">Instead, use the non-key properties of the <xref:System.Windows.SystemFonts> class.</span></span> <span data-ttu-id="dab59-115">Mimo że niekluczowych właściwości najwyraźniej są definiowane jako właściwości statyczne zachowania w czasie wykonywania z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako hostowanej przez system spowoduje to ponowne ocenienie właściwości w czasie rzeczywistym i prawidłowo będzie uwzględniać zmiany wartości systemu oparte na użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dab59-115">Although the non-key properties are apparently defined as static properties, the run-time behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in real time and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="dab59-116">Poniższy przykład pokazuje, jak określić ustawienia czcionki przycisku.</span><span class="sxs-lookup"><span data-stu-id="dab59-116">The following example shows how to specify the font settings of a button.</span></span>  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="dab59-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dab59-117">See also</span></span>

- <xref:System.Windows.SystemFonts>
- [<span data-ttu-id="dab59-118">Malowanie obszaru pędzlem systemowym</span><span class="sxs-lookup"><span data-stu-id="dab59-118">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="dab59-119">Używanie elementu SystemParameters</span><span class="sxs-lookup"><span data-stu-id="dab59-119">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="dab59-120">Używanie kluczy czcionek systemowych</span><span class="sxs-lookup"><span data-stu-id="dab59-120">Use System Fonts Keys</span></span>](how-to-use-system-fonts-keys.md)
- [<span data-ttu-id="dab59-121">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="dab59-121">How-to Topics</span></span>](resources-how-to-topics.md)
- [<span data-ttu-id="dab59-122">x:Static, rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="dab59-122">x:Static Markup Extension</span></span>](../../xaml-services/x-static-markup-extension.md)
- [<span data-ttu-id="dab59-123">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="dab59-123">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="dab59-124">DynamicResource, rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="dab59-124">DynamicResource Markup Extension</span></span>](dynamicresource-markup-extension.md)
