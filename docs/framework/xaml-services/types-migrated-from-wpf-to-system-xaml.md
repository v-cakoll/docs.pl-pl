---
title: Typy migrowane z WPF do System.Xaml
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
caps.latest.revision: "14"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: db227b5c7915b6ce0b0fe8400a8545256ea6d6b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Typy migrowane z WPF do System.Xaml
W [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] i [!INCLUDE[net_v30_long](../../../includes/net-v30-long-md.md)], oba [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] uwzględnione implementacji języka XAML. Wiele typy publiczne, podane rozszerzalności dla implementacji WPF XAML istniał w zestawach WindowsBase, PresentationCore i PresentationFramework. Podobnie, publicznego typy, które podano rozszerzalności dla [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] XAML istniał w zestawie System.Workflow.ComponentModel. W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], niektóre typy związane z XAML są migrowane do System.Xaml zestawu. Najczęstszą implementacją .NET Framework usług języka XAML umożliwia obsługę wielu scenariuszy rozszerzalności XAML, pierwotnie zostały określone przez implementację XAML określonej platformy, które są teraz częścią ogólnych [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] obsługę języka XAML. Ten temat zawiera listę typów, które są migrowane i w tym artykule omówiono zagadnienia związane z migracją.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Zestawy i przestrzenie nazw  
 W [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] i [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], typy, które WPF zaimplementowana do obsługi XAML zostały zazwyczaj w <xref:System.Windows.Markup> przestrzeni nazw. Większość tych typów były w zestawie WindowsBase.  
  
 W [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], jest dostępna nowa <xref:System.Xaml> przestrzeni nazw i nowego zestawu System.Xaml. Podano wiele typów, które zostały po raz pierwszy wprowadzone dla WPF XAML teraz jako punkty rozszerzeń lub usługi, implementacji języka XAML. W ramach przygotowywania ich do scenariuszy bardziej ogólne typy są typ przesłany dalej z ich oryginalnego zestawu WPF do System.Xaml zestawu. Dzięki temu scenariusze rozszerzalności XAML bez konieczności dołączania zestawy innych platform (takich jak WPF i [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]).  
  
 Dla typów migrowanych większość typów pozostają w <xref:System.Windows.Markup> przestrzeni nazw. Częściowo to pozwala uniknąć przerwy CLR mapowania przestrzeni nazw w istniejących wdrożeniach na poziomie każdego pliku. W związku z tym <xref:System.Windows.Markup> przestrzeni nazw w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zawiera mieszane typy obsługi języka XAML ogólne (na podstawie zestawu System.Xaml) i typy, które są specyficzne dla implementacji WPF XAML (od innych zestawów WPF i WindowsBase). Typ migracji do System.Xaml, ale wcześniej istniały w zestawie WPF obsługuje przekazywanie dalej typu w wersji 4 zestawu WPF.  
  
### <a name="workflow-xaml-support-types"></a>Typy obsługi XAML przepływu pracy  
 [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]również pod warunkiem XAML obsługi typów, a w wielu przypadkach te mają identyczne krótkich nazw na równoważne WPF. Poniżej przedstawiono listę [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] XAML obsługi typów:  
  
