---
title: Przegląd Obiekty Freezable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
ms.openlocfilehash: a1006816168e405d0d79786b8430b802f1ec0928
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615595"
---
# <a name="freezable-objects-overview"></a>Przegląd Obiekty Freezable
W tym temacie opisano, jak skutecznie używać i Utwórz <xref:System.Windows.Freezable> obiektów, które zapewniają funkcje specjalne, które mogą pomóc zwiększyć wydajność aplikacji. Przykładami obiektów freezable pędzle, pióra, przekształcenia, geometrii i animacji.  
  
<a name="whatisafreezable"></a>   
## <a name="what-is-a-freezable"></a>Co to jest Freezable?  
 A <xref:System.Windows.Freezable> to specjalny typ obiektu, który ma dwa stany: odblokowany i zablokowane. Jeśli są, <xref:System.Windows.Freezable> wydaje się zachowują się jak każdego innego obiektu. Jeśli zamrożone, <xref:System.Windows.Freezable> nie może być modyfikowany.  
  
 A <xref:System.Windows.Freezable> zapewnia <xref:System.Windows.Freezable.Changed> zdarzenie, aby powiadomić obserwatorów wszelkie modyfikacje obiektu. Zamrażanie <xref:System.Windows.Freezable> może zwiększyć jej wydajność, ponieważ nie jest już konieczne dokonywania zasobów powiadomień o zmianach. Zamrożone <xref:System.Windows.Freezable> również mogą być współużytkowane przez wątków podczas odblokowanej <xref:System.Windows.Freezable> nie.  
  
 Mimo że <xref:System.Windows.Freezable> klasa ma wiele aplikacji, najbardziej <xref:System.Windows.Freezable> obiekty w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] są powiązane z podsystem grafiki.  
  
 <xref:System.Windows.Freezable> Klas sprawia, że łatwiej używać niektórych obiektów systemowych grafiki i może zwiększyć wydajność aplikacji. Przykłady typów, które dziedziczą z <xref:System.Windows.Freezable> obejmują <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>, i <xref:System.Windows.Media.Geometry> klasy. Ponieważ zawierają one niezarządzane zasoby, system musi monitorować te obiekty do modyfikacji, a następnie zaktualizować ich odpowiednie zasoby niezarządzane, gdy brak zmian do oryginalnego obiektu. Nawet wtedy, gdy rzeczywiście nie zmodyfikować obiektu systemowego grafiki, system nadal poświęcić kilka jej zasobów monitorowania obiektu, w przypadku, gdy została zmieniona.  
  
 Załóżmy na przykład, możesz utworzyć <xref:System.Windows.Media.SolidColorBrush> Pędzel i użyć go do rysowania tła przycisku.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 Po wyrenderowaniu przycisku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podsystem grafiki korzysta z informacji podanych namalować grupy pikseli, aby utworzyć wyglądu przycisku. Mimo że pędzel pełnego koloru jest używany do opisywania, jak przycisk powinien malowane, pełny kolor pędzla faktycznie nie malowania. Szybkie i niskiego poziomu obiektów dla przycisku i Pędzel wygenerowany przez system grafiki i jest tych obiektów, które faktycznie są wyświetlane na ekranie.  
  
 W przypadku modyfikowania pędzel tych obiektów niskiego poziomu musi zostać wygenerowane ponownie. Klasa freezable jest o tym, co umożliwia pędzel jego odpowiednimi obiektami wygenerowane, niskiego poziomu znajdować i aktualizować je, gdy zmienia się. Ta możliwość jest włączona, Pędzel jest określane jako "odblokowanej".  
  
 Freezable <xref:System.Windows.Freezable.Freeze%2A> metoda umożliwia wyłączenie tę możliwość samoaktualizacji. Aby pędzla stają się "zamrożoną" lub niemodyfikowalnych, można użyć tej metody.  
  
> [!NOTE]
>  Nie każdy obiekt Freezable może być zablokowany. Aby uniknąć zgłaszania <xref:System.InvalidOperationException>, sprawdź wartość obiektu Freezable <xref:System.Windows.Freezable.CanFreeze%2A> właściwości w celu określenia, czy może być zablokowany przed podjęciem próby go zablokować.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 W przypadku nie trzeba modyfikować freezable zawiesza się go zapewnia korzyści w wydajności. Jeśli masz zamiar zablokować pędzla, w tym przykładzie systemu grafiki nie jest już należałoby monitorowania zmian. System grafiki można również ustawić inne optymalizacje, ponieważ wie, że pędzel nie ulegnie zmianie.  
  
> [!NOTE]
>  Dla wygody obiektów freezable pozostają odblokowanej, chyba że je jawnie zablokować.  
  
