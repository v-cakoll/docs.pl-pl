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
ms.openlocfilehash: 28eda94914125f2c5849a471671c8e283475c82c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44066750"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="11868-102">x:TypeArguments — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="11868-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="11868-103">Przebiegi, ograniczając wpisz argumenty ogólne do konstruktora typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="11868-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="11868-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="11868-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="11868-105">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="11868-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="11868-106">Deklaracja elementu obiektu typu XAML, która jest wspierana przez CLR typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="11868-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="11868-107">Jeśli `object` odwołuje się do typu XAML, który nie pochodzi z domyślna przestrzeń nazw XAML, `object` wymaga prefiksu, aby wskazać, przestrzeń nazw XAML gdzie `object` istnieje.</span><span class="sxs-lookup"><span data-stu-id="11868-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="11868-108">Ciąg, który deklaruje co najmniej jeden XAML wpisz nazwy użytkowników jako ciągi, które dostarcza argumentów typu dla typu ogólnego środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="11868-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="11868-109">Informacje o dodatkowych składni, zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="11868-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11868-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11868-110">Remarks</span></span>  
 <span data-ttu-id="11868-111">W większości przypadków i typy XAML, które są używane jako element informacji w `typeString` są poprzedzone ciągiem.</span><span class="sxs-lookup"><span data-stu-id="11868-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="11868-112">Typowe typy CLR ograniczenia ogólne (na przykład <xref:System.Int32> i <xref:System.String>) pochodzą z biblioteki klas bazowych CLR.</span><span class="sxs-lookup"><span data-stu-id="11868-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="11868-113">Te biblioteki nie są zmapowane do typowych domyślnych właściwa dla struktury XAML w przestrzeni nazw i dlatego wymagają mapowania prefiks do użycia XAML.</span><span class="sxs-lookup"><span data-stu-id="11868-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="11868-114">Można określić więcej niż jedną nazwę typu XAML przy użyciu ogranicznika przecinkami.</span><span class="sxs-lookup"><span data-stu-id="11868-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="11868-115">Użycie typów ogólnych, ograniczenia ogólne, same argumenty typu zagnieżdżonego ograniczenia mogą być zawarte w nawiasy ().</span><span class="sxs-lookup"><span data-stu-id="11868-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="11868-116">Należy pamiętać, że ta definicja `x:TypeArguments` jest przeznaczony dla usług programu .NET Framework XAML i przy użyciu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="11868-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="11868-117">Definicja poziomu języka znajdują się w [ \[MS-XAML\] sekcji 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="11868-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="11868-118">Przykłady użycia</span><span class="sxs-lookup"><span data-stu-id="11868-118">Usage Examples</span></span>  
 <span data-ttu-id="11868-119">W poniższych przykładach założono, że następujące definicje przestrzeń nazw XAML są deklarowane:</span><span class="sxs-lookup"><span data-stu-id="11868-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="11868-120">Lista\<ciąg ></span><span class="sxs-lookup"><span data-stu-id="11868-120">List\<String></span></span>  
 <span data-ttu-id="11868-121">`<scg:List x:TypeArguments="sys:String" ...>` Tworzy nową <xref:System.Collections.Generic.List%601> z <xref:System.String> argument typu.</span><span class="sxs-lookup"><span data-stu-id="11868-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="11868-122">Słownik\<String, String ></span><span class="sxs-lookup"><span data-stu-id="11868-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="11868-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` Tworzy nową <xref:System.Collections.Generic.Dictionary%602> przy użyciu dwóch <xref:System.String> argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="11868-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="11868-124">Kolejka < KeyValuePair\<String, String >></span><span class="sxs-lookup"><span data-stu-id="11868-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="11868-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` Tworzy nową <xref:System.Collections.Generic.Queue%601> zawierający ograniczenie <xref:System.Collections.Generic.KeyValuePair%602> z argumentami typu Ograniczenie wewnętrzne <xref:System.String> i <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11868-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="11868-126">Wartości XAML 2006 i środowisku WPF XAML ogólnego użycia</span><span class="sxs-lookup"><span data-stu-id="11868-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="11868-127">Użycie XAML 2006 i XAML, która jest używana dla aplikacji WPF, obowiązują następujące ograniczenia dla `x:TypeArguments` i użycia typu ogólnego z XAML w ogólne:</span><span class="sxs-lookup"><span data-stu-id="11868-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
-   <span data-ttu-id="11868-128">Tylko element główny plik XAML może obsługiwać ogólnego użycia XAML, który odwołuje się do typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="11868-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
-   <span data-ttu-id="11868-129">Element główny musi być mapowane z co najmniej jeden typ argumentu typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="11868-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="11868-130">Na przykład <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="11868-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="11868-131">Funkcje strony są podstawowy scenariusz obsługi ogólnego użycia XAML w WPF.</span><span class="sxs-lookup"><span data-stu-id="11868-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
-   <span data-ttu-id="11868-132">Element główny element XAML obiektu dla ogólnej musi również zadeklarować klasy częściowej przy użyciu `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="11868-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="11868-133">Ta zasada obowiązuje, nawet w przypadku definiowania WPF Akcja kompilacji.</span><span class="sxs-lookup"><span data-stu-id="11868-133">This is true even if defining a WPF build action.</span></span>  
  
-   <span data-ttu-id="11868-134">`x:TypeArguments` Nie można odwołać zagnieżdżonych ograniczenia ogólne.</span><span class="sxs-lookup"><span data-stu-id="11868-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="11868-135">XAML 2009 lub XAML 2006 bez WPF 3.0 lub WPF 3.5 zależności</span><span class="sxs-lookup"><span data-stu-id="11868-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="11868-136">W przypadku usług .NET Framework XAML XAML 2006 lub XAML 2009 ograniczenia związane z WPF ogólnego użycia XAML są złagodzone.</span><span class="sxs-lookup"><span data-stu-id="11868-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="11868-137">Można utworzyć wystąpienia elementu obiekt rodzajowy, w dowolnym miejscu w znaczniku XAML, który zapasowy typ systemu i obiekt modelu mogą obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="11868-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="11868-138">Jeśli używasz XAML 2009 zamiast mapowania środowiska CLR typy uzyskać typy XAML dla wspólnych elementów podstawowych języka podstawowe, możesz użyć [typy wbudowane dla wspólnych elementów podstawowych języka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) jako elementy informacji w programie `typeString`.</span><span class="sxs-lookup"><span data-stu-id="11868-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="11868-139">Na przykład, można zadeklarować następujące (przestrzeń nazw XAML języka XAML dla XAML 2009 jest mapowania prefiksów, które nie są wyświetlane, ale x):</span><span class="sxs-lookup"><span data-stu-id="11868-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="11868-140">Na platformie WPF i przeznaczonych dla [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć XAML 2009 — funkcje wraz z `x:TypeArguments` , ale tylko w przypadku luźne XAML (XAML, która nie jest kompilowana do znaczników).</span><span class="sxs-lookup"><span data-stu-id="11868-140">In WPF and when targeting [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="11868-141">XAML kompilowana do znaczników dla platformy WPF i formularz BAML XAML aktualnie nie obsługują tych funkcji i słowa kluczowe XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="11868-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="11868-142">Jeśli potrzebujesz do znaczników kompilacji XAML, musi działać w ramach ograniczenia, o których wspomniano w sekcji "XAML 2006 i WPF ogólny XAML użycia".</span><span class="sxs-lookup"><span data-stu-id="11868-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11868-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11868-143">See Also</span></span>  
 [<span data-ttu-id="11868-144">x:Class, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="11868-144">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="11868-145">x:Type, rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="11868-145">x:Type Markup Extension</span></span>](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [<span data-ttu-id="11868-146">Typy wbudowane dla wspólnych elementów podstawowych języka XAML</span><span class="sxs-lookup"><span data-stu-id="11868-146">Built-in Types for Common XAML Language Primitives</span></span>](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [<span data-ttu-id="11868-147">Typy ogólne w XAML</span><span class="sxs-lookup"><span data-stu-id="11868-147">Generics in XAML</span></span>](../../../docs/framework/xaml-services/generics-in-xaml.md)
