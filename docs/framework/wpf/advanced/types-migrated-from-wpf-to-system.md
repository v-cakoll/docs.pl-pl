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
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Typy migrowane z WPF do pliku System.Xaml

W programie .NET Framework 3.5 i .NET Framework 3.0 zarówno Windows Presentation Foundation (WPF) i Windows Workflow Foundation zawierały implementację języka XAML. Wiele typów publicznych, które dostarczyły rozszerzalność dla WPF XAML implementacji istniał w WindowsBase, PresentationCore i PresentationFramework zestawów. Podobnie w zestawie System.Workflow.ComponentModel istniały typy publiczne, które zapewniały rozszerzalność xaml programu Windows Workflow Foundation. W .NET Framework 4 niektóre typy związane z XAML zostały zmigrowane do zestawu System.Xaml. Wspólna implementacja języka XAML w ramach platformy .NET Framework umożliwia wiele scenariuszy rozszerzalności języka XAML, które zostały pierwotnie zdefiniowane przez implementację XAML określonej struktury, ale są teraz częścią ogólnej obsługi języka XAML programu .NET Framework 4. W tym artykule wymieniono typy, które zostały zmigrowane i omówiono problemy związane z migracją.

## <a name="assemblies-and-namespaces"></a>Zestawy i przestrzenie nazw

W .NET Framework 3.5 i .NET Framework 3.0 typy, które WPF implementowane do obsługi XAML były zazwyczaj w obszarze <xref:System.Windows.Markup> nazw. Większość z tych typów znajdowała się w zestawie WindowsBase.

W .NET Framework 4 jest <xref:System.Xaml> nowy obszar nazw i nowy zestaw System.Xaml. Wiele typów, które zostały pierwotnie zaimplementowane dla WPF XAML są teraz dostarczane jako punkty rozszerzalności lub usług dla dowolnej implementacji XAML. W ramach udostępniania ich dla bardziej ogólnych scenariuszy typy są przekazywane z ich oryginalnego zestawu WPF do Zestawu System.Xaml. Dzięki temu scenariusze rozszerzalności XAML bez konieczności dołączania zestawów innych struktur (takich jak WPF I Windows Workflow Foundation).

W przypadku typów migrowanych większość <xref:System.Windows.Markup> typów pozostaje w obszarze nazw. Miało to częściowo zapobiec przerywaniu mapowania obszaru nazw CLR w istniejących implementacjach na podstawie dla jednego pliku. W rezultacie obszar <xref:System.Windows.Markup> nazw w programie .NET Framework 4 zawiera kombinację typów obsługi języka ogólnego XAML (z zestawu System.Xaml) i typów, które są specyficzne dla implementacji WPF XAML (z WindowsBase i innych zestawów WPF). Każdy typ, który został zmigrowany do System.Xaml, ale istniał wcześniej w zestawie WPF, ma obsługę przekazywania tekstu w wersji 4 zestawu WPF.

### <a name="workflow-xaml-support-types"></a>Typy obsługi XAML przepływu pracy

Windows Workflow Foundation również pod warunkiem, typy obsługi XAML i w wielu przypadkach miały identyczne krótkie nazwy do odpowiednika WPF. Poniżej znajduje się lista typów obsługi XAML programu Windows Workflow Foundation:

- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>

Te typy pomocy technicznej nadal istnieją w zestawach Fundacji przepływu pracy systemu Windows dla platformy .NET Framework 4 i nadal mogą być używane dla określonych aplikacji Programu Windows Workflow Foundation; jednak nie powinny się odwoływać aplikacje lub struktury, które nie używają programu Windows Workflow Foundation.

## <a name="markupextension"></a>MarkupExtension

W .NET Framework 3.5 i .NET Framework 3.0 <xref:System.Windows.Markup.MarkupExtension> klasa dla WPF WPF była w zestawie WindowsBase. Klasa równoległa dla fundacji <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>przepływu pracy systemu Windows, istniała w zestawie System.Workflow.ComponentModel. W .NET Framework 4 <xref:System.Windows.Markup.MarkupExtension> klasa jest migrowana do zestawu System.Xaml. W programie .NET Framework <xref:System.Windows.Markup.MarkupExtension> 4 jest przeznaczony dla dowolnego scenariusza rozszerzalności XAML, który używa usług .NET XAML Services, a nie tylko dla tych, które opierają się na określonych platformach. Jeśli to możliwe, określone struktury lub kod użytkownika <xref:System.Windows.Markup.MarkupExtension> w ramach należy również opierać się na klasie dla rozszerzenia XAML.

## <a name="markupextension-supporting-service-classes"></a>Klasy usługi pomocniczej naciśnienia znaczników

.NET Framework 3.5 i .NET Framework 3.0 dla WPF dostarczył kilka usług, które były dostępne dla <xref:System.Windows.Markup.MarkupExtension> realizatorów i <xref:System.ComponentModel.TypeConverter> implementacji do obsługi użycia typu/właściwości w XAML. Usługi te są następujące:

- <xref:System.Windows.Markup.IProvideValueTarget>

- <xref:System.Windows.Markup.IUriContext>

- <xref:System.Windows.Markup.IXamlTypeResolver>

> [!NOTE]
> Inną usługą z platformy .NET Framework 3.5, <xref:System.Windows.Markup.IReceiveMarkupExtension> która jest powiązana z rozszerzeniami znaczników, jest interfejs. <xref:System.Windows.Markup.IReceiveMarkupExtension>nie został zmigrowany i jest oznaczony `[Obsolete]` dla programu .NET Framework 4. Scenariusze, które <xref:System.Windows.Markup.IReceiveMarkupExtension> wcześniej używane <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> należy zamiast tego użyć przypisanych wywołań zwrotnych. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute>jest również `[Obsolete]`oznaczony .

