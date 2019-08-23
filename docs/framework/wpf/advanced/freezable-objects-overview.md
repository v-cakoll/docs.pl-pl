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
ms.openlocfilehash: d1fd626921cd17987770ced822be104fb2a42906
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937502"
---
# <a name="freezable-objects-overview"></a>Przegląd Obiekty Freezable
W tym temacie opisano sposób efektywnego używania i <xref:System.Windows.Freezable> tworzenia obiektów, które zapewniają specjalne funkcje, które mogą pomóc w zwiększeniu wydajności aplikacji. Przykłady obiektów Freezable obejmują pędzle, pióra, przekształcenia, geometrie i animacje.  
  
<a name="whatisafreezable"></a>   
## <a name="what-is-a-freezable"></a>Co to jest Freezable?  
 A <xref:System.Windows.Freezable> jest specjalnym typem obiektu, który ma dwa stany: Niezamrożone i zamrożone. Gdy nie zamrożone <xref:System.Windows.Freezable> , wydaje się, że zachowuje się tak jak każdy inny obiekt. Po zamrożoniu <xref:System.Windows.Freezable> nie można już modyfikować.  
  
 <xref:System.Windows.Freezable> A<xref:System.Windows.Freezable.Changed> zawiera zdarzenie, aby powiadomić obserwatorów o wszelkich modyfikacjach obiektu. Zamrażanie <xref:System.Windows.Freezable> a może poprawić wydajność, ponieważ nie musi już poświęcać zasobów na powiadomienia o zmianach. Zamrożone <xref:System.Windows.Freezable> może być również współużytkowane przez wątki, podczas <xref:System.Windows.Freezable> gdy nie można zablokować.  
  
 Chociaż Klasa ma wiele aplikacji, większość <xref:System.Windows.Freezable> obiektów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest związanych z podsystemem graficznym. <xref:System.Windows.Freezable>  
  
 <xref:System.Windows.Freezable> Klasa ułatwia korzystanie z pewnych obiektów systemu grafiki i pozwala zwiększyć wydajność aplikacji. Przykłady typów, które dziedziczą <xref:System.Windows.Freezable> z <xref:System.Windows.Media.Brush>, obejmują <xref:System.Windows.Media.Transform>klasy, <xref:System.Windows.Media.Geometry> i. Ponieważ zawierają one niezarządzane zasoby, system musi monitorować te obiekty do modyfikacji, a następnie aktualizować odpowiednie zasoby niezarządzane w przypadku zmiany oryginalnego obiektu. Nawet jeśli nie modyfikujesz obiektu systemowego Graphics, system musi nadal spędzać niektóre z zasobów monitorujących obiekt, w przypadku jego zmiany.  
  
 Załóżmy na przykład, że tworzysz <xref:System.Windows.Media.SolidColorBrush> pędzel i używasz go do rysowania tła przycisku.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 Gdy przycisk jest renderowany, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podsystem graficzny używa dostarczonych informacji do malowania grupy pikseli w celu utworzenia wyglądu przycisku. Mimo że używasz pełnego pędzla kolorów do opisywania, w jaki sposób przycisk powinien być namalowany, Pędzel pełnego koloru nie jest w rzeczywistości używany do malowania. System grafiki generuje szybkie i niskiego poziomu obiekty dla przycisku i pędzla. są to obiekty, które faktycznie pojawiają się na ekranie.  
  
 W przypadku zmodyfikowania pędzla należy ponownie wygenerować te obiekty niskiego poziomu. Klasa Freezable to co daje pędzlowi możliwość znalezienia odpowiednich, wygenerowanych obiektów niskiego poziomu i zaktualizowania ich w momencie zmiany. Gdy ta możliwość jest włączona, Pędzel jest określany jako "Niezamrożone".  
  
 <xref:System.Windows.Freezable.Freeze%2A> Metoda Freezable umożliwia wyłączenie tej możliwości samoaktualizacji. Możesz użyć tej metody, aby pędzel stał się "zablokowany" lub nie można go modyfikować.  
  
> [!NOTE]
> Nie każdy obiekt Freezable można zablokować. Aby uniknąć zgłaszania <xref:System.InvalidOperationException>, sprawdź wartość <xref:System.Windows.Freezable.CanFreeze%2A> właściwości obiektu Freezable, aby ustalić, czy można ją zamrozić przed próbą jej wstrzymania.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 Gdy nie musisz już modyfikować Freezable, zamrażanie zapewnia korzyści z wydajności. W przypadku zablokowania pędzla w tym przykładzie system grafiki nie musi już monitorować go pod kątem zmian. System grafiki może również wykonywać inne optymalizacje, ponieważ wie, że pędzel nie ulegnie zmianie.  
  
