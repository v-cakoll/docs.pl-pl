---
title: "ComponentResourceKey — Rozszerzenie znaczników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b7f959318c5991fea2df92ff8000e85345fb35ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="componentresourcekey-markup-extension"></a><span data-ttu-id="606c3-102">ComponentResourceKey — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="606c3-102">ComponentResourceKey Markup Extension</span></span>
<span data-ttu-id="606c3-103">Definiuje i odwołuje się do kluczy dla zasobów, które są ładowane z zewnętrznych zestawów.</span><span class="sxs-lookup"><span data-stu-id="606c3-103">Defines and references keys for resources that are loaded from external assemblies.</span></span> <span data-ttu-id="606c3-104">Dzięki temu wyszukiwania zasobów określić typ docelowy w zestawie, a nie słownika jawne zasobów w zestawie lub klasy.</span><span class="sxs-lookup"><span data-stu-id="606c3-104">This enables a resource lookup to specify a target type in an assembly, rather than an explicit resource dictionary in an assembly or on a class.</span></span>  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a><span data-ttu-id="606c3-105">Użycie atrybutu XAML (klucz Ustawienia, compact)</span><span class="sxs-lookup"><span data-stu-id="606c3-105">XAML Attribute Usage (setting key, compact)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a><span data-ttu-id="606c3-106">Użycie atrybutu XAML (ustawienie klucza, verbose)</span><span class="sxs-lookup"><span data-stu-id="606c3-106">XAML Attribute Usage (setting key, verbose)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a><span data-ttu-id="606c3-107">Użycie atrybutu XAML (żądania zasobów, compact)</span><span class="sxs-lookup"><span data-stu-id="606c3-107">XAML Attribute Usage (requesting resource, compact)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a><span data-ttu-id="606c3-108">Użycie atrybutu XAML (żądania zasobów, verbose)</span><span class="sxs-lookup"><span data-stu-id="606c3-108">XAML Attribute Usage (requesting resource, verbose)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="606c3-109">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="606c3-109">XAML Values</span></span>  
  
|||  
|-|-|  
|`targetTypeName`|<span data-ttu-id="606c3-110">Nazwa publicznego [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] typu, który jest zdefiniowany w zestawie zasobów.</span><span class="sxs-lookup"><span data-stu-id="606c3-110">The name of the public [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] type that is defined in the resource assembly.</span></span>|  
|`targetID`|<span data-ttu-id="606c3-111">Klucz zasobu.</span><span class="sxs-lookup"><span data-stu-id="606c3-111">The key for the resource.</span></span> <span data-ttu-id="606c3-112">Gdy zasoby są wyszukiwane, `targetID` jest odpowiednikiem [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) zasobu.</span><span class="sxs-lookup"><span data-stu-id="606c3-112">When resources are looked up, `targetID` will be analogous to the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) of the resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="606c3-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="606c3-113">Remarks</span></span>  
 <span data-ttu-id="606c3-114">Jak pokazano powyżej, użycia {`ComponentResourceKey`} użycie rozszerzenia znaczników znajduje się w dwóch miejscach:</span><span class="sxs-lookup"><span data-stu-id="606c3-114">As seen in the usages above, a {`ComponentResourceKey`} markup extension usage is found in two places:</span></span>  
  
-   <span data-ttu-id="606c3-115">Definicja klucz w słowniku zasobów motywu, określone przez autora formantu.</span><span class="sxs-lookup"><span data-stu-id="606c3-115">The definition of a key within a theme resource dictionary, as provided by a control author.</span></span>  
  
