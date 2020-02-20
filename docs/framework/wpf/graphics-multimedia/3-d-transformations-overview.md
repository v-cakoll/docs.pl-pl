---
title: Przegląd Przekształcenia 3-D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D transformations
- transformations [WPF], 3-D
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
ms.openlocfilehash: 983ae51fb74255b3331237825755449a00c9f95c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453146"
---
# <a name="3-d-transformations-overview"></a>Przegląd Przekształcenia 3-D
W tym temacie opisano sposób stosowania transformacji do modeli trójwymiarowych w systemie grafiki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Przekształcenia umożliwiają deweloperowi zmianę położenia, zmiana rozmiaru i skalowanie modeli bez zmiany wartości podstawowych, które je definiują.  

## <a name="3-d-coordinate-space"></a>Przestrzeń współrzędnych 3-D  
 zawartość grafiki trójwymiarowej w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest hermetyzowana w elemencie, <xref:System.Windows.Controls.Viewport3D>, która może uczestniczyć w dwuwymiarowej strukturze elementów. System grafiki traktuje Viewport3D jako dwuwymiarowy element wizualny, taki jak wiele innych w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Viewport3D funkcje jako okno — okienko ekranu — w trójwymiarowej scenie. Dokładniej, jest to powierzchnia, na której jest rzutowana scena 3-w.  Chociaż można używać Viewport3D z innymi obiektami rysowania 2-D w tym samym grafie sceny, nie można przeciągać obiektów 2-D i 3-D w Viewport3D. W poniższej dyskusji, opisana powyżej obszar koordynacji jest zawarty w elemencie Viewport3D.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] układu współrzędnych dla grafiki 2-D lokalizuje źródło w lewym górnym rogu powierzchni renderowania (zazwyczaj ekranu). W systemie 2-D dodatnie wartości osi x przechodzą do prawej i dodatniej wartości osi y przechodzą w dół. Jednak w układzie współrzędnych 3-D początek znajduje się na środku ekranu, a dodatnie wartości osi x przechodzą w prawo, ale dodatnie wartości osi y przechodzą w górę, a dodatnie wartości osi z są realizowane na zewnątrz od początku, w kierunku Przeglądarka.  
  
 ![Systemy współrzędnych](./media/coordsystem-1.png "CoordSystem-1")  
Porównanie systemu współrzędnych  
  
 Przestrzeń zdefiniowana przez te osie jest nieruchomą ramką odwołania dla obiektów 3-D w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. W miarę kompilowania modeli w tym miejscu i tworzenia lamp i kamer w celu ich wyświetlania, warto rozróżnić tę nieruchomą ramkę odniesienia lub "przestrzeń świata" z lokalnej ramki odniesienia, którą tworzysz dla każdego modelu, gdy stosowane są przekształcenia. Należy pamiętać, że obiekty w przestrzeni świata mogą wyglądać zupełnie inaczej lub nie być widoczne w ogóle, w zależności od ustawień świateł i aparatu, ale położenie kamery nie zmienia lokalizacji obiektów w przestrzeni świata.  
  
## <a name="transforming-models"></a>Transformowanie modeli  
 Podczas tworzenia modeli mają one określoną lokalizację w scenie. Aby przenieść te modele wokół sceny, aby je obrócić lub zmienić ich rozmiar, nie można zmienić wierzchołków, które definiują same modele. Zamiast tego, podobnie jak w przypadku 2-D, stosowane są przekształcenia do modeli.  
  
 Każdy obiekt modelu ma właściwość <xref:System.Windows.Media.Media3D.Model3D.Transform%2A>, za pomocą której można przesuwać, zmieniać orientację lub skalować model. Po zastosowaniu przekształcenia można efektywnie przesunąć wszystkie punkty modelu według dowolnego wektora lub wartości określonego przez transformację. Innymi słowy, została przekształcona przestrzeń współrzędnych, w której zdefiniowany jest model ("przestrzeń modelowa"), ale nie zmieniono wartości, które tworzą geometrię modelu w układzie współrzędnych całej sceny ("przestrzeń świata").  
  
