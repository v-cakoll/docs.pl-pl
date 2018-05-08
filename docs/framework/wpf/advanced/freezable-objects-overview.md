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
ms.openlocfilehash: d3b9f6f7af22b2a846f4ee34e8d4d00bb032fd69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="freezable-objects-overview"></a>Przegląd Obiekty Freezable
W tym temacie opisano, jak skutecznie używać i utworzyć <xref:System.Windows.Freezable> obiektów, które dostarczają specjalnych funkcji, które może zwiększyć wydajność aplikacji. Przykładami obiektu freezable obiektów pędzle, pióra przekształcenia, mają geometrię i animacji.  
  
<a name="whatisafreezable"></a>   
## <a name="what-is-a-freezable"></a>Co to jest obiektu Freezable?  
 A <xref:System.Windows.Freezable> to specjalny typ obiektu, który ma dwa stany: odblokowana i jest zablokowana. Gdy odblokowany, <xref:System.Windows.Freezable> wydaje się zachowują się podobnie jak każdy inny obiekt. Jeśli zablokowany, <xref:System.Windows.Freezable> nie może być modyfikowany.  
  
 A <xref:System.Windows.Freezable> zapewnia <xref:System.Windows.Freezable.Changed> zdarzenie, aby powiadomić obserwatorów wszelkie modyfikacje obiektu. Zamrażanie <xref:System.Windows.Freezable> może zwiększyć jej wydajność, ponieważ nie jest już konieczne wydatkami zasobów powiadomień o zmianach. Zablokowane <xref:System.Windows.Freezable> również może być współużytkowana przez wątki, podczas odblokowanej <xref:System.Windows.Freezable> nie.  
  
 Mimo że <xref:System.Windows.Freezable> klasa ma wiele aplikacji najbardziej <xref:System.Windows.Freezable> obiekty w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] są związane z podsystem grafiki.  
  
 <xref:System.Windows.Freezable> Klasy, ułatwia działanie do używania określonych obiektów systemowych grafiki i może zwiększyć wydajność aplikacji. Przykłady typów dziedziczących po <xref:System.Windows.Freezable> obejmują <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>, i <xref:System.Windows.Media.Geometry> klasy. Ponieważ zawierają one niezarządzane zasoby, system musi monitorować tych obiektów w celu zmiany, a następnie zaktualizuj ich odpowiednich zasobów niezarządzanych, po zmianie do oryginalnego obiektu. Nawet jeśli nie faktycznie zmodyfikować obiektu systemowego grafiki, system musi nadal spędzają na niektórych zasobów monitorowania obiektu, w przypadku, gdy zostanie zmieniony.  
  
 Załóżmy na przykład, możesz utworzyć <xref:System.Windows.Media.SolidColorBrush> pędzla i używać go do rysowania tła przycisku.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 Podczas renderowania przycisku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podsystem grafiki używa informacji dostępnych do malowania grupy pikseli, aby utworzyć wygląd przycisku. Mimo że pędzla pełnego koloru jest używany do opisywania, jak przycisk powinien zostać narysowany, pędzla pełnego koloru faktycznie nie rysowania. Obiekty szybkie i niskiego poziomu dla przycisku i pędzla wygenerowany przez system grafiki i jest te obiekty widoczne na ekranie.  
  
 Gdyby zmodyfikować pędzla tych obiektów niskiego poziomu musi być ponownie wygenerowany. Klasa obiektu freezable jest, co umożliwia Pędzel można znaleźć jego odpowiednimi obiektami generowany, niskiego poziomu, a ich aktualizacji, gdy zmieni się. Ta możliwość jest włączona, pędzla jest określane jako "odblokowanej."  
  
 Obiektu freezable na <xref:System.Windows.Freezable.Freeze%2A> metoda pozwala wyłączyć tę możliwość samoaktualizacji. Ta metoda umożliwia także pędzla stają się "zablokowane" lub unmodifiable.  
  
> [!NOTE]
>  Nie każdy obiekt obiektu Freezable może być zablokowana. Aby uniknąć generowania <xref:System.InvalidOperationException>, sprawdź wartość obiektu Freezable obiektu <xref:System.Windows.Freezable.CanFreeze%2A> właściwości w celu określenia, czy może być zablokowany przed próbą jej zablokować.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 W przypadku nie trzeba już modyfikować obiektu freezable, zamrażanie go zapewnia zwiększenia wydajności. Jeśli masz zamiar zablokować pędzla w tym przykładzie, system grafiki już musi monitorować jej zmiany. System grafiki można również ustawić inne optymalizacje, ponieważ że pędzel nie zmieni się.  
  
