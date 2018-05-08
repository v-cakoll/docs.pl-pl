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
ms.openlocfilehash: 3f212cd89fe9fe1bcf95a374fa0cd92aedadefa9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="custom-animations-overview"></a>Przegląd Niestandardowe animacje
W tym temacie opisano, jak i kiedy rozszerzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemu animacji, tworząc niestandardowe klatek kluczowych animacji klas, lub za pomocą wywołania zwrotnego na ramki do obejścia go.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy się zapoznać z różnymi typami animacje pochodzącymi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Aby uzyskać więcej informacji, zobacz Omówienie animacje From/To/By, [klucza ramki animacji omówienie](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)i [omówienie animacje ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md).  
  
 Ponieważ dziedziczy klasy animacji <xref:System.Windows.Freezable> klasy, należy się zapoznać z <xref:System.Windows.Freezable> obiektów oraz sposób dziedziczyć <xref:System.Windows.Freezable>. Aby uzyskać więcej informacji, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>Rozszerzanie systemu animacji  
 Istnieje wiele sposobów, aby rozszerzyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemu animacji, w zależności od poziomu wbudowanej funkcji, dla którego chcesz użyć.  Istnieją trzy punkty rozszerzalności głównej w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparatu animacji:  
  
-   Tworzenie obiektu niestandardowych klatki przez dziedziczenie z jednego z  *\<typu >* klasy klatki kluczowej, takich jak <xref:System.Windows.Media.Animation.DoubleKeyFrame>. Ta metoda używa większość wbudowanych funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparat animacji.  
  
-   Tworzenie klasy animacji przez dziedziczenie z <xref:System.Windows.Media.Animation.AnimationTimeline> lub jednego z  *\<typu >* klasy podstawy animacji.  
  
-   Umożliwia generowanie animacji na podstawie na ramki na ramki wywołania zwrotnego. Takie podejście całkowicie pomijany animacji i czasu systemu.  
  
 W poniższej tabeli opisano niektóre scenariusze rozszerzanie systemu animacji.  
  
