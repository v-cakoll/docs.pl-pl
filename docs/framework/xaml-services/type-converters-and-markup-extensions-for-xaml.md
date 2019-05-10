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
ms.openlocfilehash: ff820256a27ce455b8eda0c4e7192bc26a3199c3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663226"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>Typy konwerterów i rozszerzenia znaczników dla XAML
Typy konwerterów i rozszerzenia znaczników są dwie techniki, korzystających z systemów typu XAML i moduły zapisujące XAML można wygenerować składniki wykresu obiektu. Mimo że korzystają z niektórych właściwości, typy konwerterów i rozszerzenia znaczników są reprezentowane inaczej w strumień węzłów XAML. W tej dokumentacji zestawu, konwerterów typów, rozszerzenia znaczników i podobne konstrukcje są czasami nazywane zbiorczo konwertery wartości.  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>Konwertery wartości  
 W XAML konwertery wartości są używane dla różnych scenariuszy. Na poniższej liście przedstawiono różne rodzaje konwertery wartości w XAML:  
  
- Konwertera typów  
  
- Rozszerzenie znaczników  
  
- Wartość serializatora  
  
- Pokrewne klasy lub klasy pomocy technicznej, która udostępnia logikę do składni tekstu XAML  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Konwertery typu  
 W definicji usług programu .NET Framework XAML konwerterów typów są klas, które pochodzą ze środowiska CLR <xref:System.ComponentModel.TypeConverter> klasy. <xref:System.ComponentModel.TypeConverter> to klasa, która była w Microsoft .NET Framework, przed wprowadzeniem XAML. Jego oryginalnym celem było do obsługi systemu windows właściwość i podobne oparte na tekście owoce cytrusowe metafory edycji dla [!INCLUDE[TLA2#tla_ide](../../../includes/tla2sharptla-ide-md.md)] właściwości. Wprowadzenie XAML .NET Framework używa <xref:System.ComponentModel.TypeConverter> do konwertowania składni tekstu (tak jak w wartości atrybutu lub węzła wartości XAML) do obiektu. <xref:System.ComponentModel.TypeConverter> Ponadto można serializować wartość obiektu do składni tekstu. <xref:System.ComponentModel.TypeConverter> była już używana w poprzednich implementacjach XAML określonej platformy Windows Presentation Foundation (WPF) i Windows Communication Foundation (WCF). Aby uzyskać więcej informacji na temat <xref:System.ComponentModel.TypeConverter> w XAML, zobacz [typy konwerterów dla XAML — omówienie](type-converters-for-xaml-overview.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Rozszerzenia znaczników  
 W implementacji .NET Framework XAML usługi rozszerzenia znaczników są klas, które wynikają z <xref:System.Windows.Markup.MarkupExtension> klasy. Rozszerzenia znaczników to pojęcie utworzonych w tym formularzu jest w języku XAML. Można traktować jako rozszerzenie znacznika, co nie wygląda sekwencja unikowa rozszerzonego, która wywołuje klasy usługi w celu zapewnienia swojej logiki. Pod względem znaczników procesory XAML rozpoznaje rozszerzenie znaczników powszechnie przez sekwencją tekstu, który zaczyna się od nawiasu otwierającego ({}) w ciągu tekstowym.  
  
 Rozszerzenia znaczników różnią się od konwerterów typów. Konwertery typu są zwykle skojarzone z typów ani elementów członkowskich. Są one wywoływane podczas tworzenia wykresu obiektu lub serializacji napotka składni tekstu, który jest skojarzony z tych jednostek.  
  
 Rozszerzenia znaczników są skojarzone z jednej klasy pomocnicze usługi, ale może być stosowane do dowolnej wartości elementu członkowskiego. (Jednak można zaimplementować celowo ograniczyć jego użycia do niektórych elementów członkowskich i typy docelowej, używając kontekstu usługi rozszerzenia znaczników.) Rozszerzenia znaczników można zastąpić skojarzenie konwertera typu. Także można go użyć do określenia wartości atrybutu dla elementów członkowskich, które w przeciwnym razie będzie nie obsługuje składni tekstu.  
  
 Aby uzyskać więcej informacji o implementacji wzorca rozszerzenia znaczników dla XAML, zobacz [rozszerzenia znaczników dla przeglądu XAML](markup-extensions-for-xaml-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Markup.MarkupExtension> i <xref:System.Windows.Markup.ValueSerializer> typów znajdują się w <xref:System.Windows.Markup> przestrzeni nazw i nie <xref:System.Xaml> przestrzeni nazw. Oznacza to, że te typy są specyficzne dla technologii WPF lub formularzy Windows, które w przeciwnym razie wypełnić przestrzeni nazw CLR, który zawiera ciąg `Windows`. <xref:System.Windows.Markup.MarkupExtension> i <xref:System.Windows.Markup.ValueSerializer> znajdują się w zestawie System.Xaml i mają niezależne określonym środowiskiem. Te typy istniał w przestrzeni nazw CLR [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] i pozostają w przestrzeni nazw CLR w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] pozwala uniknąć przerwy odwołania w istniejących projektach WPF. Aby uzyskać więcej informacji, zobacz [typy migrowane z WPF do System.Xaml](types-migrated-from-wpf-to-system-xaml.md).  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>Wartość serializatorów  
 Element <xref:System.Windows.Markup.ValueSerializer> jest konwertera typów specjalne, które jest zoptymalizowane pod kątem konwersji obiektu na ciąg. A <xref:System.Windows.Markup.ValueSerializer> dla XAML nie może implementować `ConvertFrom` metody w ogóle. A <xref:System.Windows.Markup.ValueSerializer> implementacji uzyskuje usług w sposób przypominający <xref:System.ComponentModel.TypeConverter> implementacji. Metody wirtualne podawanie danych wejściowych `context` parametru. `context` Parametr jest typu <xref:System.Windows.Markup.IValueSerializerContext>, który dziedziczy z <xref:System.IServiceProvider> interfejs i ma <xref:System.IServiceProvider.GetService%2A> metody.  
  
 W systemie typu XAML oraz implementacji modułu zapisującego XAML, które przetwarzanie pętli węzłów XAML na użytek serializacji konwerter wartości, który jest skojarzony z typu lub elementu członkowskiego jest zgłoszone przez własny <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> właściwości. Znaczenie autorom XAML, które wykonują serializacji jest że jeśli <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> i <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> istnieje, konwertera typów powinna być używana dla ścieżki obciążenia i serializator wartość powinna być używana do zapisywania ścieżki. Jeśli <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> istnieje, ale <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> jest `null`, konwertera typów jest również używany do zapisywania ścieżki.  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>Inne konwertery wartości  
 Konwerter wartości jest rozszerzalny poza określonych wzorców konwertera typów lub rozszerzenie znaczników. Jednak to dostosowanie również wymagać ponowna definicja w systemie typu XAML zgodnie z informacjami od usług programu .NET Framework XAML. W istniejącym systemie typu XAML ma reprezentacji i systemy raportowania dla konwerterów typów, rozszerzenia znaczników i serializatorów wartość, ale nie dla niestandardowych formularzy konwersja wartości. Jeśli chcesz utworzyć konwertery wartości niestandardowych, należy użyć <xref:System.Xaml.Schema.XamlValueConverter%601> typu.  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>Typy konwerterów i rozszerzenia znaczników w połączeniu  
 Konwertery rozszerzenia i typu znaczników są używane w różnych sytuacjach w XAML. Mimo że kontekstu jest dostępna do użycia rozszerzenia znaczników, zachowanie konwersji typu właściwości, których rozszerzenie znaczników zawiera wartość jest zazwyczaj nie zostanie zaznaczona w implementacji rozszerzenia znaczników. Innymi słowy nawet jeśli rozszerzenie znaczników zwraca ciąg tekstowy jako jego `ProvideValue` dane wyjściowe, zachowanie konwersji typu dla tego ciągu jako dotyczą określoną właściwość lub typ wartości właściwości nie jest wywoływany. Ogólnie rzecz biorąc celem rozszerzenia znacznika jest przetwarzania ciągu i zwraca obiekt bez żadnych konwertera typów zaangażowanych.  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>Kontekst usługi dla konwertera wartości  
 Podczas implementowania konwerter wartości, często wymagany jest dostęp do kontekstu, w której jest stosowany konwertera wartości. Ten kontekst jest określany jako kontekst usługi. Kontekst usługi może zawierać informacje, takie jak active kontekst schematu XAML, dostęp do system mapowania typu, który kontekst schematu XAML i modułu zapisywania obiektu XAML zapewniają i tak dalej. Aby uzyskać więcej informacji na temat konteksty usług dostępne dla konwertera wartości i sposobu uzyskiwania dostępu do usług, które mogą dostarczać kontekstu usługi zobacz [usługi kontekstów dostępne dla typów konwerterów i rozszerzeń znaczników](service-contexts-available-to-type-converters-and-markup-extensions.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Rozszerzenia znaczników dla przeglądu XAML](markup-extensions-for-xaml-overview.md)
- [Typy konwerterów dla XAML — omówienie](type-converters-for-xaml-overview.md)
- [Konteksty usług dostępne dla typów konwerterów i rozszerzeń znaczników](service-contexts-available-to-type-converters-and-markup-extensions.md)