> [!NOTE]
>  Dla wygody obiektu freezable obiekty pozostają odblokowanej, chyba że ich jawnie zablokować.  
  
<a name="frozenfreezables"></a>   
## <a name="using-freezables"></a>Za pomocą obiektów Freezable  
 Przy użyciu odblokowanej obiektu freezable przypomina innego typu obiektu. W poniższym przykładzie kolor <xref:System.Windows.Media.SolidColorBrush> zostaje zmieniony z żółtym czerwony, gdy jest używany do rysowania tła przycisku. System grafiki działa w tle automatycznie zmienić przycisk z żółtym czerwony po następnym odświeżeniu ekranu.  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### <a name="freezing-a-freezable"></a>Zamrażanie obiektu Freezable  
 Aby <xref:System.Windows.Freezable> wywołania unmodifiable, jego <xref:System.Windows.Freezable.Freeze%2A> metody. Po zablokowaniu obiekt zawierający obiekty obiektu freezable te obiekty są również zablokowane. Na przykład, jeśli zablokowanie <xref:System.Windows.Media.PathGeometry>, rysunki i segmentów zawiera może zostać zamrożony zbyt.  
  
 Obiekt Freezable **nie** zablokowane, jeśli spełnione są następujące:  
  
-   Ma on animowany lub właściwości powiązany z danymi.  
  
-   Ma on właściwości ustawione przez zasób dynamicznych. (Zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) Aby uzyskać więcej informacji o zasobach dynamicznych.)  
  
-   Zawiera on <xref:System.Windows.Freezable> obiekty podrzędne, które nie może być zablokowany.  
  
 Jeśli te warunki są false, a nie zamierzasz zmodyfikować <xref:System.Windows.Freezable>, następnie zablokowaniu powinien opisanych wcześniej korzyści wydajności.  
  
 Po wywołaniu obiektu freezable na <xref:System.Windows.Freezable.Freeze%2A> metody, nie może być modyfikowany. Próba zmodyfikowania zablokowane obiekt przyczyny <xref:System.InvalidOperationException> zostanie wygenerowany. Poniższy kod zgłasza wyjątek, ponieważ będziemy próbuje zmodyfikować pędzla po jest została zablokowana.  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 Aby uniknąć generowania tego wyjątku, można użyć <xref:System.Windows.Freezable.IsFrozen%2A> metodę, aby określić, czy <xref:System.Windows.Freezable> jest zablokowana.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 W poprzednim przykładzie kodu, można modyfikować kopii obiektu zablokowane przy użyciu <xref:System.Windows.Freezable.Clone%2A> metody. W następnej sekcji omówiono w klonowania bardziej szczegółowo.  
  
 **Uwaga** ponieważ zablokowane obiektu freezable nie można animować, system animacji automatycznie utworzy można modyfikować klonów zablokowane <xref:System.Windows.Freezable> obiekty podczas próby animować je za pomocą <xref:System.Windows.Media.Animation.Storyboard>. Aby wyeliminować obciążenie spowodowane przez klonowanie wydajność, pozostaw odblokowany, jeśli zamierzasz animować go obiektu. Aby uzyskać więcej informacji na temat animacji z scenorys, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