> [!NOTE]
> Dla wygody Obiekty Freezable pozostają Niezamrożone, chyba że zostaną jawnie zablokowane.  
  
<a name="frozenfreezables"></a>   
## <a name="using-freezables"></a>Korzystanie z obiektów Freezable platformie  
 Użycie niezablokowanego Freezable przypomina użycie dowolnego innego typu obiektu. W poniższym przykładzie kolor <xref:System.Windows.Media.SolidColorBrush> obiektu jest zmieniany z żółtego na czerwony, gdy jest używany do rysowania tła przycisku. System grafiki działa w tle, aby automatycznie zmienić przycisk z żółtego na czerwony, przy następnym odświeżeniu ekranu.  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### <a name="freezing-a-freezable"></a>Zamrażanie elementu Freezable  
 Aby nie modyfikować, należy <xref:System.Windows.Freezable.Freeze%2A> wywołać metodę. <xref:System.Windows.Freezable> Po zablokowaniu obiektu, który zawiera obiekty Freezable, te obiekty również są zamrożone. Na przykład w przypadku zablokowania <xref:System.Windows.Media.PathGeometry>, cyfry i segmenty, które zawiera, byłyby zablokowane.  
  
 **Nie** można zamrozić elementu Freezable, jeśli którykolwiek z następujących warunków jest spełniony:  
  
- Ma właściwości animowane lub powiązane z danymi.  
  
- Ma właściwości ustawione przez zasób dynamiczny. (Zobacz [zasoby XAML](xaml-resources.md) , aby uzyskać więcej informacji na temat zasobów dynamicznych).  
  
- Zawiera <xref:System.Windows.Freezable> obiekty podrzędne, które nie mogą być zamrożone.  
  
 Jeśli te warunki mają wartość FAŁSZ i nie zamierzasz modyfikować <xref:System.Windows.Freezable>, należy zamrozić go, aby uzyskać korzyści wynikające z wydajności opisane wcześniej.  
  
 Po wywołaniu <xref:System.Windows.Freezable.Freeze%2A> metody Freezable nie można już jej modyfikować. Próba modyfikacji zamrożonego obiektu powoduje, że <xref:System.InvalidOperationException> zostanie zgłoszony. Poniższy kod zgłasza wyjątek, ponieważ próbujemy zmodyfikować pędzel po jego zamrożoniu.  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 Aby uniknąć zgłaszania tego wyjątku, można użyć <xref:System.Windows.Freezable.IsFrozen%2A> metody, aby określić, <xref:System.Windows.Freezable> czy jest zablokowany.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 W poprzednim przykładzie kodu, modyfikowalna kopia została wykonana z zamrożonego obiektu za pomocą <xref:System.Windows.Freezable.Clone%2A> metody. W następnej sekcji omówiono klonowanie bardziej szczegółowo.  
  
 **Uwaga** Ponieważ zamrożony Freezable nie może być animowany, system animacji automatycznie utworzy modyfikowalne klony <xref:System.Windows.Freezable> zablokowanych obiektów podczas próby animowania ich <xref:System.Windows.Media.Animation.Storyboard>przy użyciu. Aby wyeliminować narzuty wydajności wynikające z klonowania, pozostaw obiekt niezamrożony, jeśli zamierzasz go animować. Aby uzyskać więcej informacji na temat animacji przy użyciu scenorysów, zobacz [Omówienie scenorysów](../graphics-multimedia/storyboards-overview.md).  
  
