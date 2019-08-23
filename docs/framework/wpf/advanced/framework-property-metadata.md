---
title: Metadane właściwości szablonu
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: c08cf28880d86331e3b561f1749333d401ba903e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964213"
---
# <a name="framework-property-metadata"></a>Metadane właściwości szablonu
Opcje metadanych właściwości platformy są raportowane dla właściwości elementów obiektów uznawanych za na poziomie platformy WPF w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] architekturze. Ogólnie rzecz biorąc, oznaczenie poziomu platformy WPF wymaga, aby funkcje takie jak renderowanie, wiązanie danych i udoskonalenia systemu właściwości były obsługiwane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsy API prezentacji i pliki wykonywalne. Te systemy mogą badać metadane właściwości platformy, aby określić charakterystykę specyficzną dla danej właściwości elementu.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że właściwości zależności są rozpoznawane w perspektywie odbiorcy istniejących [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] właściwości zależności w klasach i odczytywane są [Przegląd właściwości zależności](dependency-properties-overview.md). Należy również mieć odczytywanie [metadanych właściwości zależności](dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Co jest przekazywane przez metadane właściwości struktury  
 Metadane właściwości platformy można podzielić na następujące kategorie:  
  
- Właściwości układu raportowania, które mają wpływ na<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>element <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>( <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>,,). Można ustawić te flagi w metadanych, jeśli właściwość ma wpływ na te aspekty, a także implementować <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody w klasie, aby dostarczyć konkretne zachowanie renderowania i informacje do układu. systemami. Typowo, taka implementacja sprawdzi obecność Unieważnień właściwości we właściwościach zależności, w których każda z tych właściwości układu była prawdziwa w metadanych właściwości, a tylko te unieważnienia spowodują konieczność żądania nowego układu.  
  
- Właściwości układu raportowania, które mają wpływ na element nadrzędny elementu (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>). Niektóre przykłady, w których te flagi są ustawione domyślnie <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> , <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>to i.  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Domyślnie właściwości zależności nie dziedziczą wartości. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>umożliwia ścieżki dziedziczenia również do drzewa wizualnego, co jest niezbędne w przypadku niektórych scenariuszy składania formantów.  
  
    > [!NOTE]
    > Termin "Inherits" w kontekście wartości właściwości to coś specyficznego dla właściwości zależności; oznacza to, że elementy podrzędne mogą dziedziczyć rzeczywistą wartość właściwości zależności od elementów nadrzędnych ze względu na możliwość poziomu platformy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] WPF w systemie właściwości. Nie ma nic do wykonania bezpośrednio z typem kodu zarządzanego i dziedziczeniem składowych przez typy pochodne. Aby uzyskać szczegółowe informacje, zobacz [dziedziczenie wartości właściwości](property-value-inheritance.md).  
  
- Charakterystyki powiązań danych raportowania (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Domyślnie właściwości zależności w ramach powiązania danych obsługiwane przez platformę mają jednokierunkowe zachowanie powiązania. Można wyłączyć powiązanie danych, jeśli nie ma żadnego z nich scenariusza (ponieważ są one przeznaczone do elastyczności i rozszerzalności, nie ma wielu przykładów takich właściwości w domyślnych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsów API). Można ustawić powiązanie tak, aby miało dwukierunkową wartość domyślną dla właściwości, które łączą się ze sobą zachowania kontrolki<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> na jego części składowe (jest to przykład) lub gdzie powiązanie dwukierunkowe jest typowym i oczekiwanym scenariuszem dla użytkowników (<xref:System.Windows.Controls.TextBox.Text%2A> jest to przykład). Zmiana metadanych związanych z powiązaniem danych ma wpływ tylko na wartość domyślną; dla każdego powiązania, które domyślnie można zmienić. Aby uzyskać ogólne informacje na temat trybów powiązań i powiązań, zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md).  
  
