---
title: 'Porady: korzystanie z SystemFonts'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 63ba7a6fb1c8776cc35c0e6f07a6b78f5b3d93d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459506"
---
# <a name="how-to-use-systemfonts"></a><span data-ttu-id="25498-102">Porady: korzystanie z SystemFonts</span><span class="sxs-lookup"><span data-stu-id="25498-102">How to: Use SystemFonts</span></span>
<span data-ttu-id="25498-103">Ten przykład pokazuje, jak używać zasobów statycznych klasy <xref:System.Windows.SystemFonts> w celu uzyskania stylu lub dostosowania przycisku.</span><span class="sxs-lookup"><span data-stu-id="25498-103">This example shows how to use the static resources of the <xref:System.Windows.SystemFonts> class in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25498-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="25498-104">Example</span></span>  
 <span data-ttu-id="25498-105">Zasoby systemowe uwidaczniają kilka wartości określanych przez system jako zasoby i właściwości w celu ułatwienia tworzenia wizualizacji, które są spójne z ustawieniami systemowymi.</span><span class="sxs-lookup"><span data-stu-id="25498-105">System resources expose several system-determined values as both resources and properties in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="25498-106"><xref:System.Windows.SystemFonts> jest klasą, która zawiera obie wartości czcionki systemowej jako właściwości statyczne i właściwości, które odwołują się do kluczy zasobów, których można użyć do dynamicznego uzyskiwania dostępu do tych wartości w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="25498-106"><xref:System.Windows.SystemFonts> is a class that contains both system font values as static properties, and properties that reference resource keys that can be used to access those values dynamically at run time.</span></span> <span data-ttu-id="25498-107">Na przykład <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> jest wartością <xref:System.Windows.SystemFonts>, a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> jest odpowiednim kluczem zasobu.</span><span class="sxs-lookup"><span data-stu-id="25498-107">For example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> is a <xref:System.Windows.SystemFonts> value, and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> is a corresponding resource key.</span></span>  
  
 <span data-ttu-id="25498-108">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]można użyć elementów członkowskich <xref:System.Windows.SystemFonts> jako właściwości statycznych lub dynamicznych odwołań do zasobów (z wartością właściwości statycznej jako klucz).</span><span class="sxs-lookup"><span data-stu-id="25498-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemFonts> as either static properties or dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="25498-109">Użyj odwołania do zasobów dynamicznych, jeśli chcesz, aby Metryka czcionki była automatycznie aktualizowana podczas uruchamiania aplikacji; w przeciwnym razie użyj statycznego odwołania do wartości.</span><span class="sxs-lookup"><span data-stu-id="25498-109">Use a dynamic resource reference if you want the font metric to automatically update while the application runs; otherwise, use a static value reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25498-110">Klucze zasobów mają sufiks "klucz" dołączony do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="25498-110">The resource keys have the suffix "Key" appended to the property name.</span></span>  
  
 <span data-ttu-id="25498-111">Poniższy przykład pokazuje, jak uzyskać dostęp do właściwości <xref:System.Windows.SystemFonts> jako wartości statycznych i używać ich w celu uzyskania stylu lub dostosowywania przycisku.</span><span class="sxs-lookup"><span data-stu-id="25498-111">The following example shows how to access and use the properties of <xref:System.Windows.SystemFonts> as static values in order to style or customize a button.</span></span> <span data-ttu-id="25498-112">Ten przykład znacznika służy do przypisywania wartości <xref:System.Windows.SystemFonts> do przycisku.</span><span class="sxs-lookup"><span data-stu-id="25498-112">This markup example assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 <span data-ttu-id="25498-113">Aby użyć wartości <xref:System.Windows.SystemFonts> w kodzie, nie trzeba używać wartości statycznej ani dynamicznego odwołania do zasobów.</span><span class="sxs-lookup"><span data-stu-id="25498-113">To use the values of <xref:System.Windows.SystemFonts> in code, you do not have to use either a static value or a dynamic resource reference.</span></span> <span data-ttu-id="25498-114">Zamiast tego należy użyć właściwości, które nie są kluczami klasy <xref:System.Windows.SystemFonts>.</span><span class="sxs-lookup"><span data-stu-id="25498-114">Instead, use the non-key properties of the <xref:System.Windows.SystemFonts> class.</span></span> <span data-ttu-id="25498-115">Chociaż właściwości, które nie są kluczami, są prawdopodobnie zdefiniowane jako właściwości statyczne, zachowanie w czasie wykonywania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], które jest hostowane przez system, będzie ponownie szacować właściwości w czasie rzeczywistym i będzie prawidłowo obsługiwać zmiany wartości systemu przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="25498-115">Although the non-key properties are apparently defined as static properties, the run-time behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in real time and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="25498-116">Poniższy przykład pokazuje, jak określić ustawienia czcionki przycisku.</span><span class="sxs-lookup"><span data-stu-id="25498-116">The following example shows how to specify the font settings of a button.</span></span>  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="25498-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25498-117">See also</span></span>

- <xref:System.Windows.SystemFonts>
- [<span data-ttu-id="25498-118">Malowanie obszaru pędzlem systemowym</span><span class="sxs-lookup"><span data-stu-id="25498-118">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="25498-119">Używanie elementu SystemParameters</span><span class="sxs-lookup"><span data-stu-id="25498-119">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="25498-120">Używanie kluczy czcionek systemowych</span><span class="sxs-lookup"><span data-stu-id="25498-120">Use System Fonts Keys</span></span>](how-to-use-system-fonts-keys.md)
- [<span data-ttu-id="25498-121">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="25498-121">How-to Topics</span></span>](resources-how-to-topics.md)
- [<span data-ttu-id="25498-122">x:Static, rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="25498-122">x:Static Markup Extension</span></span>](../../xaml-services/x-static-markup-extension.md)
- [<span data-ttu-id="25498-123">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="25498-123">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="25498-124">DynamicResource, rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="25498-124">DynamicResource Markup Extension</span></span>](dynamicresource-markup-extension.md)
