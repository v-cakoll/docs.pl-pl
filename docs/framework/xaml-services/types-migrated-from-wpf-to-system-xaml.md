---
title: Typy migrowane z WPF do System.Xaml
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 943cdb2a21cbf2f95ef7fe2feefe6c0e71f57be4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939683"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Typy migrowane z WPF do System.Xaml
W .NET Framework 3,5 i .NET Framework 3,0, zarówno [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , jak i Windows Workflow Foundation zawierać implementację języka XAML. Wiele typów publicznych, które dostarczyły rozszerzalność implementacji XAML WPF, istniało w zestawach 'Windowsbase, 'Presentationcore i platformie docelowej. Podobnie typy publiczne, które dostarczyły rozszerzalność Windows Workflow Foundation XAML, istniały w zestawie System. Workflow. ComponentModel. W .NET Framework 4 niektóre typy powiązane z XAML są migrowane do zestawu System. XAML. Wspólna .NET Framework implementacja usług języka XAML umożliwia wiele scenariuszy rozszerzalności XAML, które zostały pierwotnie zdefiniowane przez implementację języka XAML określonej struktury, ale są teraz częścią ogólnej .NET Framework 4 obsługi języków XAML. Ten temat zawiera listę migrowanych typów i omawiające problemy związane z migracją.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Zestawy i przestrzenie nazw  
 W .NET Framework 3,5 i .NET Framework 3,0 Typy obsługiwane przez WPF obsługujące język XAML zostały ogólnie uwzględnione w <xref:System.Windows.Markup> przestrzeni nazw. Większość z tych typów była w zestawie 'Windowsbase.  
  
 W .NET Framework 4 istnieje nowa <xref:System.Xaml> przestrzeń nazw i nowy zestaw system. XAML. Wiele typów, które zostały pierwotnie zaimplementowane dla języka XAML WPF, są teraz udostępniane jako punkty rozszerzalności lub usługi dla dowolnej implementacji języka XAML. W ramach udostępniania im bardziej ogólnych scenariuszy typy są przekazywane z oryginalnego zestawu WPF do zestawu System. XAML. Dzięki temu scenariusze rozszerzalności XAML nie muszą obejmować zestawów innych struktur (takich jak WPF i Windows Workflow Foundation).  
  
 W przypadku migrowanych typów większość typów pozostaje w <xref:System.Windows.Markup> przestrzeni nazw. Było to częściowo, aby uniknąć przerywania mapowania przestrzeni nazw środowiska CLR w istniejących implementacjach dla poszczególnych plików. W związku z tym <xref:System.Windows.Markup> przestrzeń nazw w .NET Framework 4 zawiera kombinację ogólnych typów obsługi języka XAML (z zestawu System. XAML) i typy, które są specyficzne dla implementacji języka XAML WPF (z 'windowsbase i innych zestawów WPF). Każdy typ, który został zmigrowany do System. XAML, ale istniał wcześniej w zestawie WPF, ma obsługę przekazywania typu w wersji 4 zestawu WPF.  
  
### <a name="workflow-xaml-support-types"></a>Typy obsługi języka XAML przepływu pracy  
 Windows Workflow Foundation podano również typy obsługi języka XAML, a w wielu przypadkach te same krótkie nazwy są równoważne. Poniżej znajduje się lista typów Windows Workflow Foundation pomocy technicznej XAML:  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Te typy pomocy technicznej nadal istnieją w zestawach Windows Workflow Foundation dla .NET Framework 4 i nadal mogą być używane dla określonych aplikacji Windows Workflow Foundation. nie należy jednak odwoływać się do nich za pomocą aplikacji ani struktur, które nie używają Windows Workflow Foundation.  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 W .NET Framework 3,5 i .NET Framework 3,0 <xref:System.Windows.Markup.MarkupExtension> Klasa dla WPF znajdowała się w zestawie 'windowsbase. Klasa równoległa dla Windows Workflow Foundation, <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>w zestawie System. Workflow. ComponentModel. W .NET Framework 4, <xref:System.Windows.Markup.MarkupExtension> Klasa jest migrowana do zestawu System. XAML. W .NET Framework 4 <xref:System.Windows.Markup.MarkupExtension> jest przeznaczony dla dowolnego scenariusza rozszerzalności XAML, który używa .NET Framework usług XAML, a nie tylko dla tych, które kompilują w określonych strukturach. Jeśli jest to możliwe, określone struktury lub kod użytkownika w strukturze powinien również kompilować <xref:System.Windows.Markup.MarkupExtension> klasy dla rozszerzenia XAML.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>Klasy usług pomocniczych MarkupExtension  
 .NET Framework 3,5 i .NET Framework 3,0 dla platformy WPF udostępniają kilka usług, które <xref:System.Windows.Markup.MarkupExtension> były dostępne dla <xref:System.ComponentModel.TypeConverter> implementacji i implementacji do obsługi użycia typu/właściwości w języku XAML. Są to następujące usługi:  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
> Inną usługą z .NET Framework 3,5, która jest związana z rozszerzeniami znaczników <xref:System.Windows.Markup.IReceiveMarkupExtension> jest interfejs. <xref:System.Windows.Markup.IReceiveMarkupExtension>nie została zmigrowana i jest oznaczona `[Obsolete]` dla .NET Framework 4. Scenariusze, które wcześniej <xref:System.Windows.Markup.IReceiveMarkupExtension> były używane, <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> powinny zamiast tego używać przypisanych wywołań zwrotnych. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute>jest również oznaczona `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>Funkcje języka XAML  
 Niektóre funkcje języka XAML i składniki dla WPF wcześniej istniały w zestawie platformie docelowej. Zostały one zaimplementowane jako <xref:System.Windows.Markup.MarkupExtension> podklasa, aby udostępnić użycie rozszerzenia znaczników w znacznikach XAML. W .NET Framework 4 znajdują się one w zestawie System. XAML, aby projekty, które nie zawierają zestawów WPF, mogły korzystać z tych funkcji na poziomie języka XAML. WPF używa tych samych implementacji dla aplikacji .NET Framework 4. Podobnie jak w przypadku innych przypadków wymienionych w tym temacie, typy pomocnicze nadal istnieją w <xref:System.Windows.Markup> przestrzeni nazw, aby uniknąć przerywania poprzednich odwołań.  
  
 Poniższa tabela zawiera listę klas obsługi funkcji języka XAML, które są zdefiniowane w pliku System. XAML.  
  
|Funkcja języka XAML|Użycie|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 Chociaż system. XAML może nie mieć określonych klas pomocy technicznej, ogólna logika przetwarzania funkcji językowych języka XAML jest teraz dostępna w pliku System. XAML i jego implementacjach czytników XAML i autorzy języka XAML. Na przykład, `x:TypeArguments` jest atrybut, który jest przetwarzany przez czytniki XAML i autorzy XAML z implementacji system. XAML. można go zauważyć w strumieniu węzła XAML, który obsługuje domyślny kontekst schematu XAML (oparty na CLR), ma system typu XAML Reprezentacja i tak dalej. W związku z tym dokumentacja referencyjna dla wszystkich funkcji poziomu języka XAML jest podtematem dla [usług XAML](index.md) i tym ogólnym obszarem zestawu dokumentacji .NET Framework, zamiast być częścią zestawu dokumentacji WPF jako podtematem [Zaawansowane ( Windows Presentation Foundation)](../wpf/advanced/index.md) (podobnie jak w przypadku zestawów dokumentacji 3,5).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer i klasy pomocnicze  
 <xref:System.Windows.Markup.ValueSerializer> Klasa obsługuje konwersję typu na ciąg, szczególnie w przypadku serializacji XAML, gdzie Serializacja może wymagać wielu trybów lub węzłów w danych wyjściowych. W .NET Framework 3,5 i .NET Framework 3,0, <xref:System.Windows.Markup.ValueSerializer> dla WPF, znajdował się w zestawie 'windowsbase. W .NET Framework 4, <xref:System.Windows.Markup.ValueSerializer> Klasa znajduje się w pliku System. XAML i jest przeznaczona dla dowolnego scenariusza rozszerzalności XAML, a nie tylko dla tych, które kompilują w WPF. <xref:System.Windows.Markup.IValueSerializerContext>(usługa pomocnicza) i <xref:System.Windows.Markup.DateTimeValueSerializer> (określona podklasa) są również migrowane do System. XAML.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>Atrybuty dotyczące języka XAML  
 W języku XAML WPF uwzględniono kilka atrybutów, które mogą być stosowane do typów CLR, aby wskazać coś na temat zachowania języka XAML. Poniżej znajduje się lista atrybutów, które istniały w zestawach WPF w .NET Framework 3,5 i .NET Framework 3,0. Te atrybuty są migrowane do pliku System. XAML w .NET Framework 4.  
  
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
## <a name="miscellaneous-classes"></a>Klasy różne  
 <xref:System.Windows.Markup.IComponentConnector> Interfejs istniał w 'windowsbase w .NET Framework 3,5 i .NET Framework 3,0, ale istnieje w pliku System. XAML w .NET Framework 4. <xref:System.Windows.Markup.IComponentConnector>jest przeznaczony głównie do obsługi narzędzi i kompilatorów znaczników języka XAML.  
  
 <xref:System.Windows.Markup.INameScope> Interfejs istniał w 'windowsbase w .NET Framework 3,5 i .NET Framework 3,0, ale istnieje w pliku System. XAML w .NET Framework 4. <xref:System.Windows.Markup.INameScope>Definiuje podstawowe operacje dla namescope języka XAML.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Klasy związane z językiem XAML z nazwami udostępnionymi, które istnieją w WPF i system. XAML  
 Następujące klasy istnieją zarówno w zestawach WPF, jak i w zestawie System. XAML w .NET Framework 4:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 Implementacja WPF znajduje się w <xref:System.Windows.Markup> przestrzeni nazw, a zestaw platformie docelowej. Implementacja System. XAML znajduje się w <xref:System.Xaml> przestrzeni nazw. Jeśli używasz typów WPF lub są one wyprowadzane z typów WPF, zazwyczaj należy używać implementacji WPF dla <xref:System.Windows.Markup.XamlReader> i <xref:System.Windows.Markup.XamlWriter> zamiast implementacji system. XAML. Aby uzyskać więcej informacji, zobacz uwagi <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> w <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>i.  
  
 Jeśli są to odwołania do zestawów WPF i system. XAML, a także są używane `include` instrukcje dla <xref:System.Windows.Markup> i <xref:System.Xaml> przestrzeni nazw, może być konieczne pełne zakwalifikowanie wywołań do tych interfejsów API w celu rozpoznania typów bez niejednoznaczności.  
  
## <a name="see-also"></a>Zobacz także

- [Usługi XAML](index.md)
