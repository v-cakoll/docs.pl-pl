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
ms.openlocfilehash: c5f315992e8ae37bc79602e6986d90e7af591fb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186546"
---
# <a name="custom-animations-overview"></a>Przegląd Niestandardowe animacje
W tym temacie opisano sposób [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i czas rozszerzania systemu animacji przez tworzenie niestandardowych klatek kluczowych, klas animacji lub za pomocą wywołania zwrotnego na klatkę, aby go pominąć.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy zapoznać się z różnymi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]typami animacji dostarczonych przez program . Aby uzyskać więcej informacji, zobacz omówienie animacji od/do/według, [omówienie animacji klatek kluczowych](key-frame-animations-overview.md)i [omówienie animacji ścieżek](path-animations-overview.md).  
  
 Ponieważ klasy animacji <xref:System.Windows.Freezable> dziedziczą z klasy, <xref:System.Windows.Freezable> należy zapoznać <xref:System.Windows.Freezable>się z obiektami i jak dziedziczyć z . Aby uzyskać więcej informacji, zobacz [Omówienie obiektów freezable](../advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>
## <a name="extending-the-animation-system"></a>Rozszerzanie systemu animacji  
 Istnieje wiele sposobów rozszerzenia systemu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji, w zależności od poziomu wbudowanych funkcji, których chcesz użyć.  W silniku animacji znajdują [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] się trzy podstawowe punkty rozszerzalności:  
  
- Utwórz niestandardowy obiekt klatki kluczowej, dziedzicząc z jednej z <xref:System.Windows.Media.Animation.DoubleKeyFrame>klas * \<>* Klatki Kluczowej, takiej jak . Takie podejście wykorzystuje większość wbudowanych funkcji aparatu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji.  
  
- Utwórz własną klasę animacji, dziedzicząc z lub jednej z <xref:System.Windows.Media.Animation.AnimationTimeline> klas * \<Type>* AnimationBase.  
  
- Używanie wywołania zwrotnego na klatkę do generowania animacji dla klatki. Takie podejście całkowicie omija system animacji i chronometrażu.  
  
 W poniższej tabeli opisano niektóre scenariusze rozszerzania systemu animacji.  
  
|Jeśli chcesz...|Użyj tego podejścia|  
|-------------------------|-----------------------|  
|Dostosowywanie interpolacji między wartościami typu, * \< *który ma odpowiedni typ>AnimationUsingKeyFrames|Utwórz niestandardową klatkę kluczową. Aby uzyskać więcej informacji, zobacz [sekcję Tworzenie niestandardowej klatki kluczowej.](#createacustomkeyframe)|  
|Dostosuj więcej niż tylko interpolację między wartościami typu, który ma odpowiedni * \<typ>* animacji.|Utwórz niestandardową klasę animacji, która dziedziczy z * \<klasy Type>* AnimationBase, która odpowiada typowi, który chcesz animować. Aby uzyskać więcej informacji, zobacz [sekcję Tworzenie niestandardowej klasy animacji.](#createacustomanimationtype)|  
|Animowanie typu, który [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie ma odpowiedniej animacji|Użyj <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> lub utwórz klasę, <xref:System.Windows.Media.Animation.AnimationTimeline>która dziedziczy po . Aby uzyskać więcej informacji, zobacz [sekcję Tworzenie niestandardowej klasy animacji.](#createacustomanimationtype)|  
|Animowanie wielu obiektów z wartościami obliczanymi w każdej klatce i opartymi na ostatnim zestawie interakcji z obiektami|Użyj wywołania zwrotnego na klatkę. Aby uzyskać więcej informacji, zobacz [sekcję Tworzenie wywołania zwrotnego na klatkę.](#useperframecallback)|  
  
<a name="createacustomkeyframe"></a>
## <a name="create-a-custom-key-frame"></a>Tworzenie niestandardowej ramki klawiszy  
 Tworzenie niestandardowej klasy klatek kluczowych jest najprostszym sposobem rozszerzenia systemu animacji. Użyj tej metody, jeśli chcesz użyć innej metody interpolacji dla animacji klatki kluczowej.  Zgodnie z opisem w [przeglądzie animacji klatek kluczowych](key-frame-animations-overview.md)animacja klatki kluczowej używa obiektów klatki kluczowej do generowania wartości wyjściowych. Każdy obiekt klatki kluczowej pełni trzy funkcje:  
  
- Określa wartość docelową <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> przy użyciu jego właściwości.  
  
- Określa czas, w którym ta wartość <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> powinna zostać osiągnięta przy użyciu jego właściwości.  
  
- Interpoluje wartość poprzedniej klatki kluczowej a jego własną wartość, implementując metodę InterpolateValueCore.  
  
 **Instrukcje implementacji**  
  
 Wywodź z * \<klasy *abstrakcyjnej Typ>KeyFrame i zaimplementuj metodę InterpolateValueCore. Metoda InterpolateValueCore zwraca bieżącą wartość klatki kluczowej. Wymaga dwóch parametrów: wartość poprzedniej klatki kluczowej i wartość postępu, która waha się od 0 do 1. Postęp 0 wskazuje, że klatka kluczowa właśnie się rozpoczęła, a wartość 1 wskazuje, że klatka <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> kluczowa właśnie została ukończona i powinna zwrócić wartość określoną przez jego właściwość.  
  
 Ponieważ * \<Typ>* Klasy KeyFrame dziedziczą z <xref:System.Windows.Freezable> klasy, należy <xref:System.Windows.Freezable.CreateInstanceCore%2A> również zastąpić core, aby zwrócić nowe wystąpienie klasy. Jeśli klasa nie używa właściwości zależności do przechowywania swoich danych lub wymaga dodatkowego inicjowania po utworzeniu, może być konieczne zastąpienie dodatkowych metod; Zobacz [Freezable Obiektów Omówienie, aby](../advanced/freezable-objects-overview.md) uzyskać więcej informacji.  
  
 Po utworzeniu niestandardowej * \< *animacji>keyframe można jej używać z elementami * \<Type>* AnimationUsingKeyFrames dla tego typu.  
  
<a name="createacustomanimationtype"></a>
## <a name="create-a-custom-animation-class"></a>Tworzenie niestandardowej klasy animacji  
 Tworzenie własnego typu animacji daje większą kontrolę nad tym, jak obiekt w animowany. Istnieją dwa zalecane sposoby tworzenia własnego typu animacji: <xref:System.Windows.Media.Animation.AnimationTimeline> można wyprowadzić z klasy lub * \<Typ>* AnimationBase klasy. Nie zaleca się wyprowadzania z klasy * \<Animacja>* typu lub * \<Typ>. *  
  
### <a name="derive-from-typeanimationbase"></a>Wywodząc się z \<bazy animacji>typu  
 Pochodna klasy * \<Type>* AnimationBase jest najprostszym sposobem utworzenia nowego typu animacji. Użyj tej metody, jeśli chcesz utworzyć nową animację * \< *dla typu, który ma już odpowiednią klasę Type>AnimationBase.  
  
 **Instrukcje implementacji**  
  
 Wynik z * \<klasy Type>* Animation i zaimplementuj metodę GetCurrentValueCore. Metoda GetCurrentValueCore zwraca bieżącą wartość animacji. Potrzeba trzech parametrów: sugerowanej wartości początkowej, sugerowanej <xref:System.Windows.Media.Animation.AnimationClock>wartości zakończenia i , której używasz do określenia postępu animacji.  
  
 Ponieważ * \<Typ>* AnimationBase klasy dziedziczą <xref:System.Windows.Freezable> z klasy, należy <xref:System.Windows.Freezable.CreateInstanceCore%2A> również zastąpić core, aby zwrócić nowe wystąpienie klasy. Jeśli klasa nie używa właściwości zależności do przechowywania swoich danych lub wymaga dodatkowego inicjowania po utworzeniu, może być konieczne zastąpienie dodatkowych metod; Zobacz [Freezable Obiektów Omówienie, aby](../advanced/freezable-objects-overview.md) uzyskać więcej informacji.  
  
 Aby uzyskać więcej informacji, zobacz GetCurrentValueCore dokumentacji metody * \<dla typu>* AnimationBase klasy dla typu, który chcesz animować. Na przykład zobacz [przykład animacji niestandardowej](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)  
  
 **Alternatywne podejścia**  
  
 Jeśli chcesz po prostu zmienić sposób interpolacji wartości animacji, biorąc pod uwagę wynikające z jednej z * \<klasy Type>* KeyFrame. Utworzona klatka kluczowa może być używana z odpowiednim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] * \<typem>* AnimationUsingKeyFrames dostarczonym przez program .  
  
### <a name="derive-from-animationtimeline"></a>Wywodź z animationtimeline  
 Wynik z <xref:System.Windows.Media.Animation.AnimationTimeline> klasy, gdy chcesz utworzyć animację dla typu, który [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie ma jeszcze pasujące animacji lub chcesz utworzyć animację, która nie jest silnie wpisane.  
  
 **Instrukcje implementacji**  
  
 Wyprowadzić <xref:System.Windows.Media.Animation.AnimationTimeline> z klasy i zastąpić następujące elementy członkowskie:  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A>– Jeśli nowa klasa jest konkretne, <xref:System.Windows.Freezable.CreateInstanceCore%2A> należy zastąpić, aby zwrócić nowe wystąpienie klasy.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>– Zastądnąć tę metodę, aby zwrócić bieżącą wartość animacji. Potrzeba trzech parametrów: domyślnej wartości początku układu <xref:System.Windows.Media.Animation.AnimationClock>współrzędnych, domyślnej wartości docelowej i pliku . Użyj, <xref:System.Windows.Media.Animation.AnimationClock> aby uzyskać bieżący czas lub postęp animacji. Można wybrać, czy mają być używane domyślne wartości początkowe i docelowe.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>– Zastądnie tej właściwości, aby wskazać, czy <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> animacja używa domyślnej wartości docelowej określonej przez metodę.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>– Zastądeń tę <xref:System.Type> właściwość, aby wskazać dane wyjściowe, które tworzy animacja.  
  
 Jeśli klasa nie używa właściwości zależności do przechowywania swoich danych lub wymaga dodatkowego inicjowania po utworzeniu, może być konieczne zastąpienie dodatkowych metod; Zobacz [Freezable Obiektów Omówienie, aby](../advanced/freezable-objects-overview.md) uzyskać więcej informacji.  
  
 Zalecany paradygmat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (używany przez animacje) polega na użyciu dwóch poziomów dziedziczenia:  
  
1. Utwórz * \< *abstrakcyjną klasę Type>AnimationBase, <xref:System.Windows.Media.Animation.AnimationTimeline>która wywodzi się z . Ta klasa powinna zastąpić <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> metodę. Należy również wprowadzić nową metodę abstrakcyjną, GetCurrentValueCore <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> i zastąpić tak, aby sprawdzał typy domyślnej wartości początku układu współrzędnych i domyślnych parametrów wartości docelowej, a następnie wywołuje GetCurrentValueCore.  
  
2. Utwórz inną klasę, która * \< *dziedziczy z nowego typu>AnimationBase klasy i zastępuje <xref:System.Windows.Freezable.CreateInstanceCore%2A> metodę, GetCurrentValueCore metody, które zostały wprowadzone i <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> właściwości.  
  
 **Alternatywne podejścia**  
  
 Jeśli chcesz animować typ, który nie ma odpowiadającej animacji Od/Do/Przez lub animacji klatki kluczowej, rozważ użycie programu <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Ponieważ jest słabo wpisany, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> może animować dowolny typ wartości. Wadą tego podejścia jest <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> to, że obsługuje tylko interpolacji dyskretnej.  
  
<a name="useperframecallback"></a>
## <a name="use-per-frame-callback"></a>Używanie wywołania zwrotnego na klatkę  
 Użyj tego podejścia, gdy trzeba [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] całkowicie pominąć system animacji. Jednym ze scenariuszy dla tego podejścia jest animacje fizyki, gdzie na każdym kroku animacji nowy kierunek lub położenie animowanych obiektów musi być ponownie skompensowany na podstawie ostatniego zestawu interakcji z obiektami.  
  
 **Instrukcje implementacji**  
  
 W przeciwieństwie do innych metod opisanych w tym przeglądzie, aby użyć wywołania zwrotnego na klatkę, nie trzeba tworzyć niestandardowej animacji lub klasy klatki kluczowej.  
  
 Zamiast tego można zarejestrować <xref:System.Windows.Media.CompositionTarget.Rendering> zdarzenie obiektu, który zawiera obiekty, które chcesz animować. Ta metoda obsługi zdarzeń zostanie wywołana raz na klatkę. Za każdym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] razem, gdy marshals utrwalone dane renderowania w drzewie wizualnym w poprzek drzewa kompozycji, metoda obsługi zdarzeń jest wywoływana.  
  
 W programie obsługi zdarzeń wykonaj wszelkie obliczenia niezbędne dla efektu animacji i ustaw właściwości obiektów, które chcesz animować z tymi wartościami.  
  
 Aby uzyskać czas prezentacji bieżącej <xref:System.EventArgs> ramki, skojarzone z <xref:System.Windows.Media.RenderingEventArgs>tym zdarzeniem <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> można rzutować jako , które zapewniają właściwość, której można użyć do uzyskania bieżącego czasu renderowania ramki.  
  
 Aby uzyskać więcej <xref:System.Windows.Media.CompositionTarget.Rendering> informacji, zobacz stronę.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [Techniki animacji właściwości — przegląd](property-animation-techniques-overview.md)
- [Przegląd Obiekty Freezable](../advanced/freezable-objects-overview.md)
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Animacje ścieżki — przegląd](path-animations-overview.md)
- [Przegląd Animacja](animation-overview.md)
- [Przegląd Animacja i system chronometrażu](animation-and-timing-system-overview.md)
- [Próbka animacji niestandardowej](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)
