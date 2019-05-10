---
title: Metadane właściwości szablonu
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: f0385280cf01502a5b2786541c3d959fca24d239
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912460"
---
# <a name="framework-property-metadata"></a>Metadane właściwości szablonu
Opcje metadane właściwości struktury są zgłaszane właściwości elementów obiektu uważane za w ramach WPF poziomie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] architektury. Ogólnie rzecz biorąc oznaczenia poziomie struktury WPF pociąga za sobą tej funkcji, np. renderowania wiązania danych, a właściwość systemu uściślenia są obsługiwane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prezentacji [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] i plików wykonywalnych. Metadane właściwości szablonu zostaje przesłane zapytanie przez te systemy, aby określić właściwości specyficzne dla funkcji właściwości określonego elementu.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że rozumiesz właściwości zależności z punktu widzenia użytkownika istniejących właściwości zależności na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klasy, a po ich przeczytaniu [Przegląd właściwości zależności](dependency-properties-overview.md). Należy również przeczytanie [metadane zależności właściwości](dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Co to jest przekazywane przez metadane właściwości szablonu  
 Metadane właściwości szablonu można podzielić na następujące kategorie:  
  
- Właściwości układu, które wpływają na element raportowania (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>). Możesz ustawić te flagi w metadanych Jeśli właściwość ma wpływ na te aspekty odpowiednie, a także w przypadku wdrażania <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody w klasie zachowanie określonego renderowania i informacji do układu System. Zazwyczaj takie implementację będzie Sprawdź, czy właściwość invalidations w właściwości zależności, gdzie zostały żadnej z tych właściwości układu wartość true w metadanych właściwości modelu, a tylko te invalidations wymagałyby żądanie nowego przekazanie układu.  
  
- Raportowanie właściwości układu, które wpływają na element nadrzędny elementu (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>). Oto kilka przykładów, w którym te flagi są ustawiane domyślnie <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> i <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Domyślnie właściwości zależności nie dziedziczą wartości. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A> Umożliwia ścieżki dziedziczenia także przechodzić do drzewa wizualnego, co jest niezbędne w niektórych scenariuszach składania kontroli.  
  
    > [!NOTE]
    >  Termin "inherits" w kontekście właściwości wartości oznacza, że coś specyficzne dla właściwości zależności; oznacza, że elementy podrzędne mogą dziedziczą zależności rzeczywiste wartości właściwości z elementów nadrzędnych ze względu na możliwość poziomie struktury WPF [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości systemu. Go nie ma nic wspólnego bezpośrednio z kodu zarządzanego typów i elementów członkowskich dziedziczenie przez typy pochodne. Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](property-value-inheritance.md).  
  
- Właściwości powiązania danych raportowania (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Domyślnie właściwości zależności w ramach obsługuje powiązanie danych, z zachowaniem powiązania jednokierunkowe. Powiązanie danych można wyłączyć, gdyby nie scenariusz szkody (ponieważ mają one być elastyczny i rozszerzalny, nie ma wiele przykładów tych właściwości w domyślnym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]). Możesz ustawić powiązanie dwukierunkowe domyślny dla właściwości, które integrowanie kontroli zachowania oraz jego fragmentów (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> znajduje się przykład) lub Jeśli powiązanie dwustronne jest scenariusz typowe i oczekiwany dla użytkowników (<xref:System.Windows.Controls.TextBox.Text%2A> znajduje się przykład). Tylko zmiana metadanych związanych z powiązania danych wpływa na domyślny; na podstawie na powiązanie zawsze można zmienić tej wartości domyślnej. Szczegółowe informacje na temat trybów powiązania i powiązania ogólnie rzecz biorąc, [Data Binding Overview](../data/data-binding-overview.md).  
  
- Raportowanie, czy właściwości powinny być umieszczanych w dzienniku przez aplikacje lub usługi, które obsługują rejestrowanie (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>). Ogólne elementy rejestrowanie nie jest domyślnie włączona, ale selektywnie jest włączony dla niektórych kontrolek wejściowych użytkownika. Ta właściwość jest przeznaczona do przeczytania przez rejestrowanie usługi, w tym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacja rejestrowania i jest zwykle ustawiana tylko dla kontrolek użytkownika, takich jak opcje wybrane przez użytkownika w obrębie listy, które powinny być zachowywany kroki nawigacji. Aby uzyskać informacje o arkuszu, zobacz [Nawigacja — omówienie](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>Odczytywanie FrameworkPropertyMetadata  
 Poszczególne właściwości linki umieszczono powyżej są określone właściwości, <xref:System.Windows.FrameworkPropertyMetadata> dodaje do jej klasy bazowej natychmiastowego <xref:System.Windows.UIPropertyMetadata>. Każdy z tych właściwości będzie `false` domyślnie. Żądanie metadanych dla właściwości, których wartości tych właściwości, wiedząc, jest ważna ma podejmować próbę rzutowania zwróconych metadanych do <xref:System.Windows.FrameworkPropertyMetadata>, a następnie sprawdź wartości w poszczególnych właściwości, zgodnie z potrzebami.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Określanie metadanych  
 Podczas tworzenia nowego wystąpienia metadanych dla celów stosowania metadanych do nową rejestrację właściwości zależności, masz do wyboru, które klasy metadanych do użycia: Podstawa <xref:System.Windows.PropertyMetadata> lub niektóre wywodzącej się klasy takie jak <xref:System.Windows.FrameworkPropertyMetadata>. Ogólnie rzecz biorąc, należy użyć <xref:System.Windows.FrameworkPropertyMetadata>, szczególnie w przypadku, jeśli Twoja własność ma żadnej interakcji z systemu właściwości i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje, takie jak układ i powiązanie danych. Innym rozwiązaniem dla bardziej zaawansowanych scenariuszy jest pochodną <xref:System.Windows.FrameworkPropertyMetadata> można utworzyć własne metadanych raportowania klasy przy użyciu dodatkowych informacji przenoszone w jej członków. Lub możesz użyć <xref:System.Windows.PropertyMetadata> lub <xref:System.Windows.UIPropertyMetadata> do komunikowania się stopień obsługę funkcji implementacji.  
  
 Dla istniejących właściwości (<xref:System.Windows.DependencyProperty.AddOwner%2A> lub <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> wywołania), należy zawsze zastąpić z typem metadanych używane przez pierwotnej rejestracji.  
  
 Jeśli tworzysz <xref:System.Windows.FrameworkPropertyMetadata> wystąpienia, istnieją dwa sposoby wypełniania tych metadanych z wartościami dla określonych właściwości, które przekazują charakterystyki właściwość framework:  
  
1. Użyj <xref:System.Windows.FrameworkPropertyMetadata> sygnatury konstruktora, który umożliwia `flags` parametru. Ten parametr powinny być widoczne wszystkie żądane połączone wartości <xref:System.Windows.FrameworkPropertyMetadataOptions> wyliczenie flag.  
  
2. Użyj jednej z podpisów bez `flags` parametru, a następnie ustaw każdy raportowanie właściwość typu Boolean <xref:System.Windows.FrameworkPropertyMetadata> do `true` dla każdego żądanego cech zmiany. Jeśli to zrobisz, należy ustawić te właściwości przed żadnych elementów z tą właściwością zależności są konstruowane; Operatory logiczne są odczytu i zapisu, aby umożliwić takie zachowanie unikania `flags` parametr nadal wypełnić metadanych, ale metadane musi stać się skutecznie zapieczętowany przed użyciem właściwości. W związku z tym próby ustawienia właściwości po otrzymaniu żądania metadanych będzie nieprawidłowa operacja.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Zachowanie scalania metadane właściwości struktury  
 Podczas zastąpienia metadane właściwości szablonu właściwości metadanych są scalane lub zastąpiony.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> scalone. W przypadku dodania nowego <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, wywołanie zwrotne jest przechowywany w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> w przesłonięciu wartość <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> jest podnoszony jako odwołanie z najbliższym elemencie nadrzędnym, która zostanie określona, w metadanych.  
  
- Zachowanie systemu rzeczywiste właściwości dla <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> to implementacje dla wszystkich właścicieli metadanych w hierarchii są zachowywane i dodawane do tabeli, za pomocą kolejność wykonywania przez system właściwości podpisu wywołania zwrotne najgłębiej pochodnej klasy najpierw wywołane. Odziedziczone wywołania zwrotne są wykonywane tylko raz, liczy się jako własność klasę, która je umieścić w metadanych.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A> zostanie zastąpiona. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> w przesłonięciu wartość <xref:System.Windows.PropertyMetadata.DefaultValue%2A> pochodzi z najbliższym elemencie nadrzędnym, która zostanie określona, w metadanych.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementacje są zastępowane. W przypadku dodania nowego <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, wywołanie zwrotne jest przechowywany w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> w przesłonięciu wartość <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> jest podnoszony jako odwołanie z najbliższym elemencie nadrzędnym, która zostanie określona, w metadanych.  
  
- Zachowanie systemu właściwość jest tylko <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> w bezpośrednim metadanych jest wywołana. Nie odwołania do innych <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementacji w hierarchii są zachowywane.  
  
- Flagi o <xref:System.Windows.FrameworkPropertyMetadataOptions> wyliczenia są łączone bitowe operacji OR.  Jeśli określisz <xref:System.Windows.FrameworkPropertyMetadataOptions>, oryginalnym opcje nie są zastępowane.  Aby zmienić opcję, należy ustawić właściwość odpowiednie na <xref:System.Windows.FrameworkPropertyMetadata>. Na przykład jeśli oryginalny <xref:System.Windows.FrameworkPropertyMetadata> obiektu zestawy <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> flagi, to można zmienić, ustawiając <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> do `false`.  
  
 To zachowanie jest implementowany przez <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>i może zostać zastąpiona w klasach pochodnych metadanych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
