---
title: Typy migrowane z WPF do System.Xaml
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 5aa2d8a39be47d9affb97c3b60e53c4722c63cce
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249803"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a><span data-ttu-id="22fdc-102">Typy migrowane z WPF do pliku System.Xaml</span><span class="sxs-lookup"><span data-stu-id="22fdc-102">Types migrated from WPF to System.Xaml</span></span>

<span data-ttu-id="22fdc-103">W programie .NET Framework 3.5 i .NET Framework 3.0 zarówno Windows Presentation Foundation (WPF) i Windows Workflow Foundation zawierały implementację języka XAML.</span><span class="sxs-lookup"><span data-stu-id="22fdc-103">In .NET Framework 3.5 and .NET Framework 3.0, both Windows Presentation Foundation (WPF) and Windows Workflow Foundation included a XAML language implementation.</span></span> <span data-ttu-id="22fdc-104">Wiele typów publicznych, które dostarczyły rozszerzalność dla WPF XAML implementacji istniał w WindowsBase, PresentationCore i PresentationFramework zestawów.</span><span class="sxs-lookup"><span data-stu-id="22fdc-104">Many of the public types that provided extensibility for the WPF XAML implementation existed in the WindowsBase, PresentationCore, and PresentationFramework assemblies.</span></span> <span data-ttu-id="22fdc-105">Podobnie w zestawie System.Workflow.ComponentModel istniały typy publiczne, które zapewniały rozszerzalność xaml programu Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="22fdc-105">Likewise, public types that provided extensibility for Windows Workflow Foundation XAML existed in the System.Workflow.ComponentModel assembly.</span></span> <span data-ttu-id="22fdc-106">W .NET Framework 4 niektóre typy związane z XAML zostały zmigrowane do zestawu System.Xaml.</span><span class="sxs-lookup"><span data-stu-id="22fdc-106">In the .NET Framework 4, some of the XAML-related types were migrated to the System.Xaml assembly.</span></span> <span data-ttu-id="22fdc-107">Wspólna implementacja języka XAML w ramach platformy .NET Framework umożliwia wiele scenariuszy rozszerzalności języka XAML, które zostały pierwotnie zdefiniowane przez implementację XAML określonej struktury, ale są teraz częścią ogólnej obsługi języka XAML programu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="22fdc-107">A common .NET Framework implementation of XAML language services enables many XAML extensibility scenarios that were originally defined by a specific framework's XAML implementation but are now part of overall .NET Framework 4 XAML language support.</span></span> <span data-ttu-id="22fdc-108">W tym artykule wymieniono typy, które zostały zmigrowane i omówiono problemy związane z migracją.</span><span class="sxs-lookup"><span data-stu-id="22fdc-108">This article lists the types that were migrated and discusses issues related to the migration.</span></span>

## <a name="assemblies-and-namespaces"></a><span data-ttu-id="22fdc-109">Zestawy i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="22fdc-109">Assemblies and Namespaces</span></span>

<span data-ttu-id="22fdc-110">W .NET Framework 3.5 i .NET Framework 3.0 typy, które WPF implementowane do obsługi XAML były zazwyczaj w obszarze <xref:System.Windows.Markup> nazw.</span><span class="sxs-lookup"><span data-stu-id="22fdc-110">In .NET Framework 3.5 and .NET Framework 3.0, the types that WPF implemented to support XAML were generally in the <xref:System.Windows.Markup> namespace.</span></span> <span data-ttu-id="22fdc-111">Większość z tych typów znajdowała się w zestawie WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="22fdc-111">Most of these types were in the WindowsBase assembly.</span></span>

<span data-ttu-id="22fdc-112">W .NET Framework 4 jest <xref:System.Xaml> nowy obszar nazw i nowy zestaw System.Xaml.</span><span class="sxs-lookup"><span data-stu-id="22fdc-112">In .NET Framework 4, there is a new <xref:System.Xaml> namespace and a new System.Xaml assembly.</span></span> <span data-ttu-id="22fdc-113">Wiele typów, które zostały pierwotnie zaimplementowane dla WPF XAML są teraz dostarczane jako punkty rozszerzalności lub usług dla dowolnej implementacji XAML.</span><span class="sxs-lookup"><span data-stu-id="22fdc-113">Many of the types that were originally implemented for WPF XAML are now provided as extensibility points or services for any implementation of XAML.</span></span> <span data-ttu-id="22fdc-114">W ramach udostępniania ich dla bardziej ogólnych scenariuszy typy są przekazywane z ich oryginalnego zestawu WPF do Zestawu System.Xaml.</span><span class="sxs-lookup"><span data-stu-id="22fdc-114">As part of making them available for more general scenarios, the types are type-forwarded from their original WPF assembly to the System.Xaml assembly.</span></span> <span data-ttu-id="22fdc-115">Dzięki temu scenariusze rozszerzalności XAML bez konieczności dołączania zestawów innych struktur (takich jak WPF I Windows Workflow Foundation).</span><span class="sxs-lookup"><span data-stu-id="22fdc-115">This enables XAML extensibility scenarios without having to include the assemblies of other frameworks (such as WPF and Windows Workflow Foundation).</span></span>