-   <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Te obsługi typów nadal istnieć w [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] zestawy dla [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] i nadal mogą służyć do konkretnego [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] aplikacji, jednak ich powinien nie można odwoływać się przez aplikacje lub platformy, które nie korzystają z [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)].  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 W [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] i [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], <xref:System.Windows.Markup.MarkupExtension> klasy została WPF w zestawie WindowsBase. Równoległe klasę [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)], <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, istniał już w zestawie System.Workflow.ComponentModel. W [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.Windows.Markup.MarkupExtension> klasy jest migrowana do System.Xaml zestawu. W [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.Windows.Markup.MarkupExtension> ma w żadnym scenariuszu rozszerzalności XAML, który korzysta z usług programu .NET Framework XAML, nie tylko dla tych, które kompilacji na określonych platformach. Jeśli to możliwe, określonych platform lub kod użytkownika w ramach powinny także wykorzystywać <xref:System.Windows.Markup.MarkupExtension> klasy dla rozszerzenia języka XAML.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>Klasy obsługi usługi MarkupExtension  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]i [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] dla WPF podać kilka usług, które były dostępne dla <xref:System.Windows.Markup.MarkupExtension> implementacje i <xref:System.ComponentModel.TypeConverter> implementacje do obsługi użycia typu/właściwości w języku XAML. Te usługi są następujące:  
  
-   <xref:System.Windows.Markup.IProvideValueTarget>  
  
-   <xref:System.Windows.Markup.IUriContext>  
  
-   <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  Inną usługę z [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] który jest powiązany z rozszerzenia znaczników jest <xref:System.Windows.Markup.IReceiveMarkupExtension> interfejsu. <xref:System.Windows.Markup.IReceiveMarkupExtension>nie zostały poddane migracji, a jest oznaczona jako `[Obsolete]` dla [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Scenariusze, które wcześniej używane <xref:System.Windows.Markup.IReceiveMarkupExtension> zamiast tego należy użyć <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> przypisanych wywołań zwrotnych. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute>jest również oznaczona `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>Funkcje języka XAML  
 Niektórych funkcji języka XAML i składniki WPF wcześniej istniały w zestawie PresentationFramework. Te zostały zaimplementowane jako <xref:System.Windows.Markup.MarkupExtension> podklasy do udostępnienia użycia rozszerzenia znacznika w kodzie XAML. W [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], istnieją one w zestawie System.Xaml tak, aby projekty, które nie zawierają zestawy WPF można korzystać z funkcji poziom języka XAML. WPF używa tych tej samej implementacji dla [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] aplikacji. Zgodnie z innych przypadkach opisanych w tym temacie pomocnicze typy nadal istnieje w <xref:System.Windows.Markup> przestrzeni nazw, aby uniknąć dzielenia poprzednie.  
  
 Poniższa tabela zawiera listę klas obsługę funkcji XAML, które są zdefiniowane w System.Xaml.  
  
|Funkcja języka XAML|Użycie|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 Mimo że System.Xaml nie może mieć klasy wspomagające, ogólne logikę przetwarzania funkcje językowe dla języka XAML teraz znajduje się w System.Xaml i jego zaimplementowanym czytników XAML i zapisywania XAML. Na przykład `x:TypeArguments` jest atrybut, który jest przetwarzany przez czytelników XAML i autorzy XAML z implementacji System.Xaml; można zauważyć w strumieniu węzłów XAML, nie ma obsługi w domyślny kontekst schematu XAML (w oparciu o CLR), ma system typu XAML Reprezentacja i tak dalej. W związku z tym dokumentacji dla wszystkich funkcji poziom języka XAML jest podrzędny dla [usługi XAML](../../../docs/framework/xaml-services/index.md) i tego obszaru Ogólne zestawu dokumentacji .NET Framework, zamiast część dokumentacji WPF Ustaw jako podrzędny z [Zaawansowane (Windows Presentation Foundation)](../../../docs/framework/wpf/advanced/index.md) (ponieważ jest nadal w przypadku 3.5 zestawy dokumentacji).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer i klasy pomocnicze  
 <xref:System.Windows.Markup.ValueSerializer> Klasa obsługuje konwersji typu ciąg, szczególnie dla przypadków serializacji XAML, gdzie serializacji może wymagać wielu trybów lub być węzłami w danych wyjściowych. W [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] i [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], <xref:System.Windows.Markup.ValueSerializer> została WPF w zestawie WindowsBase. W [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.Windows.Markup.ValueSerializer> klasy jest System.Xaml i ma w żadnym scenariuszu rozszerzalności XAML nie tylko te, które kompilacji na WPF. <xref:System.Windows.Markup.IValueSerializerContext>(usługa pomocnicza) i <xref:System.Windows.Markup.DateTimeValueSerializer> (podklasą określonej) również są migrowane do System.Xaml.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>Atrybuty związane z XAML  
 WPF XAML uwzględnione kilka atrybutów, które można stosować do typów CLR, aby wskazać, jak ich zachowanie języka XAML. Poniżej przedstawiono listę atrybutów, które były dostępne w zestawach WPF w [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] i [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]. Te atrybuty są migrowane do System.Xaml w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
-   <xref:System.Windows.Markup.AmbientAttribute>  
  
-   <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
-   <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
-   <xref:System.Windows.Markup.DependsOnAttribute>  
  
-   <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
-   <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
-   <xref:System.Windows.Markup.RootNamespaceAttribute>  
  
-   <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
-   <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
-   <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
-   <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>Różne klasy  
 <xref:System.Windows.Markup.IComponentConnector> Interfejsu istniał w WindowsBase w [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] i [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], ale nie istnieje w System.Xaml w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. <xref:System.Windows.Markup.IComponentConnector>jest przeznaczone głównie dla narzędzia pomocy technicznej i kompilatory znaczników w XAML.  
  
 <xref:System.Windows.Markup.INameScope> Interfejsu istniał w WindowsBase w [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] i [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], ale nie istnieje w System.Xaml w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. <xref:System.Windows.Markup.INameScope>Definiuje podstawowe operacje dla XAML namescope.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Klasy związane z XAML z nazwami udostępnionych, które istnieją w podsystemie WPF i System.Xaml  
 Następujące klasy istnieje zarówno w przypadku zestawów WPF, jak i zestawu System.Xaml w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 Implementacja WPF znajduje się w <xref:System.Windows.Markup> przestrzeni nazw i zestawu PresentationFramework. Implementacja System.Xaml znajduje się w <xref:System.Xaml> przestrzeni nazw. Jeśli używasz typy WPF lub są wynikających z typów WPF, zazwyczaj należy używać implementacje WPF <xref:System.Windows.Markup.XamlReader> i <xref:System.Windows.Markup.XamlWriter> zamiast System.Xaml implementacji. Aby uzyskać więcej informacji, zobacz uwagi w <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> i <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.  
  
 Jeśli zawierają odwołania do System.Xaml i WPF zestawy, a także w przypadku korzystania `include` instrukcje dla obu <xref:System.Windows.Markup> i <xref:System.Xaml> przestrzeni nazw, konieczne może być pełnej kwalifikacji wywołań do tych interfejsów API w celu rozpoznania typów bez niejednoznaczności.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi XAML](../../../docs/framework/xaml-services/index.md)
