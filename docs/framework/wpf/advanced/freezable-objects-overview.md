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
ms.openlocfilehash: 755240859829042e9790b9c89e47bb7a2013ceef
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460447"
---
# <a name="freezable-objects-overview"></a>Przegląd Obiekty Freezable

W tym temacie opisano sposób efektywnego używania i tworzenia obiektów <xref:System.Windows.Freezable>, które udostępniają specjalne funkcje, które mogą pomóc w zwiększeniu wydajności aplikacji. Przykłady obiektów Freezable obejmują pędzle, pióra, przekształcenia, geometrie i animacje.

<a name="whatisafreezable"></a>

## <a name="what-is-a-freezable"></a>Co to jest Freezable?

<xref:System.Windows.Freezable> jest specjalnym typem obiektu, który ma dwa stany: Niezamrożone i zamrożone. Gdy nie zamrożono, <xref:System.Windows.Freezable> wygląda tak jak każdy inny obiekt. Po zamrożoniu nie można już modyfikować <xref:System.Windows.Freezable>.

<xref:System.Windows.Freezable> zawiera zdarzenie <xref:System.Windows.Freezable.Changed>, które powiadamia obserwatorów o wszelkich modyfikacjach obiektu. Zamrożenie <xref:System.Windows.Freezable> może zwiększyć jego wydajność, ponieważ nie trzeba już poświęcać zasobów na powiadomienia o zmianach. Zamrożone <xref:System.Windows.Freezable> mogą być również współużytkowane przez wątki, podczas gdy nie zamrożone <xref:System.Windows.Freezable>.

Chociaż Klasa <xref:System.Windows.Freezable> ma wiele aplikacji, większość <xref:System.Windows.Freezable> obiektów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest związana z podsystemem graficznym.

Klasa <xref:System.Windows.Freezable> ułatwia korzystanie z pewnych obiektów systemu grafiki i pozwala zwiększyć wydajność aplikacji. Przykłady typów, które dziedziczą z <xref:System.Windows.Freezable> zawierają klasy <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>i <xref:System.Windows.Media.Geometry>. Ponieważ zawierają one niezarządzane zasoby, system musi monitorować te obiekty do modyfikacji, a następnie aktualizować odpowiednie zasoby niezarządzane w przypadku zmiany oryginalnego obiektu. Nawet jeśli nie modyfikujesz obiektu systemowego Graphics, system musi nadal spędzać niektóre z zasobów monitorujących obiekt, w przypadku jego zmiany.

Załóżmy na przykład, że tworzysz pędzel <xref:System.Windows.Media.SolidColorBrush> i użyjesz go do malowania tła przycisku.

