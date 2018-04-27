---
title: x:Type — Rozszerzenie znaczników
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
caps.latest.revision: 27
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: db56c2bcdca14b87de320dfe19a6c364c76ecef7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="22e35-102">x:Type — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="22e35-102">x:Type Markup Extension</span></span>
<span data-ttu-id="22e35-103">Dostarcza CLR <xref:System.Type> obiekt, który jest typem podstawowym dla określonego typu XAML.</span><span class="sxs-lookup"><span data-stu-id="22e35-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="22e35-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="22e35-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="22e35-105">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="22e35-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="22e35-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="22e35-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`prefix`|<span data-ttu-id="22e35-107">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="22e35-107">Optional.</span></span> <span data-ttu-id="22e35-108">Prefiks, który mapuje przestrzeń nazw XAML innych niż domyślne.</span><span class="sxs-lookup"><span data-stu-id="22e35-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="22e35-109">Określenie prefiksu często nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="22e35-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="22e35-110">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="22e35-110">See Remarks.</span></span>|  
|`typeNameValue`|<span data-ttu-id="22e35-111">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="22e35-111">Required.</span></span> <span data-ttu-id="22e35-112">Nazwa typu rozpoznać bieżącej domyślnej XAML przestrzeni nazw; lub określony zamapować prefiksu Jeśli `prefix` podano.</span><span class="sxs-lookup"><span data-stu-id="22e35-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22e35-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22e35-113">Remarks</span></span>  
 <span data-ttu-id="22e35-114">`x:Type` — Rozszerzenie znaczników ma podobną funkcję do `typeof()` operatora w języku C# lub `GetType` operatora programu Microsoft Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="22e35-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in C# or the `GetType` operator in Microsoft Visual Basic.</span></span>  
  
 <span data-ttu-id="22e35-115">`x:Type` — Rozszerzenie znaczników dostarcza zachowanie konwersję z ciągu dla właściwości, które przyjmują typ <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="22e35-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="22e35-116">Dane wejściowe są typu XAML.</span><span class="sxs-lookup"><span data-stu-id="22e35-116">The input is a XAML type.</span></span> <span data-ttu-id="22e35-117">Relacja między XAML typ danych wejściowych i wyjściowych CLR <xref:System.Type> jest to, że dane wyjściowe <xref:System.Type> jest <xref:System.Xaml.XamlType.UnderlyingType%2A> danych wejściowych <xref:System.Xaml.XamlType>, po wyszukiwania niezbędnych <xref:System.Xaml.XamlType> na podstawie kontekst schematu XAML i <xref:System.Windows.Markup.IXamlTypeResolver>usługi udostępnia kontekst.</span><span class="sxs-lookup"><span data-stu-id="22e35-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="22e35-118">W programie .NET Framework XAML Services obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.Markup.TypeExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="22e35-118">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>  
  
 <span data-ttu-id="22e35-119">W ramach określonej implementacji, niektóre właściwości, które wymagają <xref:System.Type> jako wartość może zaakceptować nazwę typu bezpośrednio (ciąg typu `Name`).</span><span class="sxs-lookup"><span data-stu-id="22e35-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="22e35-120">Jednak implementacja to zachowanie jest złożonych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="22e35-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="22e35-121">Przykłady można znaleźć w sekcji "Uwagi dotyczące użycia WPF".</span><span class="sxs-lookup"><span data-stu-id="22e35-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>  
  
 <span data-ttu-id="22e35-122">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="22e35-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="22e35-123">Token ciągu po `x:Type` przypisany jako identyfikator ciągu <xref:System.Windows.Markup.TypeExtension.TypeName%2A> wartości podstawowych <xref:System.Windows.Markup.TypeExtension> rozszerzenie klasy.</span><span class="sxs-lookup"><span data-stu-id="22e35-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="22e35-124">W obszarze domyślny kontekst schematu XAML dla usług .NET Framework XAML, które jest oparte na typy CLR, wartość tego atrybutu to <xref:System.Reflection.MemberInfo.Name%2A> odpowiedniego typu, lub które zawiera <xref:System.Reflection.MemberInfo.Name%2A> poprzedzone prefiksu dla przestrzeni nazw XAML innych niż domyślne mapowania.</span><span class="sxs-lookup"><span data-stu-id="22e35-124">Under the default XAML schema context for .NET Framework XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>  
  
 <span data-ttu-id="22e35-125">`x:Type` — Rozszerzenie znaczników mogą być używane w składni elementu obiekt.</span><span class="sxs-lookup"><span data-stu-id="22e35-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="22e35-126">W takim przypadku określającą wartość <xref:System.Windows.Markup.TypeExtension.TypeName%2A> jest wymagana właściwość, aby poprawnie zainicjować rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="22e35-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="22e35-127">`x:Type` — Rozszerzenie znaczników mogą służyć jako atrybut pełne; mimo to nie jest typowe: `<``object` `property``="{x:Type TypeName=``typeNameValue``}" .../>`</span><span class="sxs-lookup"><span data-stu-id="22e35-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<``object` `property``="{x:Type TypeName=``typeNameValue``}" .../>`</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="22e35-128">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="22e35-128">WPF Usage Notes</span></span>  
  
### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="22e35-129">Domyślne mapowanie typu i Namespace XAML</span><span class="sxs-lookup"><span data-stu-id="22e35-129">Default XAML Namespace and Type Mapping</span></span>  
 <span data-ttu-id="22e35-130">Większość typów XAML potrzebnych dla typowych scenariuszy XAML; zawiera domyślnej przestrzeni nazw XAML programowania WPF w związku z tym można często uniknąć prefiksy podczas odwoływania się do wartości typu XAML.</span><span class="sxs-lookup"><span data-stu-id="22e35-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="22e35-131">Konieczne może być zamapować prefiksu, jeśli utworzono odwołanie do typu z niestandardowego zestawu lub dla typów, które istnieją w zestawie WPF, ale z przestrzeni nazw CLR, która nie została zmapowana na domyślnej przestrzeni nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="22e35-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="22e35-132">Aby uzyskać więcej informacji na temat prefiksy przestrzeni nazw XAML i mapowania nazw CLR, zobacz [przestrzeń nazw XAML i Namespace mapowanie dla WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="22e35-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>  
  
### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="22e35-133">Typ właściwości tej obsługi Typename jako ciągu</span><span class="sxs-lookup"><span data-stu-id="22e35-133">Type Properties That Support Typename-as-String</span></span>  
 <span data-ttu-id="22e35-134">WPF obsługuje techniki, które umożliwiają określanie wartości niektórych właściwości typu <xref:System.Type> bez konieczności `x:Type` użycie rozszerzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="22e35-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="22e35-135">Zamiast tego można określić wartość jako ciąg nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="22e35-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="22e35-136">Przykładami są <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> i <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="22e35-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="22e35-137">Obsługa tego zachowania nie jest zapewniana za pomocą typy konwerterów i rozszerzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="22e35-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="22e35-138">Zamiast tego jest to zachowanie odroczenia implementowane za pośrednictwem <xref:System.Windows.FrameworkElementFactory>.</span><span class="sxs-lookup"><span data-stu-id="22e35-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>  
  
 <span data-ttu-id="22e35-139">Silverlight obsługuje podobne Konwencji.</span><span class="sxs-lookup"><span data-stu-id="22e35-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="22e35-140">W rzeczywistości Silverlight nie obsługuje obecnie `{x:Type}` w jego obsługę języka XAML i nie akceptuje `{x:Type}` użycia poza w niektórych przypadkach, które są przeznaczone do obsługi migracji WPF Silverlight XAML.</span><span class="sxs-lookup"><span data-stu-id="22e35-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="22e35-141">W związku z tym zachowanie typename jako parametry są wbudowane wszystkie oceny właściwości macierzystej Silverlight gdzie <xref:System.Type> jest wartość.</span><span class="sxs-lookup"><span data-stu-id="22e35-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="22e35-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="22e35-142">XAML 2009</span></span>  
 <span data-ttu-id="22e35-143">XAML 2009 zapewnia obsługę dodatkowych rodzajowa typów i modyfikuje zachowanie funkcji `x:TypeArguments` i `x:Type` aby zapewnić obsługę tego.</span><span class="sxs-lookup"><span data-stu-id="22e35-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>  
  
-   <span data-ttu-id="22e35-144">`x:TypeArguments` i elementu skojarzonego obiektu dla wystąpienia obiektu ogólny może być na elementów innych niż katalog główny.</span><span class="sxs-lookup"><span data-stu-id="22e35-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="22e35-145">Aby uzyskać więcej informacji, zobacz sekcję "XAML 2009" [x: typearguments — dyrektywa](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span><span class="sxs-lookup"><span data-stu-id="22e35-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span></span>  
  
-   <span data-ttu-id="22e35-146">XAML 2009 obsługuje składnię służący do określania ograniczenie typu ogólnego w znaczniku.</span><span class="sxs-lookup"><span data-stu-id="22e35-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="22e35-147">Może być używany przez `x:TypeArguments`, przez `x:Type`, lub obu tych funkcji w połączeniu.</span><span class="sxs-lookup"><span data-stu-id="22e35-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>  
  
-   <span data-ttu-id="22e35-148">Implementacja WPF XAML podczas przetwarzania XAML 2009 dla obciążenia dodaje również tej możliwości do zachowanie konwersji typu niejawnego pewne właściwości framework, które używają typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="22e35-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="22e35-149">Na platformie WPF można użyć XAML 2009 — funkcje, ale tylko w przypadku utracić XAML (XAML, który nie jest kompilowany do znaczników).</span><span class="sxs-lookup"><span data-stu-id="22e35-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="22e35-150">Skompilowany kod znaczników XAML w WPF i BAML formę XAML aktualnie nie obsługują słowa kluczowe języka XAML 2009 i funkcje.</span><span class="sxs-lookup"><span data-stu-id="22e35-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e35-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22e35-151">See Also</span></span>  
 <xref:System.Windows.Style>  
 [<span data-ttu-id="22e35-152">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="22e35-152">Styling and Templating</span></span>](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="22e35-153">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="22e35-153">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="22e35-154">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="22e35-154">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
