---
title: Omówienie przekształceń 3D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D transformations
- transformations [WPF], 3D
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
ms.openlocfilehash: 0efd6d247f23760c878c82cc92e99f1b83c1b9d2
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112352"
---
# <a name="3d-transformations-overview"></a>Omówienie przekształceń 3D
W tym temacie opisano sposób stosowania przekształceń [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] do modeli 3D w systemie graficznym. Przekształcenia umożliwiają deweloperowi zmianę położenia, zmiany rozmiaru i zmiany orientacji modeli bez zmiany wartości podstawowych, które je definiują.  

## <a name="3d-coordinate-space"></a>Przestrzeń współrzędnych 3D  
 Zawartość grafiki 3D jest [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] hermetyzowana <xref:System.Windows.Controls.Viewport3D>w elemencie, który może uczestniczyć w strukturze elementów dwuwymiarowych. System graficzny traktuje Viewport3D jako dwuwymiarowy element [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]wizualny, jak wiele innych w programie . Viewport3D działa jako okno — rzutnia — w scenę trójwymiarową. Dokładniej, jest to powierzchnia, na której wyświetlana jest scena 3D.  Chociaż viewport3D z innymi obiektami rysunkowymi 2D można używać na tym samym wykresie sceny, nie można przenikać obiektów 2D i 3D w widoku3D. W poniższej dyskusji opisana przestrzeń współrzędnych jest zawarta w viewport3D elementu.  
  
 Układ [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] współrzędnych grafiki 2D lokalizuje początek układu współrzędnych w lewym górnym rogu powierzchni renderowania (zazwyczaj na ekranie). W systemie 2D dodatnie wartości osi x przebiegają w prawo, a dodatnie wartości osi y przebiegają w dół. W układzie współrzędnych 3D początek układu początkowego znajduje się jednak pośrodku ekranu, z dodatnimi wartościami osi X przechodzącymi w prawo, ale dodatnie wartości osi y, które zamiast tego postępują w górę, a dodatnie wartości osi Z wychodzą na zewnątrz od początku układu współrzędnych, w kierunku widza.  
  
 ![Układy współrzędnych](./media/coordsystem-1.png "CoordSystem-1")  
Porównanie układu współrzędnych  
  
 Przestrzeń zdefiniowana przez te osie jest nieruchomą ramką [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]odniesienia dla obiektów 3D w . Podczas tworzenia modeli w tej przestrzeni i tworzenia świateł i kamer, aby je wyświetlić, warto odróżnić tę stacjonarną ramkę odniesienia lub "przestrzeń świata" od lokalnej ramki odniesienia utworzonej dla każdego modelu po zastosowaniu do niego przekształceń. Pamiętaj również, że obiekty w przestrzeni świata mogą wyglądać zupełnie inaczej lub nie być w ogóle widoczne, w zależności od ustawień światła i kamery, ale położenie kamery nie zmienia położenia obiektów w przestrzeni świata.  
  
## <a name="transforming-models"></a>Przekształcanie modeli  
 Podczas tworzenia modeli mają one określoną lokalizację w scenie. Aby przenieść te modele w scenie, aby je obrócić lub zmienić ich rozmiar, nie jest praktyczne, aby zmienić wierzchołki, które definiują same modele. Zamiast tego, podobnie jak w 2D, stosuje się przekształcenia do modeli.  
  
 Każdy obiekt modelu <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> ma właściwość, za pomocą której można przenosić, ponownie orientować lub zmienić rozmiar modelu. Po zastosowaniu przekształcenia skutecznie przesuniesz wszystkie punkty modelu przez dowolny wektor lub wartość określoną przez transformację. Innymi słowy przekształciliśmy przestrzeń współrzędnych, w której zdefiniowano model ("przestrzeń modelu"), ale nie zmieniono wartości, które tworzą geometrię modelu w układzie współrzędnych całej sceny ("przestrzeń świata").  
  