<a name="frozenfreezables"></a>   
## <a name="using-freezables"></a>Przy użyciu obiektów Freezable  
 Za pomocą odblokowanej freezable jest jak przy użyciu innego typu obiektu. W poniższym przykładzie kolor <xref:System.Windows.Media.SolidColorBrush> zostaje zmieniony z żółtym na czerwony, gdy jest używany do rysowania tła przycisku. System grafiki działa w tle automatycznie zmienić przycisk z żółty czerwony przy następnym odświeżeniu ekranu.  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### <a name="freezing-a-freezable"></a>Zamrażanie Freezable  
 Aby <xref:System.Windows.Freezable> wywołania niemodyfikowalnych, jego <xref:System.Windows.Freezable.Freeze%2A> metody. Zablokowanie obiekt, który zawiera obiekty freezable te obiekty są również zablokowane. Na przykład, jeśli zablokowanie <xref:System.Windows.Media.PathGeometry>, dane i segmentów zawiera będzie zbyt zamrożone.  
  
 Freezable **nie** nelze zmrazit w przypadku spełnienia dowolnego z następujących czynności:  
  
-   Ma ona animowane lub powiązania danych właściwości.  
  
-   Zawiera właściwości ustawione przez zasób dynamiczny. (Zobacz [zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) Aby uzyskać więcej informacji o zasobach dynamicznych.)  
  