<span data-ttu-id="22fdc-116">W przypadku typów migrowanych większość <xref:System.Windows.Markup> typów pozostaje w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="22fdc-116">For migrated types, most of the types remain in the <xref:System.Windows.Markup> namespace.</span></span> <span data-ttu-id="22fdc-117">Miało to częściowo zapobiec przerywaniu mapowania obszaru nazw CLR w istniejących implementacjach na podstawie dla jednego pliku.</span><span class="sxs-lookup"><span data-stu-id="22fdc-117">This was partially to avoid breaking CLR namespace mappings in existing implementations on a per-file basis.</span></span> <span data-ttu-id="22fdc-118">W rezultacie obszar <xref:System.Windows.Markup> nazw w programie .NET Framework 4 zawiera kombinację typów obsługi języka ogólnego XAML (z zestawu System.Xaml) i typów, które są specyficzne dla implementacji WPF XAML (z WindowsBase i innych zestawów WPF).</span><span class="sxs-lookup"><span data-stu-id="22fdc-118">As a result, the <xref:System.Windows.Markup> namespace in .NET Framework 4 contains a mixture of general XAML language support types (from the System.Xaml assembly) and types that are specific to the WPF XAML implementation (from WindowsBase and other WPF assemblies).</span></span> <span data-ttu-id="22fdc-119">Każdy typ, który został zmigrowany do System.Xaml, ale istniał wcześniej w zestawie WPF, ma obsługę przekazywania tekstu w wersji 4 zestawu WPF.</span><span class="sxs-lookup"><span data-stu-id="22fdc-119">Any type that was migrated to System.Xaml, but existed previously in a WPF assembly, has type-forwarding support in version 4 of the WPF assembly.</span></span>

### <a name="workflow-xaml-support-types"></a><span data-ttu-id="22fdc-120">Typy obsługi XAML przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="22fdc-120">Workflow XAML Support Types</span></span>

<span data-ttu-id="22fdc-121">Windows Workflow Foundation również pod warunkiem, typy obsługi XAML i w wielu przypadkach miały identyczne krótkie nazwy do odpowiednika WPF.</span><span class="sxs-lookup"><span data-stu-id="22fdc-121">Windows Workflow Foundation also provided XAML support types, and in many cases these had identical short names to a WPF equivalent.</span></span> <span data-ttu-id="22fdc-122">Poniżej znajduje się lista typów obsługi XAML programu Windows Workflow Foundation:</span><span class="sxs-lookup"><span data-stu-id="22fdc-122">The following is a list of Windows Workflow Foundation XAML support types:</span></span>

- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>

<span data-ttu-id="22fdc-123">Te typy pomocy technicznej nadal istnieją w zestawach Fundacji przepływu pracy systemu Windows dla platformy .NET Framework 4 i nadal mogą być używane dla określonych aplikacji Programu Windows Workflow Foundation; jednak nie powinny się odwoływać aplikacje lub struktury, które nie używają programu Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="22fdc-123">These support types still exist in the Windows Workflow Foundation assemblies for .NET Framework 4 and can still be used for specific Windows Workflow Foundation applications; however, they should not be referenced by applications or frameworks that do not use Windows Workflow Foundation.</span></span>

## <a name="markupextension"></a><span data-ttu-id="22fdc-124">MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="22fdc-124">MarkupExtension</span></span>