-   <span data-ttu-id="606c3-116">Dostęp do zasobów motyw z zestawu, jeżeli są retemplating formantu, ale chcesz użyć wartości właściwości, które pochodzą z zasobów udostępnianych przez motywy formantu.</span><span class="sxs-lookup"><span data-stu-id="606c3-116">Accessing a theme resource from the assembly, when you are retemplating the control but want to use property values that come from resources provided by the control's themes.</span></span>  
  
 <span data-ttu-id="606c3-117">Dla odwołania do składnika zasoby, które pochodzą z kompozycje, ogólnie zalecane jest używanie `{DynamicResource}` zamiast `{StaticResource}`.</span><span class="sxs-lookup"><span data-stu-id="606c3-117">For referencing component resources that come from themes, it is generally recommended that you use `{DynamicResource}` rather than `{StaticResource}`.</span></span> <span data-ttu-id="606c3-118">Przedstawiono to w użyciach.</span><span class="sxs-lookup"><span data-stu-id="606c3-118">This is shown in the usages.</span></span> <span data-ttu-id="606c3-119">`{DynamicResource}`jest zalecane, ponieważ można zmienić motyw się przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="606c3-119">`{DynamicResource}` is recommended because the theme itself can be changed by the user.</span></span> <span data-ttu-id="606c3-120">Chcąc zasobów składnika, najlepiej pasujący zamiar autora sterowania do obsługi motywu, należy włączyć składnik zasobów odwołania do dynamicznej można również.</span><span class="sxs-lookup"><span data-stu-id="606c3-120">If you want the component resource that most closely matches the control author's intent for supporting a theme, you should enable your component resource reference to be dynamic also.</span></span>  
  
 <span data-ttu-id="606c3-121"><xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Określa typ, który istnieje w zestawie docelowym, których zasób faktycznie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="606c3-121">The <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifies a type that exists in the target assembly where the resource is actually defined.</span></span> <span data-ttu-id="606c3-122">A `ComponentResourceKey` mogą być definiowane i używane niezależnie od wiedząc dokładnie gdzie <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> jest określony, ale ostatecznie musi rozpoznać typu za pomocą zestawów występujących w odwołaniach.</span><span class="sxs-lookup"><span data-stu-id="606c3-122">A `ComponentResourceKey` can be defined and used independently of knowing exactly where the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> is defined, but eventually must resolve the type through referenced assemblies.</span></span>  
  
 <span data-ttu-id="606c3-123">Użycie wspólnych <xref:System.Windows.ComponentResourceKey> jest określenie kluczy, które następnie są dostępne jako elementy członkowskie klasy.</span><span class="sxs-lookup"><span data-stu-id="606c3-123">A common usage for <xref:System.Windows.ComponentResourceKey> is to define keys that are then exposed as members of a class.</span></span> <span data-ttu-id="606c3-124">W przypadku użycia, możesz używać <xref:System.Windows.ComponentResourceKey> konstruktora klasy, nie rozszerzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="606c3-124">For this usage, you use the <xref:System.Windows.ComponentResourceKey> class constructor, not the markup extension.</span></span> <span data-ttu-id="606c3-125">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.ComponentResourceKey>, lub w części "Definiowanie i odwołuje się do kluczy dla motywu zasoby" tematu [informacje o formancie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="606c3-125">For more information, see <xref:System.Windows.ComponentResourceKey>, or the "Defining and Referencing Keys for Theme Resources" section of the topic [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="606c3-126">Dla zarówno ustanawiania kluczy i odwołuje się do zasobów z kluczem, składnia atrybutu jest najczęściej używana w `ComponentResourceKey` — rozszerzenie znaczników.</span><span class="sxs-lookup"><span data-stu-id="606c3-126">For both establishing keys and referencing keyed resources, attribute syntax is commonly used for the `ComponentResourceKey` markup extension.</span></span>  
  
 <span data-ttu-id="606c3-127">Zależy od zwięzłą składnią pokazano <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> sygnatury konstruktora i korzystaniu z parametrów pozycyjnych rozszerzenia znacznika.</span><span class="sxs-lookup"><span data-stu-id="606c3-127">The compact syntax shown relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> constructor signature and positional parameter usage of a markup extension.</span></span> <span data-ttu-id="606c3-128">Kolejność `targetTypeName` i `targetID` podano jest ważna.</span><span class="sxs-lookup"><span data-stu-id="606c3-128">The order in which the `targetTypeName` and `targetID` are given is important.</span></span> <span data-ttu-id="606c3-129">Pełna składnia polega na <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> Konstruktor domyślny, a następnie ustawia <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> w taki sposób, który jest odpowiednikiem Składnia atrybutu wartość true w elemencie obiektu.</span><span class="sxs-lookup"><span data-stu-id="606c3-129">The verbose syntax relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> default constructor, and then sets the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> in a way that is analogous to a true attribute syntax on an object element.</span></span> <span data-ttu-id="606c3-130">W Pełna składnia kolejność, w którym są ustawione właściwości nie jest ważna.</span><span class="sxs-lookup"><span data-stu-id="606c3-130">In the verbose syntax, the order in which the properties are set is not important.</span></span> <span data-ttu-id="606c3-131">Relacja i mechanizmów tych dwóch alternatyw (compact i pełne) jest opisany bardziej szczegółowo w temacie [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="606c3-131">The relationship and mechanisms of these two alternatives (compact and verbose) is described in more detail in the topic [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="606c3-132">Z technicznego punktu widzenia wartość `targetID` może być dowolny obiekt, ale nie musi być ciągiem.</span><span class="sxs-lookup"><span data-stu-id="606c3-132">Technically, the value for `targetID` can be any object, it does not have to be a string.</span></span> <span data-ttu-id="606c3-133">Jednak najbardziej typowe obciążenie na platformie WPF jest, aby były wyrównane `targetID` wartości z formularzami ciągów, które są i gdzie tych ciągów są prawidłowe w [xamlname — gramatyka](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="606c3-133">However, the most common usage in WPF is to align the `targetID` value with forms that are strings, and where such strings are valid in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span>  
  
 <span data-ttu-id="606c3-134">`ComponentResourceKey`można w składni elementu obiekt.</span><span class="sxs-lookup"><span data-stu-id="606c3-134">`ComponentResourceKey` can be used in object element syntax.</span></span> <span data-ttu-id="606c3-135">W takim przypadku określającą wartość oba <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> właściwości jest wymagana, aby poprawnie zainicjować rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="606c3-135">In this case, specifying the value of both the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> properties is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="606c3-136">W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji czytnika obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.ComponentResourceKey> klasy.</span><span class="sxs-lookup"><span data-stu-id="606c3-136">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader implementation, the handling for this markup extension is defined by the <xref:System.Windows.ComponentResourceKey> class.</span></span>  
  
 <span data-ttu-id="606c3-137">`ComponentResourceKey`to rozszerzenie znacznika.</span><span class="sxs-lookup"><span data-stu-id="606c3-137">`ComponentResourceKey` is a markup extension.</span></span> <span data-ttu-id="606c3-138">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="606c3-138">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="606c3-139">Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w ich składni atrybutu Konwencji za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybutu.</span><span class="sxs-lookup"><span data-stu-id="606c3-139">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="606c3-140">Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="606c3-140">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="606c3-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="606c3-141">See Also</span></span>  
 <xref:System.Windows.ComponentResourceKey>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="606c3-142">Formant tworzenia — omówienie</span><span class="sxs-lookup"><span data-stu-id="606c3-142">Control Authoring Overview</span></span>](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [<span data-ttu-id="606c3-143">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="606c3-143">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="606c3-144">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="606c3-144">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
