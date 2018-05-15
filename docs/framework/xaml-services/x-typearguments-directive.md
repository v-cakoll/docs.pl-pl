---
title: x:TypeArguments — dyrektywa
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 94f09bdd3b6ee0b180e30bab0993f0b4e41730ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="fa846-102">x:TypeArguments — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="fa846-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="fa846-103">Przekazuje ograniczający wpisz argumenty ogólne do konstruktora typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="fa846-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="fa846-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="fa846-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="fa846-105">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="fa846-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="fa846-106">Deklaracja elementu obiektu typu XAML, który nie jest obsługiwana przez CLR typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="fa846-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="fa846-107">Jeśli `object` odwołuje się do typu XAML, który nie pochodzi z domyślnej przestrzeni nazw XAML, `object` wymaga prefiksu przestrzeni nazw XAML wskazująca, gdzie `object` istnieje.</span><span class="sxs-lookup"><span data-stu-id="fa846-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="fa846-108">Ciąg, który deklaruje co najmniej jeden XAML wpisz nazwy jako ciąg, który dostarcza argumentów typu dla typu ogólnego środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="fa846-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="fa846-109">Zobacz uwagi dla uwagi dodatkowe składni.</span><span class="sxs-lookup"><span data-stu-id="fa846-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa846-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa846-110">Remarks</span></span>  
 <span data-ttu-id="fa846-111">W większości przypadków typów XAML, które są używane jako element informacji w `typeString` są poprzedzane w postaci ciągu.</span><span class="sxs-lookup"><span data-stu-id="fa846-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="fa846-112">Typowe typy CLR ograniczenia ogólne (na przykład <xref:System.Int32> i <xref:System.String>) pochodzą z biblioteki podstawowej klasy CLR.</span><span class="sxs-lookup"><span data-stu-id="fa846-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="fa846-113">Te biblioteki nie są mapowane na typowy domyślny określonej struktury przestrzeń nazw XAML i w związku z tym muszą być mapowane prefiks dla użycie języka XAML.</span><span class="sxs-lookup"><span data-stu-id="fa846-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="fa846-114">Za pomocą ogranicznik przecinkami, można określić więcej niż jedną nazwę typu XAML.</span><span class="sxs-lookup"><span data-stu-id="fa846-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="fa846-115">Ograniczenia ogólne, same użycie typów ogólnych argumentów typu zagnieżdżonego ograniczenia mogą wchodzić w skład nawiasów ().</span><span class="sxs-lookup"><span data-stu-id="fa846-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="fa846-116">Należy pamiętać, że ta definicja `x:TypeArguments` jest przeznaczony dla usług .NET Framework XAML i przy użyciu zapasowy CLR.</span><span class="sxs-lookup"><span data-stu-id="fa846-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="fa846-117">Poziom języka definicji znajduje się w [ \[MS XAML\] sekcji 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="fa846-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="fa846-118">Przykłady użycia</span><span class="sxs-lookup"><span data-stu-id="fa846-118">Usage Examples</span></span>  
 <span data-ttu-id="fa846-119">Te przykłady założono, że następujące definicje przestrzeni nazw XAML są deklarowane jako:</span><span class="sxs-lookup"><span data-stu-id="fa846-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="fa846-120">Lista\<ciąg ></span><span class="sxs-lookup"><span data-stu-id="fa846-120">List\<String></span></span>  
 <span data-ttu-id="fa846-121">`<scg:List x:TypeArguments="sys:String" ...>` Tworzy nowy <xref:System.Collections.Generic.List%601> z <xref:System.String> argument typu.</span><span class="sxs-lookup"><span data-stu-id="fa846-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="fa846-122">Słownik\<ciąg, ciąg ></span><span class="sxs-lookup"><span data-stu-id="fa846-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="fa846-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` Tworzy nowy <xref:System.Collections.Generic.Dictionary%602> z dwoma <xref:System.String> argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="fa846-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="fa846-124">Kolejki < KeyValuePair\<ciąg, ciąg >></span><span class="sxs-lookup"><span data-stu-id="fa846-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="fa846-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` Tworzy nowy <xref:System.Collections.Generic.Queue%601> mający ograniczenie <xref:System.Collections.Generic.KeyValuePair%602> z argumentami typu Ograniczenie wewnętrzne <xref:System.String> i <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="fa846-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="fa846-126">XAML 2006 i WPF XAML ogólnego zastosowania</span><span class="sxs-lookup"><span data-stu-id="fa846-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="fa846-127">Dla XAML 2006 użycia i XAML, który jest używany w aplikacji WPF, istnieją następujące ograniczenia `x:TypeArguments` i użycia typu ogólnego z XAML w ogólne:</span><span class="sxs-lookup"><span data-stu-id="fa846-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
-   <span data-ttu-id="fa846-128">Tylko element główny pliku XAML może obsługiwać ogólnego użycia XAML, który odwołuje się do typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="fa846-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
-   <span data-ttu-id="fa846-129">Element główny musi być zamapowany przy użyciu co najmniej jeden typ argumentu typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="fa846-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="fa846-130">Na przykład <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="fa846-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="fa846-131">Funkcje strony są podstawowego scenariusza obsługi ogólnego użycia XAML w WPF.</span><span class="sxs-lookup"><span data-stu-id="fa846-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
-   <span data-ttu-id="fa846-132">Element główny element XAML obiektu dla ogólnych musi również deklarować częściowej klasy przy użyciu `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="fa846-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="fa846-133">Dotyczy to nawet wtedy, gdy akcja kompilacji Definiowanie WPF.</span><span class="sxs-lookup"><span data-stu-id="fa846-133">This is true even if defining a WPF build action.</span></span>  
  
-   <span data-ttu-id="fa846-134">`x:TypeArguments` Nie można odwołać zagnieżdżonych ograniczenia ogólne.</span><span class="sxs-lookup"><span data-stu-id="fa846-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="fa846-135">XAML 2009 lub 2006 XAML bez WPF 3.0 lub WPF 3.5 zależności</span><span class="sxs-lookup"><span data-stu-id="fa846-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="fa846-136">.NET Framework XAML Services for XAML 2006 lub XAML 2009 rozluźnić są ograniczenia związane z WPF na ogólne użycie języka XAML.</span><span class="sxs-lookup"><span data-stu-id="fa846-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="fa846-137">Można utworzyć wystąpienia elementu obiekt generyczny w każdej pozycji w XAML kod znaczników, który może obsługiwać zapasowy typ systemu i obiekt modelu.</span><span class="sxs-lookup"><span data-stu-id="fa846-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="fa846-138">Jeśli używasz XAML 2009 zamiast mapowania CLR typy uzyskać dla wspólnych elementów podstawowych języka XAML typy podstawowe, możesz użyć [typy wbudowane dla wspólnych elementów podstawowych języka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) jako elementów informacji w `typeString`.</span><span class="sxs-lookup"><span data-stu-id="fa846-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="fa846-139">Na przykład można zadeklarować następujące (przestrzeń nazw XAML języka XAML dla XAML 2009 jest mapowania prefiksów, które nie są wyświetlane, ale x):</span><span class="sxs-lookup"><span data-stu-id="fa846-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="fa846-140">Na platformie WPF i przeznaczonych dla [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć XAML 2009 — funkcje razem z `x:TypeArguments` , ale tylko w przypadku utracić XAML (XAML, który nie jest kompilowany do znaczników).</span><span class="sxs-lookup"><span data-stu-id="fa846-140">In WPF and when targeting [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="fa846-141">Skompilowany kod znaczników XAML w WPF i BAML formę XAML aktualnie nie obsługują słowa kluczowe języka XAML 2009 i funkcje.</span><span class="sxs-lookup"><span data-stu-id="fa846-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="fa846-142">Jeśli potrzebne do znaczników kompilowania pliku XAML, muszą być ustawione na ograniczenia wymienione w sekcji "XAML 2006 and WPF ogólny XAML użycia".</span><span class="sxs-lookup"><span data-stu-id="fa846-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa846-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa846-143">See Also</span></span>  
 [<span data-ttu-id="fa846-144">x:Class, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="fa846-144">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="fa846-145">x:Type, rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="fa846-145">x:Type Markup Extension</span></span>](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [<span data-ttu-id="fa846-146">Typy wbudowane dla wspólnych elementów podstawowych języka XAML</span><span class="sxs-lookup"><span data-stu-id="fa846-146">Built-in Types for Common XAML Language Primitives</span></span>](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [<span data-ttu-id="fa846-147">Typy ogólne w XAML</span><span class="sxs-lookup"><span data-stu-id="fa846-147">Generics in XAML</span></span>](../../../docs/framework/xaml-services/generics-in-xaml.md)