<span data-ttu-id="22fdc-125">W .NET Framework 3.5 i .NET Framework 3.0 <xref:System.Windows.Markup.MarkupExtension> klasa dla WPF WPF była w zestawie WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="22fdc-125">In the .NET Framework 3.5 and .NET Framework 3.0, the <xref:System.Windows.Markup.MarkupExtension> class for WPF was in the WindowsBase assembly.</span></span> <span data-ttu-id="22fdc-126">Klasa równoległa dla fundacji <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>przepływu pracy systemu Windows, istniała w zestawie System.Workflow.ComponentModel.</span><span class="sxs-lookup"><span data-stu-id="22fdc-126">A parallel class for Windows Workflow Foundation, <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, existed in the System.Workflow.ComponentModel assembly.</span></span> <span data-ttu-id="22fdc-127">W .NET Framework 4 <xref:System.Windows.Markup.MarkupExtension> klasa jest migrowana do zestawu System.Xaml.</span><span class="sxs-lookup"><span data-stu-id="22fdc-127">In the .NET Framework 4, the <xref:System.Windows.Markup.MarkupExtension> class is migrated to the System.Xaml assembly.</span></span> <span data-ttu-id="22fdc-128">W programie .NET Framework <xref:System.Windows.Markup.MarkupExtension> 4 jest przeznaczony dla dowolnego scenariusza rozszerzalności XAML, który używa usług .NET XAML Services, a nie tylko dla tych, które opierają się na określonych platformach.</span><span class="sxs-lookup"><span data-stu-id="22fdc-128">In the .NET Framework 4, <xref:System.Windows.Markup.MarkupExtension> is intended for any XAML extensibility scenario that uses .NET XAML Services, not just for those that build on specific frameworks.</span></span> <span data-ttu-id="22fdc-129">Jeśli to możliwe, określone struktury lub kod użytkownika <xref:System.Windows.Markup.MarkupExtension> w ramach należy również opierać się na klasie dla rozszerzenia XAML.</span><span class="sxs-lookup"><span data-stu-id="22fdc-129">When possible, specific frameworks or user code in the framework should also build on the <xref:System.Windows.Markup.MarkupExtension> class for XAML extension.</span></span>

## <a name="markupextension-supporting-service-classes"></a><span data-ttu-id="22fdc-130">Klasy usługi pomocniczej naciśnienia znaczników</span><span class="sxs-lookup"><span data-stu-id="22fdc-130">MarkupExtension Supporting Service Classes</span></span>

<span data-ttu-id="22fdc-131">.NET Framework 3.5 i .NET Framework 3.0 dla WPF dostarczył kilka usług, które były dostępne dla <xref:System.Windows.Markup.MarkupExtension> realizatorów i <xref:System.ComponentModel.TypeConverter> implementacji do obsługi użycia typu/właściwości w XAML.</span><span class="sxs-lookup"><span data-stu-id="22fdc-131">.NET Framework 3.5 and .NET Framework 3.0 for WPF provided several services that were available to <xref:System.Windows.Markup.MarkupExtension> implementers and <xref:System.ComponentModel.TypeConverter> implementations to support type/property usage in XAML.</span></span> <span data-ttu-id="22fdc-132">Usługi te są następujące:</span><span class="sxs-lookup"><span data-stu-id="22fdc-132">These services are the following:</span></span>

- <xref:System.Windows.Markup.IProvideValueTarget>

- <xref:System.Windows.Markup.IUriContext>

- <xref:System.Windows.Markup.IXamlTypeResolver>

> [!NOTE]
> <span data-ttu-id="22fdc-133">Inną usługą z platformy .NET Framework 3.5, <xref:System.Windows.Markup.IReceiveMarkupExtension> która jest powiązana z rozszerzeniami znaczników, jest interfejs.</span><span class="sxs-lookup"><span data-stu-id="22fdc-133">Another service from .NET Framework 3.5 that is related to markup extensions is the <xref:System.Windows.Markup.IReceiveMarkupExtension> interface.</span></span> <span data-ttu-id="22fdc-134"><xref:System.Windows.Markup.IReceiveMarkupExtension>nie został zmigrowany i jest oznaczony `[Obsolete]` dla programu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="22fdc-134"><xref:System.Windows.Markup.IReceiveMarkupExtension> was not migrated and is marked `[Obsolete]` for .NET Framework 4.</span></span> <span data-ttu-id="22fdc-135">Scenariusze, które <xref:System.Windows.Markup.IReceiveMarkupExtension> wcześniej używane <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> należy zamiast tego użyć przypisanych wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="22fdc-135">Scenarios that previously used <xref:System.Windows.Markup.IReceiveMarkupExtension> should instead use <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> attributed callbacks.</span></span> <span data-ttu-id="22fdc-136"><xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute>jest również `[Obsolete]`oznaczony .</span><span class="sxs-lookup"><span data-stu-id="22fdc-136"><xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> is also marked `[Obsolete]`.</span></span>

