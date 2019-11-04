---
title: Metadane właściwości szablonu
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: 3e40dfbcbe88f424337ee5a32fb3e3aaaddd68d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460467"
---
# <a name="framework-property-metadata"></a>Metadane właściwości szablonu
Opcje metadanych właściwości platformy są raportowane dla właściwości elementów obiektów uznawanych za na poziomie platformy WPF w architekturze [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Ogólnie rzecz biorąc, oznaczenie poziomu platformy WPF wymaga, aby funkcje takie jak renderowanie, wiązanie danych i udoskonalenia systemu właściwości były obsługiwane przez interfejsy API prezentacji i pliki wykonywalne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Te systemy mogą badać metadane właściwości platformy, aby określić charakterystykę specyficzną dla danej właściwości elementu.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że rozumiesz właściwości zależności od perspektywy konsumenta istniejących właściwości zależności w klasach [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] i zapoznaj się z [omówieniem właściwości zależności](dependency-properties-overview.md). Należy również mieć odczytywanie [metadanych właściwości zależności](dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Co jest przekazywane przez metadane właściwości struktury  
 Metadane właściwości platformy można podzielić na następujące kategorie:  
  
- Właściwości układu raportowania, które mają wpływ na element (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>). Można ustawić te flagi w metadanych, jeśli właściwość ma wpływ na te aspekty, a także wdrażać <xref:System.Windows.FrameworkElement.MeasureOverride%2A> / <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody w klasie, aby dostarczyć konkretne zachowanie renderowania i informacje do systemu układu. Typowo, taka implementacja sprawdzi obecność Unieważnień właściwości we właściwościach zależności, w których każda z tych właściwości układu była prawdziwa w metadanych właściwości, a tylko te unieważnienia spowodują konieczność żądania nowego układu.  
  
- Właściwości układu raportowania, które mają wpływ na element nadrzędny elementu (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>). Niektóre przykłady, w których te flagi są ustawione domyślnie są <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> i <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>., Domyślnie właściwości zależności nie dziedziczą wartości. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A> pozwala na umieszczenie w drzewie wizualnym ścieżki dziedziczenia, która jest niezbędna w przypadku niektórych scenariuszy składania elementów sterujących.  
  
    > [!NOTE]
    > Termin "Inherits" w kontekście wartości właściwości to coś specyficznego dla właściwości zależności; oznacza to, że elementy podrzędne mogą dziedziczyć rzeczywistą wartość właściwości zależności od elementów nadrzędnych z powodu możliwości poziomu platformy WPF w systemie właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Nie ma nic do wykonania bezpośrednio z typem kodu zarządzanego i dziedziczeniem składowych przez typy pochodne. Aby uzyskać szczegółowe informacje, zobacz [dziedziczenie wartości właściwości](property-value-inheritance.md).  
  
- Charakterystyki powiązań danych raportowania (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Domyślnie właściwości zależności w ramach powiązania danych obsługiwane przez platformę mają jednokierunkowe zachowanie powiązania. Można wyłączyć powiązanie danych, jeśli nie ma żadnego z nich scenariusza (ponieważ są one przeznaczone do elastyczności i rozszerzalności, nie ma wielu przykładów takich właściwości w domyślnych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsów API). Można ustawić powiązanie tak, aby miało dwukierunkową wartość domyślną dla właściwości, które łączą się z zachowaniem kontrolki na jego części składowych (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> jest przykładem) lub Jeśli powiązanie dwukierunkowe jest typowym i oczekiwanym scenariuszem dla użytkowników (<xref:System.Windows.Controls.TextBox.Text%2A> jest przykładem). Zmiana metadanych związanych z powiązaniem danych ma wpływ tylko na wartość domyślną; dla każdego powiązania, które domyślnie można zmienić. Aby uzyskać ogólne informacje na temat trybów powiązań i powiązań, zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).  
  
- Raportowanie, czy właściwości powinny być zapisane w dzienniku przez aplikacje lub usługi obsługujące dzienniki (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>). W przypadku elementów ogólnych funkcja rejestrowania nie jest domyślnie włączona, ale jest selektywnie włączona dla określonych kontrolek danych wejściowych użytkownika. Ta właściwość jest przeznaczona do odczytywania przez usługi rejestrowania, w tym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacja rejestrowania i jest zazwyczaj ustawiana w kontrolkach użytkownika, takich jak wybory użytkowników w listach, które powinny być utrwalane w ramach kroków nawigacji. Aby uzyskać informacje na temat dziennika, zobacz [Omówienie nawigacji](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>Odczytywanie FrameworkPropertyMetadata  
 Każda z właściwości podanych powyżej to określone właściwości, które <xref:System.Windows.FrameworkPropertyMetadata> dodać do swojej bezpośredniej klasy podstawowej <xref:System.Windows.UIPropertyMetadata>. Każda z tych właściwości zostanie domyślnie `false`. Żądanie metadanych dla właściwości, gdzie znajomość wartości tych właściwości jest ważne, powinno próbować rzutować zwrócone metadane na <xref:System.Windows.FrameworkPropertyMetadata>, a następnie sprawdzić wartości poszczególnych właściwości stosownie do potrzeb.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Określanie metadanych  
 Podczas tworzenia nowego wystąpienia metadanych do celów zastosowania metadanych do nowej rejestracji właściwości zależności można wybrać klasę metadanych, która ma być używana: Base <xref:System.Windows.PropertyMetadata> lub niektórych klas pochodnych, takich jak <xref:System.Windows.FrameworkPropertyMetadata>. Ogólnie rzecz biorąc należy używać <xref:System.Windows.FrameworkPropertyMetadata>, szczególnie jeśli właściwość zawiera interakcję z systemem właściwości i funkcjami [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], takimi jak układ i powiązanie danych. Kolejną opcją w przypadku bardziej zaawansowanych scenariuszy <xref:System.Windows.FrameworkPropertyMetadata> jest tworzenie własnych klas raportowania metadanych przy użyciu dodatkowych informacji przeprowadzonych w jego składach. Można też użyć <xref:System.Windows.PropertyMetadata> lub <xref:System.Windows.UIPropertyMetadata> do przekazywania informacji o stopniu obsługi funkcji implementacji.  
  
 W przypadku istniejących właściwości (<xref:System.Windows.DependencyProperty.AddOwner%2A> lub wywołania <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>) należy zawsze przesłonić typ metadanych używany przez oryginalną rejestrację.  
  
 Jeśli tworzysz wystąpienie <xref:System.Windows.FrameworkPropertyMetadata>, istnieją dwa sposoby wypełniania metadanych wartościami dla konkretnych właściwości, które komunikują się z charakterystyką właściwości Framework:  
  
1. Użyj sygnatury konstruktora <xref:System.Windows.FrameworkPropertyMetadata>, która zezwala na parametr `flags`. Ten parametr powinien zawierać wszystkie żądane połączone wartości flag wyliczenia <xref:System.Windows.FrameworkPropertyMetadataOptions>.  
  
2. Użyj jednego z podpisów bez parametru `flags`, a następnie ustaw każdą właściwość Boolean raportowania na <xref:System.Windows.FrameworkPropertyMetadata>, aby `true` dla każdej wymaganej zmiany cechy. Jeśli to zrobisz, musisz ustawić te właściwości przed utworzeniem jakichkolwiek elementów z tą właściwością zależności; Właściwości logiczne są odczytywane w trybie do odczytu i zapisu, aby umożliwić uniknięcie `flags` parametru i nadal wypełnia metadane, ale metadane muszą zostać skutecznie zapieczętowane przed użyciem właściwości. W rezultacie próba ustawienia właściwości po żądaniu metadanych będzie nieprawidłową operacją.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Zachowanie scalania metadanych właściwości platformy  
 Podczas przesłonięcia metadanych właściwości struktury są scalone lub zastępowane różne cechy metadanych.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> został scalony. W przypadku dodania nowego <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>wywołanie zwrotne będzie przechowywane w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> w przesłonięciu, wartość <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> zostanie podwyższona jako odwołanie z najbliższego elementu nadrzędnego, który określono w metadanych.  
  
- Rzeczywiste zachowanie systemu właściwości dla <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> polega na tym, że implementacje dla wszystkich właścicieli metadanych w hierarchii są zachowywane i dodawane do tabeli z kolejnością wykonywania przez system właściwości, że wywołania zwrotne najbardziej głębokiej klasy pochodnej są wywoływane pierwszego. Dziedziczone wywołania zwrotne są uruchamiane tylko raz, licząc jako należące do klasy, która umieszcza je w metadanych.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A> został zastąpiony. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> w przesłonięciu, wartość <xref:System.Windows.PropertyMetadata.DefaultValue%2A> pochodzi z najbliższego elementu nadrzędnego, który został określony w metadanych.  
  
- implementacje <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> są zastępowane. W przypadku dodania nowego <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>wywołanie zwrotne będzie przechowywane w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> w przesłonięciu, wartość <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> zostanie podwyższona jako odwołanie z najbliższego elementu nadrzędnego, który określono w metadanych.  
  
- Zachowanie systemu właściwości polega na tym, że wywoływana jest tylko <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> w ramach natychmiastowych metadanych. Żadne odwołania do innych implementacji <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> w hierarchii nie są zachowywane.  
  
- Flagi wyliczenia <xref:System.Windows.FrameworkPropertyMetadataOptions> są łączone jako operacje bitowe OR.  W przypadku określenia <xref:System.Windows.FrameworkPropertyMetadataOptions>pierwotne opcje nie są zastępowane.  Aby zmienić opcję, ustaw odpowiednią właściwość na <xref:System.Windows.FrameworkPropertyMetadata>. Na przykład jeśli oryginalny obiekt <xref:System.Windows.FrameworkPropertyMetadata> ustawi flagę <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType>, można to zmienić, ustawiając <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> na `false`.  
  
 To zachowanie jest implementowane przez <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>i można je zastąpić w pochodnych klasach metadanych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