## <a name="translation-transformations"></a>Przekształcenia tłumaczeń  
 Przekształcenia 3D dziedziczą <xref:System.Windows.Media.Media3D.Transform3D>z abstrakcyjnej klasy podstawowej; należą do nich klasy <xref:System.Windows.Media.Media3D.TranslateTransform3D>przekształcania afinów i <xref:System.Windows.Media.Media3D.ScaleTransform3D>. <xref:System.Windows.Media.Media3D.RotateTransform3D> System [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D zapewnia <xref:System.Windows.Media.Media3D.MatrixTransform3D> również klasę, która pozwala określić te same przekształcenia w bardziej zwięzłych operacjach macierzy.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D>przesuwa wszystkie punkty modelamo3D w kierunku wektora odsunięcia określonego za pomocą <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>, i <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A> właściwości. Na przykład, biorąc pod uwagę jeden wierzchołek sześcianu w (2,2,2), wektor odsunięcia (0,1.6,1) spowoduje przeniesienie tego wierzchołka (2,2,2) do (2,3,6,3). Wierzchołek modułu jest nadal (2,2,2) w przestrzeni modelu, ale teraz przestrzeń modelu zmieniła swoją relację z przestrzenią świata, tak aby (2,2,2) w przestrzeni modelu było (2,3,6,3) w przestrzeni świata.  
  
 ![Rysunek tłumaczenia](./media/transforms-translate.png "Transformacje-Translate")  
Tłumaczenie z przesunięciem  
  
 Poniższe przykłady kodu pokazują, jak zastosować tłumaczenie.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Skaluj przekształcenia  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D>zmienia skalę modelu o określony wektor skali w odniesieniu do punktu środkowego. Określ jednolitą skalę, która skaluje model o tę samą wartość w osiach X, Y i Z, aby proporcjonalnie zmienić rozmiar modelu. Na przykład ustawienie <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>transform's <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> i właściwości do 0,5 zmniejsza rozmiar modelu; ustawienie tych samych właściwości na 2 podwaja swoją skalę we wszystkich trzech osiach.  
  
 ![Jednolita skalaTransform3D](./media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
Przykład ScaleVector  
  
 Określając niejednorodne przekształcenie skali — transformację skali, której wartości X, Y i Z nie są takie same — można spowodować, że model rozciągnie się lub skurczy się w jednym lub dwóch wymiarach bez wpływu na inne. Na przykład <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> ustawienie na <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 1, do <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> 2 i do 1 spowodowałoby, że przekształcony model podwoi wysokość, ale pozostanie niezmieniony wzdłuż osi X i Z.  
  
 Domyślnie ScaleTransform3D powoduje wierzchołki, aby rozwinąć lub umowy o początku układu współrzędnych (0,0,0). Jeśli model, który chcesz przekształcić nie jest pobierana od początku układu współrzędnych, skalowanie modelu z początku nie będzie skalować modelu "w miejscu". Zamiast tego, gdy wierzchołki modelu są mnożone przez wektor skali, operacja skalowania będzie miała wpływ na tłumaczenie modelu, a także skalowanie go.  
  
 ![Trzy kostki skalowane z określonym punktem środkowym](./media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Przykład środka skalowania  
  
 Aby skalować model "na miejscu", należy określić środek modelu, ustawiając <xref:System.Windows.Media.ScaleTransform.CenterY%2A>opcję <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> ScaleTransform3D <xref:System.Windows.Media.ScaleTransform.CenterX%2A>i właściwości. Dzięki temu system graficzny skaluje przestrzeń modelu, a następnie tłumaczy <xref:System.Windows.Media.Media3D.Point3D>go na środek na określonym . Z drugiej strony, jeśli model został zbudowany o początku układu współrzędnych i określić inny punkt środkowy, spodziewać się modelu przetłumaczone z dala od początku układu współrzędnych.  
  
## <a name="rotation-transformations"></a>Przekształcenia obrotu  
 Model można obracać w 3D na kilka różnych sposobów. Typowa transformacja obrotu określa oś i kąt obrotu wokół tej osi. Klasa <xref:System.Windows.Media.Media3D.RotateTransform3D> umożliwia zdefiniowanie <xref:System.Windows.Media.Media3D.Rotation3D> a <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> z jego właściwości. Następnie należy <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> określić i właściwości na Rotation3D, w tym przypadku <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>, aby zdefiniować transformację. Poniższe przykłady obracają model o 60 stopni wokół osi Y.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Uwaga:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D jest systemem praworęcznym, co oznacza, że dodatnia wartość kąta dla obrotu powoduje obrót w kierunku przeciwnym do ruchu wskazówek zegara wokół osi.  
  
 Obroty kąta osi zakładają obrót względem początku układu <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A> <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>współrzędnych, jeśli wartość nie jest określona dla , i <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> właściwości na RotateTransform3D. Podobnie jak w skalowaniu, warto pamiętać, że obrót przekształca całą przestrzeń współrzędnych modelu. Jeśli model nie został utworzony o początku układu współrzędnych lub został przetłumaczony wcześniej, obrót może "przestawiać się" na początku układu współrzędnych zamiast obracać w miejscu.  
  
 ![Obrót z nowym punktem środkowym](./media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Obrót z nowym środkiem określonym  
  
 Aby obrócić model "na miejscu", należy określić rzeczywisty środek modelu jako środek obrotu. Ponieważ geometria jest zazwyczaj modelowana względem początku układu współrzędnych, najczęściej można uzyskać oczekiwany wynik zestawu przekształceń, najpierw dokonując zmiany rozmiaru modelu (skalowanie), a następnie ustawiając jego orientację (obracając go), a na końcu przesuwając go w żądane miejsce ( tłumaczenie).  
  
 ![Obrót o 60 stopni w osiach x&#45; i y&#45;](./media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Przykład obrotu  
  
 Obroty kąta osi działają dobrze w przypadku przekształceń statycznych i niektórych animacji. Należy jednak rozważyć obrócenie modelu sześcianu o 60 stopni wokół osi X, a następnie o 45 stopni wokół osi Z. Transformację można opisać jako dwa dyskretne przekształcenia afiniowe lub jako macierz. Jednak może być trudno płynnie animować obrót zdefiniowany w ten sposób. Mimo że pozycje początkowe i końcowe modelu obliczane przez obie metody są takie same, pozycje pośrednie zajmowane przez model są niepewne obliczeniowo. Kwaterniony stanowią alternatywny sposób obliczania interpolacji między rozpoczęciem a końcem obrotu.  
  
 Kwaternion reprezentuje oś w przestrzeni 3D i obrót wokół tej osi. Na przykład kwaternion może reprezentować (1,1,2) osi i obrót o 50 stopni. Moc kwaternionów w definiowaniu obrotów pochodzi z dwóch operacji, które można wykonać na nich: skład i interpolacji. Skład dwóch kwaternionów zastosowanych do geometrii oznacza "obróć geometrię wokół osi2 przez obrót2, a następnie obróć ją wokół osi1 przez obrót1." Za pomocą kompozycji, można połączyć dwa obroty na geometrii, aby uzyskać pojedynczy kwaterni, który reprezentuje wynik. Ponieważ interpolacja kwaternika może obliczyć gładką i rozsądną ścieżkę z jednej osi i orientacji do drugiej, można interpolować z oryginału do złożonego kwaternionego, aby uzyskać płynne przejście z jednego do drugiego, umożliwiając animowanie Transformacji. Dla modeli, które mają być animowane, <xref:System.Windows.Media.Media3D.Quaternion> można określić <xref:System.Windows.Media.Media3D.QuaternionRotation3D> miejsce <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> docelowe dla obrotu za pomocą dla właściwości.  
  
## <a name="using-transformation-collections"></a>Korzystanie z kolekcji transformacji  
 Podczas tworzenia sceny, jest często zastosować więcej niż jedną transformację do modelu. Dodaj przekształcenia <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> do <xref:System.Windows.Media.Media3D.Transform3DGroup> kolekcji klasy do grupy przekształca wygodnie zastosować do różnych modeli w scenie. Często jest wygodne do ponownego użycia transformacji w kilku różnych grupach, w taki sposób, że można ponownie użyć modelu, stosując inny zestaw przekształceń do każdego wystąpienia. Należy zauważyć, że kolejność, w której przekształcenia są dodawane do kolekcji jest istotne: przekształcenia w kolekcji są stosowane od pierwszego do ostatniego.  
  
## <a name="animating-transformations"></a>Animowanie przekształceń  
 Implementacja [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D uczestniczy w tym samym systemie chronometrażu i animacji co grafika 2D. Innymi słowy, aby animować scenę 3D, animuj właściwości jej modeli. Istnieje możliwość animowania właściwości umietywnych bezpośrednio, ale zazwyczaj łatwiej jest animować przekształcenia, które zmieniają położenie lub wygląd modeli. Ponieważ przekształcenia mogą <xref:System.Windows.Media.Media3D.Model3DGroup> być stosowane do obiektów, a także poszczególnych modeli, istnieje możliwość zastosowania jednego zestawu animacji do obrażeń śr grupy Model3D i innego zestawu animacji do grupy obiektów.  Aby uzyskać podstawowe [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] informacje na temat systemu chronometrażu i animacji, zobacz [Omówienie animacji](animation-overview.md) i [scenorysu](storyboards-overview.md).  
  
 Aby animować [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]obiekt w programie , utwórz oś czasu, zdefiniuj animację (która jest naprawdę zmianą w niektórych wartości właściwości w czasie) i określ właściwość, do której ma być stosowana animacja. Ta właściwość musi być właściwością FrameworkElement. Ponieważ wszystkie obiekty w scenie 3D są częściami podrzędnymi viewport3D, właściwości, do których chcesz zastosować dowolną animację, którą chcesz zastosować do sceny, są właściwościami viewport3D. Ważne jest, aby dokładnie wypracować ścieżkę właściwości dla animacji, ponieważ składnia może być pełne.  
  
 Załóżmy, że chcesz obrócić obiekt w miejscu, ale także zastosować ruch wahadłowy, aby odsłonić więcej obiektu do wyświetlenia. Można zastosować RotateTransform3D do modelu i animować oś jego obrotu z jednego wektora do drugiego. Poniższy przykład kodu pokazuje <xref:System.Windows.Media.Animation.Vector3DAnimation> zastosowanie a do Axis właściwości transformacji Rotation3D, przy założeniu RotateTransform3D jest jednym z <xref:System.Windows.Media.TransformGroup>kilku przekształceń stosowanych do modelu z .  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Użyj podobnej składni, aby kierować inne właściwości transformacji, aby przenieść lub skalować obiekt.  Na przykład można zastosować <xref:System.Windows.Media.Animation.Point3DAnimation> a do ScaleCenter właściwości na przekształcenie skali spowodować model płynnie zniekształcić jego kształt.  
  
 Chociaż w poprzednich przykładach przekształcają właściwości <xref:System.Windows.Media.Media3D.GeometryModel3D>, możliwe jest również przekształcenie właściwości innych modeli w scenie.  Na przykład animację tłumaczeń zastosowanych do obiektów jasnych można tworzyć ruchome efekty światła i cienia, które mogą radykalnie zmienić wygląd modeli.  
  
 Ponieważ kamery są również modelami, możliwe jest również przekształcenie właściwości kamery.  Chociaż z pewnością można zmienić wygląd sceny, przekształcając położenie kamery lub odległości płaszczyzny - w efekcie, przekształcając całą projekcję sceny - należy zauważyć, że wiele efektów, które osiągniesz w ten sposób, może nie mieć tak "wizualnego sensu" dla widza jako przekształcenia zastosowane do lokalizacji lub położenia modeli w scenie.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie grafiki 3D](3-d-graphics-overview.md)
- [Przekształcenia — przegląd](transforms-overview.md)
- [Przykład transformacji 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