|Jeśli chcesz...|Posłuż się tą metodą|  
|-------------------------|-----------------------|  
|Dostosowywanie interpolacji między wartościami typu, który ma odpowiadające mu  *\<typu >* AnimationUsingKeyFrames|Utwórz ramkę klucza niestandardowego. Aby uzyskać więcej informacji, zobacz [Utwórz ramkę, klucz niestandardowy](#createacustomkeyframe) sekcji.|  
|Dostosowywanie więcej niż tylko interpolacji między wartościami typu, który ma odpowiadające mu  *\<typu >* animacji.|Utwórz klasę animacji niestandardowej, która dziedziczy  *\<typu >* klasę podstawy animacji, która odpowiada typowi mają być animowane. Aby uzyskać więcej informacji, zobacz [utworzyć klasę animacji niestandardowej](#createacustomanimationtype) sekcji.|  
|Animowanie typu, który nie ma odpowiedniego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji|Użyj <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> lub utworzyć klasę, która dziedziczy <xref:System.Windows.Media.Animation.AnimationTimeline>. Aby uzyskać więcej informacji, zobacz [utworzyć klasę animacji niestandardowej](#createacustomanimationtype) sekcji.|  
|Animacja wiele obiektów o wartości, które są obliczane każdy ramki i są oparte na ostatni zestaw obiektów interakcji|Użyj wywołania zwrotnego na ramki. Aby uzyskać więcej informacji, zobacz [utworzyć Użyj wywołania zwrotnego na ramce](#useperframecallback) sekcji.|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>Utwórz ramkę klucza niestandardowego  
 Tworzenie klasy niestandardowej klatki jest najprostszym sposobem, aby rozszerzyć systemu animacji. Tej metody należy użyć, jeśli chcesz metodę interpolacji innej animacji ramki klucza.  Zgodnie z opisem w [klucza ramki animacji omówienie](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md), animacji ramki klucz używa klatki obiektów do generowania wartości jego dane wyjściowe. Każdy obiekt klatki pełni trzy funkcje:  
  
-   Określa wartość docelowych przy użyciu jego <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> właściwości.  
  
-   Określa czas, w którym ta wartość zostanie osiągnięty przy użyciu jego <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> właściwości.  
  
-   Zaimplementowanie metody InterpolateValueCore wartość argumentu wartości poprzedniej ramki klucza z własnej wartości.  
  
 **Instrukcje dotyczące wdrażania**  
  
 Pochodzić od  *\<typu >* klatki kluczowej klasę abstrakcyjną i zaimplementuj metodę InterpolateValueCore. Metoda InterpolateValueCore zwraca bieżącą wartość klucza ramki. Trwa dwa parametry: wartość poprzedniej ramki klucza i wartość postępu zakresu od 0 do 1. Wskazuje postęp 0 klatek kluczowych właśnie zostało uruchomione, a wartość 1 oznacza, że klatek kluczowych został ukończony i powinien zwrócić wartość określoną przez jego <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> właściwości.  
  
 Ponieważ  *\<typu >* klatki kluczowej klasy dziedziczą <xref:System.Windows.Freezable> klasy, należy również zmienić <xref:System.Windows.Freezable.CreateInstanceCore%2A> core, aby zwrócić nowe wystąpienie klasy. Jeśli klasa nie używa właściwości zależności do przechowywania danych lub wymaga dodatkową inicjację po utworzeniu, konieczne może być zastąpienie dodatkowe metody; zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) Aby uzyskać więcej informacji.  
  
 Po utworzeniu niestandardowe  *\<typu >* klatek kluczowych animacji, użytkownik może być używany z  *\<typu >* AnimationUsingKeyFrames dla tego typu.  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>Utwórz klasę animacji niestandardowej  
 Tworzenie własnych animacji umożliwia typu większa kontrola nad jak animowany obiektu w. Istnieją dwa sposoby zalecane, aby utworzyć własny typ animacji: może pochodzić od <xref:System.Windows.Media.Animation.AnimationTimeline> klasy lub  *\<typu >* klasy podstawy animacji. Wyprowadzanie z  *\<typu >* animacji lub  *\<typu >* AnimationUsingKeyFrames klasy nie jest zalecane.  
  
### <a name="derive-from-typeanimationbase"></a>Pochodzić od \<typu > podstawy animacji  
 Wyprowadzanie z  *\<typu >* klasy podstawy animacji jest najprostszym sposobem, aby utworzyć nowy typ animacji. Tej metody należy użyć, gdy chcesz utworzyć nowe animacji dla typu, który ma już odpowiadający  *\<typu >* klasy podstawy animacji.  
  
 **Instrukcje dotyczące wdrażania**  
  
 Pochodzić od  *\<typu >* klasy animacji i zaimplementuj metodę GetCurrentValueCore. Metoda GetCurrentValueCore zwraca wartość bieżącą animacji. Trwa trzy parametry: sugerowane wartości początkowej, sugerowane wartości końcowej i <xref:System.Windows.Media.Animation.AnimationClock>, który służy do określania postęp animacji.  
  
 Ponieważ  *\<typu >* podstawy animacji klasy dziedziczą <xref:System.Windows.Freezable> klasy, należy również zmienić <xref:System.Windows.Freezable.CreateInstanceCore%2A> core, aby zwrócić nowe wystąpienie klasy. Jeśli klasa nie używa właściwości zależności do przechowywania danych lub wymaga dodatkową inicjację po utworzeniu, konieczne może być zastąpienie dodatkowe metody; zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) Aby uzyskać więcej informacji.  
  
 Aby uzyskać więcej informacji, zobacz dokumentację metody GetCurrentValueCore dla  *\<typu >* klasę podstawy animacji dla typu, który ma być animowane. Na przykład zobacz [próbki animacji niestandardowej](http://go.microsoft.com/fwlink/?LinkID=159981)  
  
 **Alternatywnych metod**  
  
 Jeśli po prostu chcesz zmienić sposób interpolowane z wartości animacji, biorąc pod uwagę, wynikające z jednego z  *\<typu >* klatki kluczowej klasy. Klatki tworzenia może być używany z odpowiadającego  *\<typu >* AnimationUsingKeyFrames dostarczonych przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="derive-from-animationtimeline"></a>Pochodzi od klasy AnimationTimeline  
 Pochodzić od <xref:System.Windows.Media.Animation.AnimationTimeline> klasy, jeśli chcesz utworzyć animację dla typu, który nie ma jeszcze odpowiadającego mu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji lub gdy chcesz utworzyć animację, który nie jest silnie typu.  
  
 **Instrukcje dotyczące wdrażania**  
  
 Pochodzić od <xref:System.Windows.Media.Animation.AnimationTimeline> klasy i przesłonięcie następujących elementów:  
  
-   <xref:System.Windows.Freezable.CreateInstanceCore%2A> — W przypadku nowej klasie konkretnych, konieczne jest przesłonięcie <xref:System.Windows.Freezable.CreateInstanceCore%2A> aby zwrócić nowe wystąpienie klasy.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> — Przesłonić tę metodę do zwracania bieżącej wartości animacji. Trwa trzy parametry: wartość pochodzenia domyślną, wartość domyślną docelowego i <xref:System.Windows.Media.Animation.AnimationClock>. Użyj <xref:System.Windows.Media.Animation.AnimationClock> uzyskać bieżącą godzinę lub postępu dla animacji. Można wybrać, czy należy użyć wartości domyślnych źródło i miejsce docelowe.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> — Zastąpić tę właściwość, aby wskazać, czy animacja używa domyślnej wartości docelowej, określone przez <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> metody.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> — Zastąpić tę właściwość, aby wskazać <xref:System.Type> danych wyjściowych tworzy animacji.  
  
 Jeśli klasa nie używa właściwości zależności do przechowywania danych lub wymaga dodatkową inicjację po utworzeniu, konieczne może być zastąpienie dodatkowe metody; zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) Aby uzyskać więcej informacji.  
  
 Zalecane modelu (używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacje) jest użycie dwa poziomy dziedziczenia:  
  
1.  Utwórz abstrakcyjnego  *\<typu >* podstawy animacji klasy, która jest pochodną <xref:System.Windows.Media.Animation.AnimationTimeline>. Ta klasa powinny zastępować <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> metody. Należy również wprowadzić nowej metody abstrakcyjnej GetCurrentValueCore i zastąpić <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> tak, aby sprawdza poprawność typów wartości domyślnej pochodzenia i domyślne parametry wartości docelowej, a następnie wywołuje GetCurrentValueCore.  
  
2.  Utwórz inną klasę, która dziedziczy z nowej  *\<typu >* klasy podstawy animacji i zastępuje <xref:System.Windows.Freezable.CreateInstanceCore%2A> metody, metoda GetCurrentValueCore wprowadzone, i <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> właściwości.  
  
 **Alternatywnych metod**  
  
 Aby animować typu, który nie ma odpowiedniego z lub do/przez animację ani klucz ramki animacji, należy rozważyć użycie <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Ponieważ jest słabo wpisany, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> można animować dowolnego typu wartości. Wadą tego podejścia jest to, że <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> obsługuje tylko interpolacji dyskretnych.  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>Użyj wywołania zwrotnego na ramki  
 Tej metody należy użyć, gdy należy całkowicie pominąć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemu animacji. Jeden scenariusz takie podejście jest animacje fizycznych, gdzie w każdej animacji kroku nowe kierunek lub położenie animowany obiektów musi to być przeliczane na podstawie ostatni zestaw obiektów interakcji.  
  
 **Instrukcje dotyczące wdrażania**  
  
 W odróżnieniu od innych metod opisanych w tym omówieniu Aby użyć wywołania zwrotnego na ramki nie trzeba utworzyć klasę klatek kluczowych animacji niestandardowej lub.  
  
 Zamiast tego należy zarejestrować dla <xref:System.Windows.Media.CompositionTarget.Rendering> zdarzeń obiektu, który zawiera obiekty mają być animowane. Ta metoda obsługi zdarzeń jest wywoływana raz na klatkę. Każdej aktualizacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshals danych utrwalonych renderowania w drzewie wizualnym w drzewie kompozycji sieci metoda obsługi zdarzeń jest wywoływana.  
  
 W program obsługi zdarzeń, wykonaj użytkownika niezależnie od obliczeń niezbędnych dla animacji efektu i ustaw właściwości obiektów mają być animowane z tymi wartościami.  
  
 Można uzyskać czasu prezentacji bieżącej ramki <xref:System.EventArgs> skojarzony z tym zdarzeń mogą być rzutowane jako <xref:System.Windows.Media.RenderingEventArgs>, które zapewniają <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> właściwości, które można użyć w celu uzyskania bieżącej ramki do renderowania czasu.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.CompositionTarget.Rendering> strony.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.IKeyFrame>  
 [Techniki animacji właściwości — przegląd](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animacje ścieżki — przegląd](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animacja i system chronometrażu — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Przykładowe animacji niestandardowej](http://go.microsoft.com/fwlink/?LinkID=159981)
