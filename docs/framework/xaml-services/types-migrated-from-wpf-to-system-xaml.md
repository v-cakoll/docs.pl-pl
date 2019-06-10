---
title: Typy migrowane z WPF do System.Xaml
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 37433768c1bca3c013fb1e505d55bd7295f34933
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758016"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Typy migrowane z WPF do System.Xaml
W .NET Framework 3.5 i .NET Framework 3.0 zarówno [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] i implementacji języka XAML w pakiecie Windows Workflow Foundation. Istnieje wiele typów publicznych, które dostarczane rozszerzalności dla implementacji WPF XAML w zestawach WindowsBase PresentationCore i PresentationFramework. Podobnie typów publicznych, które podano rozszerzalności dla programu Windows Workflow Foundation XAML istniał w zestawie System.Workflow.ComponentModel. W programie .NET Framework 4 niektóre typy związane z XAML są migrowane do System.Xaml zestawu. Typową implementację usługi języka XAML .NET Framework umożliwia obsługę wielu scenariuszy rozszerzalności XAML, zostały pierwotnie zdefiniowana przez implementację XAML określonym środowiskiem, które są teraz częścią ogólnego obsługę języka XAML programu .NET Framework 4. Ten temat zawiera listę typów, które są migrowane ale w tym artykule omówiono zagadnienia związane z migracją.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Zestawy i przestrzenie nazw  
 W .NET Framework 3.5 i .NET Framework 3.0, typy które są wdrażane WPF, aby wspierać XAML zostały ogólnie w <xref:System.Windows.Markup> przestrzeni nazw. Większość z tych typów znajdowały się w zestawie WindowsBase.  
  
 W programie .NET Framework 4 jest dostępny nowy <xref:System.Xaml> przestrzeni nazw i nowego assembly System.Xaml. Wiele typów, które zostały wprowadzone dla WPF XAML teraz jako dostępne są punkty rozszerzeń lub usług w celach implementacji XAML. W ramach udostępnienie ich dla bardziej ogólnych scenariuszy typy są przekazane dalej od ich oryginalnego zestawu WPF do System.Xaml zestawu. Umożliwia to obsługę scenariuszy rozszerzalności XAML bez konieczności dołączania zestawów innych środowisk (takich jak WPF i Windows Workflow Foundation).  
  
 Dla migrowanych typów, większość typów pozostają w <xref:System.Windows.Markup> przestrzeni nazw. Taka konfiguracja była częściowo pozwala uniknąć przerwy CLR mapowania przestrzeni nazw w istniejących wdrożeniach na poziomie każdego pliku. W rezultacie <xref:System.Windows.Markup> przestrzeń nazw w programie .NET Framework 4 zawiera kombinację ogólne typy obsługi języka XAML (z zestawu System.Xaml) oraz typy, które są specyficzne dla implementacji WPF XAML (z WindowsBase i innych podzespołów WPF). Dowolny typ, który był migrowane do System.Xaml, ale wcześniej istniejących w zestawie WPF obsługuje przekazywanie dalej typu w zestawie WPF w wersji 4.  
  