## <a name="xaml-language-features"></a><span data-ttu-id="22fdc-137">Funkcje języka XAML</span><span class="sxs-lookup"><span data-stu-id="22fdc-137">XAML Language Features</span></span>

<span data-ttu-id="22fdc-138">Kilka funkcji języka XAML i składników dla WPF wcześniej istniało w PresentationFramework zestawu.</span><span class="sxs-lookup"><span data-stu-id="22fdc-138">Several XAML language features and components for WPF previously existed in the PresentationFramework assembly.</span></span> <span data-ttu-id="22fdc-139">Zostały one zaimplementowane jako podklasa, <xref:System.Windows.Markup.MarkupExtension> aby udostępnić użycie rozszerzenia znaczników w znacznikach XAML.</span><span class="sxs-lookup"><span data-stu-id="22fdc-139">These were implemented as a <xref:System.Windows.Markup.MarkupExtension> subclass to expose markup extension usages in XAML markup.</span></span> <span data-ttu-id="22fdc-140">W .NET Framework 4 istnieją one w zestawie System.Xaml, dzięki czemu projekty, które nie zawierają zestawów WPF, mogą używać tych funkcji na poziomie języka XAML.</span><span class="sxs-lookup"><span data-stu-id="22fdc-140">In .NET Framework 4, these exist in the System.Xaml assembly so that projects that do not include WPF assemblies can use these XAML language-level features.</span></span> <span data-ttu-id="22fdc-141">WPF WPF używa tych samych implementacji dla aplikacji .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="22fdc-141">WPF uses these same implementations for .NET Framework 4 applications.</span></span> <span data-ttu-id="22fdc-142">Podobnie jak w przypadku innych przypadków, które są wymienione w <xref:System.Windows.Markup> tym temacie, typy pomocnicze nadal istnieją w obszarze nazw, aby uniknąć przerywania poprzednich odwołań.</span><span class="sxs-lookup"><span data-stu-id="22fdc-142">As with the other cases that are listed in this topic, the supporting types continue to exist in the <xref:System.Windows.Markup> namespace to avoid breaking previous references.</span></span>

<span data-ttu-id="22fdc-143">Poniższa tabela zawiera listę klas obsługi funkcji XAML zdefiniowanych w pliku System.Xaml.</span><span class="sxs-lookup"><span data-stu-id="22fdc-143">The following table contains a list of the XAML feature-support classes that are defined in System.Xaml.</span></span>

|<span data-ttu-id="22fdc-144">Funkcja języka XAML</span><span class="sxs-lookup"><span data-stu-id="22fdc-144">XAML Language Feature</span></span>|<span data-ttu-id="22fdc-145">Sposób użycia</span><span class="sxs-lookup"><span data-stu-id="22fdc-145">Usage</span></span>|
|---------------------------|-----------|
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|

<span data-ttu-id="22fdc-146">Chociaż system.Xaml może nie mieć określonych klas pomocy technicznej, ogólna logika przetwarzania funkcji języka języka XAML znajduje się obecnie w systemie.Xaml i jego zaimplementowanych czytnikach XAML i modułach zapisu XAML.</span><span class="sxs-lookup"><span data-stu-id="22fdc-146">Although System.Xaml may not have specific support classes, the general logic for processing language features for the XAML language now resides in System.Xaml and its implemented XAML readers and XAML writers.</span></span> <span data-ttu-id="22fdc-147">Na przykład `x:TypeArguments` jest atrybutem, który jest przetwarzany przez czytniki XAML i moduły zapisującej XAML z implementacji System.Xaml; można zauważyć w strumieniu węzła XAML, ma obsługę w domyślnym (opartym na PROGRAMIE CLR) kontekście schematu XAML, ma reprezentację systemu typu XAML i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="22fdc-147">For example, `x:TypeArguments` is an attribute that is processed by XAML readers and XAML writers from System.Xaml implementations; it can be noted in the XAML node stream, has handling in the default (CLR-based) XAML schema context, has a XAML type-system representation, and so on.</span></span> <span data-ttu-id="22fdc-148">W rezultacie dokumentacja referencyjna dla wszystkich funkcji na poziomie języka XAML jest podtematem [usług XAML](../../../desktop-wpf/xaml-services/index.md) w [Podręczniku pulpitu dla programu Windows Presentation Foundation (WPF)](../../../desktop-wpf/overview/index.md).</span><span class="sxs-lookup"><span data-stu-id="22fdc-148">As a result, the reference documentation for all XAML language-level features is a subtopic for [XAML Services](../../../desktop-wpf/xaml-services/index.md) in the [Desktop Guide for Windows Presentation Foundation (WPF)](../../../desktop-wpf/overview/index.md).</span></span>

