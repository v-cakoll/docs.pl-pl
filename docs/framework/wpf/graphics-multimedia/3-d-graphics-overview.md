---
title: Przegląd Grafika 3-D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D graphics [WPF]
- graphics [WPF], 3-D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: 7f9f3d21d14a8eac862186a41bd8771cffb7375c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352870"
---
# <a name="3-d-graphics-overview"></a>Przegląd Grafika 3-D
<a name="introduction"></a> [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Funkcji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umożliwia deweloperom rysowania, przekształcania i animować grafika 3-D w kodzie znaczników i procedur. Deweloperzy mogą łączyć [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] i [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafiki, tworzyć zaawansowane kontrolki, ilustrują złożonych danych i poszerz możliwości użytkownika środowisko interfejsu aplikacji. [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Obsługa w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie ma na celu zapewnienie platformy programowania gier w pełni funkcjonalne. Ten temat zawiera omówienie [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system grafiki.  
 
  
<a name="threed_in_2d"></a>   
## <a name="3-d-in-a-2-d-container"></a>3-w w kontenerze 2-D  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Grafika zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są hermetyzowane w elemencie <xref:System.Windows.Controls.Viewport3D>, mogą uczestniczyć w strukturze dwuwymiarową elementu. System grafiki traktuje <xref:System.Windows.Controls.Viewport3D> jako dwuwymiarową elementu wizualnego, takich jak wiele innych osób w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Viewport3D> Funkcje jako okno — okienko ekranu — na scenie trójwymiarowej. Dokładniej, jest powierzchni, na którym [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] jest rzutowany sceny.  
  
 W konwencjonalnych [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] aplikacji, użyj <xref:System.Windows.Controls.Viewport3D> tak jak inny element kontenera, takich jak siatki lub kanwy.  Chociaż można używać <xref:System.Windows.Controls.Viewport3D> z innymi [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] Rysowanie obiektów w ten sam wykres scen, nie interpenetrate [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] i [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obiektów w ramach <xref:System.Windows.Controls.Viewport3D>.  Ten temat koncentruje się na sposób rysowania [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] grafiki wewnątrz <xref:System.Windows.Controls.Viewport3D>.  
  
<a name="coord_space"></a>   
## <a name="3-d-coordinate-space"></a>3-przestrzeni współrzędnych  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Współrzędnych dla [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafiki lokalizuje punkt początkowy w lewym górnym rogu obszaru renderowania (zazwyczaj ekranu). W [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] system dodatnie wartości osi x mają kontynuować po prawej stronie i wartości dodatnie y przejść w dół.  W [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] współrzędnych, jednak źródła znajduje się w środku obszaru renderowania przy użyciu wartości dodatnie osi x z prawej strony, ale wartości dodatnie y kontynuowanie zamiast tego w górę i na zewnątrz wartości dodatnie osi z ze źródła do przeglądarki.  
  
 ![Współrzędnych](./media/coordsystem-1.png "CoordSystem-1")  
Reprezentacje konwencjonalne układ współrzędnych 2W i 3W  
  
 Obszar zdefiniowany przez te osi jest nieruchomy układem odniesienia dla [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obiekty w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tworzenie modeli, w tym miejscu i utworzyć światła i aparaty fotograficzne, aby je wyświetlić, warto odróżnienia lokalnego układem odniesienia tworzone dla każdego modelu, jeśli zastosujesz przekształcenia do niego stacjonarnych układem odniesienia lub "miejsca na świecie,". Pamiętaj również, że obiekty w przestrzeni świata mogą różnić się całkowicie lub być niewidoczne na wszystkich, w zależności od jasny i aparatu ustawienia, ale pozycja kamery nie zmienia lokalizację obiektów w przestrzeni świata.  
  
<a name="cameras"></a>   
## <a name="cameras-and-projections"></a>Aparaty fotograficzne i projekcji  
 Deweloperzy, którzy pracują w [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] są przyzwyczajeni do pozycjonowania Rysowanie w nim elementów podstawowych na ekranie dwuwymiarową. Po utworzeniu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sceny, ważne jest, aby pamiętać naprawdę tworzenia [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] reprezentacja [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obiektów. Ponieważ [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sceny wygląda inaczej w zależności od onlooker punktu widzenia, należy określić tego punktu widzenia. <xref:System.Windows.Media.Media3D.Camera> Klasa służy do określania tego punktu widzenia dla [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sceny.  
  
 Innym sposobem, aby zrozumieć, jak [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sceny jest reprezentowana w [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] powierzchni jest poprzez opisanie sceny jako projekcji na powierzchnię wyświetlania. <xref:System.Windows.Media.Media3D.ProjectionCamera> Umożliwia określenie różnych projekcje i ich właściwości w celu zmiany sposobu czytania onlooker [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modeli. A <xref:System.Windows.Media.Media3D.PerspectiveCamera> określa rzutowanie, na którym foreshortens sceny.  Innymi słowy <xref:System.Windows.Media.Media3D.PerspectiveCamera> zawiera perspektywę punktu podczas wykonywania.  Można określić położenie kamery w układzie współrzędnych sceny, kierunku i pole widzenia aparatu i wektor definiujący kierunek "up" w scenie. Na poniższym diagramie przedstawiono <xref:System.Windows.Media.Media3D.PerspectiveCamera>w projekcji.  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> i <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> właściwości <xref:System.Windows.Media.Media3D.ProjectionCamera> ograniczyć zakres aparatu projekcji. Aparaty fotograficzne, mogą być umieszczony w dowolnym miejscu w scenie, istnieje możliwość, że aparat, który faktycznie został umieszczony wewnątrz modelu lub bardzo blisko modelu, co utrudnia odróżniać obiekty prawidłowo.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> Pozwala określić minimalną odległość z aparatu, po przekroczeniu którego będzie nie rysowany obiektów.  Z drugiej strony <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> umożliwia określenie odległości od aparatu po przekroczeniu których obiektów nie będą pobierane, który zapewnia, że obiektów zbyt daleko rozpoznawalnych nie będą uwzględniane w scenie.  
  
 ![Ustawienia aparatu fotograficznego](./media/coordsystem-6.png "CoordSystem 6")  
Położenie kamery  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera> Określa prostopadły rzut [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modelu do [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] visual powierzchni. Podobnie jak inne aparaty fotograficzne Określa położenie wyświetlania kierunku i kierunek "w górę". W odróżnieniu od <xref:System.Windows.Media.Media3D.PerspectiveCamera>, jednak <xref:System.Windows.Media.Media3D.OrthographicCamera> opisuje projekcji, który nie obejmuje foreshortening perspektywy. Innymi słowy <xref:System.Windows.Media.Media3D.OrthographicCamera> Opisuje okno wyświetlania, którego boki są równolegle, zamiast jednego którego boki spotykają się w punkcie aparatu. Na poniższej ilustracji przedstawiono ten sam model, jak wyświetlać za pomocą <xref:System.Windows.Media.Media3D.PerspectiveCamera> i <xref:System.Windows.Media.Media3D.OrthographicCamera>.  
  
 ![Rzutowanie prostopadłe i perspektywiczne](./media/camera-projections4.png "Camera_projections4")  
Perspektywy i prostopadły prognozy  
  
 Poniższy kod przedstawia niektóre ustawienia typowe aparatu.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>   
## <a name="model-and-mesh-primitives"></a>Model i podstawowych siatki  
  
 <xref:System.Windows.Media.Media3D.Model3D> jest abstrakcyjna klasa bazowa, która reprezentuje ogólnego [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obiektu. Tworzenie [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scen, potrzebujesz niektórych obiektów, aby wyświetlić i obiekty, które tworzą wykres scen pochodzić od <xref:System.Windows.Media.Media3D.Model3D>. Obecnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje modelowania geometrii za pomocą <xref:System.Windows.Media.Media3D.GeometryModel3D>. <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> Właściwość ten model ma siatki pierwotnych.  
  
 Budowanie modelu, Rozpocznij od utworzenia elementu podstawowego lub siatki. A [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] pierwotnych to zbiór wierzchołki, które tworzą pojedynczy [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] jednostki. Większość [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] systemy zapewniają podstawowych wzorowana na figurę zamkniętą najprostszym: trójkąt definicją wierzchołków trzy.  Ponieważ coplanar trzy punkty trójkąta, możesz kontynuować dodawanie trójkąty w celu modelowania więcej złożonych kształtów, nazywanych siatki.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Udostępnia obecnie system <xref:System.Windows.Media.Media3D.MeshGeometry3D> klasy, która umożliwia określenie dowolnego geometrii; obecnie nie obsługuje wstępnie zdefiniowanych [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] podstawowych, takich jak obszary i formularze trzeciego stopnia. Rozpocznij tworzenie <xref:System.Windows.Media.Media3D.MeshGeometry3D> przez określenie listy wierzchołków trójkąt jako jego <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> właściwości. Każdy wierzchołek jest określony jako <xref:System.Windows.Media.Media3D.Point3D>.  (W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], określić tę właściwość jako listę liczb pogrupowane w trzy, które reprezentują współrzędne każdego wierzchołka.) W zależności od jego geometrii Twojej sieci może składać się z wielu trójkątów, niektóre z nich udostępnianie tych samych rogi (wierzchołków). Aby narysować siatkę poprawnie, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] potrzebuje informacji o tym, które wierzchołki są współużytkowane przez które trójkąty. Te informacje zostaną podane, określając listę wskaźników trójkąt przy użyciu <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> właściwości. Ta lista określa kolejność, w jakiej punkty określone w <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listy określi trójkąt.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 W powyższym przykładzie <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> lista określa osiem wierzchołki, aby zdefiniować moduł w kształcie siatki. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> Właściwość określa listę grup dwunastu trzech indeksów.  Każdy numer na liście odnosi się do przesunięcie <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listy.  Na przykład, określony przez pierwsze trzy wierzchołki <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listy są (1,1,0) (0,1,0) i (0,0,0). Pierwszych trzech indeksów, określony przez <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> listy są 0, 2 i 1, które odpowiadają pierwszym, trzeci i drugie punktów w <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listy. W rezultacie pierwszy trójkąt, który tworzy model sześcianu będzie składać się z (1,1,0) do (0,1,0) do (0,0,0), a pozostałe trójkąty jedenaście zależą podobnie.  
  
 Możesz kontynuować definiowania modelu, określając wartości <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> i <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> właściwości.  Do renderowania powierzchni modelu, system grafiki wymaga informacji o tym, które skierowany w dowolnym danym trójkąt kierunek powierzchni. Używa tych informacji do przeprowadzania obliczeń oświetlenia dla modelu: powierzchniach, które stają się bezpośrednio do źródła światła pojawiają się jaśniejszy niż pod kątem od światła. Chociaż [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można określić wektory normalne domyślny za pomocą współrzędnych pozycji, można również określić różne wektory normalne zbliżenie wygląd krzywych powierzchni.  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> Właściwość określa zbiór <xref:System.Windows.Point>s, który poinformować system grafiki sposób mapowania współrzędne, które określają, jak rysowane tekstury wierzchołków siatkę. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> są określane jako wartość z zakresu od 0 do 1 (włącznie).  Podobnie jak w przypadku <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> właściwości, można obliczyć system grafiki, domyślnie współrzędne tekstury, ale można także ustawić różne tekstury współrzędne do kontrolowania mapowanie teksturę, która zawiera część wzorca powtarzające się, na przykład. Więcej informacji na temat współrzędnych tekstury można znaleźć w kolejnych tematach lub w zestawie SDK zarządzanego Direct3D.  
  
 Poniższy przykład przedstawia sposób tworzenia jednej powierzchni modelu modułu w kodzie proceduralnym. Należy pamiętać, że można narysować cały moduł jako pojedynczy GeometryModel3D; w tym przykładzie rysuje Ściana sześcianu jako odrębne model, aby można było zastosować oddzielne tekstury do każdej twarzy później.  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>   
## <a name="applying-materials-to-the-model"></a>Stosowanie materiałów do modelu  
  
 Siatka wygląd obiektu trójwymiarowego musi on mieć zastosowane tekstury, aby pokrywał powierzchni zdefiniowany przez jego wierzchołki i trójkąty, dzięki czemu mogą być świeci i chroniony przez aparat. W [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], możesz użyć <xref:System.Windows.Media.Brush> klasy dotyczą kolorów, wzorce, gradientów lub innych zawartości wizualnej powierzchni ekranu.  Wygląd [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obiektów, jednak jest funkcją modelu oświetlenia, nie tylko z kolor lub deseń zastosowanych do nich. Obiekty w świecie rzeczywistym jasnego inaczej w zależności od jakość ich powierzchni: błyszczący i shiny powierzchnie nie wyglądają tak samo jak nierównej lub otoczki powierzchnie, a niektóre obiekty wydaje się, że ochrony przed rozproszonymi światła, podczas gdy inne jasna. Można zastosować ten sam pędzle, aby [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obiektów, które można zastosować do [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] obiektów, ale nie można zastosować je bezpośrednio.  
  
 Zdefiniowanie powierzchni modelu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa <xref:System.Windows.Media.Media3D.Material> klasy abstrakcyjnej. Konkretnych podklas materiału określić pewne cechy wygląd powierzchni modelu, a także każda właściwość pędzla, do którego można przekazać SolidColorBrush, TileBrush lub VisualBrush.  
  
-   <xref:System.Windows.Media.Media3D.DiffuseMaterial> Określa, że pędzel zostaną zastosowane do modelu tak, jakby modelu zostały włączone rozproszenia. Za pomocą DiffuseMaterial najbardziej przypomina przy użyciu pędzli bezpośrednio na [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] modeli; powierzchni modelu nie odzwierciedlają światła, jak jednak shiny.  
  
-   <xref:System.Windows.Media.Media3D.SpecularMaterial> Określa, że pędzel zostaną zastosowane do modelu tak, jakby powierzchni modelu zostały twardym lub shiny, umożliwiający Odbijanie światła. Stopień, w którym sugeruje tekstury odbijającą jakości lub "lśnienia", można ustawić, określając wartość dla <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> właściwości.  
  
-   <xref:System.Windows.Media.Media3D.EmissiveMaterial> Pozwala określić, że tekstury, będzie stosowany, tak, jakby modelu zostały emitowania równy jasny kolor pędzla. To nie oznacza, że model światła; jednak będzie uczestniczyć inaczej w przesłanianie, niż gdyby teksturę za pomocą DiffuseMaterial lub SpecularMaterial.  
  
 Aby uzyskać lepszą wydajność i powierzchnie, z <xref:System.Windows.Media.Media3D.GeometryModel3D> (te powierzchnie, które są poza widokiem, ponieważ są one w przeciwną stronę modelu z aparatu fotograficznego) są ubitych z sceny.  Aby określić <xref:System.Windows.Media.Media3D.Material> dotyczą odrzucanie tylnych modelu, takich jak płaszczyznę modelu zestawu <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> właściwości.  
  
 Uzyskanie niektórych klas powierzchni, takich jak świecącymi lub odbijającą skutki, można zastosować wiele różnych pędzli do modelu w odstępie czasu. Można zastosować i ponowne użycie wielu materiałów za pomocą <xref:System.Windows.Media.Media3D.MaterialGroup> klasy. Elementy podrzędne MaterialGroup są stosowane najpierw ostatni w wielu przebiegów renderowania.  
  
 W poniższych przykładach kodu pokazano, jak stosowanie jednolitego koloru i rysowania jako pędzle, aby [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modeli.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  
 [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
  
 [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
 [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>   
## <a name="illuminating-the-scene"></a>Dostępne na scenie  
 Świateł w [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] do grafiki, co zrobić w świecie rzeczywistym światła: ich widoczności powierzchnie. Więcej z punktem światła ustalić, jaka część sceny zostaną uwzględnione w projekcji. Lekkie obiekty w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tworzyć różne efekty jasny i w tle i są wzorowane na zachowanie różnych rzeczywistych światła. Musi zawierać co najmniej jedno źródło światła sceny lub brak modeli będą widoczne.  
  
 Następujące kontrolki pochodzi z klasy bazowej <xref:System.Windows.Media.Media3D.Light>:  
  
-   <xref:System.Windows.Media.Media3D.AmbientLight>: Udostępnia oświetleniem otoczenia, który świeci wszystkie obiekty w jednolity sposób niezależnie od ich lokalizacji i orientacji.  
  
-   <xref:System.Windows.Media.Media3D.DirectionalLight>: Świeci, takie jak odległości źródła światła.  Masz światła kierunkowego <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> określony jako Vector3D, ale nie określonej lokalizacji.  
  
-   <xref:System.Windows.Media.Media3D.PointLight>: Świeci, takich jak pobliskich źródła światła. PointLights stanowiska i rzutowania światła z tej pozycji. W zależności od ich pozycji i odległość względem światła podświetlonych obiektów w scenie. <xref:System.Windows.Media.Media3D.PointLightBase> udostępnia <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> właściwość, która określa odległość, po przekroczeniu których modeli będzie nie być podświetlenie światła. PointLight udostępnia również tłumienie właściwości, które określają, jak zmniejsza się intensywność światła odległości. Można określić stałe liniowej i drugiego stopnia interpolations dla tłumienie światła.  
  
-   <xref:System.Windows.Media.Media3D.SpotLight>: dziedziczy <xref:System.Windows.Media.Media3D.PointLight>. W dniach oświetlenia, takich jak PointLight i położenie i kierunku. One projektu światła w kształcie stożek ustawionego <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> i <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> określonych w stopniach właściwości.  
  
 Światła są <xref:System.Windows.Media.Media3D.Model3D> obiektów, dzięki czemu może przekształcić i animować właściwości światła, w tym pozycji, kolorów, kierunku i zakresu.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>   
## <a name="transforming-models"></a>Przekształcanie modeli  
 Podczas tworzenia modeli mają one określonej lokalizacji w scenie. Przenoszenie tych modeli w scenie, przenosić je lub zmieniać ich rozmiar nie jest praktyczne zmienić wierzchołki, które definiują samych modeli.  Zamiast tego po prostu jak [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], zastosujesz przekształcenia do modeli.  
  
 Każdy obiekt modelu ma <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> właściwości, za pomocą którego można przenosić, ponownie poznaniu lub zmienić rozmiar modelu.  Po zastosowaniu przekształcenia skutecznie przesunięcia wszystkie punkty modelu niezależnie od wektora lub wartość określoną przez transformacji. Innymi słowy, zostały przekształcone współrzędnych miejsca, w którym model jest zdefiniowana, ("model miejsca"), ale nie zostały zmienione wartości, które tworzą geometrii modelu w układzie współrzędnych całej sceny ("miejsca na świecie").  
  
 Aby uzyskać więcej informacji na temat przekształcania modeli, zobacz [Przegląd przekształcenia 3-D](3-d-transformations-overview.md).  
  
<a name="animations"></a>   
## <a name="animating-models"></a>Animowanie modeli  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] Implementacji bierze udział w tym samym systemie czasu i animacji, co [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafiki. Oznacza to aby animować scenę 3-D, animować właściwości jego modeli. Można animować właściwości elementów podstawowych bezpośrednio, ale jest zazwyczaj łatwiejsze animować przekształceń, które Zmienianie położenia lub wyglądu modeli. Ponieważ przekształcenia można zastosować do <xref:System.Windows.Media.Media3D.Model3DGroup> obiektów oraz poszczególne modele, istnieje możliwość, stosuje się jeden zestaw animacji do elementu podrzędnego Model3DGroup i inny zestaw animacji do grupy obiektów podrzędnych. Można również uzyskać różne efektów wizualnych przez animowanie właściwości oświetlenia swoje sceny. Na koniec można animować projekcji, sama przez animowanie położenia kamery lub pole widzenia. Informacje o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system chronometrażu i animacji, zobacz [Przegląd animacja](animation-overview.md), [Przegląd Scenorysy](storyboards-overview.md), i [Przegląd obiektów Freezable](../advanced/freezable-objects-overview.md)tematów.  
  
 Animowanie obiektu w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], Tworzenie osi czasu, zdefiniuj animacji (czyli tak naprawdę zmianę niektórych wartości właściwości wraz z upływem czasu) i określa właściwość, do którego należy zastosować animacji. Ponieważ wszystkie obiekty w [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sceny są elementami podrzędnymi <xref:System.Windows.Controls.Viewport3D>, właściwości objęte wszystkie animacje, który chcesz zastosować do sceny są właściwości właściwości Viewport3D.  
  
 Załóżmy, że chcesz, aby model prawdopodobnie luzu w miejscu. Można także zastosować <xref:System.Windows.Media.Media3D.RotateTransform3D> modelu, animować osi jego obrotu z wektora jednego do drugiego. Poniższy przykład kodu pokazuje, stosując Vector3DAnimation właściwości osi Rotation3D transformacji, zakładając, że RotateTransform3D, aby być jednym z kilku zastosowane do modelu z TransformGroup przekształcenia.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>   
## <a name="add-3-d-content-to-the-window"></a>Dodawanie zawartości 3-w do okna  
 Renderowanie sceny, Dodawanie modeli i świateł do <xref:System.Windows.Media.Media3D.Model3DGroup>, a następnie ustaw <xref:System.Windows.Media.Media3D.Model3DGroup> jako <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> z <xref:System.Windows.Media.Media3D.ModelVisual3D>. Dodaj <xref:System.Windows.Media.Media3D.ModelVisual3D> do <xref:System.Windows.Controls.Viewport3D.Children%2A> zbiór <xref:System.Windows.Controls.Viewport3D>. Dodaj z kamer monitorujących w celu <xref:System.Windows.Controls.Viewport3D> , ustawiając jego <xref:System.Windows.Controls.Viewport3D.Camera%2A> właściwości.  
  
 Na koniec należy dodać <xref:System.Windows.Controls.Viewport3D> do okna. Gdy <xref:System.Windows.Controls.Viewport3D> jest uwzględniony, ponieważ zawartość elementu układu, takich jak kanwy, określić rozmiar Viewport3D, ustawiając jego <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> właściwości (odziedziczone <xref:System.Windows.FrameworkElement>).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [Przekształcenia 3D — przegląd](3-d-transformations-overview.md)
- [Maksymalizowanie wydajności 3D WPF](maximize-wpf-3d-performance.md)
- [Tematy z instrukcjami](3-d-graphics-how-to-topics.md)
- [Kształty i podstawowe rysowanie w programie WPF — przegląd](shapes-and-basic-drawing-in-wpf-overview.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