### <a name="freezing-from-markup"></a>Zamrażanie z adjustacji  
 Aby zablokować <xref:System.Windows.Freezable> obiekt zadeklarowany w znacznikach, należy `PresentationOptions:Freeze` użyć atrybutu. W poniższym przykładzie <xref:System.Windows.Media.SolidColorBrush> jest zadeklarowana jako zasób strony i zamrożona. Jest on następnie używany do ustawiania tła przycisku.  
  
 [!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 Aby użyć `Freeze` atrybutu, należy zmapować do obszaru nazw opcji prezentacji: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. `PresentationOptions`jest zalecanym prefiksem do mapowania tej przestrzeni nazw:  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 Ponieważ nie wszyscy czytelnicy XAML rozpoznają ten atrybut, zaleca się użycie [atrybutu MC:](mc-ignorable-attribute.md) , który można zignorować, aby oznaczyć `Presentation:Freeze` atrybut jako ignorowany:  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 Aby uzyskać więcej informacji, zobacz stronę z [atrybutem MC: ignorowany](mc-ignorable-attribute.md) .  
  
### <a name="unfreezing-a-freezable"></a>"Odmrożenie" a Freezable  
 Po zamrożoniu <xref:System.Windows.Freezable> nie można nigdy modyfikować ani odmrozić. można jednak utworzyć niezablokowany klon <xref:System.Windows.Freezable.Clone%2A> przy użyciu metody lub <xref:System.Windows.Freezable.CloneCurrentValue%2A> .  
  
 W poniższym przykładzie tło przycisku jest ustawione przy użyciu pędzla, a następnie Pędzel jest zablokowany. Niezablokowana kopia pędzla przy użyciu <xref:System.Windows.Freezable.Clone%2A> metody. Klon jest modyfikowany i używany do zmiany tła przycisku z żółtego na czerwony.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
> Niezależnie od używanej metody klonowania animacje nigdy nie są kopiowane do nowego <xref:System.Windows.Freezable>.  
  
 Metody <xref:System.Windows.Freezable.Clone%2A> i<xref:System.Windows.Freezable.CloneCurrentValue%2A> wytwarzają głębokie kopie Freezable. Jeśli Freezable zawiera inne zamrożone Obiekty Freezable, są one również klonowane i modyfikowane. Na przykład w przypadku klonowania zamrożonego <xref:System.Windows.Media.PathGeometry> w celu zmodyfikowania tego elementu dane i segmenty, które zawiera, są również kopiowane i modyfikowane.  
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a>Tworzenie własnej klasy Freezable  
 Klasa, która powodzi <xref:System.Windows.Freezable> się od, uzyskuje następujące funkcje.  
  
- Specjalne Stany: tylko do odczytu (zamrożony) i zapisywalny.  
  
- Bezpieczeństwo wątków: zamrożone <xref:System.Windows.Freezable> mogą być współużytkowane przez wątki.  
  
- Szczegółowe powiadomienie o zmianie: W przeciwieństwie <xref:System.Windows.DependencyObject>do innych, Obiekty Freezable zapewniają powiadomienia o zmianach w przypadku zmiany wartości właściwości podrzędnych.  
  
- Łatwe Klonowanie: Klasa Freezable już wdrożyła kilka metod, które tworzą głębokie klony.  
  
 A <xref:System.Windows.Freezable> jest<xref:System.Windows.DependencyObject>typem, i w związku z tym używa systemu właściwości zależności. Właściwości klasy nie muszą być właściwościami zależności, ale użycie właściwości zależności spowoduje zmniejszenie ilości kodu, który trzeba napisać, ponieważ <xref:System.Windows.Freezable> Klasa została zaprojektowana z uwzględnieniem właściwości zależności. Aby uzyskać więcej informacji na temat systemu właściwości zależności, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md).  
  
 Każda <xref:System.Windows.Freezable> podklasa musi <xref:System.Windows.Freezable.CreateInstanceCore%2A> zastąpić metodę. Jeśli Klasa używa właściwości zależności dla wszystkich danych, zostanie zakończona.  
  
 Jeśli Klasa zawiera elementy członkowskie danych niezależności, należy również zastąpić następujące metody:  
  
- <xref:System.Windows.Freezable.CloneCore%2A>  
  
- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
- <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 Należy również przestrzegać następujących reguł dostępu i zapisu do elementów członkowskich danych, które nie są właściwościami zależności:  
  
- Na początku dowolnego interfejsu API, który odczytuje elementy członkowskie danych niezależności, wywołaj <xref:System.Windows.Freezable.ReadPreamble%2A> metodę.  
  
- Na początku dowolnego interfejsu API, który zapisuje elementy członkowskie danych właściwości niezależności, wywołaj <xref:System.Windows.Freezable.WritePreamble%2A> metodę. (Po wywołaniu <xref:System.Windows.Freezable.WritePreamble%2A> w interfejsie API nie trzeba wykonywać dodatkowych <xref:System.Windows.Freezable.ReadPreamble%2A> wywołań w przypadku odczytywania także elementów członkowskich danych niezależności).  
  
- Wywołaj <xref:System.Windows.Freezable.WritePostscript%2A> metodę przed wyjściem z metod, które zapisują do elementów członkowskich danych niezależnych.  
  
 Jeśli Klasa zawiera niezależne składowe danych, które są <xref:System.Windows.DependencyObject> obiektami, należy również wywołać metodę za <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> każdym razem, gdy zmieniasz jedną z jej wartości, nawet jeśli tworzysz element członkowski `null`.  
  
> [!NOTE]
> Bardzo ważne jest, aby rozpocząć każdą <xref:System.Windows.Freezable> metodę przesłonięcia z wywołaniem podstawowej implementacji.  
  
 Przykład klasy niestandardowej <xref:System.Windows.Freezable> można znaleźć w [przykładowej animacji niestandardowej](https://go.microsoft.com/fwlink/?LinkID=159981).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Freezable>
- [Przykład animacji niestandardowej](https://go.microsoft.com/fwlink/?LinkID=159981)
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