## <a name="valueserializer-and-supporting-classes"></a><span data-ttu-id="22fdc-149">ValueSerializer i klasy pomocnicze</span><span class="sxs-lookup"><span data-stu-id="22fdc-149">ValueSerializer and Supporting Classes</span></span>

<span data-ttu-id="22fdc-150">Klasa <xref:System.Windows.Markup.ValueSerializer> obsługuje konwersji typu do ciągu, szczególnie w przypadku serializacji XAML, gdzie serializacji może wymagać wielu trybów lub węzłów w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="22fdc-150">The <xref:System.Windows.Markup.ValueSerializer> class supports type conversion to a string, particularly for XAML serialization cases where serialization may require multiple modes or nodes in the output.</span></span> <span data-ttu-id="22fdc-151">W programie .NET Framework 3.5 i .NET <xref:System.Windows.Markup.ValueSerializer> Framework 3.0 for WPF był w zestawie WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="22fdc-151">In .NET Framework 3.5 and .NET Framework 3.0, the <xref:System.Windows.Markup.ValueSerializer> for WPF was in the WindowsBase assembly.</span></span> <span data-ttu-id="22fdc-152">W programie .NET Framework <xref:System.Windows.Markup.ValueSerializer> 4 klasa znajduje się w system.Xaml i jest przeznaczona dla dowolnego scenariusza rozszerzalności XAML, nie tylko dla tych, które opierają się na WPF.</span><span class="sxs-lookup"><span data-stu-id="22fdc-152">In the .NET Framework 4, the <xref:System.Windows.Markup.ValueSerializer> class is in System.Xaml and is intended for any XAML extensibility scenario, not just for those that build on WPF.</span></span> <span data-ttu-id="22fdc-153"><xref:System.Windows.Markup.IValueSerializerContext>(usługa pomocnicza) <xref:System.Windows.Markup.DateTimeValueSerializer> i (określona podklasa) są również migrowane do system.Xaml.</span><span class="sxs-lookup"><span data-stu-id="22fdc-153"><xref:System.Windows.Markup.IValueSerializerContext> (a supporting service) and <xref:System.Windows.Markup.DateTimeValueSerializer> (a specific subclass) are also migrated to System.Xaml.</span></span>

## <a name="xaml-related-attributes"></a><span data-ttu-id="22fdc-154">Atrybuty związane z XAML</span><span class="sxs-lookup"><span data-stu-id="22fdc-154">XAML-Related Attributes</span></span>

<span data-ttu-id="22fdc-155">WPF XAML zawiera kilka atrybutów, które mogą być stosowane do typów CLR, aby wskazać coś o ich zachowanie XAML.</span><span class="sxs-lookup"><span data-stu-id="22fdc-155">WPF XAML included several attributes that can be applied to CLR types to indicate something about their XAML behavior.</span></span> <span data-ttu-id="22fdc-156">Poniżej znajduje się lista atrybutów, które istniały w zestawach WPF w .NET Framework 3.5 i .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="22fdc-156">The following is a list of the attributes that existed in WPF assemblies in .NET Framework 3.5 and .NET Framework 3.0.</span></span> <span data-ttu-id="22fdc-157">Te atrybuty są migrowane do systemu System.Xaml w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="22fdc-157">These attributes are migrated to System.Xaml in .NET Framework 4.</span></span>

- <xref:System.Windows.Markup.AmbientAttribute>

- <xref:System.Windows.Markup.ContentPropertyAttribute>

- <xref:System.Windows.Markup.ContentWrapperAttribute>

- <xref:System.Windows.Markup.DependsOnAttribute>

- <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

- <xref:System.Windows.Markup.NameScopePropertyAttribute>

- <xref:System.Windows.Markup.RootNamespaceAttribute>

- <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

- <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

- <xref:System.Windows.Markup.ValueSerializerAttribute>

- <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

- <xref:System.Windows.Markup.XmlLangPropertyAttribute>

- <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

- <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

- <xref:System.Windows.Markup.XmlnsPrefixAttribute>

## <a name="miscellaneous-classes"></a><span data-ttu-id="22fdc-158">Różne klasy</span><span class="sxs-lookup"><span data-stu-id="22fdc-158">Miscellaneous Classes</span></span>