### <a name="freezing-from-markup"></a>Zamrażanie z znaczników  
 Aby zablokować <xref:System.Windows.Freezable> obiektu zadeklarowany w znaczniku, możesz użyć `PresentationOptions:Freeze` atrybutu. W poniższym przykładzie <xref:System.Windows.Media.SolidColorBrush> jest zadeklarowany jako zasobu strony i zablokowane. Następnie służy do ustawiania tło przycisku.  
  
 [!code-xaml[FreezableSample#FreezeFromMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 Aby użyć `Freeze` atrybutu, musisz zamapować do przestrzeni nazw opcje prezentacji: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. `PresentationOptions` jest zalecana prefiks dla mapowania tej przestrzeni nazw:  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 Ponieważ nie wszystkie czytników XAML rozpoznaje tego atrybutu, zaleca się używanie [mc: atrybut Ignorable](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) do oznaczania `Presentation:Freeze` atrybutu jako ignorowalna:  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 Aby uzyskać więcej informacji, zobacz [mc: atrybut Ignorable](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) strony.  
  
### <a name="unfreezing-a-freezable"></a>"Unfreezing" obiektu Freezable  
 Zablokowane na raz, <xref:System.Windows.Freezable> nigdy nie może być zmodyfikowany lub odblokowana; można jednak utworzyć klonu odblokowanej przy użyciu <xref:System.Windows.Freezable.Clone%2A> lub <xref:System.Windows.Freezable.CloneCurrentValue%2A> metody.  
  
 W poniższym przykładzie tło przycisku jest ustawiony za pomocą pędzla i że pędzla jest następnie zablokowana. Odblokowanej kopiowania składa się z pomocą pędzla <xref:System.Windows.Freezable.Clone%2A> metody. Klon jest zmodyfikowany, a następnie używać do zmieniania tło przycisku z żółtym na czerwony.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  Niezależnie od klonowania wybranej metody, animacje nigdy nie są kopiowane do nowego <xref:System.Windows.Freezable>.  
  
 <xref:System.Windows.Freezable.Clone%2A> i <xref:System.Windows.Freezable.CloneCurrentValue%2A> metody uzyskanie bezpośrednich kopii obiektu freezable. Jeśli obiektu freezable zawierają inne obiekty obiektu freezable zablokowane, są one również sklonować i wprowadzone można modyfikować. Na przykład, jeśli Sklonowanie zablokowane <xref:System.Windows.Media.PathGeometry> aby umożliwić można modyfikować, rysunki i segmentów zawiera są również kopiowane i wprowadzone można modyfikować.  
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a>Tworzenie obiektu Freezable klasy  
 Klasa, która pochodzi z <xref:System.Windows.Freezable> uzyska następujące funkcje.  
  
-   Stany specjalne: tylko do odczytu (zablokowany) i stanie zapisywalnym.  
  
-   Bezpieczeństwo wątków: zablokowane <xref:System.Windows.Freezable> może być współużytkowana przez wątki.  
  
-   Szczegółowe powiadomienia o zmianie: w odróżnieniu od innych <xref:System.Windows.DependencyObject>s, obiekty obiektu Freezable dostarczają powiadomienia o zmianie po zmianie wartości właściwości podrzędnych.  
  
-   Klonowanie łatwe: klasa obiektu Freezable został już zaimplementowany kilka metod, które wywołują klony głębokie.  
  
 A <xref:System.Windows.Freezable> jest typem <xref:System.Windows.DependencyObject>i w związku z tym korzysta z systemu właściwości zależności. Właściwości nie muszą być właściwości zależności, ale przy użyciu właściwości zależności zmniejsza ilość kodu, trzeba napisać, ponieważ <xref:System.Windows.Freezable> klasy została zaprojektowana z właściwości zależności na uwadze. Aby uzyskać więcej informacji o systemie właściwości zależności, zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 Każdy <xref:System.Windows.Freezable> musi zastąpić podklas <xref:System.Windows.Freezable.CreateInstanceCore%2A> metody. Jeśli klasa używa właściwości zależności dla wszystkich jego danych, zakończeniu.  
  
 Jeśli klasa zawiera elementy członkowskie danych właściwości z systemem innym niż zależności, musi także zastępować następujących metod:  
  
-   <xref:System.Windows.Freezable.CloneCore%2A>  
  
-   <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
-   <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 Należy również zgodna z poniższymi regułami uzyskiwania dostępu do oraz zapisywanie do elementów członkowskich danych, które nie są właściwości zależności:  
  
-   Na początku dowolnego [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] które odczytuje właściwości zależności z systemem innym niż elementy członkowskie danych, należy wywołać <xref:System.Windows.Freezable.ReadPreamble%2A> metody.  
  
-   Na początku jakiegokolwiek interfejsu API, który zapisuje elementy członkowskie danych właściwości zależności nie należy wywoływać <xref:System.Windows.Freezable.WritePreamble%2A> metody. (Po została wywołana <xref:System.Windows.Freezable.WritePreamble%2A> w [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], nie trzeba wywoływania dodatkowe <xref:System.Windows.Freezable.ReadPreamble%2A> Jeśli również przeczytanie elementy członkowskie danych właściwości z systemem innym niż zależności.)  
  
-   Wywołanie <xref:System.Windows.Freezable.WritePostscript%2A> metoda przed zamknięciem metody modyfikujące właściwości zależności z systemem innym niż elementy członkowskie danych.  
  
 Jeśli klasa zawiera elementy członkowskie danych niż właściwość zależności, które są <xref:System.Windows.DependencyObject> obiekty, musisz również wywołać <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> metody każdej zmianie na ich wartości, nawet jeśli ustawiasz element członkowski `null`.  
  
> [!NOTE]
>  Jest bardzo ważne, Rozpocznij każdego <xref:System.Windows.Freezable> zastąpienia z wywołaniem do podstawowej implementacji metody.  
  
 Na przykład niestandardowy <xref:System.Windows.Freezable> , zobacz [próbki animacji niestandardowej](http://go.microsoft.com/fwlink/?LinkID=159981).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Freezable>  
 [Przykładowe animacji niestandardowej](http://go.microsoft.com/fwlink/?LinkID=159981)  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