-   Zawiera on <xref:System.Windows.Freezable> obiekty podrzędne, które nie mogą być zablokowane.  
  
 Jeśli te warunki mają wartość false, a nie zamierzasz zmodyfikować <xref:System.Windows.Freezable>, wówczas powinien zablokowaniu, opisanych wcześniej korzyści wydajności.  
  
 Gdy wywołujesz freezable <xref:System.Windows.Freezable.Freeze%2A> metody, nie może być modyfikowany. Próby zmodyfikowania zamrożonych obiektów powoduje, że <xref:System.InvalidOperationException> zostanie wygenerowany. Poniższy kod zgłasza wyjątek, ponieważ próby zmodyfikowania pędzla, po jest zablokowane.  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 Aby uniknąć zgłaszania tego wyjątku, można użyć <xref:System.Windows.Freezable.IsFrozen%2A> metodę pozwala ustalić czy <xref:System.Windows.Freezable> jest zablokowane.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 W poprzednim przykładzie kodu, można modyfikować kopii zamrożonych obiektów przy użyciu <xref:System.Windows.Freezable.Clone%2A> metody. W następnej sekcji omówiono klonowanie bardziej szczegółowo.  
  
 **Uwaga** ponieważ zamrożone freezable nie można animować, system animacji automatycznie utworzy modyfikowalne klony zamrożone <xref:System.Windows.Freezable> obiekty podczas próby animować je za pomocą <xref:System.Windows.Media.Animation.Storyboard>. Aby wyeliminować wydajności, obciążenie jest spowodowane przez klonowanie, pozostaw obiektu są, jeśli zamierzasz jej animować. Aby uzyskać więcej informacji na temat Animowanie za pomocą scenorysów, zobacz [Przegląd Scenorysy](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
### <a name="freezing-from-markup"></a>Zamrażanie z kodu znaczników  
 Aby zablokować <xref:System.Windows.Freezable> obiekt zadeklarowany w znaczniku, możesz użyć `PresentationOptions:Freeze` atrybutu. W poniższym przykładzie <xref:System.Windows.Media.SolidColorBrush> jest zadeklarowany jako zasobu strony i zablokowane. Ustawianie tła przycisku jest użyty.  
  
 [!code-xaml[FreezableSample#FreezeFromMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 Aby użyć `Freeze` atrybutu, musisz dokonać mapowania na przestrzeń nazw opcje prezentacji: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. `PresentationOptions` to zalecana prefiks dla mapowania tej przestrzeni nazw:  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 Ponieważ nie wszystkie czytelnicy XAML rozpoznaje tego atrybutu, zalecane jest użycie [mc: Ignorable — atrybut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) do oznaczania `Presentation:Freeze` atrybutu jako ignorable:  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 Aby uzyskać więcej informacji, zobacz [mc: Ignorable — atrybut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) strony.  
  
### <a name="unfreezing-a-freezable"></a>"Unfreezing" Freezable  
 Raz zamrożone, <xref:System.Windows.Freezable> nigdy nie mogą zostać zmodyfikowane lub są; jednak można utworzyć klon odblokowanej przy użyciu <xref:System.Windows.Freezable.Clone%2A> lub <xref:System.Windows.Freezable.CloneCurrentValue%2A> metody.  
  
 W poniższym przykładzie ustawiono tło przycisku pędzlem i pędzla ten jest następnie zamrożony. Kopia odblokowanej składa się z pomocą pędzla <xref:System.Windows.Freezable.Clone%2A> metody. Klon jest zmodyfikowany i pozwala zmienić tło przycisku z żółty czerwony.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  Niezależnie od tego, w której możesz użyć metody klonowania, animacji, nigdy nie są kopiowane do nowego <xref:System.Windows.Freezable>.  
  
 <xref:System.Windows.Freezable.Clone%2A> i <xref:System.Windows.Freezable.CloneCurrentValue%2A> metody uzyskanie kopii głębokiego freezable. Jeśli freezable zawiera inne mrożone obiekty freezable, są również sklonować i wprowadzone można modyfikować. Na przykład, jeśli zamrożone klonowania <xref:System.Windows.Media.PathGeometry> charakteryzowanych można modyfikować, dane i zawiera segmentów są również kopiowane i wprowadzone można modyfikować.  
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a>Tworzenie klasy Freezable  
 Klasa, która pochodzi od klasy <xref:System.Windows.Freezable> uzyskuje się następujące funkcje.  
  
-   Stany specjalne: tylko do odczytu (zamrożona) i stanie zapisywalnym.  
  
-   Bezpieczeństwo wątków: zamrożone <xref:System.Windows.Freezable> udostępniona w wielu wątkach.  
  
-   Szczegółowe powiadomienia o zmianie: w odróżnieniu od innych <xref:System.Windows.DependencyObject>s, obiekty Freezable zapewniają powiadomienia o zmianie po zmianie wartości właściwości podrzędnych.  
  
-   Klonowanie proste: Freezable klasy zaimplementował już kilka metod, które tworzą klony głębokiego.  
  
 A <xref:System.Windows.Freezable> jest typem <xref:System.Windows.DependencyObject>i w związku z tym korzysta z systemu właściwości zależności. Właściwości klasy nie muszą być właściwościami zależności, ale przy użyciu właściwości zależności zmniejsza ilość kodu, który trzeba napisać, ponieważ <xref:System.Windows.Freezable> klasy został zaprojektowany przy użyciu właściwości zależności na uwadze. Aby uzyskać więcej informacji na temat systemu właściwość zależności zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 Każdy <xref:System.Windows.Freezable> zastąpić podklasy <xref:System.Windows.Freezable.CreateInstanceCore%2A> metody. Jeśli klasa używa właściwości zależności dla wszystkich swoich danych, jesteś gotowy.  
  
 Jeśli klasa zawiera elementy członkowskie danych właściwości bez zależności, należy również zastąpić następujące metody:  
  
-   <xref:System.Windows.Freezable.CloneCore%2A>  
  
-   <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
-   <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 Należy również zgodna z poniższymi regułami do uzyskiwania dostępu i zapisywanie do elementów członkowskich danych, które nie są właściwości zależności:  
  
-   Na początku dowolnego [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] , odczytuje elementy członkowskie danych właściwości bez zależności, wywołaj <xref:System.Windows.Freezable.ReadPreamble%2A> metody.  
  
-   Na początku dowolnego interfejsu API, który zapisuje elementy członkowskie danych właściwości bez zależności, należy wywołać <xref:System.Windows.Freezable.WritePreamble%2A> metody. (Gdy została wywołana <xref:System.Windows.Freezable.WritePreamble%2A> w [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], nie potrzebujesz do wywoływania dodatkowych <xref:System.Windows.Freezable.ReadPreamble%2A> Jeśli przeczytaj również elementy członkowskie danych właściwości innych zależności.)  
  
-   Wywołaj <xref:System.Windows.Freezable.WritePostscript%2A> metoda przed wyjściem metody modyfikujące właściwość zależności innych składowych danych.  
  
 Jeśli klasa zawiera składowe danych inną niż właściwość zależności, które są <xref:System.Windows.DependencyObject> obiektów, musisz również wywołać <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> metody po każdej zmianie na ich wartości, nawet wtedy, gdy element członkowski jest ustawienie na `null`.  
  
> [!NOTE]
>  Bardzo ważne, Rozpocznij każdy <xref:System.Windows.Freezable> zastąpić wywołaniem implementację podstawową metody.  
  
 Na przykład niestandardowy <xref:System.Windows.Freezable> klasy, zobacz [przykład animacji niestandardowej](https://go.microsoft.com/fwlink/?LinkID=159981).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Freezable>  
 [Przykład animacji niestandardowej](https://go.microsoft.com/fwlink/?LinkID=159981)  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
