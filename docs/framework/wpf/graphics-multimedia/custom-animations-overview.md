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
ms.openlocfilehash: 20bf15040d22d334800d6a163937c22928499f3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527643"
---
# <a name="custom-animations-overview"></a>Przegląd Niestandardowe animacje
W tym temacie opisano, jak i kiedy rozszerzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji systemu, tworząc niestandardowe klatki kluczowe animacji klas, lub za pomocą wywołania zwrotnego w poszczególnych klatkach pomijają je.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy się zapoznać z różnymi typami animacje, udostępniane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Aby uzyskać więcej informacji, zobacz animacje — Przegląd From/To/By [Przegląd Animacja kluczowych klatek](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)i [animacje ścieżki — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md).  
  
 Ponieważ dziedziczyć klasy animacji <xref:System.Windows.Freezable> klasy, należy zapoznać się z <xref:System.Windows.Freezable> obiektów i jak można dziedziczyć <xref:System.Windows.Freezable>. Aby uzyskać więcej informacji, zobacz [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>Rozszerzanie systemu animacji  
 Istnieje wiele sposobów, aby rozszerzyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemu animacji, w zależności od poziomu wbudowana funkcjonalność, której chcesz użyć.  Istnieją trzy punkty rozszerzalności podstawowej w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji aparatu:  
  
-   Tworzenie obiektu niestandardowego klatek kluczowych przez dziedziczenie z jednego z  *\<typ >* ramki kluczowej klasy takie jak <xref:System.Windows.Media.Animation.DoubleKeyFrame>. Ta metoda wykorzystuje większość wbudowane funkcje programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparatu animacji.  
  
-   Tworzenie klasy animacji przez dziedziczenie z <xref:System.Windows.Media.Animation.AnimationTimeline> lub jednego z  *\<typ >* klasy podstawy animacji.  
  
-   Użyj wywołania zwrotnego w poszczególnych klatkach do wygenerowania animacji na podstawie poszczególnych klatkach. To podejście jest całkowicie pomija Animacja i system chronometrażu.  
  
 W poniższej tabeli opisano niektóre scenariusze rozszerzanie systemu animacji.  
  
|Jeśli chcesz...|Korzystając z tego podejścia|  
|-------------------------|-----------------------|  
|Dostosowywanie interpolacji między wartościami typu, który ma odpowiadające mu  *\<typ >* AnimationUsingKeyFrames|Utwórz niestandardowe klatek kluczowych. Aby uzyskać więcej informacji, zobacz [Utwórz ramkę klucza niestandardowego](#createacustomkeyframe) sekcji.|  
|Dostosowywanie więcej niż tylko interpolacji między wartościami typu, który ma odpowiadające mu  *\<typ >* animacji.|Utwórz klasę animacji niestandardowej, która dziedziczy po elemencie  *\<typ >* klasy podstawy animacji, która odnosi się do typu ma być animowany. Aby uzyskać więcej informacji, zobacz [utworzyć niestandardowe klasy animacji](#createacustomanimationtype) sekcji.|  
|Animowanie typ, który nie ma odpowiedniego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji|Użyj <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> lub utworzyć klasę, która dziedziczy po elemencie <xref:System.Windows.Media.Animation.AnimationTimeline>. Aby uzyskać więcej informacji, zobacz [utworzyć niestandardowe klasy animacji](#createacustomanimationtype) sekcji.|  
|Animowanie wiele obiektów o wartości, które są obliczane w każdej ramki i są oparte na ostatni zestaw interakcje obiektu|Użyj wywołania zwrotnego w poszczególnych klatkach. Aby uzyskać więcej informacji, zobacz [Utwórz wywołanie zwrotne użycia poszczególnych klatkach](#useperframecallback) sekcji.|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>Tworzenie niestandardowych klatek kluczowych  
 Tworzenie klasy niestandardowej klatka kluczowa jest najprostszym sposobem, aby rozszerzyć system animacji. Tej metody należy użyć, gdy użytkownik chce metodę różnych interpolacji animacji kluczowych klatek.  Zgodnie z opisem w [Przegląd Animacja kluczowych klatek](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md), animacji kluczowych klatek używa klatek kluczowych obiektów, aby wygenerować jej wartości danych wyjściowych. Każdy obiekt w ramce klucza wykonuje trzy funkcje:  
  
-   Określa wartość docelowej przy użyciu jego <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> właściwości.  
  
-   Określa czas, w którym ta wartość zostanie osiągnięty przy użyciu jego <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> właściwości.  
  
-   Wartość argumentu wartości poprzedniej ramki kluczy z własnej wartości poprzez implementację metody InterpolateValueCore.  
  
 **Instrukcje dotyczące wdrażania**  
  
 Pochodzi od  *\<typ >* ramki kluczowej klasy abstrakcyjnej i zaimplementować metodę InterpolateValueCore. Metoda InterpolateValueCore zwraca bieżącą wartość klatek kluczowych. Trwa dwa parametry: wartość poprzedniej ramki klucza i wartości postępu z zakresu od 0 do 1. Postęp 0 wskazuje klatek kluczowych właśnie zostało uruchomione, a wartość 1 oznacza, że klatek kluczowych został ukończony i powinna zwrócić wartość określoną przez jego <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> właściwości.  
  
 Ponieważ  *\<typ >* ramki kluczowej klasy dziedziczą <xref:System.Windows.Freezable> klasy, konieczne jest również przesłonięcie <xref:System.Windows.Freezable.CreateInstanceCore%2A> core, aby zwrócić nowe wystąpienie klasy. Jeśli klasa nie używa właściwości zależności do przechowywania swoich danych lub wymaga ona dodatkową inicjację po utworzeniu, może być konieczne zastąpienie dodatkowe metody; zobacz [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) Aby uzyskać więcej informacji.  
  
 Po utworzeniu niestandardowego  *\<typ >* Animacja klatki kluczowej, można jej używać z  *\<typ >* AnimationUsingKeyFrames dla tego typu.  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>Utwórz klasę animacji niestandardowej  
 Tworzenie własnych animacji umożliwia typu większa kontrola nad jak animowane obiektu w. Istnieją dwa sposoby zalecane, aby utworzyć swój własny typ animacji: może pochodzić z <xref:System.Windows.Media.Animation.AnimationTimeline> klasy lub  *\<typ >* klasy podstawy animacji. Wyprowadzanie z  *\<typ >* animacji lub  *\<typ >* AnimationUsingKeyFrames klasy nie jest zalecane.  
  
### <a name="derive-from-typeanimationbase"></a>Pochodzi od \<typ > podstawy animacji  
 Wyprowadzanie z  *\<typ >* klasa podstawy animacji jest najprostszym sposobem utworzenia nowego typu animacji. Korzystając z tego podejścia, gdy chcesz tworzyć nowej animacji dla typu, który już ma odpowiadające mu  *\<typ >* klasy podstawy animacji.  
  
 **Instrukcje dotyczące wdrażania**  
  
 Pochodzi od  *\<typ >* klasy animacji i zaimplementuj metodę GetCurrentValueCore. Metoda GetCurrentValueCore zwraca bieżącą wartość animacji. Zajmuje trzy parametry: sugerowane wartości początkowej, sugerowana wartość końcową, a <xref:System.Windows.Media.Animation.AnimationClock>, którego używasz, aby określić postęp animacji.  
  
 Ponieważ  *\<typ >* podstawy animacji klasy dziedziczą <xref:System.Windows.Freezable> klasy, konieczne jest również przesłonięcie <xref:System.Windows.Freezable.CreateInstanceCore%2A> core, aby zwrócić nowe wystąpienie klasy. Jeśli klasa nie używa właściwości zależności do przechowywania swoich danych lub wymaga ona dodatkową inicjację po utworzeniu, może być konieczne zastąpienie dodatkowe metody; zobacz [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) Aby uzyskać więcej informacji.  
  
 Aby uzyskać więcej informacji, zobacz w dokumentacji metody GetCurrentValueCore  *\<typ >* podstawy animacji klasy dla typu, który ma być animowany. Aby uzyskać przykład, zobacz [przykład animacji niestandardowych](https://go.microsoft.com/fwlink/?LinkID=159981)  
  
 **Alternatywnych metod**  
  
 Jeśli po prostu chcesz zmienić, jak są interpolowane wartości animacji, biorąc pod uwagę elementu pochodnego dla jednego z  *\<typ >* klasy klatki kluczowej. Klatka kluczowa tworzenia mogą być używane z odpowiednich  *\<typ >* AnimationUsingKeyFrames dostarczone przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="derive-from-animationtimeline"></a>Pochodzi od AnimationTimeline  
 Pochodzi od <xref:System.Windows.Media.Animation.AnimationTimeline> klasy, gdy użytkownik chce utworzyć animację dla typu, który nie ma już pasujący obiekt typu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji lub gdy chcesz utworzyć animację, który nie jest silnie typizowane.  
  
 **Instrukcje dotyczące wdrażania**  
  
 Pochodzi od <xref:System.Windows.Media.Animation.AnimationTimeline> klasy i jest przesłonięcie następujących składowych:  
  
-   <xref:System.Windows.Freezable.CreateInstanceCore%2A> — W przypadku nowej klasie konkretnych, konieczne jest przesłonięcie <xref:System.Windows.Freezable.CreateInstanceCore%2A> zwrócić nowe wystąpienie klasy.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> — Przesłonić tę metodę w celu zwracania bieżącej wartości animacji. Zajmuje trzy parametry: wartość domyślną pochodzenia, wartość domyślna docelowego i <xref:System.Windows.Media.Animation.AnimationClock>. Użyj <xref:System.Windows.Media.Animation.AnimationClock> uzyskiwania bieżącego czasu i postęp animacji. Możesz wybrać, czy próba wykorzystania domyślnych wartości początkowe i docelowe.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> — Zastąpić tę właściwość, aby wskazać, czy animacja używa domyślnej wartości docelowej, określone przez <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> metody.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> — Zastąpić tę właściwość, aby wskazać <xref:System.Type> danych wyjściowych tworzy animacji.  
  
 Jeśli klasa nie używa właściwości zależności do przechowywania swoich danych lub wymaga ona dodatkową inicjację po utworzeniu, może być konieczne zastąpienie dodatkowe metody; zobacz [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) Aby uzyskać więcej informacji.  
  
 Zalecane paradygmat (używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji) jest użycie dwóch poziomach dziedziczenia:  
  
1.  Utwórz abstrakcyjną  *\<typ >* klasy podstawy animacji, która pochodzi od klasy <xref:System.Windows.Media.Animation.AnimationTimeline>. Ta klasa powinien przesłonić <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> metody. Należy również wprowadzenie nowej metody abstrakcyjne GetCurrentValueCore i Zastąp <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> tak, aby typy wartość domyślna, pochodzenia i domyślne parametry wartości docelowej jest sprawdzane, a następnie wywołuje GetCurrentValueCore.  
  
2.  Tworzenie innej klasy, która dziedziczy z nowego  *\<typ >* klasy podstawy animacji i zastępuje <xref:System.Windows.Freezable.CreateInstanceCore%2A> metody, metoda GetCurrentValueCore, która zostanie wprowadzona i <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> właściwości.  
  
 **Alternatywnych metod**  
  
 Aby animować typ, który nie ma odpowiedniego animacji od/do/przez ani animacji kluczowych klatek, należy rozważyć użycie <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Ponieważ ze słabą kontrolą typów, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> można animować wartość dowolnego typu. Wadą tego podejścia jest to, że <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> obsługuje tylko interpolacji dyskretnych.  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>Użyj wywołania zwrotnego w poszczególnych klatkach  
 Korzystając z tego podejścia, gdy trzeba całkowicie pominąć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system animacji. Jeden scenariusz, w tym podejściu jest fizyki animacje, gdzie na każdą animację kroku nowym kierunku lub położenie obiektów animowany musi być obliczane ponownie na podstawie ostatni zestaw interakcje obiektu.  
  
 **Instrukcje dotyczące wdrażania**  
  
 W przeciwieństwie do innych podejść opisanych w tym omówieniu używać wywołania zwrotnego w poszczególnych klatkach nie potrzebujesz do tworzenia animacji niestandardowej lub klasa klatek kluczowych.  
  
 Zamiast tego należy zarejestrować dla <xref:System.Windows.Media.CompositionTarget.Rendering> zdarzenia obiektu, który zawiera obiekty mają być animowane. Ta metoda obsługi zdarzeń jest wywoływana raz na klatkę. Każdym razem, gdy program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshals danych utrwalonych renderowania, w drzewie wizualnym w drzewie kompozycji, Twoja metoda programu obsługi zdarzeń jest wywoływana.  
  
 W obsługi zdarzenia wykonują swoje niezależnie od obliczeń niezbędnych animacji efektu i ustaw właściwości obiektów, aby animować z tymi wartościami.  
  
 Uzyskać czasu prezentacji bieżącej ramki <xref:System.EventArgs> skojarzony z tym zdarzeń może być rzutowany jako <xref:System.Windows.Media.RenderingEventArgs>, które zapewniają <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> właściwość, która służy do uzyskania bieżącej ramki przez renderowanie czasu.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.CompositionTarget.Rendering> strony.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [Techniki animacji właściwości — przegląd](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
- [Przegląd obiektów Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [Animacje ścieżki — przegląd](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)
- [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Animacja i system chronometrażu — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)
- [Przykład animacji niestandardowej](https://go.microsoft.com/fwlink/?LinkID=159981)
