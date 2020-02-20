---
title: Przegląd Niestandardowe animacje
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes [WPF], animation
- key frames [WPF], custom
- custom key frames [WPF]
- animation [WPF], custom classes
- custom animation classes [WPF]
ms.assetid: 9be69d50-3384-4938-886f-08ce00e4a7a6
ms.openlocfilehash: 5a9ca51b87f73a24b90d0bd843ee306f8a1b970a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453094"
---
# <a name="custom-animations-overview"></a>Przegląd Niestandardowe animacje
W tym temacie opisano, jak i kiedy należy rozłożyć system animacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tworząc niestandardowe ramki kluczowe, klasy animacji lub używając wywołania zwrotnego dla ramki, aby je pominąć.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy zapoznać się z różnymi typami animacji udostępnianymi przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Aby uzyskać więcej informacji, zobacz Omówienie animacji "od/do/z [", omówienie animacji klatek kluczowych](key-frame-animations-overview.md)i [Podgląd animacji ścieżki](path-animations-overview.md).  
  
 Ponieważ klasy animacji dziedziczą z klasy <xref:System.Windows.Freezable>, należy znać <xref:System.Windows.Freezable> obiektów i sposób dziedziczenia <xref:System.Windows.Freezable>. Aby uzyskać więcej informacji, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>Rozszerzanie systemu animacji  
 Istnieje kilka sposobów na rozszerzenie systemu animacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], w zależności od poziomu wbudowanych funkcji, których chcesz użyć.  W aparacie animacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] znajdują się trzy podstawowe punkty rozszerzalności:  
  
- Utwórz obiekt niestandardowego ramki klucza przez dziedziczenie z jednego z *\<typu >* klas klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DoubleKeyFrame>. To podejście używa większości wbudowanych funkcji aparatu animacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Utwórz własną klasę animacji, dziedzicząc <xref:System.Windows.Media.Animation.AnimationTimeline> lub jeden z *typów\<>* klas podstawy animacji.  
  
- Użyj wywołania zwrotnego dla ramki, aby generować animacje dla poszczególnych klatek. To podejście całkowicie pomija animację i system chronometrażu.  
  
 W poniższej tabeli opisano niektóre scenariusze rozszerzania systemu animacji.  
  
