---
title: Metadane właściwości szablonu
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: 8fb6e1b4cf6aed9454e9e9f1a77277d2f3611ca8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186654"
---
# <a name="framework-property-metadata"></a>Metadane właściwości szablonu
Framework opcje metadanych właściwości są zgłaszane dla właściwości elementów obiektu uważane [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] za na poziomie struktury WPF w architekturze. Ogólnie rzecz biorąc, oznaczenie na poziomie struktury WPF pociąga za sobą, że funkcje, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] takie jak renderowanie, powiązanie danych i udoskonalenia systemu właściwości są obsługiwane przez interfejsy API prezentacji i pliki wykonywalne. Metadane właściwości framework jest wyszukiwany przez te systemy w celu określenia właściwości specyficzne dla funkcji właściwości określonego elementu.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że rozumiesz właściwości zależności z perspektywy konsumenta istniejących właściwości zależności w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klasach i przeczytałeś przegląd właściwości [zależności.](dependency-properties-overview.md) Należy również przeczytać [metadane właściwości zależności](dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>
## <a name="what-is-communicated-by-framework-property-metadata"></a>Co jest przekazywane przez metadane właściwości framework  
 Metadane właściwości framework można podzielić na następujące kategorie:  
  
- Właściwości układu raportowania, które<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>wpływają <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>na element ( , , ). Możesz ustawić te flagi w metadanych, jeśli właściwość wpływa na <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> te odpowiednie aspekty, a także implementujesz metody w klasie, aby dostarczyć określone zachowanie renderowania i informacje do systemu układu. Zazwyczaj taka implementacja będzie sprawdzić unieważnienia właściwości we właściwościach zależności, gdzie dowolne z tych właściwości układu były prawdziwe w metadanych właściwości i tylko te unieważnienia wymagałoby żądania nowego przebiegu układu.  
  
- Właściwości układu raportowania, które wpływają na<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A> <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>element nadrzędny elementu ( , ). Niektóre przykłady, w których te <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>flagi są ustawione domyślnie są i .  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Domyślnie właściwości zależności nie dziedziczą wartości. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>pozwala ścieżki dziedziczenia również podróżować do drzewa wizualnego, co jest niezbędne dla niektórych scenariuszy kompozycji kontroli.  
  
    > [!NOTE]
    > Termin "dziedziczy" w kontekście wartości właściwości oznacza coś specyficznego dla właściwości zależności; oznacza, że elementy podrzędne mogą dziedziczyć wartość właściwości rzeczywistej zależności z elementów nadrzędnych ze względu na możliwości na poziomie struktury WPF systemu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości. Nie ma nic wspólnego bezpośrednio z typu kodu zarządzanego i dziedziczenia elementów członkowskich za pośrednictwem typów pochodnych. Aby uzyskać szczegółowe informacje, zobacz [Dziedziczenie wartości właściwości](property-value-inheritance.md).  
  
- Raportowanie cech<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>wiązania <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>danych ( , ). Domyślnie właściwości zależności w ramach obsługują powiązania danych, z zachowaniem wiązania jednokierunkowego. Możesz wyłączyć powiązanie danych, jeśli nie było żadnego scenariusza dla niego w ogóle (ponieważ są one przeznaczone do elastyczne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i rozszerzalne, nie istnieje wiele przykładów takich właściwości w domyślnych interfejsów API). Można ustawić powiązanie mieć dwukierunkowe domyślne dla właściwości, które łączą ze sobą zachowania<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> formantu między jego części składowych (jest przykładem) lub gdzie dwukierunkowe powiązanie jest typowy i oczekiwany scenariusz dla użytkowników (<xref:System.Windows.Controls.TextBox.Text%2A> jest przykładem). Zmiana metadanych związanych z powiązaniem danych ma wpływ tylko na wartość domyślną; na podstawie wiązania, że domyślne zawsze można zmienić. Aby uzyskać szczegółowe informacje na temat trybów wiązania i powiązania w ogóle, zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).  
  
