---
title: Typy konwerterów i rozszerzenia znaczników dla XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services
- XAML [XAML Services], value converters
- XAML [XAML Services], markup extension services
- value converters for XAML [XAML Services]
- XAML [XAML Services], service context
ms.assetid: db07a952-05ce-4aa4-b6f9-aac7397d0326
ms.openlocfilehash: 0c9cb7e87416860dda98df0da967ffbc070bc270
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565866"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>Typy konwerterów i rozszerzenia znaczników dla XAML
Typy konwerterów i rozszerzeń znaczników są dwie metody, które systemów typu XAML i zapisywania XAML służy do generowania elementów wykresu obiektu. Mimo że mają pewne cechy typy konwerterów i rozszerzeń znaczników znajdują się inaczej w strumień węzłów XAML. W tej dokumentacji zestawu, konwertery typu rozszerzenia znaczników i podobne konstrukcje są czasami zbiorczo nazywane konwertery wartości.  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>Konwertery wartości  
 W języku XAML konwertery wartości są używane dla różnych scenariuszy. Poniższa lista przedstawia różne typy konwertery wartości w języku XAML:  
  
-   Konwerter typów  
  
-   Rozszerzenie znaczników  
  
-   Serializator wartość  
  
-   Klasy pokrewne lub klasy pomocy technicznej, która zawiera logikę składni tekstu XAML  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Konwertery typu  
 W definicji usług .NET Framework XAML konwertery typu są klasy, które pochodzą ze środowiska CLR <xref:System.ComponentModel.TypeConverter> klasy. <xref:System.ComponentModel.TypeConverter> jest klasą, który był w programie Microsoft .NET Framework, przed wprowadzeniem XAML. Jego celem oryginalnego było do obsługi systemu windows właściwości i podobne tekstowych owoce cytrusowe metafory edycji dla [!INCLUDE[TLA2#tla_ide](../../../includes/tla2sharptla-ide-md.md)] właściwości. Wprowadzenie XAML .NET Framework używa <xref:System.ComponentModel.TypeConverter> można przekonwertować na obiekt składnię tekst (jako znajdujące się w wartości atrybutu lub węzeł wartość XAML). <xref:System.ComponentModel.TypeConverter> można również do serializacji obiektu wartości do składni tekstu. <xref:System.ComponentModel.TypeConverter> wykorzystano w poprzednich implementacjach XAML określonej struktury Windows Presentation Foundation (WPF) i Windows Communication Foundation (WCF). Aby uzyskać więcej informacji na temat <xref:System.ComponentModel.TypeConverter> w języku XAML, zobacz [typy konwerterów dla przeglądu XAML](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozszerzenia znaczników  
 W implementacji usług .NET Framework XAML rozszerzenia znaczników są klasy, które pochodzą z <xref:System.Windows.Markup.MarkupExtension> klasy. Rozszerzenia znaczników to pojęcie utworzonych w tym formularzu jest za pomocą języka XAML. Można potraktować jako ekran podobny do rozszerzonego sekwencja, który odwołuje się do klasy usługi, aby zapewnić jego logiki rozszerzenia znaczników. Pod względem znaczników procesory XAML powszechnie rozpoznaje rozszerzenie znaczników przez sekwencją tekstu, który rozpoczyna się od nawiasu otwierającego ({}) w ciągu tekstowym.  
  
 Rozszerzenia znaczników różnią się od konwertery typu. Konwertery typu są zwykle skojarzone z typów albo elementów członkowskich. Są one wywoływane podczas tworzenia wykresu obiektu lub serializacja napotka składni tekst, który jest skojarzony z tymi podmiotami.  
  
 Rozszerzenia znaczników skojarzonych z jednym pomocnicze klasy usługi, ale mogą być stosowane dla wartości elementu członkowskiego. (Jednak można zaimplementować celowo ograniczyć jej użycia do określonych członków lub typy docelowym przy użyciu kontekstu usługi rozszerzenia znaczników.) Rozszerzenia znaczników można zastąpić skojarzenia konwertera typu. Lub też użyć ich do określenia wartości atrybutu dla elementów członkowskich, które w przeciwnym razie nie będzie obsługiwać składni tekstu.  
  
 Aby uzyskać więcej informacji o wzorcu implementacji rozszerzenia znaczników dla XAML, zobacz [rozszerzenia znaczników dla przeglądu XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Markup.MarkupExtension> i <xref:System.Windows.Markup.ValueSerializer> typów znajdują się w <xref:System.Windows.Markup> przestrzeni nazw, a nie w <xref:System.Xaml> przestrzeni nazw. Oznacza to, że te typy są specyficzne dla technologii WPF i formularze systemu Windows, które w przeciwnym razie wypełnić przestrzenie nazw CLR, które zawierają ciąg znaków `Windows`. <xref:System.Windows.Markup.MarkupExtension> i <xref:System.Windows.Markup.ValueSerializer> zestaw System.Xaml i mieć nie zależności określonej platformy. Te typy istniał w przestrzeni nazw CLR dla [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] i pozostają w przestrzeni nazw CLR w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] pozwala uniknąć przerwy odwołań w istniejących projektach WPF. Aby uzyskać więcej informacji, zobacz [typy migrowane z WPF do System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md).  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>Wartość serializatorów  
 A <xref:System.Windows.Markup.ValueSerializer> jest konwerter specjalistyczną odmianą, który jest zoptymalizowana pod kątem Konwersja obiektu na ciąg. A <xref:System.Windows.Markup.ValueSerializer> dla XAML nie może implementować `ConvertFrom` metody wcale. A <xref:System.Windows.Markup.ValueSerializer> implementacji uzyskuje usług w sposób przypominający <xref:System.ComponentModel.TypeConverter> implementacji. Metody wirtualne podawanie danych wejściowych `context` parametru. `context` Parametr jest typu <xref:System.Windows.Markup.IValueSerializerContext>, który dziedziczy z <xref:System.IServiceProvider> interfejsu i ma <xref:System.IServiceProvider.GetService%2A> metody.  
  
 W systemie typów języka XAML i implementacji składnika zapisywania języka XAML, używające przetwarzanie pętli węzła XAML dla serializacji konwerter wartości, który jest skojarzony z typu lub elementu członkowskiego został zgłoszony przez jego własnej <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> właściwości. Jeśli jest znaczenie autorom XAML, które wykonują serializacji <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> i <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> istnieje konwerter typów ma być używane jako ścieżka obciążenia i serializator wartość powinna być używana do zapisywania ścieżki. Jeśli <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> istnieje, ale <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> jest `null`, konwerter typów służy do zapisywania ścieżki.  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>Inne konwertery wartości  
 Konwerter wartości jest rozszerzalny poza określonych wzorców konwertera typów lub rozszerzenie znaczników. Jednak takie dostosowanie również wymagać ponowna definicja system typów języka XAML, zgodnie z usługami .NET Framework XAML. Istniejący system typu XAML ma oświadczenia i systemy raportowania dla konwertery typu rozszerzenia znaczników i serializatorów wartość, ale nie dla niestandardowych formularzy konwersja wartości. Jeśli chcesz utworzyć konwertery wartości niestandardowych, użyj <xref:System.Xaml.Schema.XamlValueConverter%601> typu.  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>Typy konwerterów i rozszerzeń znaczników w połączeniu  
 Konwertery rozszerzenia i typ znaczników są używane w różnych sytuacjach w języku XAML. Mimo że kontekst jest dostępny do użycia rozszerzenia znaczników, zachowanie konwersji typu właściwości, gdy rozszerzenie znaczników zapewnia wartość jest zazwyczaj nie zostanie zaznaczona w implementacji rozszerzenia znaczników. Innymi słowy nawet wtedy, gdy rozszerzenie znaczników zwraca ciąg tekstowy jako jego `ProvideValue` output, zachowanie konwersji typu dla tego ciągu jako dotyczą określoną właściwość lub typ wartości właściwości nie jest wywoływany. Ogólnie rzecz biorąc rozszerzeniem znacznika służy do przetwarzania ciągu i zwracać obiekt bez żadnych konwerter typów związane.  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>Kontekst usługi dla konwertera wartości  
 Podczas implementowania konwerter wartości, często wymagany jest dostęp do kontekstu, w którym zastosowano konwerter wartości. Ten kontekst jest określany jako kontekst usługi. Kontekst usługi może obejmują informacje takie jak active kontekst schematu XAML, dostęp do wybranego typu mapowania systemu kontekst schematu XAML i moduł zapisywania obiektów XAML Podaj i tak dalej. Aby uzyskać więcej informacji na temat konteksty usług dostępne dla konwertera wartości oraz sposobu uzyskiwania dostępu do usług, które kontekstu usługi może zawierać zobacz [usługi kontekstów dostępne dla typów konwerterów i rozszerzeń znaczników](../../../docs/framework/xaml-services/service-contexts-available-to-type-converters-and-markup-extensions.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Markup.MarkupExtension>  
 <xref:System.Xaml.XamlObjectWriter>  
 [Rozszerzenia znaczników dla przeglądu XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)  
 [Typy konwerterów dla XAML — omówienie](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md)  
 [Konteksty usług dostępne dla typów konwerterów i rozszerzeń znaczników](../../../docs/framework/xaml-services/service-contexts-available-to-type-converters-and-markup-extensions.md)