## <a name="xaml-language-features"></a>Funkcje języka XAML

Kilka funkcji języka XAML i składników dla WPF wcześniej istniało w PresentationFramework zestawu. Zostały one zaimplementowane jako podklasa, <xref:System.Windows.Markup.MarkupExtension> aby udostępnić użycie rozszerzenia znaczników w znacznikach XAML. W .NET Framework 4 istnieją one w zestawie System.Xaml, dzięki czemu projekty, które nie zawierają zestawów WPF, mogą używać tych funkcji na poziomie języka XAML. WPF WPF używa tych samych implementacji dla aplikacji .NET Framework 4. Podobnie jak w przypadku innych przypadków, które są wymienione w <xref:System.Windows.Markup> tym temacie, typy pomocnicze nadal istnieją w obszarze nazw, aby uniknąć przerywania poprzednich odwołań.

Poniższa tabela zawiera listę klas obsługi funkcji XAML zdefiniowanych w pliku System.Xaml.

|Funkcja języka XAML|Sposób użycia|
|---------------------------|-----------|
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|

Chociaż system.Xaml może nie mieć określonych klas pomocy technicznej, ogólna logika przetwarzania funkcji języka języka XAML znajduje się obecnie w systemie.Xaml i jego zaimplementowanych czytnikach XAML i modułach zapisu XAML. Na przykład `x:TypeArguments` jest atrybutem, który jest przetwarzany przez czytniki XAML i moduły zapisującej XAML z implementacji System.Xaml; można zauważyć w strumieniu węzła XAML, ma obsługę w domyślnym (opartym na PROGRAMIE CLR) kontekście schematu XAML, ma reprezentację systemu typu XAML i tak dalej. W rezultacie dokumentacja referencyjna dla wszystkich funkcji na poziomie języka XAML jest podtematem [usług XAML](../../../desktop-wpf/xaml-services/index.md) w [Podręczniku pulpitu dla programu Windows Presentation Foundation (WPF)](../../../desktop-wpf/overview/index.md).

## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer i klasy pomocnicze

Klasa <xref:System.Windows.Markup.ValueSerializer> obsługuje konwersji typu do ciągu, szczególnie w przypadku serializacji XAML, gdzie serializacji może wymagać wielu trybów lub węzłów w danych wyjściowych. W programie .NET Framework 3.5 i .NET <xref:System.Windows.Markup.ValueSerializer> Framework 3.0 for WPF był w zestawie WindowsBase. W programie .NET Framework <xref:System.Windows.Markup.ValueSerializer> 4 klasa znajduje się w system.Xaml i jest przeznaczona dla dowolnego scenariusza rozszerzalności XAML, nie tylko dla tych, które opierają się na WPF. <xref:System.Windows.Markup.IValueSerializerContext>(usługa pomocnicza) <xref:System.Windows.Markup.DateTimeValueSerializer> i (określona podklasa) są również migrowane do system.Xaml.

## <a name="xaml-related-attributes"></a>Atrybuty związane z XAML

WPF XAML zawiera kilka atrybutów, które mogą być stosowane do typów CLR, aby wskazać coś o ich zachowanie XAML. Poniżej znajduje się lista atrybutów, które istniały w zestawach WPF w .NET Framework 3.5 i .NET Framework 3.0. Te atrybuty są migrowane do systemu System.Xaml w .NET Framework 4.

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

## <a name="miscellaneous-classes"></a>Różne klasy

Interfejs <xref:System.Windows.Markup.IComponentConnector> istniał w programie WindowsBase w programie .NET Framework 3.5 i .NET Framework 3.0, ale istnieje w systemie.Xaml w programie .NET Framework 4. <xref:System.Windows.Markup.IComponentConnector>jest przeznaczony przede wszystkim do obsługi narzędzi i kompilatorów znaczników XAML.

Interfejs <xref:System.Windows.Markup.INameScope> istniał w programie WindowsBase w programie .NET Framework 3.5 i .NET Framework 3.0, ale istnieje w systemie.Xaml w programie .NET Framework 4. <xref:System.Windows.Markup.INameScope>definiuje podstawowe operacje dla zakresu nazw XAML.

## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Klasy związane z XAML z nazwami udostępnionymi, które istnieją w WPF i System.Xaml

Następujące klasy istnieją zarówno w zestawach WPF i System.Xaml zestawu w .NET Framework 4:

`XamlReader`

`XamlWriter`

`XamlParseException`

Implementacja WPF znajduje <xref:System.Windows.Markup> się w obszarze nazw i PresentationFramework zestawu. Implementacja System.Xaml znajduje <xref:System.Xaml> się w obszarze nazw. Jeśli używasz WPF typów lub pochodzą z WPF typów, należy zazwyczaj używać <xref:System.Windows.Markup.XamlReader> <xref:System.Windows.Markup.XamlWriter> implementacji WPF i zamiast Implementacje System.Xaml. Aby uzyskać więcej informacji, <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>zobacz Uwagi w i .

Jeśli są w tym odwołania do zestawów WPF i System.Xaml, a także używasz `include` instrukcji dla obszarów nazw <xref:System.Windows.Markup> i <xref:System.Xaml> nazw, może być konieczne pełne zakwalifikowanie wywołań do tych interfejsów API w celu rozwiązania typów bez dwuznaczności.