## <a name="translation-transformations"></a>Przekształcenia translacji  
 przekształcenia trójwymiarowe dziedziczą z abstrakcyjnej klasy bazowej <xref:System.Windows.Media.Media3D.Transform3D>; obejmują one klasy transformacji afinicznym <xref:System.Windows.Media.Media3D.TranslateTransform3D>, <xref:System.Windows.Media.Media3D.ScaleTransform3D>i <xref:System.Windows.Media.Media3D.RotateTransform3D>. System [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-D udostępnia również klasę <xref:System.Windows.Media.Media3D.MatrixTransform3D>, która pozwala określić te same przekształcenia w bardziej zwięzłych operacjach macierzy.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D> przenosi wszystkie punkty w Model3D w kierunku wektora przesunięcia określonego przy użyciu właściwości <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>, <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>i <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A>. Na przykład, jeśli jeden wierzchołk modułu w (2, 2, 2), wektor przesunięcia (0, 1.6, 1) zostałby przesunięty do tego wierzchołka (2, 2, 2) do (2, 3.6, 3). Wierzchołek modułu jest nadal (2, 2, 2) w przestrzeni modelu, ale teraz przestrzeń modelu zmieniła swoją relację na przestrzeń świata, tak aby (2, 2, 2) w przestrzeni modelu była (2, 3.6, 3) w przestrzeni świata.  
  
 ![Rysunek tłumaczenia](./media/transforms-translate.png "Przekształcenia — tłumaczenie")  
Tłumaczenie z przesunięciem  
  
 Poniższy przykład kodu pokazuje, jak zastosować tłumaczenie.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Skalowanie przekształceń  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D> zmienia skalowanie modelu według określonego wektora skali z odwołaniem do punktu centralnego. Określ jednolitą skalę, która skaluje model o tej samej wartości w osiach X, Y i Z, aby zmienić rozmiar modelu proporcjonalnie. Na przykład ustawienie właściwości <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>i <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> przekształcenia na 0,5 powoduje połowę rozmiaru modelu; ustawienie tych samych właściwości na 2 podwaja swoją skalę we wszystkich trzech osiach.  
  
 ![Jednolita ScaleTransform3D](./media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
Przykład ScaleVector  
  
 Określając niejednorodną transformację skalowania — przekształcenie skali, którego wartości X, Y i Z nie są takie same — można spowodować rozciągnięcie modelu lub kontraktu w jednym lub dwóch wymiarach bez wpływania na inne. Na przykład ustawienie <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> na 1, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> do 2 i <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> na 1 spowodowałoby, że przekształcony model ma podwójną wysokość, ale pozostaje niezmieniony wzdłuż osi X i Z.  
  
 Domyślnie ScaleTransform3D powoduje powiększanie wierzchołków lub kontrakt o pochodzenie (0, 0, 0). Jeśli model, który ma zostać przekształcony, nie jest rysowany z punktu początkowego, skalowanie modelu od początku nie będzie miało skalowania modelu "w miejscu". Zamiast tego, gdy wierzchołki modelu są mnożone przez wektor skali, Operacja skalowania będzie miała wpływ na tłumaczenie modelu oraz jego skalowanie.  
  
 ![Trzy moduły skalowane do określonego punktu środkowego](./media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Przykład centrum skalowania  
  
 Aby skalować model "na miejscu", określ centrum modelu przez ustawienie właściwości <xref:System.Windows.Media.ScaleTransform.CenterX%2A>ScaleTransform3D's, <xref:System.Windows.Media.ScaleTransform.CenterY%2A>i <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A>. Dzięki temu system grafiki skaluje przestrzeń modelu, a następnie tłumaczy ją na centrum na określonym <xref:System.Windows.Media.Media3D.Point3D>. Z drugiej strony, jeśli skompilowano model o pochodzeniu i określisz inny punkt środkowy, oczekiwano, że model zostanie odliczony od źródła.  
  
## <a name="rotation-transformations"></a>Przekształcenia rotacji  
 Model można obrócić na 3-D na kilka różnych sposobów. Typowa transformacja rotacji określa oś i kąt obrotu wokół tej osi. Klasa <xref:System.Windows.Media.Media3D.RotateTransform3D> umożliwia zdefiniowanie <xref:System.Windows.Media.Media3D.Rotation3D> z właściwością <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A>. Następnie należy określić właściwości <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> i <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> w Rotation3D, w tym przypadku <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>, aby zdefiniować transformację. Poniższe przykłady obracają model o 60 stopni wokół osi Y.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Uwaga:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-D jest systemem z prawej strony, co oznacza, że dodatnia wartość kąta obrotów powoduje obrót w prawo od licznika na osi.  
  
 Obrót kątowy osi zakłada obrót na początku, jeśli wartość nie jest określona dla właściwości <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>, <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>i <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> w RotateTransform3D. Podobnie jak w przypadku skalowania, warto pamiętać, że rotacja przekształca cały obszar współrzędnych. Jeśli model nie został utworzony na początku lub został przetłumaczony wcześniej, rotacja może "Pivot" o miejscu pochodzenia zamiast obracania.  
  
 ![Obrót z nowym punktem centrum](./media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Obrót z określonym nowym centrum  
  
 Aby obrócić model "na miejscu", określ rzeczywiste centrum modelu jako środek obrotu. Ze względu na to, że geometria jest zwykle modelowana o pochodzeniu, najczęściej można uzyskać oczekiwany wynik zestawu transformacji, najpierw zmieniając rozmiar modelu (skalowanie go), a następnie ustawiając jego orientację (obracając go) i przenosząc go do żądanej lokalizacji ( tłumaczenie.  
  
 ![Obrót o 60 stopni w osi&#45; x i&#45;y](./media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Przykład rotacji  
  
 Obrót kątowy dla osi, dobrze sprawdza się w przypadku transformacji statycznych i niektórych animacji. Należy jednak rozważyć obrócenie modelu modułu 60 stopni wokół osi X, a następnie 45 stopni wokół osi Z. Tę transformację można opisać jako dwie dyskretne przekształcenia afinicznym lub jako macierz. Niemniej jednak trudno jest płynnie animować kąt zdefiniowany w ten sposób. Mimo że początkowe i końcowe pozycje modelu obliczone przez jedno z metod są takie same, pośrednie pozycje wykonywane przez model są w sposób nieokreślony. Kwaternionów reprezentuje alternatywny sposób obliczenia interpolacji między początkiem i końcem obrotu.  
  
 Quaternion reprezentuje oś w przestrzeni trójwymiarowej i rotację wokół tej osi. Na przykład Quaternion może reprezentować oś (1, 1, 2) i obrót o 50 stopni. Kwaternionów "moc definiowania rotacji pochodzi z dwóch operacji, które można wykonywać na nich: składanie i Interpolacja. Kompozycja dwóch kwaternionów zastosowana do geometrii oznacza "Obróć geometrię wokół axis2 przez rotation2, a następnie obróć ją wokół Axis1 przez rotation1". Korzystając z kompozycji, można połączyć dwa obroty w geometrii, aby uzyskać pojedynczy Quaternion, który reprezentuje wynik. Ponieważ Interpolacja Quaternion może obliczyć gładką i rozsądną ścieżkę z jednej osi i orientacji do innej, można przeprowadzić interpolację od oryginału do złożonej Quaternion w celu zapewnienia sprawnego przejścia od jednego do drugiego, co pozwala animować przekształcania. Dla modeli, które mają być animowane, można określić <xref:System.Windows.Media.Media3D.Quaternion> docelowy dla rotacji przy użyciu <xref:System.Windows.Media.Media3D.QuaternionRotation3D> dla właściwości <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A>.  
  
## <a name="using-transformation-collections"></a>Używanie kolekcji transformacji  
 Podczas kompilowania sceny często stosuje się więcej niż jedno przekształcenie do modelu. Dodaj transformacje do kolekcji <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> klasy <xref:System.Windows.Media.Media3D.Transform3DGroup>, aby grupować transformacje, wygodnie mają być stosowane do różnych modeli w scenie. Często warto ponownie wykorzystać transformację w kilku różnych grupach, w podobny sposób, aby można było ponownie wykorzystać model, stosując różne przekształceń do poszczególnych wystąpień. Należy zauważyć, że kolejność, w której przekształcenia są dodawane do kolekcji, jest istotna: przekształceń z kolekcji są stosowane od pierwszego do ostatniego.  
  
## <a name="animating-transformations"></a>Animowanie transformacji  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] implementacja 3-D uczestniczy w tym samym systemie chronometrażu i animacji co grafika 2-D. Innymi słowy, aby animować scenę 3-D, Animuj właściwości jej modeli. Istnieje możliwość bezpośredniej animacji właściwości elementów pierwotnych, ale jest to zwykle prostsze, aby animować przekształcenia, które zmieniają pozycję lub wygląd modeli. Ponieważ przekształcenia można stosować do obiektów <xref:System.Windows.Media.Media3D.Model3DGroup>, a także poszczególnych modeli, istnieje możliwość zastosowania jednego zestawu animacji do elementów podrzędnych Model3Dgroup i innego zestawu animacji do grupy obiektów.  Aby uzyskać informacje ogólne dotyczące systemu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] chronometrażu i animacji, zobacz [Omówienie animacji](animation-overview.md) i [Omówienie scenorysów](storyboards-overview.md).  
  
 Aby animować obiekt w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], Utwórz oś czasu, zdefiniuj animację (co jest naprawdę zmianą wartości właściwości w czasie) i określ właściwość, do której ma zostać zastosowana animacja. Ta właściwość musi być właściwością FrameworkElement. Ponieważ wszystkie obiekty w scenie 3-D są elementami podrzędnymi Viewport3D, właściwości, które są przeznaczone dla każdej animacji, która ma zostać zastosowana do sceny, są właściwościami Właściwości Viewport3D. Ważne jest, aby uważnie obejść ścieżkę właściwości animacji, ponieważ składnia może być pełna.  
  
 Załóżmy, że chcesz obrócić obiekt w miejscu, ale również zastosować wahadłowe ruchy, aby uwidocznić więcej obiektów do wyświetlenia. Możesz zdecydować się na stosowanie RotateTransform3D do modelu i animować oś obrotu z jednego wektora do innego. Poniższy przykład kodu demonstruje zastosowanie <xref:System.Windows.Media.Animation.Vector3DAnimation> do właściwości oo Rotation3D transformacji, przy założeniu, że RotateTransform3D jest jednym z kilku przekształceń do modelu z <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Użyj podobnej składni, aby określić inne właściwości transformacji do przenoszenia lub skalowania obiektu.  Na przykład można zastosować <xref:System.Windows.Media.Animation.Point3DAnimation> do właściwości ScaleCenter na przekształceniu skali, aby spowodować płynne zniekształcanie kształtu przez model.  
  
 Chociaż powyższe przykłady przekształcają właściwości <xref:System.Windows.Media.Media3D.GeometryModel3D>, możliwe jest również przekształcenie właściwości innych modeli w scenie.  Animowanie tłumaczeń zastosowanych do obiektów lekkich, na przykład można tworzyć efekty przesuwania światła i cieniowania, które znacząco zmieniają wygląd modeli.  
  
 Ponieważ kamery są również modele, istnieje możliwość przekształcenia właściwości kamery.  Chociaż można zmienić wygląd sceny, przenosząc położenie kamery lub odległości płaszczyzny — w efekcie Przekształć całą projekcję sceny — należy zauważyć, że wiele efektów osiąganych w ten sposób może nie należeć do przeglądarki jako "wzrokową". jako przekształcenia stosowane do lokalizacji lub położenia modeli w scenie.  
  
## <a name="see-also"></a>Zobacz też

- [Grafika 3D — przegląd](3-d-graphics-overview.md)
- [Przekształcenia — przegląd](transforms-overview.md)
- [Przykład transformacji 2-D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
