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
ms.openlocfilehash: 427840430a37f675ccc0f0ee4f423370f2a55550
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646373"
---
# <a name="3-d-transformations-overview"></a>Przegląd Przekształcenia 3-D
W tym temacie opisano, jak zastosować przekształcenia w modelach 3-D w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] system grafiki. Przekształcenia umożliwiają deweloperom zmienić położenie, rozmiar i zmienić orientację modeli bez wprowadzania zmian w podstawowej wartości, które je zdefiniować.  
  

  
## <a name="3-d-coordinate-space"></a>3-przestrzeni współrzędnych  
 Grafika 3-D zawartość [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] są hermetyzowane w elemencie <xref:System.Windows.Controls.Viewport3D>, mogą uczestniczyć w strukturze dwuwymiarową elementu. System grafiki traktuje Viewport3D jako dwuwymiarową elementu wizualnego, takich jak wiele innych osób w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Viewport3D działa jako okno — okienko ekranu — na scenie trójwymiarowej. Dokładniej mówiąc jest powierzchni, w którym przewidywany jest scenę 3-D.  Chociaż Viewport3D można używać z innymi obiektami rysunku 2-D w ten sam wykres scen, nie interpenetrate obiektów 2 D i 3-w Viewport3D. W poniższym dyskusji przestrzeni współrzędnych opisane znajduje się w elemencie Viewport3D.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Współrzędnych dla grafika 2-D lokalizuje źródła w lewym górnym rogu powierzchnię renderowania (zazwyczaj ekranu). W systemie 2-D wartości dodatnie osi x mają kontynuować po prawej stronie, a wartości dodatnie y przejść w dół. W 3-w układzie współrzędnych jednak źródła znajduje się w środku ekranu, za pomocą wartości dodatnie osi x z prawej strony, ale wartości dodatnie y kontynuowanie zamiast tego w górę i wartości współrzędnych dodatnią, kontynuowanie na zewnątrz ze źródła, w kierunku Przeglądarka.  
  
 ![Współrzędnych](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem-1")  
System współrzędnych porównania  
  
 Obszar zdefiniowany przez te osi jest nieruchomy układem odniesienia dla obiektów 3-D w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Tworzenie modeli, w tym miejscu i utworzyć światła i aparaty fotograficzne, aby je wyświetlić, warto odróżnienia lokalnego układem odniesienia tworzone dla każdego modelu, jeśli zastosujesz przekształcenia do niego stacjonarnych układem odniesienia lub "miejsca na świecie,". Pamiętaj również, że obiekty w przestrzeni świata mogą różnić się całkowicie lub być niewidoczne na wszystkich, w zależności od jasny i aparatu ustawienia, ale pozycja kamery nie zmienia lokalizację obiektów w przestrzeni świata.  
  
## <a name="transforming-models"></a>Przekształcanie modeli  
 Podczas tworzenia modeli mają one określonej lokalizacji w scenie. Przenoszenie tych modeli w scenie, przenosić je lub zmieniać ich rozmiar nie jest praktyczne zmienić wierzchołki, które definiują samych modeli. Zamiast tego podobnie jak w przypadku 2-D, zastosujesz przekształcenia do modeli.  
  
 Każdy obiekt modelu ma <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> właściwości, za pomocą którego można przenosić, ponownie poznaniu lub zmienić rozmiar modelu. Jeśli zastosujesz przekształcenia, skutecznie przesunięcia wszystkie punkty modelu, niezależnie od wartości lub wektora jest określona przez transformacji. Innymi słowy, zostały przekształcone współrzędnych miejsca, w którym model jest zdefiniowana, ("model miejsca"), ale nie zostały zmienione wartości, które tworzą geometrii modelu w układzie współrzędnych całej sceny ("miejsca na świecie").  
  
## <a name="translation-transformations"></a>Przekształcenia tłumaczenia  
 Przekształcenia 3-D dziedziczyć abstrakcyjna klasa bazowa <xref:System.Windows.Media.Media3D.Transform3D>; należą do klasy affine — przekształcenia <xref:System.Windows.Media.Media3D.TranslateTransform3D>, <xref:System.Windows.Media.Media3D.ScaleTransform3D>, i <xref:System.Windows.Media.Media3D.RotateTransform3D>. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-w systemie są także <xref:System.Windows.Media.Media3D.MatrixTransform3D> klasę, która pozwala określić przekształcenia w bardziej zwięzły widok operacje na macierzach.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D> Przenosi wszystkie punkty w Model3D w kierunku wektora przesunięcia, określ za pomocą <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>, <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>, i <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A> właściwości. Na przykład w (2,2,2), biorąc pod uwagę wierzchołka modułu, przesunięcia wektor (0,1.6,1) spowoduje przeniesienie tego wierzchołka (2,2,2) do (2,3.6,3). Wierzchołki modułu jest nadal przestrzeni (2,2,2) w modelu, ale teraz ten obszar modelu została zmieniona jego relacji z miejsca na świecie tak, aby przestrzeni (2,2,2) w modelu (2,3.6,3) w przestrzeni świata.  
  
 ![Rysunek tłumaczenia](../../../../docs/framework/wpf/graphics-multimedia/media/transforms-translate.png "tłumaczenie przekształceń")  
Tłumaczenie z przesunięciem  
  
 W poniższych przykładach kodu pokazano, jak zastosować tłumaczenia.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Przekształcenia skalowania  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D> zmiany skali modelu wektor określona skala w odniesieniu do punktu centralnego. Określ jednolitego skalę, co umożliwia skalowanie modelu przez tę samą wartość w osi X, Y i Z, aby zmienić model rozmiar proporcjonalnie. Na przykład ustawienie na przekształcenie <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>, i <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> właściwości 0,5 połówki rozmiar modelu; ustawienie tymi samymi właściwościami na 2 podwaja się jej skalowanie wszystkich trzech osi.  
  
 ![Uniform ScaleTransform3D](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
Przykład ScaleVector  
  
 Określając przekształcania skalowania obsługuje technologię niejednolitego — przekształcania skali, w których wartości X, Y i Z nie są takie same — może spowodować modelu rozciągnąć lub umowy w co najmniej dwóch wymiarów, bez wywierania wpływu na inne. Na przykład ustawienie <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 1, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 2, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> 1 spowodowałoby przekształcone modelu dwukrotnie wysokości, ale nie ulega zmianie, wzdłuż osi X i Z.  
  
 Domyślnie obiekt ScaleTransform3D powoduje, że wierzchołki, aby rozwinąć lub zwinąć o pochodzenia (0,0,0). Jeśli model który chcesz przekształcić nie jest rysowana od początku, jednak skalowanie modelu ze źródła nie będą skalowane modelu "w"miejscu. Zamiast tego pomnożona wierzchołki modelu o wektor skalowania operacji skalowania zapewniają efekt tłumaczenia modelu, a także skalowanie.  
  
 ![Trzy moduły skalowany przy użyciu określonego punktu środkowego](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Przykład skalowania Centrum  
  
 Skalowanie modelu "w miejscu", należy określić, ustawiając obiekt ScaleTransform3D środek modelu <xref:System.Windows.Media.ScaleTransform.CenterX%2A>, <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, i <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> właściwości. Dzięki temu system grafiki skaluje przestrzeni modelu, a następnie tłumaczy to, aby wyśrodkować na określonym <xref:System.Windows.Media.Media3D.Point3D>. Z drugiej strony Jeśli dołączeniu modelu o punkt początkowy, określ punkt środkowy różnych powinny być widoczne modelu przetłumaczone od źródła.  
  
## <a name="rotation-transformations"></a>Przekształceń obrotu  
 Można też obrócić modelu w 3W na kilka różnych sposobów. Przekształcenie typowe obrotu określa osi i kąt obrotu wokół tej osi. <xref:System.Windows.Media.Media3D.RotateTransform3D> Klasy pozwala na zdefiniowanie <xref:System.Windows.Media.Media3D.Rotation3D> z jego <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> właściwości. Następnie możesz określić <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> i <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> właściwości Rotation3D, w tym przypadku <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>, aby zdefiniować przekształcenia. Poniższe przykłady Obróć model przez 60 stopni wokół osi Y.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Uwaga:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-w jest prawostronnego układu systemu, co oznacza, że wartość dodatnią wartość kąta obrotu powoduje zegara obrót wokół osi.  
  
 Obroty kąt w osi założono Obrót o punkt początkowy, jeśli nie określono wartości dla <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>, <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>, i <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> RotateTransform3D we właściwościach. Podobnie jak w przypadku skalowania, warto pamiętać, że obrót przekształca modelu całej przestrzeni współrzędnych. Jeśli model nie została utworzona o pochodzenie lub został przetłumaczony wcześniej, obrót mogą "bazowego" o pochodzeniu zamiast obracanie w miejscu.  
  
 ![Obrót przy użyciu nowego punktu centralnego](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Obrót za pomocą nowego centrum określony  
  
 Aby obrócić modelu "w miejscu", należy określić Centrum rzeczywiste modelu jako środek obrotu. Ponieważ geometrii zwykle jest formowana o punkt początkowy, oczekiwanego wyniku zbiór przekształceń w większości przypadków można uzyskać najpierw rozmiary modelu (skalowanie), a następnie ustawienie orientacji (obracania) i przenieś je na koniec (żądaną lokalizację Translacja go).  
  
 ![Obrót o 60 stopni w x&#45; i y&#45;osi](../../../../docs/framework/wpf/graphics-multimedia/media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Przykład obrotu  
  
 Kąt w osi wymiany działają dobrze w przypadku statycznej przekształceń i niektórych animacji. Jednak wziąć pod uwagę obracanie model sześcianu 60 stopni wokół osi X, a następnie 45 stopni wokół osi Z. Możesz opisać to przekształcenie jako dwa osobne affine — przekształcenia lub macierzy. Jednak może być trudne do bezproblemowego animowanie obrotu zdefiniowane w ten sposób. Mimo, że początkowe i końcowe pozycji modelu obliczone przez każda z tych metod są takie same, pośrednie stanowiska podjęte przez model są wymaga dużej pewności. Kwaternionów reprezentują alternatywny sposób obliczenia interpolacji między początkiem i końcem rotację.  
  
 Quaternion reprezentuje osi w przestrzeni 3D i obrót wokół tej osi. Na przykład quaternion może reprezentować osi (1,1,2) i cyrkulację 50 stopni. Power kwaternionów podczas definiowania rotacji pochodzi z dwóch operacji, które można wykonywać na nich: kompozycji i interpolacji. Kompozycja dwóch kwaternionów stosowane do geometrii oznacza "obrócić geometrii wokół axis2 rotation2, a następnie obracać wokół axis1, przez rotation1." Za pomocą kompozycji, możesz połączyć dwa obroty geometrii można pobrać quaternion jednego, który reprezentuje wynik. Ponieważ Interpolacja quaternion można obliczyć ścieżki płynne i uzasadnione z jedną osią i orientację na inny, możesz można interpolować od oryginału do quaternion złożone, aby osiągnąć płynne przejście od jednego do drugiego, dzięki któremu można animować Przekształcenie. W przypadku modeli, które chcesz animować można określić lokalizację docelową <xref:System.Windows.Media.Media3D.Quaternion> dla obrotu przy użyciu <xref:System.Windows.Media.Media3D.QuaternionRotation3D> dla <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> właściwości.  
  
## <a name="using-transformation-collections"></a>Przy użyciu transformacji kolekcji  
 Podczas kompilowania scenę, jest powszechne stosowanie transformacji więcej niż jeden do modelu. Dodaj transformacje do <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> zbiór <xref:System.Windows.Media.Media3D.Transform3DGroup> klasy do grupowania wygodnie przekształca się do różnych modeli w scenie. Często jest to wygodne jest ponowne używanie transformacji w różnych grupach, w ten sposób możesz użyć modelu, stosując inny zbiór przekształceń do każdego wystąpienia. Należy pamiętać, że kolejność, w którym przekształcenia są dodawane do kolekcji znaczące: w kolekcji są używane od pierwszego do ostatniego.  
  
## <a name="animating-transformations"></a>Animowanie przekształcenia  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-w implementacji uczestniczy w tej samej chronometrażu animacji systemu i jak grafika 2-D. Oznacza to aby animować scenę 3-D, animować właściwości jego modeli. Można animować właściwości elementów podstawowych bezpośrednio, ale jest zazwyczaj łatwiejsze animować przekształceń, które Zmienianie położenia lub wyglądu modeli. Ponieważ przekształcenia można zastosować do <xref:System.Windows.Media.Media3D.Model3DGroup> obiektów oraz poszczególne modele, można zastosować jeden zestaw animacji elementy podrzędne Model3Dgroup i inny zestaw animacji grupy obiektów.  Informacje o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] system chronometrażu i animacji, zobacz [Przegląd animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) i [Przegląd Scenorysy](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Animowanie obiektu w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], Tworzenie osi czasu, zdefiniuj animacji (czyli tak naprawdę zmianę niektórych wartości właściwości wraz z upływem czasu) i określa właściwość, do którego należy zastosować animacji. Ta właściwość musi być właściwością FrameworkElement. Ponieważ wszystkie obiekty w scenie 3-D są elementami podrzędnymi Viewport3D, właściwości objęte wszystkie animacje, który chcesz zastosować do sceny są właściwości właściwości Viewport3D. Ważne jest pozwolimy na opracowanie ścieżkę właściwości dla animacji z rozwagą, ponieważ składnia może być pełne.  
  
 Załóżmy, że chcesz obrócić obiekt w miejscu, ale także zastosować wahadłowego ruchu, aby udostępnić więcej obiektów do wyświetlenia. Można zastosować RotateTransform3D w modelu i animować osi jego obrotu z wektora jednego do drugiego. Poniższy przykład kodu demonstruje, stosując <xref:System.Windows.Media.Animation.Vector3DAnimation> właściwości osi Rotation3D transformacji, zakładając, że RotateTransform3D, aby być jednym z kilku przekształcenia zastosowano do modelu przy użyciu <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Użyj podobnej składni pod kątem innych właściwości transformacji próbę przeniesienia lub skalowanie obiektu.  Na przykład, można także zastosować <xref:System.Windows.Media.Animation.Point3DAnimation> właściwości ScaleCenter na skalowanie — przekształcenie spowodować model, aby sprawnie zakłócić jego kształtu.  
  
 Mimo że powyższych przykładach Przekształcanie właściwości <xref:System.Windows.Media.Media3D.GeometryModel3D>, jest również możliwe jest przekształcenie właściwości innych modeli w scenie.  Przez animowanie tłumaczenia stosowana do obiektów światła, można na przykład utworzyć przenoszenia światła i efekty, które znacząco zmienić wygląd Twoich modeli.  
  
 Ponieważ aparaty fotograficzne, są również modeli, jest możliwe jest przekształcenie również właściwości kamery.  Natomiast wygląd sceny można zmienić bez obaw dzięki przekształcaniu odległości lokalizacji lub płaszczyzny aparatu — w efekcie Przekształcanie projekcji całej sceny — należy pamiętać, że wiele efekty osiągnięcia w ten sposób może być bezużyteczny tyle "visual" do podglądu jako przekształcenia stosowane do lokalizacji lub pozycji modeli w scenie.  
  
## <a name="see-also"></a>Zobacz także
- [Grafika 3D — przegląd](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [Przekształcenia — przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [Przykładowe transformacje 2-D](https://go.microsoft.com/fwlink/?LinkID=158252)
