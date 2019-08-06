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
ms.openlocfilehash: d31d970e8e95726aa789f853ac12c4830498a743
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796831"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>Typy konwerterów i rozszerzenia znaczników dla XAML
Konwertery typów i rozszerzenia znaczników to dwie techniki używane przez systemy typu XAML i moduły zapisujące XAML do generowania składników grafu obiektów. Chociaż korzystają one z pewnych cech, konwertery typów i rozszerzenia znaczników są reprezentowane inaczej w strumieniu węzła XAML. W tym zestawie dokumentacji, konwertery typów, rozszerzenia znaczników i podobne konstrukcje są czasami określane jako konwertery wartości.  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>Konwertery wartości  
 W języku XAML konwertery wartości są używane w różnych scenariuszach. Na poniższej liście przedstawiono różne typy konwerterów wartości w języku XAML:  
  
- Konwerter typów  
  
- Rozszerzenie znaczników  
  
- Serializator wartości  
  
- Klasa pokrewna lub pomoc techniczna, która udostępnia logikę składni tekstu XAML  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Konwertery typów  
 W definicji usług .NET Framework XAML typy są klasy, które pochodzą od klasy CLR <xref:System.ComponentModel.TypeConverter> . <xref:System.ComponentModel.TypeConverter>jest klasą, która znajdowała się w Microsoft .NET Framework przed Existing XAML. Pierwotnie miało to na celu obsługę okien właściwości i podobnych metafory edycji tekstowych na podstawie właściwości IDE. Wprowadzenie kodu XAML do .NET Framework używa <xref:System.ComponentModel.TypeConverter> do konwersji składni tekstowej (jak znaleziono w wartości atrybutu lub węzła wartości XAML) do obiektu. <xref:System.ComponentModel.TypeConverter>można go również użyć do serializacji wartości Object na składnię tekstu. <xref:System.ComponentModel.TypeConverter>został również użyty w poprzednich implementacjach języka XAML specyficznych dla platformy w Windows Presentation Foundation (WPF) i Windows Communication Foundation (WCF). Aby uzyskać więcej informacji na <xref:System.ComponentModel.TypeConverter> temat języka XAML, zobacz [Typy konwerterów dla języka XAML — Omówienie](type-converters-for-xaml-overview.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozszerzenia struktury znaczników  
 W implementacji usług XAML .NET Framework rozszerzenia znaczników to klasy, które pochodzą od <xref:System.Windows.Markup.MarkupExtension> klasy. Rozszerzenia znaczników to koncepcja, w tym formularzu pochodzi od języka XAML. Można traktować rozszerzenie znaczników jako takie jak rozszerzalna sekwencja ucieczki, która wywołuje klasę usługi w celu zapewnienia jej logiki. W odniesieniu do znaczników, procesory XAML rozpoznają uniwersalnie rozszerzenie znaczników przez sekwencję tekstu rozpoczynającą się od otwierającego nawiasu klamrowego ({) w ciągu tekstowym.  
  
 Rozszerzenia znaczników różnią się od konwerterów typów. Konwertery typów są zwykle skojarzone z typami lub elementami członkowskimi. Są wywoływane, gdy utworzenie grafu obiektów lub Serializacja napotka składnię tekstu, która jest skojarzona z tymi jednostkami.  
  
 Rozszerzenia znaczników są skojarzone z pojedynczą klasą usługi pomocniczej, ale mogą być stosowane dla dowolnej wartości elementu członkowskiego. (Jednak można zaimplementować rozszerzenie znacznika, aby celowo ograniczyć jego użycie do określonych elementów członkowskich lub typów docelowych przy użyciu kontekstu usługi). Rozszerzenia znaczników mogą przesłaniać skojarzenie konwertera typów. Można też użyć ich do określenia wartości atrybutu dla elementów członkowskich, które w przeciwnym razie nie obsługują składni tekstu.  
  
 Aby uzyskać więcej informacji na temat wzorca implementacji rozszerzenia znaczników dla języka XAML, zobacz [rozszerzenia znaczników dla języka XAML — Omówienie](markup-extensions-for-xaml-overview.md).  
  
> [!NOTE]
>  Typy i są<xref:System.Windows.Markup.ValueSerializer> zarówno w <xref:System.Xaml> przestrzeni nazw, jak i nie w przestrzeni nazw. <xref:System.Windows.Markup> <xref:System.Windows.Markup.MarkupExtension> Nie oznacza to, że te typy są specyficzne dla technologii WPF lub Windows Forms, które w przeciwnym razie wypełniają przestrzenie nazw CLR `Windows`, które zawierają ciąg. <xref:System.Windows.Markup.MarkupExtension>i <xref:System.Windows.Markup.ValueSerializer> znajdują się w zestawie System. XAML i nie mają żadnej konkretnej zależności struktury. Te typy istniały w przestrzeni nazw środowiska CLR dla .NET Framework 3,0 i pozostają w przestrzeni nazw środowiska CLR w .NET Framework 4, aby uniknąć przerywania odwołań w istniejących projektach WPF. Aby uzyskać więcej informacji, zobacz [typy migrowane z WPF do System. XAML](types-migrated-from-wpf-to-system-xaml.md).  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>Serializatory wartości  
 A <xref:System.Windows.Markup.ValueSerializer> to wyspecjalizowany konwerter typów, który jest zoptymalizowany pod kątem konwersji obiektu na ciąg. W przypadku języka XAML nie można `ConvertFrom` zaimplementować metody w ogóle. <xref:System.Windows.Markup.ValueSerializer> Implementacja uzyskuje usługi w sposób, który jest <xref:System.ComponentModel.TypeConverter> jak implementacja. <xref:System.Windows.Markup.ValueSerializer> Metody wirtualne zapewniają parametr wejściowy `context` . Parametr jest typu <xref:System.Windows.Markup.IValueSerializerContext> ,którydziedziczyz<xref:System.IServiceProvider.GetService%2A> interfejsu i ma metodę. <xref:System.IServiceProvider> `context`  
  
 W systemie typu XAML i dla implementacji składnika zapisywania języka XAML, które używają przetwarzania pętli węzłów języka XAML do serializacji, konwerter wartości, który jest skojarzony z typem lub składową, jest <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> raportowany za pomocą własnej właściwości. Znaczenie dla autorów XAML, które wykonują serializacji, jest to <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> , <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> że jeśli i istnieje, konwerter typu powinien być używany dla ścieżki ładowania i dla ścieżki zapisu należy użyć serializatora wartości. Jeśli <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> istnieje, <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> ale `null`jest, konwerter typu jest również używany dla ścieżki zapisu.  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>Inne konwertery wartości  
 Konwerter wartości jest rozszerzalny poza określonymi wzorcami konwertera typów lub rozszerzenia znaczników. Jednak takie dostosowanie wymaga również ponownej definicji systemu typów XAML zgodnie z .NET Framework usług XAML. Istniejący system typów XAML ma reprezentacje i systemy raportowania dla konwerterów typów, rozszerzeń znaczników i serializatorów wartości, ale nie dla niestandardowych formularzy konwersji wartości. Jeśli chcesz utworzyć niestandardowe konwertery wartości, użyj <xref:System.Xaml.Schema.XamlValueConverter%601> typu.  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>Konwertery typów i rozszerzenia znaczników w połączeniu  
 Rozszerzenia znaczników i konwertery typów są używane w różnych sytuacjach języka XAML. Chociaż kontekst jest dostępny dla użycia rozszerzenia znaczników, zachowanie konwersji typu dla właściwości, w których rozszerzenie znacznika zapewnia wartość, zazwyczaj nie jest zaznaczone w implementacjach rozszerzenia znaczników. Innymi słowy, nawet jeśli rozszerzenie znaczników zwraca ciąg tekstowy jako `ProvideValue` dane wyjściowe, zachowanie konwersji typu dla tego ciągu zgodnie z określoną właściwością lub typem wartości właściwości nie jest wywoływane. Ogólnie rzecz biorąc, przeznaczenie rozszerzenia znacznika ma przetwarzać ciąg i zwracać obiekt bez żadnego z nich.  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>Kontekst usługi dla konwertera wartości  
 Podczas implementowania konwertera wartości często potrzebny jest dostęp do kontekstu, w którym jest stosowany konwerter wartości. Ten kontekst jest znany jako kontekst usługi. Kontekst usługi może zawierać informacje, takie jak kontekst aktywnego schematu XAML, dostęp do systemu mapowania typów, który udostępnia kontekst schematu XAML i moduł zapisujący obiektów XAML, i tak dalej. Aby uzyskać więcej informacji na temat kontekstów usługi dostępnych dla konwertera wartości i sposobu uzyskiwania dostępu do usług, które mogą być udostępniane przez kontekst usługi, zobacz [konteksty usługi dostępne dla typów konwerterów i rozszerzeń znaczników](service-contexts-available-to-type-converters-and-markup-extensions.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Rozszerzenia znaczników dla przeglądu XAML](markup-extensions-for-xaml-overview.md)
- [Typy konwerterów dla XAML — omówienie](type-converters-for-xaml-overview.md)
- [Konteksty usług dostępne dla typów konwerterów i rozszerzeń znaczników](service-contexts-available-to-type-converters-and-markup-extensions.md)