- Raportowanie, czy właściwości powinny być zapisane w dzienniku przez aplikacje lub usługi obsługujące dzienniki<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>(). W przypadku elementów ogólnych funkcja rejestrowania nie jest domyślnie włączona, ale jest selektywnie włączona dla określonych kontrolek danych wejściowych użytkownika. Ta właściwość jest przeznaczona do odczytywania przez usługi rejestrowania, w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tym implementacja rejestrowania, i jest zazwyczaj ustawiana w kontrolkach użytkownika, takich jak wybory użytkownika w listach, które powinny być utrwalane w ramach kroków nawigacji. Aby uzyskać informacje na temat dziennika, zobacz [Omówienie nawigacji](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>Odczytywanie FrameworkPropertyMetadata  
 Każda z właściwości podanych powyżej to określone właściwości, które <xref:System.Windows.FrameworkPropertyMetadata> dodaje do bezpośredniej klasy <xref:System.Windows.UIPropertyMetadata>podstawowej. Każda z tych właściwości będzie `false` domyślnie. Żądanie metadanych dla właściwości, gdzie znajomość wartości tych właściwości jest ważne, powinno próbować rzutować zwracanych metadanych na <xref:System.Windows.FrameworkPropertyMetadata>, a następnie sprawdzić wartości poszczególnych właściwości stosownie do potrzeb.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Określanie metadanych  
 Podczas tworzenia nowego wystąpienia metadanych do celów zastosowania metadanych do nowej rejestracji właściwości zależności można wybrać klasę metadanych, która ma być używana: podstawowa <xref:System.Windows.PropertyMetadata> lub pewna klasa pochodna, taka jak. <xref:System.Windows.FrameworkPropertyMetadata> Ogólnie rzecz biorąc, należy użyć <xref:System.Windows.FrameworkPropertyMetadata>, szczególnie jeśli właściwość zawiera interakcję z systemem właściwości i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcjami, takimi jak układ i powiązanie danych. Kolejną opcją dla bardziej złożonych scenariuszy jest <xref:System.Windows.FrameworkPropertyMetadata> utworzenie własnej klasy raportowania metadanych z dodatkowymi informacjami przeprowadzonymi w jego składach. Lub możesz użyć <xref:System.Windows.PropertyMetadata> programu lub <xref:System.Windows.UIPropertyMetadata> , aby komunikować się z zakresem obsługi funkcji implementacji.  
  
 Dla istniejących właściwości (<xref:System.Windows.DependencyProperty.AddOwner%2A> lub <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> wywołaniu) należy zawsze przesłonić typ metadanych używany przez oryginalną rejestrację.  
  
 Jeśli tworzysz <xref:System.Windows.FrameworkPropertyMetadata> wystąpienie, istnieją dwa sposoby wypełniania metadanych wartościami dla konkretnych właściwości, które komunikują się z charakterystyką właściwości Framework:  
  
1. Użyj podpisu `flags` konstruktora, który zezwala na parametr. <xref:System.Windows.FrameworkPropertyMetadata> Ten parametr powinien zawierać wszystkie żądane połączone wartości <xref:System.Windows.FrameworkPropertyMetadataOptions> flag wyliczenia.  
  
2. Użyj jednego z podpisów bez `flags` parametru, a następnie ustaw `true` dla każdej <xref:System.Windows.FrameworkPropertyMetadata> właściwości logicznej raportowania dla każdej wymaganej zmiany cechy. Jeśli to zrobisz, musisz ustawić te właściwości przed utworzeniem jakichkolwiek elementów z tą właściwością zależności; Właściwości logiczne są do odczytu i zapisu, aby można było uniknąć `flags` tego zachowania parametru i nadal wypełniają metadane, ale metadane muszą zostać skutecznie zapieczętowane przed użyciem właściwości. W rezultacie próba ustawienia właściwości po żądaniu metadanych będzie nieprawidłową operacją.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Zachowanie scalania metadanych właściwości platformy  
 Podczas przesłonięcia metadanych właściwości struktury są scalone lub zastępowane różne cechy metadanych.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>jest scalony. Jeśli dodasz nowe <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, to wywołanie zwrotne zostanie zapisane w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> w przesłonięciu, <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> wartość jest podwyższana jako odwołanie z najbliższego elementu nadrzędnego, który określono w metadanych.  
  
- Rzeczywiste zachowanie systemu właściwości dla <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> to, że implementacje dla wszystkich właścicieli metadanych w hierarchii są zachowywane i dodawane do tabeli, z kolejnością wykonywania przez system właściwości, że wywołania zwrotne najbardziej głębokiej klasy pochodnej są wywoływana jako pierwsza. Dziedziczone wywołania zwrotne są uruchamiane tylko raz, licząc jako należące do klasy, która umieszcza je w metadanych.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>jest zastępowany. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> w przesłonięciu, <xref:System.Windows.PropertyMetadata.DefaultValue%2A> wartość pochodzi z najbliższego elementu nadrzędnego, który został określony w metadanych.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>implementacje zostały zastąpione. Jeśli dodasz nowe <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, to wywołanie zwrotne zostanie zapisane w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> w przesłonięciu, <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> wartość jest podwyższana jako odwołanie z najbliższego elementu nadrzędnego, który określono w metadanych.  
  
- Zachowanie systemu właściwości polega na tym, że <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> tylko w metadanych bezpośrednich jest wywoływana. Żadne odwołania do innych <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementacji w hierarchii nie są zachowywane.  
  
- Flagi <xref:System.Windows.FrameworkPropertyMetadataOptions> wyliczenia są łączone jako operacje bitowe OR.  W przypadku określenia <xref:System.Windows.FrameworkPropertyMetadataOptions>opcji oryginalne opcje nie są zastępowane.  Aby zmienić opcję, należy ustawić odpowiadającą jej właściwość <xref:System.Windows.FrameworkPropertyMetadata>. Na przykład jeśli <xref:System.Windows.FrameworkPropertyMetadata> oryginalny obiekt <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> ustawi flagę, można to zmienić, ustawiając wartość <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> na `false`.  
  
 To zachowanie jest implementowane <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>przez program i można je zastąpić w pochodnych klasach metadanych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
