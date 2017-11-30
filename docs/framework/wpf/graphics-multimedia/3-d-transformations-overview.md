---
title: "Przegląd Przekształcenia 3-D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D transformations
- transformations [WPF], 3-D
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 431f4abd55da3b8c4e348d3abbd107e2f6344d5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="3-d-transformations-overview"></a>Przegląd Przekształcenia 3-D
W tym temacie opisano sposób stosowania przekształcenia do modeli 3-w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systemu grafiki. Przekształcenia umożliwiają deweloperom położenia, zmienianie rozmiaru i zmienić orientację modeli bez zmiany podstawowego wartości, które je zdefiniować.  
  

  
## <a name="3-d-coordinate-space"></a>3-przestrzeni współrzędnych  
 3-grafiki zawartości w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest hermetyzowany w elemencie <xref:System.Windows.Controls.Viewport3D>, które mogą uczestniczyć w strukturze dwuwymiarowa elementu. System grafiki traktuje Viewport3D jako dwuwymiarowa elementu wizualnego, takich jak wiele innych w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Viewport3D działa jako okno — okienko ekranu — do sceny trójwymiarowych. Dokładniej jest powierzchni, na którym jest zaprojektowana 3-sceny.  Chociaż Viewport3D można używać z innymi obiektami rysunku 2-D, w tym samym wykresie sceny, nie interpenetrate 2 D i 3-w obiektach Viewport3D. W następujących dyskusji przestrzeni współrzędnych opisane jest zawarty w elemencie Viewport3D.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Współrzędnych grafiki 2-D lokalizuje punkt początkowy, w lewym górnym rogu powierzchnię renderowania (zazwyczaj ekranu). W systemie 2-D wartości na osi x dodatnią przejść do prawej i wartości y dodatnią kontynuować w dół. 3-układu współrzędnych jednak źródła znajduje się w środku ekranu, wartości dodatnie osi x z prawej strony, ale dodatnią osi y wartości w górę zamiast i dodatnią osi z wartości na zewnątrz ze źródła, kierunku Podgląd.  
  
 ![System współrzędnych](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem-1")  
Porównanie współrzędnych  
  
 Obszar zdefiniowany przez te osi jest nieruchomy ramy odniesienia dla obiektów 3-w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Tworzenie modeli w tym miejscu i utworzyć świateł i aparaty fotograficzne, aby je wyświetlić, jest przydatne odróżnienia lokalnego ramy odniesienia utworzonym dla każdego modelu podczas stosowania przekształcenia do niego nieruchomy układ odniesienia lub "miejsca na świecie,". Pamiętaj również, że obiekty w przestrzeni świata może różnić się całkowicie lub nie jest widoczny w ogóle, w zależności od jasnym i aparatu ustawienia, ale pozycja kamery nie zmienia lokalizację obiektów w przestrzeni świata.  
  
## <a name="transforming-models"></a>Przekształcanie modeli  
 Podczas tworzenia modeli, mają one określonej lokalizacji na scenie. Do tych modeli przenoszenia sceny, obracanie lub zmienić ich rozmiar nie jest praktyczne zmienić wierzchołków, które definiują samych modeli. Zamiast tego należy tak jak w przypadku 2-D, należy zastosować przekształcenia do modeli.  
  
 Każdy obiekt modelu ma <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> właściwości, z którego można przenieść, ponownie ustawić orientację lub zmienić rozmiar modelu. Podczas stosowania przekształcenia skutecznie przesunięcia wszystkie punkty modelu przez niezależnie od wektora lub wartość określono za pomocą przekształcania. Innymi słowy, zostały przekształcone przestrzeni współrzędnych, w którym model jest zdefiniowane ("model miejsca"), ale nie zostały zmienione wartości, które tworzą geometrii modelu w układzie współrzędnych całej sceny ("miejsca na świecie").  
  
## <a name="translation-transformations"></a>Przekształcenia tłumaczenia  
 3-przekształcenia dziedziczyć abstrakcyjna klasa podstawowa <xref:System.Windows.Media.Media3D.Transform3D>; należą do klasy affine — przekształcenia <xref:System.Windows.Media.Media3D.TranslateTransform3D>, <xref:System.Windows.Media.Media3D.ScaleTransform3D>, i <xref:System.Windows.Media.Media3D.RotateTransform3D>. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-w systemie są także <xref:System.Windows.Media.Media3D.MatrixTransform3D> klasy, która pozwala określić przekształcenia w bardziej zwięzły operacji macierzy.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D>Przenosi wszystkie punkty w Model3D w kierunku przesunięcia wektora z <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>, <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>, i <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A> właściwości. Na przykład mając jednego wierzchołka modułu w (2,2,2), przesunięcia wektora (0,1.6,1) przeniosłaby tego wierzchołków (2,2,2) do (2,3.6,3). Wierzchołki modułu jest nadal miejsca (2,2,2) w modelu, ale teraz miejsca modelu została zmieniona jego relacji przestrzeni świata tak, aby miejsca (2,2,2) w modelu (2,3.6,3) w przestrzeni świata.  
  
 ![Rysunek tłumaczenia](../../../../docs/framework/wpf/graphics-multimedia/media/transforms-translate.png "tłumaczenie transformacji")  
Tłumaczenie z przesunięciem  
  
 W poniższych przykładach kodu przedstawiają sposób zastosowania tłumaczenia.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Przekształcenia skali  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D>zmiany skali modelu wektor określona Skala odwołaniem do punktu centralnego. Określ skalę uniform skaluje modelu przez tę samą wartość w osi X, Y i Z, aby zmienić rozmiar modelu proporcjonalnie. Na przykład ustawienie przekształcenia <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>, i <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> właściwości 0,5 połowy rozmiar modelu; ustawienie tej samej właściwości 2 podwaja jego skali w wszystkie trzy osie.  
  
 ![Jednolite obiekt ScaleTransform3D](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
Przykład ScaleVector  
  
 Określając transformację skali niejednolitego — transformację skali, których wartości X, Y i Z nie są takie same — może spowodować rozciągnąć lub kontraktu w co najmniej dwa wymiary bez wpływu na pozostałe przy użyciu modelu. Na przykład ustawienie <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 1, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 2, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> 1 spowodowałoby przekształcone modelu dwukrotnie w wysokości, ale pozostają niezmienione wzdłuż osi X i Z.  
  
 Domyślnie obiekt ScaleTransform3D powoduje, że wierzchołki rozwiń lub Zwiń o pochodzenia (0,0,0). Jeśli model, który ma być przekształcenie nie jest rysowana ze źródła, jednak skalowanie modelu ze źródła nie skalują modelu "w"miejscu. Zamiast tego modelu wierzchołków pomnożona przez o wektor skalowania operacja skalowania będzie działało tłumaczenia modelu, a także jej skalowania.  
  
 ![Trzy moduły skalowany przy punktu centralnego określony](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Przykład Center skali  
  
 Aby skalować modelu "w miejscu", określ Centrum modelu, ustawiając dla obiekt ScaleTransform3D <xref:System.Windows.Media.ScaleTransform.CenterX%2A>, <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, i <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> właściwości. To zapewnia, że system grafiki skaluje przestrzeni modelu i przetwarza go do środka na określonym <xref:System.Windows.Media.Media3D.Point3D>. Z drugiej strony został utworzony model o punkt początkowy, określ inną środka było się spodziewać modelu translacji od źródła.  
  
## <a name="rotation-transformations"></a>Obracanie przekształcenia  
 Model w 3-w można obracać na kilka różnych sposobów. Przekształcenie obrotu typowe określa osi i kąt obrotu wokół tej osi. <xref:System.Windows.Media.Media3D.RotateTransform3D> Klasy można zdefiniować <xref:System.Windows.Media.Media3D.Rotation3D> z jego <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> właściwości. Następnie możesz określić <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> i <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> właściwości Rotation3D, w tym przypadku <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>, aby zdefiniować transformacji. Poniższe przykłady Obróć model pod kątem 60 stopni wokół osi Y.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Uwaga:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-w jest praworęczny systemu, co oznacza, że wartość dodatnią wartość kąta obrotu powoduje przeciwnie obrót wokół osi.  
  
 Kąt osi obrotów założono obrót wokół miejsca początkowego, jeśli nie określono wartości dla <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>, <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>, i <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> RotateTransform3D we właściwościach. Podobnie jak w przypadku skalowania, warto pamiętać, że obrót przekształca modelu całej przestrzeni współrzędnych. Jeśli model nie została utworzona o źródła lub został przetłumaczony wcześniej, obrót może "przestawnego" wokół miejsca początkowego zamiast obracanie w miejscu.  
  
 ![Obrót o nowy punkt centralny](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Obrót o nowe Centrum określony  
  
 Aby Obróć model "w miejscu", należy określić center rzeczywiste modelu jako środek obrotu. Ponieważ geometrii zwykle jest modelowana o punkt początkowy, najpierw rozmiary modelu (skalowanie go), a następnie ustawienie orientacji (obrót) i finally przenoszenia go do odpowiedniej lokalizacji (oczekiwany wynik zestaw przekształcenia najczęściej można uzyskać Translacja go).  
  
 ![Obrót o 60 stopni w x &#45; t &#45; i osie](../../../../docs/framework/wpf/graphics-multimedia/media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Przykład obrotu  
  
 Obrotów kąt osi działa dobrze w przypadku przekształcenia statycznego i niektórych animacji. Jednak wziąć pod uwagę obracanie model sześcianu 60 stopni wokół osi X, a następnie 45 stopni wokół osi Z. Można opisać tej transformacji jako dwa osobne affine — przekształcenia lub macierzy. Jednak może być trudne do animowania bezproblemowe obracanie, zdefiniowane w ten sposób. Mimo że początkowy i końcowy pozycji modelu obliczone przez albo podejścia są takie same, pośrednie stanowiska podjęte przez model pewności praktyce. Quaternions reprezentuje alternatywny sposób obliczeniowe interpolacji między rozpoczęcia i zakończenia obrotu.  
  
 Quaternion reprezentuje osi w 3-miejsca i obrót wokół tej osi. Na przykład quaternion może reprezentować osi (1,1,2) i obrotu 50 stopni. Power quaternions podczas definiowania obrotów pochodzi z tych dwóch operacji, które można wykonywać na nich: kompozycji i interpolacji. Złożeniem dwóch quaternions dotyczą geometrię oznacza "obrócić geometrii wokół axis2 rotation2, a następnie go obracać wokół axis1 przez rotation1." Za pomocą kompozycji, można połączyć dwóch obrotów geometrii uzyskanie pojedynczego quaternion, który reprezentuje wynik. Ponieważ interpolacji quaternion można obliczyć ścieżki płynne i uzasadnione z jedną osią i orientacji do innego, należy można interpolować z oryginalnego do składa quaternion do osiągnięcia płynne przejście od jednego do drugiego, dzięki któremu można animować transformacja. W przypadku modeli, które mają być animowane, można określić miejsce docelowe <xref:System.Windows.Media.Media3D.Quaternion> dla obrotu przy użyciu <xref:System.Windows.Media.Media3D.QuaternionRotation3D> dla <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> właściwości.  
  
## <a name="using-transformation-collections"></a>Przy użyciu kolekcji przekształcania  
 Podczas kompilowania sceny, jest często stosowanym rozwiązaniem zastosować więcej niż jeden transformacji do modelu. Dodaj przekształceń do <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> Kolekcja <xref:System.Windows.Media.Media3D.Transform3DGroup> klasy do grupy przekształca znajdują się do różnych modeli sceny. Często jest to wygodny ponowne transformację z różnych grup, w ten sposób możesz użyć modelu, stosując inny zestaw przekształceń do każdego wystąpienia. Należy pamiętać, że kolejność, w którym przekształceń są dodawane do kolekcji znaczących: w kolekcji są używane od pierwszego do ostatniego.  
  
## <a name="animating-transformations"></a>Animowanie przekształcenia  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-implementacji uczestniczy w tym samym systemie harmonogram i animacji jako grafiki 2-D. Innymi słowy Aby animować 3-sceny, animowania właściwości jego modeli. Jest możliwe do animowania właściwości elementów podstawowych bezpośrednio, ale zazwyczaj ułatwia animować transformacje, których zmiana pozycji i wyglądu modeli. Ponieważ przekształcenia można zastosować do <xref:System.Windows.Media.Media3D.Model3DGroup> obiektów oraz poszczególnych modeli, można zastosować jeden zestaw animacji dzieci Model3Dgroup i inny zestaw animacji grupy obiektów.  Informacje o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] harmonogram i animacji systemu, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) i [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Aby animować obiektu w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], Tworzenie osi czasu, zdefiniuj animacji (która jest naprawdę zmiany niektórych wartości właściwości wraz z upływem czasu) i określ właściwość, do którego należy zastosować animacji. Ta właściwość musi być właściwością typu FrameworkElement. Ponieważ wszystkie obiekty w 3-sceny są elementami podrzędnymi Viewport3D, właściwości objęci żadnych animacji, które chcesz zastosować do sceny są właściwości właściwości Viewport3D. Ważne jest opracowywanie ścieżki właściwości dla animacji, ponieważ składnia może być pełne.  
  
 Załóżmy, że chcesz obiektu w miejscu, ale również do zastosowania wahadłowego ruchu do udostępnienia jednego obiektu do wyświetlenia. Można zastosować RotateTransform3D w modelu, a oś jego obrotu z jednego wektora do innego animowania. Poniższy przykład kodu pokazuje stosowania <xref:System.Windows.Media.Animation.Vector3DAnimation> do właściwości osi Rotation3D przekształcania, przy założeniu RotateTransform3D jest jednym z kilku transformacji zastosowanych do modelu z <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Użyj składni podobne pod kątem innych właściwości przekształcania przenosić i skalować obiektu.  Na przykład mogą być stosowane <xref:System.Windows.Media.Animation.Point3DAnimation> właściwości ScaleCenter w transformacji skali spowodować sprawnie zakłócić jego kształtu przy użyciu modelu.  
  
 Chociaż w powyższych przykładach przekształcenie właściwości <xref:System.Windows.Media.Media3D.GeometryModel3D>, jest również możliwe jest przekształcenie właściwości innych modeli sceny.  Przez animacji tłumaczeń zastosowany do prostych obiektów, można na przykład utworzyć przenoszenie jasnym i efekty cienia, które znacznie można zmienić wygląd modeli.  
  
 Ponieważ aparaty fotograficzne są również modeli, jest możliwe jest przekształcenie również właściwości kamery.  Gdy na pewno można zmienić wygląd sceny poprzez przekształcanie odległości lokalizacji lub płaszczyzny aparatu — w efekcie Przekształcanie projekcji całej sceny — należy pamiętać, że wiele efektów osiągnięcia w ten sposób może nie mieć tyle "sensu visual" podglądzie jako przekształcenia zastosowane do lokalizacji lub pozycji modeli sceny.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd grafiki 3-w](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Przekształca — omówienie](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Przykład 2-D transformacji](http://go.microsoft.com/fwlink/?LinkID=158252)