[!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
[!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]

Gdy przycisk jest renderowany, podsystem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Graphics używa dostarczonych informacji do malowania grupy pikseli w celu utworzenia wyglądu przycisku. Mimo że używasz pełnego pędzla kolorów do opisywania, w jaki sposób przycisk powinien być namalowany, Pędzel pełnego koloru nie jest w rzeczywistości używany do malowania. System grafiki generuje szybkie i niskiego poziomu obiekty dla przycisku i pędzla. są to obiekty, które faktycznie pojawiają się na ekranie.

W przypadku zmodyfikowania pędzla należy ponownie wygenerować te obiekty niskiego poziomu. Klasa Freezable to co daje pędzlowi możliwość znalezienia odpowiednich, wygenerowanych obiektów niskiego poziomu i zaktualizowania ich w momencie zmiany. Gdy ta możliwość jest włączona, Pędzel jest określany jako "Niezamrożone".

Freezable Metoda <xref:System.Windows.Freezable.Freeze%2A> umożliwia wyłączenie tej możliwości samoaktualizacji. Możesz użyć tej metody, aby pędzel stał się "zablokowany" lub nie można go modyfikować.

> [!NOTE]
> Nie każdy obiekt Freezable można zablokować. Aby uniknąć zgłaszania <xref:System.InvalidOperationException>, sprawdź wartość właściwości <xref:System.Windows.Freezable.CanFreeze%2A> obiektu Freezable, aby ustalić, czy można ją zamrozić przed podjęciem próby jego zablokowania.

[!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
[!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]

Gdy nie musisz już modyfikować Freezable, zamrażanie zapewnia korzyści z wydajności. W przypadku zablokowania pędzla w tym przykładzie system grafiki nie musi już monitorować go pod kątem zmian. System grafiki może również wykonywać inne optymalizacje, ponieważ wie, że pędzel nie ulegnie zmianie.

> [!NOTE]
> Dla wygody Obiekty Freezable pozostają Niezamrożone, chyba że zostaną jawnie zablokowane.

<a name="frozenfreezables"></a>

## <a name="using-freezables"></a>Korzystanie z obiektów Freezable platformie

Użycie niezablokowanego Freezable przypomina użycie dowolnego innego typu obiektu. W poniższym przykładzie kolor <xref:System.Windows.Media.SolidColorBrush> został zmieniony z żółtego na czerwony, gdy jest używany do rysowania tła przycisku. System grafiki działa w tle, aby automatycznie zmienić przycisk z żółtego na czerwony, przy następnym odświeżeniu ekranu.

[!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
[!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]

### <a name="freezing-a-freezable"></a>Zamrażanie elementu Freezable

Aby nie modyfikować <xref:System.Windows.Freezable>, należy wywołać metodę <xref:System.Windows.Freezable.Freeze%2A>. Po zablokowaniu obiektu, który zawiera obiekty Freezable, te obiekty również są zamrożone. Na przykład jeśli zablokujesz <xref:System.Windows.Media.PathGeometry>, dane i segmenty, które zawiera, byłyby również zablokowane.

**Nie** można zamrozić elementu Freezable, jeśli którykolwiek z następujących warunków jest spełniony:

- Ma właściwości animowane lub powiązane z danymi.

- Ma właściwości ustawione przez zasób dynamiczny. (Zobacz [zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) , aby uzyskać więcej informacji na temat zasobów dynamicznych).

- Zawiera <xref:System.Windows.Freezable> obiektów podrzędnych, które nie mogą być zamrożone.

Jeśli te warunki mają wartość FAŁSZ i nie zamierzasz modyfikować <xref:System.Windows.Freezable>, należy zamrozić go, aby uzyskać korzyści wynikające z wydajności opisane wcześniej.

Po wywołaniu metody <xref:System.Windows.Freezable.Freeze%2A> Freezable nie można już jej modyfikować. Próba zmodyfikowania zablokowanego obiektu powoduje zgłoszenie <xref:System.InvalidOperationException>. Poniższy kod zgłasza wyjątek, ponieważ próbujemy zmodyfikować pędzel po jego zamrożoniu.

[!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
[!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]

Aby uniknąć zgłaszania tego wyjątku, można użyć metody <xref:System.Windows.Freezable.IsFrozen%2A>, aby określić, czy <xref:System.Windows.Freezable> jest zamrożona.

[!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
[!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]

W poprzednim przykładzie kodu, modyfikowalna kopia została wykonana z zamrożonego obiektu za pomocą metody <xref:System.Windows.Freezable.Clone%2A>. W następnej sekcji omówiono klonowanie bardziej szczegółowo.

> [!NOTE]
> Ponieważ zamrożony Freezable nie może być animowany, system animacji automatycznie tworzy modyfikowalne klony zamrożonych obiektów <xref:System.Windows.Freezable> podczas próby animowania ich przy użyciu <xref:System.Windows.Media.Animation.Storyboard>. Aby wyeliminować narzuty wydajności wynikające z klonowania, pozostaw obiekt niezamrożony, jeśli zamierzasz go animować. Aby uzyskać więcej informacji na temat animacji przy użyciu scenorysów, zobacz [Omówienie scenorysów](../graphics-multimedia/storyboards-overview.md).

### <a name="freezing-from-markup"></a>Zamrażanie z adjustacji

Aby zablokować obiekt <xref:System.Windows.Freezable> zadeklarowany w znacznikach, należy użyć atrybutu `PresentationOptions:Freeze`. W poniższym przykładzie <xref:System.Windows.Media.SolidColorBrush> jest zadeklarowana jako zasób strony i zamrożona. Jest on następnie używany do ustawiania tła przycisku.

[!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]

Aby użyć atrybutu `Freeze`, należy zmapować do obszaru nazw opcji prezentacji: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. `PresentationOptions` jest zalecanym prefiksem do mapowania tej przestrzeni nazw:

```xaml
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"
```

Ponieważ nie wszyscy czytelnicy XAML rozpoznają ten atrybut, zaleca się użycie [atrybutu MC:](mc-ignorable-attribute.md) , który można zignorować, aby oznaczyć atrybut `Presentation:Freeze` jako ignorowany:

```xaml
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="PresentationOptions"
```

Aby uzyskać więcej informacji, zobacz stronę z [atrybutem MC: ignorowany](mc-ignorable-attribute.md) .

### <a name="unfreezing-a-freezable"></a>"Odmrożenie" a Freezable

Po zamrożoniu <xref:System.Windows.Freezable> nie może być modyfikowany ani niezamrożony; można jednak utworzyć niezablokowany klon przy użyciu metody <xref:System.Windows.Freezable.Clone%2A> lub <xref:System.Windows.Freezable.CloneCurrentValue%2A>.

W poniższym przykładzie tło przycisku jest ustawione przy użyciu pędzla, a następnie Pędzel jest zablokowany. Niezablokowana kopia pędzla przy użyciu metody <xref:System.Windows.Freezable.Clone%2A>. Klon jest modyfikowany i używany do zmiany tła przycisku z żółtego na czerwony.

[!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
[!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]

> [!NOTE]
> Niezależnie od używanej metody klonowania animacje nie są nigdy kopiowane do nowego <xref:System.Windows.Freezable>.

Metody <xref:System.Windows.Freezable.Clone%2A> i <xref:System.Windows.Freezable.CloneCurrentValue%2A> dają głębokie kopie Freezable. Jeśli Freezable zawiera inne zamrożone Obiekty Freezable, są one również klonowane i modyfikowane. Na przykład w przypadku sklonowania zamrożonego <xref:System.Windows.Media.PathGeometry> w celu zmodyfikowania go elementy i segmenty, które zawiera, są również kopiowane i modyfikowane.

<a name="createyourownfreezableclass"></a>

## <a name="creating-your-own-freezable-class"></a>Tworzenie własnej klasy Freezable

Klasa, która pochodzi od <xref:System.Windows.Freezable>, ma następujące funkcje.

- Specjalne Stany: tylko do odczytu (zamrożony) i zapisywalny.

- Bezpieczeństwo wątków: zamrożone <xref:System.Windows.Freezable> mogą być współużytkowane przez wątki.

- Szczegółowe powiadomienie o zmianie: w przeciwieństwie do innych <xref:System.Windows.DependencyObject>s, Obiekty Freezable zapewniają powiadomienia o zmianach w przypadku zmiany wartości właściwości podrzędnych.

- Łatwe Klonowanie: Klasa Freezable już wdrożyła kilka metod, które tworzą głębokie klony.

<xref:System.Windows.Freezable> jest typem <xref:System.Windows.DependencyObject>i w związku z tym używa systemu właściwości zależności. Właściwości klasy nie muszą być właściwościami zależności, ale użycie właściwości zależności spowoduje zmniejszenie ilości kodu, który trzeba napisać, ponieważ Klasa <xref:System.Windows.Freezable> została zaprojektowana z uwzględnieniem właściwości zależności. Aby uzyskać więcej informacji na temat systemu właściwości zależności, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md).

Każda podklasa <xref:System.Windows.Freezable> musi zastąpić metodę <xref:System.Windows.Freezable.CreateInstanceCore%2A>. Jeśli Klasa używa właściwości zależności dla wszystkich danych, zostanie zakończona.

Jeśli Klasa zawiera elementy członkowskie danych niezależności, należy również zastąpić następujące metody:

- <xref:System.Windows.Freezable.CloneCore%2A>

- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>

- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>

- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>

- <xref:System.Windows.Freezable.FreezeCore%2A>

Należy również przestrzegać następujących reguł dostępu i zapisu do elementów członkowskich danych, które nie są właściwościami zależności:

- Na początku dowolnego interfejsu API, który odczytuje elementy członkowskie danych niezależności, wywołaj metodę <xref:System.Windows.Freezable.ReadPreamble%2A>.

- Na początku dowolnego interfejsu API, który zapisuje elementy członkowskie danych właściwości niezależności, wywołaj metodę <xref:System.Windows.Freezable.WritePreamble%2A>. (Po wywołaniu <xref:System.Windows.Freezable.WritePreamble%2A> w interfejsie API nie trzeba wykonywać dodatkowego wywołania do <xref:System.Windows.Freezable.ReadPreamble%2A>, jeśli odczytasz również elementy członkowskie danych niezależności.)

- Wywołaj metodę <xref:System.Windows.Freezable.WritePostscript%2A> przed wyjściem z metod, które zapisują elementy członkowskie danych właściwości niezależności.

Jeśli Klasa zawiera elementy członkowskie danych niezależnych, które są <xref:System.Windows.DependencyObject> obiektów, należy również wywołać metodę <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> za każdym razem, gdy zmieniasz jedną z wartości, nawet jeśli ustawiasz element członkowski na `null`.

> [!NOTE]
> Bardzo ważne jest, aby rozpocząć każdą metodę <xref:System.Windows.Freezable> przesłonięcia wywołania do implementacji podstawowej.

Przykład niestandardowej klasy <xref:System.Windows.Freezable> można znaleźć w [przykładowej animacji niestandardowej](https://go.microsoft.com/fwlink/?LinkID=159981).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Freezable>
- [Przykład animacji niestandardowej](https://go.microsoft.com/fwlink/?LinkID=159981)
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