<span data-ttu-id="22fdc-159">Interfejs <xref:System.Windows.Markup.IComponentConnector> istniał w programie WindowsBase w programie .NET Framework 3.5 i .NET Framework 3.0, ale istnieje w systemie.Xaml w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="22fdc-159">The <xref:System.Windows.Markup.IComponentConnector> interface existed in WindowsBase in .NET Framework 3.5 and .NET Framework 3.0, but exists in System.Xaml in .NET Framework 4.</span></span> <span data-ttu-id="22fdc-160"><xref:System.Windows.Markup.IComponentConnector>jest przeznaczony przede wszystkim do obsługi narzędzi i kompilatorów znaczników XAML.</span><span class="sxs-lookup"><span data-stu-id="22fdc-160"><xref:System.Windows.Markup.IComponentConnector> is primarily intended for tooling support and XAML markup compilers.</span></span>

<span data-ttu-id="22fdc-161">Interfejs <xref:System.Windows.Markup.INameScope> istniał w programie WindowsBase w programie .NET Framework 3.5 i .NET Framework 3.0, ale istnieje w systemie.Xaml w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="22fdc-161">The <xref:System.Windows.Markup.INameScope> interface existed in WindowsBase in .NET Framework 3.5 and .NET Framework 3.0, but exists in System.Xaml in .NET Framework 4.</span></span> <span data-ttu-id="22fdc-162"><xref:System.Windows.Markup.INameScope>definiuje podstawowe operacje dla zakresu nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="22fdc-162"><xref:System.Windows.Markup.INameScope> defines basic operations for a XAML namescope.</span></span>

## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a><span data-ttu-id="22fdc-163">Klasy związane z XAML z nazwami udostępnionymi, które istnieją w WPF i System.Xaml</span><span class="sxs-lookup"><span data-stu-id="22fdc-163">XAML-related Classes with Shared Names that Exist in WPF and System.Xaml</span></span>

<span data-ttu-id="22fdc-164">Następujące klasy istnieją zarówno w zestawach WPF i System.Xaml zestawu w .NET Framework 4:</span><span class="sxs-lookup"><span data-stu-id="22fdc-164">The following classes exist in both the WPF assemblies and the System.Xaml assembly in .NET Framework 4:</span></span>

`XamlReader`

`XamlWriter`

`XamlParseException`

<span data-ttu-id="22fdc-165">Implementacja WPF znajduje <xref:System.Windows.Markup> się w obszarze nazw i PresentationFramework zestawu.</span><span class="sxs-lookup"><span data-stu-id="22fdc-165">The WPF implementation is found in the <xref:System.Windows.Markup> namespace, and PresentationFramework assembly.</span></span> <span data-ttu-id="22fdc-166">Implementacja System.Xaml znajduje <xref:System.Xaml> się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="22fdc-166">The System.Xaml implementation is found in the <xref:System.Xaml> namespace.</span></span> <span data-ttu-id="22fdc-167">Jeśli używasz WPF typów lub pochodzą z WPF typów, należy zazwyczaj używać <xref:System.Windows.Markup.XamlReader> <xref:System.Windows.Markup.XamlWriter> implementacji WPF i zamiast Implementacje System.Xaml.</span><span class="sxs-lookup"><span data-stu-id="22fdc-167">If you are using WPF types or are deriving from WPF types, you should typically use the WPF implementations of <xref:System.Windows.Markup.XamlReader> and <xref:System.Windows.Markup.XamlWriter> instead of the System.Xaml implementations.</span></span> <span data-ttu-id="22fdc-168">Aby uzyskać więcej informacji, <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>zobacz Uwagi w i .</span><span class="sxs-lookup"><span data-stu-id="22fdc-168">For more information, see Remarks in <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="22fdc-169">Jeśli są w tym odwołania do zestawów WPF i System.Xaml, a także używasz `include` instrukcji dla obszarów nazw <xref:System.Windows.Markup> i <xref:System.Xaml> nazw, może być konieczne pełne zakwalifikowanie wywołań do tych interfejsów API w celu rozwiązania typów bez dwuznaczności.</span><span class="sxs-lookup"><span data-stu-id="22fdc-169">If you are including references to both WPF assemblies and System.Xaml, and you also are using `include` statements for both the <xref:System.Windows.Markup> and <xref:System.Xaml> namespaces, you may need to fully qualify the calls to these APIs in order to resolve the types without ambiguity.</span></span>