|Gdy chcesz...|Użyj tego podejścia|  
|-------------------------|-----------------------|  
|Dostosuj interpolację między wartościami typu, które mają odpowiedni *typ\<>* AnimationUsingKeyFrames|Utwórz niestandardową ramkę kluczową. Aby uzyskać więcej informacji, zobacz sekcję [Tworzenie niestandardowej ramki klucza](#createacustomkeyframe) .|  
|Dostosuj więcej niż tylko interpolację między wartościami typu, które mają odpowiedni *typ\<>* animacji.|Utwórz niestandardową klasę animacji, która dziedziczy z *typu\<>* klasy podstawy animacji, która odnosi się do typu, który ma być animowany. Aby uzyskać więcej informacji, zobacz sekcję [Tworzenie niestandardowej klasy animacji](#createacustomanimationtype) .|  
|Animuj typ, który nie ma odpowiedniej animacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]|Użyj <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> lub Utwórz klasę, która dziedziczy z <xref:System.Windows.Media.Animation.AnimationTimeline>. Aby uzyskać więcej informacji, zobacz sekcję [Tworzenie niestandardowej klasy animacji](#createacustomanimationtype) .|  
|Animuj wiele obiektów o wartościach, które są obliczane dla każdej ramki i są oparte na ostatnim zestawie interakcji obiektów|Użyj wywołania zwrotnego dla ramki. Aby uzyskać więcej informacji, zapoznaj się z sekcją [Utwórz użycie wywołania zwrotnego na ramkę](#useperframecallback) .|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>Utwórz niestandardową ramkę kluczową  
 Tworzenie niestandardowej klasy klatek kluczowych jest najprostszym sposobem na rozszerzenie systemu animacji. Użyj tej metody, jeśli chcesz użyć innej metody interpolacji dla animacji klatek kluczowych.  Zgodnie z opisem w temacie [animacje kluczowych klatek](key-frame-animations-overview.md), animacja klatek kluczowych używa obiektów klatek kluczowych do generowania wartości wyjściowych. Każdy obiekt klatek kluczowych wykonuje trzy funkcje:  
  
- Określa wartość docelową przy użyciu jej właściwości <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>.  
  
- Określa godzinę, o której ta wartość powinna zostać osiągnięta przy użyciu właściwości <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>.  
  
- Interpoluje między wartością poprzedniej klatki kluczowej i własną wartością przez implementację metody InterpolateValueCore.  
  
 **Instrukcje implementacji**  
  
 Pochodny od *typu\<>* klasy abstrakcyjnej klatki kluczowej i Implementuj metodę InterpolateValueCore. Metoda InterpolateValueCore zwraca bieżącą wartość ramki klucza. Przyjmuje dwa parametry: wartość poprzedniej klatki kluczowej i wartość postępu, która mieści się w zakresie od 0 do 1. Postęp 0 wskazuje, że klatka kluczowa została właśnie rozpoczęta, a wartość 1 oznacza, że klatka kluczowa została właśnie zakończona i powinna zwracać wartość określoną przez właściwość <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>.  
  
 Ponieważ *\<typ >* klasy klatek kluczowych dziedziczy z klasy <xref:System.Windows.Freezable>, należy również przesłonić <xref:System.Windows.Freezable.CreateInstanceCore%2A> rdzeń, aby zwracało nowe wystąpienie klasy. Jeśli Klasa nie używa właściwości zależności do przechowywania danych lub wymaga dodatkowej inicjalizacji po utworzeniu, może być konieczne przesłonięcie dodatkowych metod; Aby uzyskać więcej informacji, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md) .  
  
 Po utworzeniu niestandardowego *typu\<>* animacji klatek kluczowych można użyć go z *\<Type >* dla tego typu.  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>Utwórz niestandardową klasę animacji  
 Tworzenie własnego typu animacji daje większą kontrolę nad sposobem animowania obiektu. Istnieją dwa zalecane sposoby tworzenia własnego typu animacji: można utworzyć z klasy <xref:System.Windows.Media.Animation.AnimationTimeline> lub *typu\<>* klasie podstawy animacji. Wyprowadzanie z *typu\<>* animacji lub *\<typu >* klasy AnimationUsingKeyFrames nie jest zalecane.  
  
### <a name="derive-from-typeanimationbase"></a>Pochodny od typu \<> Podstawy animacji  
 Wyprowadzanie z *typu\<>* klasy podstawy animacji jest najprostszym sposobem tworzenia nowego typu animacji. Użyj tej metody, jeśli chcesz utworzyć nową animację dla typu, który ma już odpowiedni *typ\<>* klasie podstawy animacji.  
  
 **Instrukcje implementacji**  
  
 Pochodny od *typu\<>* klasie animacji i Implementuj metodę GetCurrentValueCore. Metoda GetCurrentValueCore zwraca bieżącą wartość animacji. Przyjmuje trzy parametry: Sugerowana wartość początkowa, sugerowana wartość końcowa i <xref:System.Windows.Media.Animation.AnimationClock>, których można użyć do określenia postępu animacji.  
  
 Ponieważ *typ\<>* klasy podstawy animacji dziedziczy z klasy <xref:System.Windows.Freezable>, należy również przesłonić rdzeń <xref:System.Windows.Freezable.CreateInstanceCore%2A>, aby zwracał nowe wystąpienie klasy. Jeśli Klasa nie używa właściwości zależności do przechowywania danych lub wymaga dodatkowej inicjalizacji po utworzeniu, może być konieczne przesłonięcie dodatkowych metod; Aby uzyskać więcej informacji, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md) .  
  
 Aby uzyskać więcej informacji, zobacz dokumentację metody GetCurrentValueCore dla *typu\<>* klasy podstawy animacji dla typu, który ma być animowany. Aby zapoznać się z przykładem, zobacz przykład [animacji niestandardowej](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)  
  
 **Alternatywne podejścia**  
  
 Jeśli po prostu chcesz zmienić sposób interpolacji wartości animacji, rozważanie pochodne jednego z *typów\<>* klas klatek kluczowych. Utworzona przez Ciebie klatkę kluczową może być używana z odpowiednim *typem\<>* AnimationUsingKeyFrames udostępnionym przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="derive-from-animationtimeline"></a>Pochodny od AnimationTimeline  
 Pochodzi z klasy <xref:System.Windows.Media.Animation.AnimationTimeline>, gdy chcesz utworzyć animację dla typu, który nie ma jeszcze pasującej animacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lub chcesz utworzyć animację, która nie jest silnie wpisana.  
  
 **Instrukcje implementacji**  
  
 Pochodny od klasy <xref:System.Windows.Media.Animation.AnimationTimeline> i Przesłoń następujące elementy członkowskie:  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A> — Jeśli nowa klasa jest konkretna, należy zastąpić <xref:System.Windows.Freezable.CreateInstanceCore%2A>, aby zwrócić nowe wystąpienie klasy.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> — Przesłoń tę metodę, aby zwrócić bieżącą wartość animacji. Przyjmuje trzy parametry: domyślną wartość pierwotną, domyślną wartość docelową i <xref:System.Windows.Media.Animation.AnimationClock>. Użyj <xref:System.Windows.Media.Animation.AnimationClock>, aby uzyskać bieżącą godzinę lub postęp dla animacji. Można wybrać, czy mają być używane domyślne wartości źródłowe i docelowe.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> — Przesłoń tę właściwość, aby wskazać, czy animacja używa domyślnej wartości docelowej określonej przez metodę <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> — Przesłoń tę właściwość, aby wskazać <xref:System.Type> danych wyjściowych wytwarzanych przez Twoją animację.  
  
 Jeśli Klasa nie używa właściwości zależności do przechowywania danych lub wymaga dodatkowej inicjalizacji po utworzeniu, może być konieczne przesłonięcie dodatkowych metod; Aby uzyskać więcej informacji, zobacz [Omówienie obiektów Freezable](../advanced/freezable-objects-overview.md) .  
  
 Zalecanym modelem (używanym przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacje) jest użycie dwóch poziomów dziedziczenia:  
  
1. Utwórz abstrakcyjny *typ\<>* klasy podstawy animacji, która pochodzi od <xref:System.Windows.Media.Animation.AnimationTimeline>. Ta klasa powinna zastąpić metodę <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>. Należy również wprowadzić nową metodę abstrakcyjną, GetCurrentValueCore i zastąpić <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> tak, aby sprawdzał poprawność typów domyślnej wartości pierwotnej i domyślnych parametrów wartości docelowej, a następnie wywołuje GetCurrentValueCore.  
  
2. Utwórz inną klasę, która dziedziczy z nowego *typu\<>* klasie podstawy animacji i zastępuje metodę <xref:System.Windows.Freezable.CreateInstanceCore%2A>, wprowadzoną przez Ciebie metodę GetCurrentValueCore i Właściwość <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>.  
  
 **Alternatywne podejścia**  
  
 Jeśli chcesz animować typ, który nie jest zgodny z animacją lub animacją klatek kluczowych, rozważ użycie <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Ponieważ jest to słabo wpisane, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> może animować dowolny typ wartości. Wadą tego podejścia jest to, że <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> obsługuje tylko dyskretne interpolacje.  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>Użyj wywołania zwrotnego dla ramki  
 Użyj tej metody, jeśli chcesz całkowicie ominąć system animacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Jednym z scenariuszy tego podejścia są animacje fizyki, w których każdy krok animacji ma nowy kierunek lub położenie animowanych obiektów, które należy ponownie obliczyć na podstawie ostatniego zestawu interakcji z obiektem.  
  
 **Instrukcje implementacji**  
  
 W przeciwieństwie do innych metod opisanych w tym omówieniu, aby użyć wywołania zwrotnego dla ramki, nie trzeba tworzyć niestandardowej animacji ani klasy klatek kluczowych.  
  
 Zamiast tego rejestruje się dla zdarzenia <xref:System.Windows.Media.CompositionTarget.Rendering> obiektu, który zawiera obiekty, które mają być animowane. Ta metoda obsługi zdarzeń jest wywoływana raz na klatkę. Za każdym razem, gdy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] organizowana utrwalone dane renderowania w drzewie wizualnym w drzewie kompozycji, wywoływana jest metoda obsługi zdarzeń.  
  
 W programie obsługi zdarzeń należy wykonać dowolne obliczenia niezbędne dla efektu animacji i ustawić właściwości obiektów, które mają być animowane przy użyciu tych wartości.  
  
 Aby uzyskać czas prezentacji bieżącej ramki, <xref:System.EventArgs> skojarzona z tym zdarzeniem może być rzutowana jako <xref:System.Windows.Media.RenderingEventArgs>, który udostępnia Właściwość <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A>, której można użyć w celu uzyskania czasu renderowania bieżącej ramki.  
  
 Aby uzyskać więcej informacji, zobacz stronę <xref:System.Windows.Media.CompositionTarget.Rendering>.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [Techniki animacji właściwości — przegląd](property-animation-techniques-overview.md)
- [Przegląd obiektów Freezable](../advanced/freezable-objects-overview.md)
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Animacje ścieżki — przegląd](path-animations-overview.md)
- [Animacja — przegląd](animation-overview.md)
- [Animacja i system chronometrażu — przegląd](animation-and-timing-system-overview.md)
- [Przykład animacji niestandardowej](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)