- Raportowanie, czy właściwości powinny być księgowane przez<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>aplikacje lub usługi obsługujące rejestrowanie ( ). W przypadku elementów ogólnych rejestrowanie nie jest domyślnie włączone, ale jest selektywnie włączone dla niektórych formantów wprowadzania danych użytkownika. Ta właściwość jest przeznaczona do odczytywania przez usługi rejestrowania, w tym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji dziennika i jest zazwyczaj ustawiana na formanty użytkownika, takie jak wybory użytkowników w listach, które powinny być utrwalane w krokach nawigacji. Aby uzyskać informacje o dzienniku, zobacz [Omówienie nawigacji](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>
## <a name="reading-frameworkpropertymetadata"></a>Czytanie FrameworkPropertyMetadata  
 Każda z właściwości połączonych powyżej są specyficzne <xref:System.Windows.FrameworkPropertyMetadata> właściwości, które <xref:System.Windows.UIPropertyMetadata>dodaje do jego natychmiastowej klasy podstawowej . Każda z tych właściwości `false` będzie domyślnie. Żądanie metadanych dla właściwości, gdzie znajomość wartości tych właściwości jest ważne, <xref:System.Windows.FrameworkPropertyMetadata>należy podjąć próbę rzutowania zwróconych metadanych do , a następnie sprawdzić wartości poszczególnych właściwości w razie potrzeby.  
  
<a name="Specifying_Metadata"></a>
## <a name="specifying-metadata"></a>Określanie metadanych  
 Podczas tworzenia nowego wystąpienia metadanych w celu zastosowania metadanych do nowej rejestracji właściwości zależności masz wybór, której <xref:System.Windows.PropertyMetadata> klasy metadanych <xref:System.Windows.FrameworkPropertyMetadata>użyć: klasy podstawowej lub pochodnej, takiej jak . Ogólnie rzecz biorąc <xref:System.Windows.FrameworkPropertyMetadata>należy użyć , szczególnie jeśli właściwość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma żadnej interakcji z systemem właściwości i funkcji, takich jak układ i powiązanie danych. Inną opcją dla bardziej zaawansowanych scenariuszy <xref:System.Windows.FrameworkPropertyMetadata> jest pochodzić z do tworzenia własnych metadanych raportowania klasy z dodatkowych informacji przenoszonych w jego członków. Możesz też <xref:System.Windows.PropertyMetadata> użyć <xref:System.Windows.UIPropertyMetadata> lub przekazać stopień obsługi funkcji implementacji.  
  
 W przypadku istniejących<xref:System.Windows.DependencyProperty.AddOwner%2A> <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> właściwości ( lub wywołania) należy zawsze zastąpić typem metadanych używanym przez oryginalną rejestrację.  
  
 Jeśli tworzysz <xref:System.Windows.FrameworkPropertyMetadata> wystąpienie, istnieją dwa sposoby wypełniania tych metadanych wartościami dla określonych właściwości, które komunikują właściwości właściwości framework:  
  
1. Użyj <xref:System.Windows.FrameworkPropertyMetadata> sygnatury `flags` konstruktora, która umożliwia parametr. Ten parametr powinien być wypełniony wszystkimi <xref:System.Windows.FrameworkPropertyMetadataOptions> żądanymi połączonymi wartościami flag wyliczenia.  
  
2. Użyj jednego z podpisów `flags` bez parametru, a następnie <xref:System.Windows.FrameworkPropertyMetadata> ustaw `true` każdą właściwość logiczną raportowania dla każdej żądanej zmiany charakterystycznej. Jeśli to zrobisz, należy ustawić te właściwości, zanim wszystkie elementy z tej właściwości zależności są konstruowane; Właściwości logiczne są odczytu i zapisu w celu `flags` umożliwienia tego zachowania unikania parametru i nadal wypełnić metadane, ale metadane muszą stać się skutecznie zapieczętowane przed użyciem właściwości. W związku z tym próba skonfigurowania właściwości po zażądaniu metadanych będzie nieprawidłową operacją.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>
## <a name="framework-property-metadata-merge-behavior"></a>Zachowanie scalania metadanych właściwości framework  
 Po zastąpieniu metadanych właściwości framework, różne właściwości metadanych są scalane lub zastępowane.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>zostanie scalona. Jeśli dodasz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>nowy , że wywołanie zwrotne jest przechowywany w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> w zastąpienia, wartość <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> jest promowana jako odwołanie od najbliższego elementa nadrzędnego, który określił go w metadanych.  
  
- Rzeczywiste zachowanie systemu <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> właściwości jest, że implementacje dla wszystkich właścicieli metadanych w hierarchii są zachowywane i dodawane do tabeli, z kolejnością wykonania przez system właściwości jest, że wywołania zwrotne najbardziej głęboko pochodnych klasy są wywoływane jako pierwsze. Dziedziczone wywołania zwrotne są uruchamiane tylko raz, licząc jako należące do klasy, która umieściła je w metadanych.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>zostanie zastąpiony. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> w zastąpienia, wartość pochodzi <xref:System.Windows.PropertyMetadata.DefaultValue%2A> od najbliższego elementa nadrzędnego, który określił go w metadanych.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>implementacje. Jeśli dodasz <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>nowy , że wywołanie zwrotne jest przechowywany w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> w zastąpienia, wartość <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> jest promowana jako odwołanie od najbliższego elementa nadrzędnego, który określił go w metadanych.  
  
- Zachowanie systemu właściwości jest <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> wywoływane tylko w bezpośrednich metadanych. Nie są zachowywane żadne odwołania do innych <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementacji w hierarchii.  
  
- Flagi wyliczenia <xref:System.Windows.FrameworkPropertyMetadataOptions> są łączone jako działanie bitowe OR.  Jeśli określisz <xref:System.Windows.FrameworkPropertyMetadataOptions>, oryginalne opcje nie zostaną zastąpione.  Aby zmienić opcję, ustaw <xref:System.Windows.FrameworkPropertyMetadata>odpowiednią właściwość na . Jeśli na przykład <xref:System.Windows.FrameworkPropertyMetadata> oryginalny obiekt <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> ustawi flagę, <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> można `false`ją zmienić, ustawiając ją na .  
  
 To zachowanie jest <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>implementowane przez programie i może zostać zastąpione przez klasy metadanych pochodnych.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Przegląd Właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
