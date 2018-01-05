---
title: "Metadane właściwości szablonu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fec11a973572dce9e8d6f77bf65ce31ee77eb41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="framework-property-metadata"></a>Metadane właściwości szablonu
Opcje metadanych właściwości Framework są zgłaszane dla właściwości elementów obiektu uważane za w ramach WPF w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] architektury. Generalnie oznaczenie poziomie struktury WPF pociąga za sobą tej funkcji, takich jak renderowania danych powiązania, a właściwość uściślenia systemu są obsługiwane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prezentacji [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] i plików wykonywalnych. Metadane właściwości Framework otrzymuje tych systemów, aby określić właściwości właściwych dla funkcji właściwości określonego elementu.  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono zrozumieć właściwości zależności z punktu widzenia użytkownika istniejących właściwości zależności na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klas i przeczytanie [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Należy również przeczytanie [metadanych właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Informacje przesyłane przez metadane właściwości Framework  
 Metadane właściwości Framework można podzielić na następujące kategorie:  
  
-   Właściwości układu, które mają wpływ na element raportowania (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>). Te flagi może być ustawiony w metadanych, jeśli właściwość ma wpływ na te aspekty odpowiednich, a także w przypadku implementowania <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody w klasie zachowanie konkretnego sposobu realizacji i informacje do układu System. Zazwyczaj takie implementację czy Sprawdź, czy właściwość invalidations we właściwościach zależności, gdzie zostały żadnej z tych właściwości układu wartości true w metadanych właściwości, a tylko tych invalidations wymagałyby żąda nowy przebieg układu.  
  
-   Raportowanie właściwości układu, które mają wpływ na element nadrzędny elementu (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>). Przykłady, których te flagi są ustawiane domyślnie <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> i <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
-   <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>., Domyślnie właściwości zależności nie dziedziczy wartości. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>Umożliwia również dziedziczenia również przejść do drzewa wizualnego, które są niezbędne dla niektórych scenariuszy składania kontroli.  
  
    > [!NOTE]
    >  Termin "inherits" w kontekście właściwości wartości oznacza, że coś określonych dla właściwości zależności; oznacza to, że elementy podrzędne można dziedziczą wartość właściwości rzeczywistych zależności z elementy nadrzędne z powodu możliwości poziomie struktury WPF [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości systemu. Go nie ma nic robić bezpośrednio z kodu zarządzanego typu i elementów członkowskich dziedziczenie przez typy pochodne. Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
-   Raportowanie właściwości powiązania danych (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Domyślnie właściwości zależności w ramach obsługuje powiązanie danych z zachowaniem powiązania jednokierunkowe. Może wyłączyć powiązania danych, jeśli nie było żadnych scenariusz jakiejkolwiek (ponieważ mają one być elastyczny i rozszerzalny, nie ma wiele przykładów takich właściwości w domyślnym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]). Można ustawić powiązanie dwukierunkowe domyślny dla właściwości, które powiązać razem zachowania formantu między jego fragmentów (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> przykład) lub jeśli Wiązanie dwukierunkowe jest scenariusz typowe i oczekiwany dla użytkowników (<xref:System.Windows.Controls.TextBox.Text%2A> przykład). Zmiana metadane związane z — wiązanie danych wpływa tylko domyślny; na podstawie na powiązanie, że zawsze można zmienić domyślny. Szczegółowe informacje o tryby powiązania i powiązania w ogólności, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Raportowanie, czy właściwości powinny być umieszczanych w dzienniku aplikacji lub usług, które obsługują rejestrowanie (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>). Ogólne elementy rejestrowanie nie jest domyślnie włączona, ale selektywnie jest włączona dla niektórych formantów wejściowych użytkownika. Ta właściwość jest przeznaczona do odczytania przez usługi rejestrowania w tym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacja rejestrowania i jest zwykle ustawiana na formanty użytkownika, takie jak wybory użytkownika w obrębie listy, które powinny być zachowywany po kroki nawigacji. Aby uzyskać informacje o arkuszu, zobacz [omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>Odczytywanie FrameworkPropertyMetadata  
 Wszystkie właściwości linki umieszczono powyżej są określone właściwości który <xref:System.Windows.FrameworkPropertyMetadata> dodaje do swojej klasy podstawowej natychmiastowego <xref:System.Windows.UIPropertyMetadata>. Każdy z tych właściwości będzie `false` domyślnie. Żądanie metadane dla właściwości, na których jest ważna wiedzy o wartości tych właściwości powinien próbować rzutowania metadane zwrócony do <xref:System.Windows.FrameworkPropertyMetadata>, a następnie sprawdź wartości poszczególnych właściwości zgodnie z potrzebami.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Określanie metadanych  
 Podczas tworzenia nowego wystąpienia metadanych do celów stosowania metadanych do nowej rejestracji właściwość zależności jest to możliwe, które klasy metadanych do użycia: base <xref:System.Windows.PropertyMetadata> lub niektóre pochodnej klasy takie jak <xref:System.Windows.FrameworkPropertyMetadata>. Ogólnie rzecz biorąc, należy użyć <xref:System.Windows.FrameworkPropertyMetadata>, zwłaszcza w przypadku, gdy Twoje właściwość ma żadnej interakcji z systemu właściwości i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji, takich jak układ i powiązania danych. Inną opcją w przypadku bardziej zaawansowanych scenariuszy ma dziedziczyć <xref:System.Windows.FrameworkPropertyMetadata> do tworzenia własnych metadanych raportowania klasa o dodatkowe informacje odbywa się w jej elementów członkowskich. Możesz również użyć <xref:System.Windows.PropertyMetadata> lub <xref:System.Windows.UIPropertyMetadata> do komunikowania się stopień obsługę funkcji implementacji.  
  
 Dla właściwości istniejącego (<xref:System.Windows.DependencyProperty.AddOwner%2A> lub <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> wywołać), należy zawsze powinny zastępować z typem metadanych używane przez pierwotnej rejestracji.  
  
 Jeśli tworzysz <xref:System.Windows.FrameworkPropertyMetadata> wystąpienia, istnieją dwa sposoby wypełniania wartościami dla określonych właściwości, które komunikują się właściwości właściwość framework metadane:  
  
1.  Użyj <xref:System.Windows.FrameworkPropertyMetadata> sygnatury konstruktora, który umożliwia `flags` parametru. Ten parametr powinno być wypełnione z wszystkich żądanych połączone wartości <xref:System.Windows.FrameworkPropertyMetadataOptions> wyliczenie flag.  
  
2.  Użyj jednej z bez `flags` parametr, a następnie ustaw każdego raportowania właściwości typu Boolean <xref:System.Windows.FrameworkPropertyMetadata> do `true` dla każdego żądanego charakterystyczny zmiany. Jeśli to zrobisz, musisz ustawić te właściwości przed elementów z tej właściwości zależności są konstruowane; Operatory logiczne są odczytu i zapisu, aby umożliwić to zachowanie unikania `flags` parametru nadal wypełnić metadanych, a metadane muszą stają się skutecznie zamknięte przed użyciem właściwości. W związku z tym próby ustawienia właściwości po zażądaniu jest metadanych jest nieprawidłowa operacja.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Zachowanie metadanych scalania właściwość Framework  
 Aby zastąpić właściwość framework — metadane, właściwości metadanych są scalane lub wymiany.  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>scalania. Po dodaniu nowego <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, wywołanie zwrotne jest przechowywany w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> w zastąpienie wartości <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> jest podwyższany jako odwołanie z najbliższym elemencie nadrzędnym on określony w metadanych.  
  
-   Właściwość rzeczywiste zachowanie systemowe dla <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> to implementacji dla wszystkich właścicieli metadanych w hierarchii są zachowywane i dodawane do tabeli, z kolejność wykonywania przez system właściwości podpisu wywołania zwrotne klasy pochodnej najbardziej głęboko wywołane najpierw. Wywołania zwrotne dziedziczone uruchomić tylko raz, liczy się jako właścicielem klasy, który umieścić je w metadanych.  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A>zostanie zastąpiony. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> w zastąpienie wartości <xref:System.Windows.PropertyMetadata.DefaultValue%2A> pochodzi z najbliższym elemencie nadrzędnym on określony w metadanych.  
  
-   <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>implementacje zostaną zastąpione. Po dodaniu nowego <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, wywołanie zwrotne jest przechowywany w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> w zastąpienie wartości <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> jest podwyższany jako odwołanie z najbliższym elemencie nadrzędnym on określony w metadanych.  
  
-   Zachowanie systemu właściwość jest tylko <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> w bezpośrednim metadanych jest wywoływany. Nie odwołania do innych <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementacji w hierarchii są zachowywane.  
  
-   Flagi z <xref:System.Windows.FrameworkPropertyMetadataOptions> wyliczenia są łączone lub operacji.  Jeśli określisz <xref:System.Windows.FrameworkPropertyMetadataOptions>, oryginalne opcje nie zostaną zastąpione.  Aby zmienić wybrane opcje, należy ustawić odpowiadających im właściwości w <xref:System.Windows.FrameworkPropertyMetadata>. Na przykład jeśli oryginalny <xref:System.Windows.FrameworkPropertyMetadata> obiekt zestawy <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> flagi, to można zmienić, ustawiając <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> do `false`.  
  
 To zachowanie jest implementowany przez <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>i może zostać zastąpiona w klasach pochodnych metadanych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.DependencyProperty.GetMetadata%2A>  
 [Metadane zależności właściwości](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
