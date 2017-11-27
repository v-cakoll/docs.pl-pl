---
title: "Przegląd Grafika 3-D"
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
- 3-D graphics [WPF]
- graphics [WPF], 3-D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 979cc7580471f616d39056f541b8374b372e8e88
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="3-d-graphics-overview"></a>Przegląd Grafika 3-D
<a name="introduction"></a>[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Funkcji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umożliwia deweloperom rysowania, transformacji i animowanie grafiki 3-w kodzie zarówno znaczników i procedur. Deweloperzy mogą łączyć [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] i [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Obsługa grafiki, tworzenie zaawansowanych formantów, złożonych ilustrują danych lub zwiększyć użytkownika interfejsu aplikacji. [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]Obsługa w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie ma na celu zapewnienie platformy projektowej gry kompletne. Ten temat zawiera omówienie [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemu grafiki.  
 
  
<a name="threed_in_2d"></a>   
## <a name="3-d-in-a-2-d-container"></a>3-w w kontenerze 2-D  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]Grafika zawartości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest hermetyzowany w elemencie <xref:System.Windows.Controls.Viewport3D>, które mogą uczestniczyć w strukturze dwuwymiarowa elementu. System grafiki traktuje <xref:System.Windows.Controls.Viewport3D> jako dwuwymiarowa elementu wizualnego, takich jak wiele innych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Viewport3D>Funkcje jako okno — okienko ekranu — do sceny trójwymiarowych. Dokładniej, jest powierzchni, na którym [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] jest zaprojektowana sceny.  
  
 W z konwencjonalnej [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] aplikacji, użyj <xref:System.Windows.Controls.Viewport3D> jak inny element kontenera, takich jak siatki lub kanwy.  Chociaż można używać <xref:System.Windows.Controls.Viewport3D> z innymi [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] Rysowanie obiektów w tym samym wykresie sceny, nie interpenetrate [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] i [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obiektów w ramach <xref:System.Windows.Controls.Viewport3D>.  Ten temat koncentruje się na sposób rysowania [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafiki wewnątrz <xref:System.Windows.Controls.Viewport3D>.  
  
<a name="coord_space"></a>   
## <a name="3-d-coordinate-space"></a>3-przestrzeni współrzędnych  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Współrzędnych dla [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafiki lokalizuje punkt początkowy w lewym górnym rogu obszaru renderowania (zazwyczaj ekranu). W [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] systemu dodatnią kontynuować wartości na osi x z prawej strony i wartości dodatnie osi y Przejdź w dół.  W [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] współrzędnych, jednak źródła znajduje się w Centrum obszaru renderowania wartości dodatnie osi x z prawej strony, ale dodatnią osi y wartości w górę zamiast i na zewnątrz wartości dodatnie osi z ze źródła do przeglądarki.  
  
 ![System współrzędnych](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem-1")  
Reprezentacje konwencjonalnej układ współrzędnych 2 D i 3-w  
  
 Obszar zdefiniowany przez te osi jest nieruchomy ramy odniesienia dla [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obiekty w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tworzenie modeli w tym miejscu i utworzyć świateł i aparaty fotograficzne, aby je wyświetlić, jest przydatne odróżnienia lokalnego ramy odniesienia utworzonym dla każdego modelu podczas stosowania przekształcenia do niego nieruchomy układ odniesienia lub "miejsca na świecie,". Pamiętaj również, że obiekty w przestrzeni świata może różnić się całkowicie lub nie jest widoczny w ogóle, w zależności od jasnym i aparatu ustawienia, ale pozycja kamery nie zmienia lokalizację obiektów w przestrzeni świata.  
  
<a name="cameras"></a>   
## <a name="cameras-and-projections"></a>Aparaty fotograficzne i projekcji  
 Deweloperzy, którzy pracują w [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] są przystosowane do rozmieszczania rysowania podstawowych na ekran dwuwymiarowy. Po utworzeniu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sceny, ważne jest, aby Pamiętaj naprawdę tworzenie [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] reprezentację [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obiektów. Ponieważ [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sceny wygląda inaczej w zależności od punktu widzenia onlooker, należy określić tego widoku. <xref:System.Windows.Media.Media3D.Camera> Klasa pozwala na określenie tego punktu widzenia dla [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sceny.  
  
 Inny sposób, aby zrozumieć, jak [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sceny jest reprezentowane na [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] powierzchni jest opisujące sceny jako projekcji na powierzchnię wyświetlania. <xref:System.Windows.Media.Media3D.ProjectionCamera> Można określić różne projekcje i ich właściwości, aby zmienić sposób widzi onlooker [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modeli. A <xref:System.Windows.Media.Media3D.PerspectiveCamera> określa projekcję, która foreshortens sceny.  Innymi słowy <xref:System.Windows.Media.Media3D.PerspectiveCamera> udostępnia z perspektywy punktu podczas wykonywania.  Można określić pozycja kamery w przestrzeni współrzędnych sceny, kierunku oraz pole widzenia aparatu i wektor definiujący kierunek "w górę" sceny. Na poniższym diagramie przedstawiono <xref:System.Windows.Media.Media3D.PerspectiveCamera>w projekcji.  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> i <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> właściwości <xref:System.Windows.Media.Media3D.ProjectionCamera> ograniczyć zakres aparatu projekcji. Ponieważ kamery może być umieszczony w dowolnym miejscu sceny, istnieje możliwość przez aparat faktycznie być umieszczony wewnątrz modelu lub bardzo blisko modelu, utrudniając odróżniać obiekty prawidłowo.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>można określić minimalną odległość z aparatu fotograficznego, po przekroczeniu których obiekty zostaną nie narysowania.  Z drugiej strony <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> pozwala określić odległość z aparatu fotograficznego po przekroczeniu których nie będzie rysowany obiektów, który zapewnia, że obiekty zbyt daleko być rozpoznawalne nie będą uwzględniane w sceny.  
  
 ![Instalator aparatu](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-6.png "CoordSystem 6")  
Pozycja kamery  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>Określa prostopadły rzut [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modelu do [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] visual powierzchni. Podobnie jak inne kamer określa pozycji, wyświetlanie kierunku, a kierunek "w górę". W odróżnieniu od <xref:System.Windows.Media.Media3D.PerspectiveCamera>, jednak <xref:System.Windows.Media.Media3D.OrthographicCamera> opisuje projekcji, który nie obejmuje foreshortening perspektywy. Innymi słowy <xref:System.Windows.Media.Media3D.OrthographicCamera> opisuje pole wyświetlenia, którego boki są równoległe, zamiast jedną którego boki spełnia w punkcie na aparatu. Na poniższej ilustracji przedstawiono ten sam model, jak wyświetlać za pomocą <xref:System.Windows.Media.Media3D.PerspectiveCamera> i <xref:System.Windows.Media.Media3D.OrthographicCamera>.  
  
 ![Rzutowanie prostopadłe i perspektywiczne](../../../../docs/framework/wpf/graphics-multimedia/media/camera-projections4.png "Camera_projections4")  
Perspektywy i projekcje rzutowanie  
  
 Poniższy kod przedstawia niektóre ustawienia typowe aparatu.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>   
## <a name="model-and-mesh-primitives"></a>Model i podstawowych siatki  
  
 <xref:System.Windows.Media.Media3D.Model3D>abstrakcyjna klasa podstawowa, która reprezentuje ogólnego jest [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obiektu. Aby utworzyć [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sceny, potrzebne są niektóre obiekty do wyświetlenia i obiekty, które tworzą wykres sceny pochodzi od <xref:System.Windows.Media.Media3D.Model3D>. Obecnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje modelowania mają geometrię z <xref:System.Windows.Media.Media3D.GeometryModel3D>. <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> Właściwość ten model ma siatki pierwotnych.  
  
 Aby utworzyć model, rozpocząć tworzenie typu pierwotnego, lub siatki. A [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] pierwotnych jest kolekcją wierzchołków, które tworzą pojedynczej [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] jednostki. Większość [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] systemy zapewniają podstawowych zaprojektowany na figurę zamkniętą najprostszym: trójkąt wynika z trzech wierzchołków.  Ponieważ trzy punkty trójkąta coplanar, można kontynuować dodawanie trójkąty celu modelu więcej kształtów złożonych, nazywanych siatki.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] System obecnie udostępnia <xref:System.Windows.Media.Media3D.MeshGeometry3D> klasy, która pozwala określić wszelkie geometrii; nie obsługuje obecnie wstępnie zdefiniowanych [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] podstawowych, takich jak obszary i formularze trzeciego stopnia. Rozpocząć tworzenie <xref:System.Windows.Media.Media3D.MeshGeometry3D> , określając listę wierzchołków trójkąt jako jego <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> właściwości. Każdy wierzchołek jest określony jako <xref:System.Windows.Media.Media3D.Point3D>.  (W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], określić tę właściwość jako listę liczb pogrupowane na trzy, które reprezentują współrzędne każdego wierzchołka.) W zależności od jego geometrii Twojej sieci może się składać z wielu trójkąty, niektóre z nich udostępnianie tego samego rogi (wierzchołków). Do rysowania siatki poprawnie, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] potrzebuje informacji o tym, które wierzchołków są współużytkowane przez które trójkąty. Te informacje są podane przez określenie listy indeksów trójkąt z <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> właściwości. Ta lista określa kolejność, w jakiej punkty określone w <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listy określi trójkąt.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 W powyższym przykładzie <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listy określa osiem wierzchołków do definiowania siatki w kształcie modułu. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> Właściwość określa listę grup dwanaście trzech indeksów.  Każdą liczbę w liście odwołuje się do przesunięcia do <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listy.  Na przykład pierwszych trzech wierzchołków określony przez <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listy są (1,1,0) (0,1,0) i (0,0,0). Pierwsze trzy indeksy określonego przez <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> listy są 0, 2 i 1, co odpowiada pierwszy, trzecie i drugie punktów <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listy. W związku z tym pierwszy trójkąt tworzącą model sześcianu będzie składać się z (1,1,0) do (0,1,0) do (0,0,0), a pozostałe trójkąty 11 będzie określana podobnie.  
  
 Można kontynuować Definiowanie modelu przez określenie wartości <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> i <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> właściwości.  Renderowanie powierzchni modelu, system grafiki wymaga informacji o tym, które kierunek powierzchni jest ukierunkowane na wszystkie trójkąta danego. Używa tych informacji do przeprowadzenia obliczania oświetlenia dla modelu: powierzchnie stają przed bezpośrednio do źródła światła pojawiają się jaśniejszy niż pod kątem od światła. Chociaż [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można określić wektory normalne domyślnego za pomocą współrzędnych pozycji, można również określić różnych wektory normalne zbliżenie wygląd zakrzywioną powierzchni.  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> Właściwość określa zbiór <xref:System.Windows.Point>s były system grafiki sposób mapowania współrzędne, które określają, jak rysowane tekstury wierzchołki siatki. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>określono jako wartość z zakresu od 0 do 1 włącznie.  Jak <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> właściwości, można obliczyć systemu grafiki, domyślne współrzędnych tekstury, ale można wybrać współrzędne tekstury różnych do kontrolowania mapowanie tekstury, który zawiera część powtarzana wzorca, na przykład ustawić. Więcej informacji na temat współrzędnych tekstury można znaleźć w kolejnych tematach lub w zestawie SDK zarządzanego Direct3D.  
  
 Poniższy przykład przedstawia sposób tworzenia krój jednego modelu modułu w procedurach kodu. Uwaga narysować cały moduł jako pojedynczy GeometryModel3D; w tym przykładzie rysuje krój modułu jako model różne Aby móc zastosować oddzielne tekstury do każdej powierzchni później.  
  
 [!code-csharp[3doverview#3DOverview3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>   
## <a name="applying-materials-to-the-model"></a>Stosowanie materiały do modelu  
  
 Siatki wyglądały jak obiekt trójwymiarowy musi on mieć zastosowane tekstury, aby pokrywał obszar zdefiniowany przez jego wierzchołki i trójkąty, dzięki czemu może być włączone i chroniony przez aparat. W [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], możesz użyć <xref:System.Windows.Media.Brush> klasy do stosowania kolorów, wzorce, gradientach lub innej zawartości visual do obszarów ekranu.  Wygląd [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obiektów, jednak jest funkcją modelu oświetlenia, nie tylko z kolor lub deseń zastosowanych do nich. Obiekty w świecie rzeczywistym jasnego inaczej w zależności od jakości ich powierzchni: błyszczący i obiektowi błyszczący nie wyglądają tak samo jak nierównej lub matowy powierzchni., a niektóre obiekty wydaje się do przyjęcia światło, podczas gdy inne jasny. Można zastosować takich samych pędzle, aby [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obiektów, które można zastosować do [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] obiektów, ale nie można zastosować je bezpośrednio.  
  
 Aby zdefiniować właściwości powierzchni modelu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa <xref:System.Windows.Media.Media3D.Material> klasy abstrakcyjnej. Konkretnych podklas materiału określić pewne cechy wygląd powierzchni modelu, a każdy oferuje również właściwość pędzla, do którego można przekazać SolidColorBrush, TileBrush lub VisualBrush.  
  
-   <xref:System.Windows.Media.Media3D.DiffuseMaterial>Określa, że pędzla zostaną zastosowane do modelu tak, jakby modelu zostały włączone rozpraszająco. Przy użyciu DiffuseMaterial najbardziej podobny przy użyciu pędzle bezpośrednio na [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] modeli; nie powierzchni modelu nie jasnego jako jednak obiektowi błyszczący.  
  
-   <xref:System.Windows.Media.Media3D.SpecularMaterial>Określa, że pędzla zostaną zastosowane do modelu tak, jakby były powierzchni modelu twardym lub obiektowi błyszczący i stanie odzwierciedlające najważniejsze funkcje. Można ustawić stopień, na które sugeruje tekstury jakości odbicia lub "świecisz", określając wartość <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> właściwości.  
  
-   <xref:System.Windows.Media.Media3D.EmissiveMaterial>Umożliwia określenie, że zostanie zastosowana tekstury, tak, jakby modelu zostały emitowanie światła równości na kolor pędzla. To nie oznacza, że model światło; jednak będzie uczestniczyć inaczej w przesłanianie niż po teksturą DiffuseMaterial lub SpecularMaterial.  
  
 W celu poprawy wydajności powierzchnie z <xref:System.Windows.Media.Media3D.GeometryModel3D> (tych powierzchni, które są poza widoku, ponieważ znajdują się w przeciwną stronę modelu z aparatu fotograficznego) są ubitych z sceny.  Aby określić <xref:System.Windows.Media.Media3D.Material> Aby zastosować wszelkie niepożądane obiekty za modelu, takie jak płaszczyźnie, ustaw modelu <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> właściwości.  
  
 Do osiągnięcia niektórych powierzchni jakości, takie jak efekty świecącego lub odbicia, można zastosować wiele różnych pędzli modelu w przedziale czasu. Można zastosować i ponowne użycie wielu materiałów za pomocą <xref:System.Windows.Media.Media3D.MaterialGroup> klasy. Element podrzędny obiekt MaterialGroup są stosowane najpierw do ostatniego w wielu przebiegach renderowania.  
  
 W poniższych przykładach kodu pokazano, jak zastosować pełny kolor i rysowanie jako pędzle, aby [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modeli.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  
 [!code-xaml[3doverview#3DOverview3DN9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
  
 [!code-csharp[3doverview#3DOverview3DN8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
 [!code-vb[3doverview#3DOverview3DN8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>   
## <a name="illuminating-the-scene"></a>Oświetlenia sceny  
 Świateł w [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] do grafiki, co zrobić w świecie rzeczywistym świateł: one uwidaczniania powierzchni. Więcej do punktu, świateł ustalić, jaka część sceny zostaną uwzględnione w projekcji. Lekkie obiekty w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tworzenia szerokiej gamy efekty jasnym i w tle i są modelowane zachowanie różnych świateł rzeczywistych. Musi zawierać co najmniej jeden światła w sceny lub żadnych modeli będą widoczne.  
  
 Następujące świateł pochodzi od klasy podstawowej <xref:System.Windows.Media.Media3D.Light>:  
  
-   <xref:System.Windows.Media.Media3D.AmbientLight>: Zawiera oświetlenia zewnętrznego, który świecą wszystkie obiekty jednolicie niezależnie od ich lokalizacji i orientacji.  
  
-   <xref:System.Windows.Media.Media3D.DirectionalLight>: Świeci jak oddalonych źródła światła.  Ma światła kierunkowe <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> określony jako Vector3D, ale nie w określonej lokalizacji.  
  
-   <xref:System.Windows.Media.Media3D.PointLight>: Świeci jak pobliskich źródła światła. PointLights mają pozycję i rzutowania światła z tej lokalizacji. W zależności od ich pozycji i odległość względem światła podświetlonych obiekty sceny. <xref:System.Windows.Media.Media3D.PointLightBase>przedstawia <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> właściwość, która określa, po przekroczeniu którego modeli zostanie nie powodować podświetlenie światła odległości. PointLight udostępnia również tłumienie właściwości, które określają sposób intensywność światła zmniejsza odległości. Można określić stałej, liniowego lub kwadratową potrzeby interpolacji do osłabienia światła.  
  
-   <xref:System.Windows.Media.Media3D.SpotLight>: Dziedziczy <xref:System.Windows.Media.Media3D.PointLight>. Światła punktowe oświetlenia jak PointLight i pozycji i kierunku. One projektu światła w obszarze stożkowym kształcie ustawione przez <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> i <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> określono w stopniach właściwości.  
  
 Świateł są <xref:System.Windows.Media.Media3D.Model3D> obiekty, dzięki czemu może przekształcić i animowania właściwości światła, łącznie z pozycji, kolorów, kierunku i zakresu.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>   
## <a name="transforming-models"></a>Przekształcanie modeli  
 Podczas tworzenia modeli, mają one określonej lokalizacji na scenie. Do tych modeli przenoszenia sceny, obracanie lub zmienić ich rozmiar nie jest praktyczne zmienić wierzchołków, które definiują samych modeli.  Zamiast tego po prostu jako w [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], należy zastosować przekształcenia do modeli.  
  
 Każdy obiekt modelu ma <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> właściwości, z którego można przenieść, ponownie ustawić orientację lub zmienić rozmiar modelu.  Podczas stosowania przekształcenia skutecznie przesunięcia wszystkie punkty modelu niezależnie od wektora lub wartość określoną przez transformacji. Innymi słowy, zostały przekształcone przestrzeni współrzędnych, w którym model jest zdefiniowane ("model miejsca"), ale nie zostały zmienione wartości, które tworzą geometrii modelu w układzie współrzędnych całej sceny ("miejsca na świecie").  
  
 Aby uzyskać więcej informacji na temat przekształcania modeli, zobacz [3-omówienie przekształcenia](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md).  
  
<a name="animations"></a>   
## <a name="animating-models"></a>Animowanie modeli  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Implementacji uczestniczy w tym samym systemie harmonogram i animacji jako [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafiki. Innymi słowy Aby animować 3-sceny, animowania właściwości jego modeli. Jest możliwe do animowania właściwości elementów podstawowych bezpośrednio, ale zazwyczaj ułatwia animować transformacje, których zmiana pozycji i wyglądu modeli. Ponieważ przekształcenia można zastosować do <xref:System.Windows.Media.Media3D.Model3DGroup> obiektów oraz poszczególnych modeli, można zastosować jeden zestaw animacji elementu podrzędnego Model3DGroup i inny zestaw animacji grupy obiektów podrzędnych. Można również uzyskać różne efekty wizualne przez animowania właściwości oświetlenia Twojej sceny. Na koniec można animować projekcji się przez animację pozycji kamery lub polu widoku. Informacje o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] harmonogram i animacji systemu, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md), [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md), i [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)tematów.  
  
 Aby animować obiektu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], Tworzenie osi czasu, zdefiniuj animacji (która jest naprawdę zmiany niektórych wartości właściwości wraz z upływem czasu) i określ właściwość, do którego należy zastosować animacji. Ponieważ wszystkie obiekty w [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sceny są elementami podrzędnymi <xref:System.Windows.Controls.Viewport3D>, właściwości właściwości Viewport3D są właściwości objęci żadnych animacji, które chcesz zastosować do sceny.  
  
 Załóżmy, że chcesz utworzyć model wydają się luzu w miejscu. Można także zastosować <xref:System.Windows.Media.Media3D.RotateTransform3D> w modelu i animować osi jego obrotu z jednego wektora do innego. Poniższy przykład kodu pokazuje stosowania Vector3DAnimation do właściwości osi Rotation3D przekształcania, przy założeniu RotateTransform3D jest jednym z kilku transformacji zastosowanych do modelu z TransformGroup.  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>   
## <a name="add-3-d-content-to-the-window"></a>Dodawanie zawartości 3-w oknie  
 Do renderowania sceny, Dodaj modele i świateł do <xref:System.Windows.Media.Media3D.Model3DGroup>, a następnie ustaw <xref:System.Windows.Media.Media3D.Model3DGroup> jako <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> z <xref:System.Windows.Media.Media3D.ModelVisual3D>. Dodaj <xref:System.Windows.Media.Media3D.ModelVisual3D> do <xref:System.Windows.Controls.Viewport3D.Children%2A> kolekcji <xref:System.Windows.Controls.Viewport3D>. Dodaj kamery do <xref:System.Windows.Controls.Viewport3D> przez ustawienie jej <xref:System.Windows.Controls.Viewport3D.Camera%2A> właściwości.  
  
 Na koniec należy dodać <xref:System.Windows.Controls.Viewport3D> do okna. Gdy <xref:System.Windows.Controls.Viewport3D> jest uwzględniona jako zawartość elementu układu, takich jak kanwy, określ rozmiar Viewport3D przez ustawienie jej <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> właściwości (dziedziczone z <xref:System.Windows.FrameworkElement>).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Viewport3D>  
 <xref:System.Windows.Media.Media3D.PerspectiveCamera>  
 <xref:System.Windows.Media.Media3D.DirectionalLight>  
 <xref:System.Windows.Media.Media3D.Material>  
 [Przekształcenia 3-omówienie](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md)  
 [Zmaksymalizować wydajność 3D WPF](../../../../docs/framework/wpf/graphics-multimedia/maximize-wpf-3d-performance.md)  
 [Tematy porad](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-how-to-topics.md)  
 [Kształty i podstawowe rysunek w omówieniu WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