### <a name="workflow-xaml-support-types"></a>Typy obsługi XAML przepływu pracy  
 Windows Workflow Foundation również podane typy obsługi XAML, a w wielu przypadkach te ma identyczny krótkich nazw na równoważne WPF. Poniżej znajduje się lista typów pomocy technicznej Windows Workflow Foundation XAML:  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Te obsługę typów nadal istnieją w zestawy Windows Workflow Foundation dla programu .NET Framework 4, a wciąż mogą służyć do określonych aplikacji systemu Windows Workflow Foundation; jednak ich powinna nie można odwoływać się przez aplikacje lub struktur, które nie korzystają z programu Windows Workflow Foundation.  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 W .NET Framework 3.5 i .NET Framework 3.0 <xref:System.Windows.Markup.MarkupExtension> klasy dla WPF, to w zestawie WindowsBase. Klas równoległych dla programu Windows Workflow Foundation, <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, istniał już w zestawie System.Workflow.ComponentModel. W programie .NET Framework 4 <xref:System.Windows.Markup.MarkupExtension> klasy jest migrowana do System.Xaml zestawu. W programie .NET Framework 4 <xref:System.Windows.Markup.MarkupExtension> jest przeznaczony dla wszystkich scenariuszy rozszerzalności XAML, które korzysta z usług programu .NET Framework XAML, nie tylko dla osób, które są kompilowane na określonych platformach. Jeśli to możliwe, określonych platform lub kod użytkownika w ramach powinny także wykorzystywać <xref:System.Windows.Markup.MarkupExtension> klasy rozszerzenia XAML.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>Klasy usługi obsługujące wyrażenia MarkupExtension  
 .NET framework 3.5 i .NET Framework 3.0 dla programu WPF podano kilka usług, które były dostępne dla <xref:System.Windows.Markup.MarkupExtension> implementacje i <xref:System.ComponentModel.TypeConverter> implementacji w celu obsługi użycia właściwości/typu w XAML. Te usługi są następujące:  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  Jest inna usługa z .NET Framework 3.5, który jest powiązany z rozszerzeń struktury znaczników <xref:System.Windows.Markup.IReceiveMarkupExtension> interfejsu. <xref:System.Windows.Markup.IReceiveMarkupExtension> nie została poddana migracji i jest oznaczony jako `[Obsolete]` dla .NET Framework 4. Scenariusze, które wcześniej używano <xref:System.Windows.Markup.IReceiveMarkupExtension> zamiast tego należy użyć <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> opartego na atrybutach wywołań zwrotnych. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> jest również oznaczony `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>Funkcje języka XAML  
 Kilka funkcji języka XAML i składniki WPF wcześniej istniały w zestawie PresentationFramework. Zostały one zaimplementowane jako <xref:System.Windows.Markup.MarkupExtension> podklasy do udostępnienia użycia rozszerzenia znaczników w znaczniku XAML. W programie .NET Framework 4 istnieją one w zestawie System.Xaml tak, aby projekty, które nie zawierają zestawy WPF można użyć tych funkcji z poziomu języka XAML. WPF używa tych implementacji tych samych aplikacji .NET Framework 4. Zgodnie z innych przypadkach, które są wymienione w tym temacie pomocnicze typy w dalszym ciągu objęte <xref:System.Windows.Markup> przestrzeni nazw pozwala uniknąć przerwy poprzedniego odwołania.  
  
 Poniższa tabela zawiera listę klas obsługę funkcji XAML, które są zdefiniowane w System.Xaml.  
  
|Funkcja języka XAML|Użycie|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 Mimo że System.Xaml nie może mieć klasy pomocy technicznej właściwe, ogólne logikę przetwarzania funkcje językowe dla języka XAML teraz znajduje się w System.Xaml i jego zaimplementowano czytelnicy XAML i moduły zapisujące XAML. Na przykład `x:TypeArguments` jest atrybut, który jest przetwarzany przez czytniki XAML i moduły zapisujące XAML, z System.Xaml implementacji; mogą zauważyć w strumień węzłów XAML, domyślny kontekst schematu XAML (w oparciu o CLR) ma obsługi, ma system typu XAML Reprezentacja i tak dalej. W rezultacie dokumentacji dla wszystkich funkcji z poziomu języka XAML jest podrzędny dla [XAML Services](index.md) i że ogólne obszar zestawie dokumentacji .NET Framework, zamiast części dokumentacji programu WPF, Ustaw jako podrzędny z [Zaawansowane (Windows Presentation Foundation)](../wpf/advanced/index.md) (co jest nadal w przypadku wersji 3.5 zestawów dokumentacji).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer i obsługa klasy  
 <xref:System.Windows.Markup.ValueSerializer> Klasa obsługuje konwersję typu na ciąg, szczególnie w przypadku XAML serializacji przypadki, gdzie serializacji może wymagać wielu trybów lub węzły w danych wyjściowych. W .NET Framework 3.5 i .NET Framework 3.0 <xref:System.Windows.Markup.ValueSerializer> WPF to w zestawie WindowsBase. W programie .NET Framework 4 <xref:System.Windows.Markup.ValueSerializer> klasa znajduje się w System.Xaml i jest przeznaczony dla dowolnego scenariusza rozszerzania XAML nie tylko dla osób, które są kompilowane na WPF. <xref:System.Windows.Markup.IValueSerializerContext> (usługa pomocnicza) i <xref:System.Windows.Markup.DateTimeValueSerializer> (podklasą określonej) również zostały zmigrowane do System.Xaml.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>Atrybuty związane z XAML  
 WPF XAML dołączone kilka atrybutów, które mogą być stosowane na typy CLR w celu wskazania coś o ich zachowanie XAML. Oto lista atrybutów, które istniały w zestawach WPF w programie .NET Framework 3.5 i .NET Framework 3.0. Te atrybuty są migrowane do System.Xaml w programie .NET Framework 4.  
  
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
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>Różne klasy  
 <xref:System.Windows.Markup.IComponentConnector> Interfejsu, który istniał w WindowsBase w .NET Framework 3.5 i .NET Framework 3.0, ale nie istnieje w System.Xaml w programie .NET Framework 4. <xref:System.Windows.Markup.IComponentConnector> jest przeznaczone głównie dla narzędzia pomocy technicznej i kompilatory znaczników XAML.  
  
 <xref:System.Windows.Markup.INameScope> Interfejsu, który istniał w WindowsBase w .NET Framework 3.5 i .NET Framework 3.0, ale nie istnieje w System.Xaml w programie .NET Framework 4. <xref:System.Windows.Markup.INameScope> Definiuje podstawowe operacje XAML namescope.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Klasy związane z XAML, za pomocą nazwy udostępnionych, które istnieją w WPF i System.Xaml  
 Następujące klasy istnieje zarówno w przypadku zestawów WPF, jak i zestaw System.Xaml w programie .NET Framework 4:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 Implementacji WPF znajduje się w <xref:System.Windows.Markup> przestrzeni nazw i PresentationFramework zestawu. Implementacja System.Xaml znajduje się w <xref:System.Xaml> przestrzeni nazw. Jeśli używasz typów WPF lub są pochodząca z typów WPF, zazwyczaj należy używać implementacji WPF <xref:System.Windows.Markup.XamlReader> i <xref:System.Windows.Markup.XamlWriter> zamiast implementacje System.Xaml. Aby uzyskać więcej informacji, zobacz uwagi w <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> i <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.  
  
 Jeśli łącznie z odwołań do System.Xaml i WPF zestawów, a także używają `include` instrukcje dla obu <xref:System.Windows.Markup> i <xref:System.Xaml> przestrzeni nazw, może być konieczne pełnej kwalifikacji wywołań do tych interfejsów API, aby rozwiązać typów bez niejednoznaczności.  
  
## <a name="see-also"></a>Zobacz także

- [Usługi XAML](index.md)
