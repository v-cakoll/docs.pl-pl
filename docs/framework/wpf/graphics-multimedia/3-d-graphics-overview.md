---
title: Omówienie grafiki 3D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D graphics [WPF]
- graphics [WPF], 3D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: e4918f7737bbe57a4f29c6c5cff1099f4f21674b
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291816"
---
# <a name="3d-graphics-overview"></a>Omówienie grafiki 3D
<a name="introduction"></a>Funkcja 3D umożliwia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] deweloperom rysowanie, przekształcanie i animowanie grafiki 3D zarówno w znacznikach, jak i w kodzie proceduralnym. Deweloperzy mogą łączyć grafikę 2D i 3D w celu tworzenia bogatych formantów, dostarczania złożonych ilustracji danych lub ulepszania środowiska użytkownika interfejsu aplikacji. Obsługa 3D [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie jest przeznaczona do zapewnienia w pełni funkcjonaj platformy tworzenia gier. W tym temacie przedstawiono omówienie funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3D w systemie graficznym.  

<a name="threed_in_2d"></a>
## <a name="3d-in-a-2d-container"></a>3D w kontenerze 2D  
 Zawartość grafiki 3D jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hermetyzowana <xref:System.Windows.Controls.Viewport3D>w elemencie, który może uczestniczyć w strukturze elementów dwuwymiarowych. System graficzny traktuje <xref:System.Windows.Controls.Viewport3D> jako dwuwymiarowy element wizualny, jak wiele innych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Viewport3D>działa jako okno — rzutnia — w scenę trójwymiarową. Dokładniej, jest to powierzchnia, na której wyświetlana jest scena 3D.  
  
 W konwencjonalnej aplikacji 2D użyj, <xref:System.Windows.Controls.Viewport3D> podobnie jak inny element kontenera, taki jak Siatka lub Kanwa.  Chociaż można <xref:System.Windows.Controls.Viewport3D> używać z innymi obiektami rysunkowymi 2D na tym samym wykresie sceny, nie <xref:System.Windows.Controls.Viewport3D>można przenikać obiektów 2D i 3D w programie .  W tym temacie skupimy się na tym, jak rysować grafikę 3D wewnątrz <xref:System.Windows.Controls.Viewport3D>.  
  
<a name="coord_space"></a>
## <a name="3d-coordinate-space"></a>Przestrzeń współrzędnych 3D  
 Układ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] współrzędnych grafiki 2D lokalizuje początek układu współrzędnych w lewym górnym rogu obszaru renderowania (zazwyczaj na ekranie). W systemie 2D dodatnie wartości osi x przebiegają w prawo, a dodatnie wartości osi y przebiegają w dół.  Jednakże w układzie współrzędnych 3D początek układu współrzędnych znajduje się w środku obszaru renderowania, z dodatnimi wartościami osi X przechodzącymi w prawo, ale dodatnie wartości osi Y, które zamiast tego postępują w górę, a dodatnie wartości osi Z wychodzą na zewnątrz od początku układu współrzędnego, w kierunku widza.  
  
 ![Układy współrzędnych](./media/coordsystem-1.png "CoordSystem-1")  
Konwencjonalne reprezentacje układu współrzędnych 2D i 3D  
  
 Przestrzeń zdefiniowana przez te osie jest nieruchomą ramką [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]odniesienia dla obiektów 3D w . Podczas tworzenia modeli w tej przestrzeni i tworzenia świateł i kamer, aby je wyświetlić, warto odróżnić tę stacjonarną ramkę odniesienia lub "przestrzeń świata" od lokalnej ramki odniesienia utworzonej dla każdego modelu po zastosowaniu do niego przekształceń. Pamiętaj również, że obiekty w przestrzeni świata mogą wyglądać zupełnie inaczej lub nie być w ogóle widoczne, w zależności od ustawień światła i kamery, ale położenie kamery nie zmienia położenia obiektów w przestrzeni świata.  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>Kamery i projekcje  
 Deweloperzy, którzy pracują w 2D są przyzwyczajeni do pozycjonowania ćwierczy rysunek na ekranie dwuwymiarowym. Podczas tworzenia sceny 3D należy pamiętać, że naprawdę tworzysz reprezentację 2D obiektów 3D. Ponieważ scena 3D wygląda inaczej w zależności od punktu widzenia obserwatora, należy określić ten punkt widzenia. Klasa <xref:System.Windows.Media.Media3D.Camera> umożliwia określenie tego punktu widzenia dla sceny 3D.  
  
 Innym sposobem zrozumienia, w jaki sposób scena 3D jest reprezentowana na powierzchni 2D, jest opisanie sceny jako projekcji na powierzchnię widokową. Umożliwia <xref:System.Windows.Media.Media3D.ProjectionCamera> określenie różnych projekcji i ich właściwości, aby zmienić sposób, w jaki obserwator widzi modele 3D. A <xref:System.Windows.Media.Media3D.PerspectiveCamera> określa projekcję, która foreshortens sceny.  Innymi słowy zapewnia <xref:System.Windows.Media.Media3D.PerspectiveCamera> perspektywę punktu zbiegu.  Można określić położenie kamery w przestrzeni współrzędnych sceny, kierunek i pole widzenia kamery oraz wektor definiujący kierunek "w górę" w scenie. Na poniższym diagramie przedstawiono projekcję. <xref:System.Windows.Media.Media3D.PerspectiveCamera>  
  
 I <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> właściwości <xref:System.Windows.Media.Media3D.ProjectionCamera> ograniczenia zakresu projekcji kamery. Ponieważ kamery mogą znajdować się w dowolnym miejscu na scenie, kamera może być faktycznie umieszczona wewnątrz modelu lub bardzo blisko modelu, co utrudnia prawidłowe rozróżnianie obiektów.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>pozwala określić minimalną odległość od kamery, po przekroszeniu której obiekty nie będą rysowane.  Z drugiej <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> strony pozwala określić odległość od kamery, po przekroju której obiekty nie będą rysowane, co zapewnia, że obiekty zbyt daleko, aby były rozpoznawalne, nie zostaną uwzględnione w scenie.  
  
 ![Konfiguracja kamery](./media/coordsystem-6.png "CoordSystem-6")  
Pozycja kamery  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>określa rzut ortogonalny modelu 3D na powierzchnię wizualną 2D. Podobnie jak inne kamery, określa położenie, kierunek wyświetlania i kierunek "w górę". W <xref:System.Windows.Media.Media3D.PerspectiveCamera>przeciwieństwie <xref:System.Windows.Media.Media3D.OrthographicCamera> do , jednak opisuje projekcji, która nie obejmuje perspektywy foreshortening. Innymi słowy, <xref:System.Windows.Media.Media3D.OrthographicCamera> opisuje pole wyświetlania, którego boki są równoległe, zamiast jednego, którego boki spotykają się w punkcie kamery. Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.Media3D.PerspectiveCamera> ten <xref:System.Windows.Media.Media3D.OrthographicCamera>sam model, który był wyświetlany przy użyciu i .  
  
 ![Projekcja ortograficzna i perspektywiczna](./media/camera-projections4.png "Camera_projections4")  
Rzuty perspektywiczne i ortograficzne  
  
 Poniższy kod pokazuje typowe ustawienia aparatu.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>Prymitywy modelu i siatki  
  
 <xref:System.Windows.Media.Media3D.Model3D>jest abstrakcyjną klasą podstawową reprezentującą ogólny obiekt 3D. Aby zbudować scenę 3D, potrzebujesz niektórych obiektów do wyświetlenia, a <xref:System.Windows.Media.Media3D.Model3D>obiekty, które tworzą wykres sceny, pochodzą od . Obecnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje modelowanie geometrii <xref:System.Windows.Media.Media3D.GeometryModel3D>za pomocą . Właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> tego modelu przyjmuje prymitywne siatki.  
  
 Aby utworzyć model, zacznij od utworzenia prymitywnego lub siatki. 3D prymityw jest zbiorem wierzchołków, które tworzą pojedynczy element 3D. Większość systemów 3D zapewnia prymitywy wzorowane na najprostszej zamkniętej postaci: trójkątze zdefiniowanym przez trzy wierzchołki.  Ponieważ trzy punkty trójkąta są współplanarne, można kontynuować dodawanie trójkątów w celu modelowania bardziej złożonych kształtów, zwanych siatkami.  
  
 System [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3D zapewnia obecnie <xref:System.Windows.Media.Media3D.MeshGeometry3D> klasę, która pozwala określić dowolną geometrię; obecnie nie obsługuje wstępnie zdefiniowanych otyminów 3D, takich jak kule i formy sześcienne. Rozpocznij <xref:System.Windows.Media.Media3D.MeshGeometry3D> tworzenie, określając listę wierzchołków trójkąta jako jego <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> właściwości. Każdy wierzchołek jest określony jako . <xref:System.Windows.Media.Media3D.Point3D>  (W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], należy określić tę właściwość jako listę liczb zgrupowanych w trójki, które reprezentują współrzędne każdego wierzchołka. W zależności od geometrii siatka może składać się z wielu trójkątów, z których niektóre mają te same narożniki (wierzchołki). Aby poprawnie narysować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] siatkę, informacje o potrzebach, które wierzchołki są współużytkowane przez trójkąty. Informacje te można podać, określając listę indeksów <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> trójkąta z właściwością. Ta lista określa kolejność, w jakiej <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> punkty określone na liście będą określać trójkąt.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 W poprzednim przykładzie <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> lista określa osiem wierzchołków do zdefiniowania siatki w kształcie sześcianu. Właściwość <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> określa listę dwunastu grup trzech indeksów.  Każdy numer na liście odnosi się <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> do przesunięcia na liście.  Na przykład pierwsze trzy wierzchołki określone przez <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listę to (1,1,0), (0,1,0) i (0,0,0). Pierwsze trzy indeksy określone <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> na liście to 0, 2 i 1, które odpowiadają pierwszemu, trzeciemu i drugiemu punktowi na <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liście. W rezultacie pierwszy trójkąt składający się na model sześcianu będzie składał się z (1,1,0) do (0,1,0) do (0,0,0), a pozostałe jedenaście trójkątów zostanie określone w podobny sposób.  
  
 Można kontynuować definiowanie modelu, określając <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> wartości <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> i właściwości.  Aby renderować powierzchnię modelu, system graficzny potrzebuje informacji o tym, w którym kierunku powierzchnia jest skierowana w danym trójkącie. Wykorzystuje te informacje do obliczeń oświetlenia dla modelu: powierzchnie skierowane bezpośrednio w kierunku źródła światła wydają się jaśniejsze niż te, które są pod kątem od światła. Chociaż [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można określić domyślne normalne wektory za pomocą współrzędnych położenia, można również określić różne normalne wektory, aby przybliżyć wygląd zakrzywionych powierzchni.  
  
 Właściwość <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> określa kolekcję <xref:System.Windows.Point>s, które informują system graficzny, jak mapować współrzędne, które określają, jak tekstura jest rysowana do wierzchołków siatki. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>są określone jako wartość od zera do 1 włącznie.  Podobnie jak <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> w przypadku właściwości, system graficzny może obliczać domyślne współrzędne tekstury, ale można ustawić różne współrzędne tekstury, aby kontrolować mapowanie tekstury, która zawiera na przykład część powtarzającego się wzorca. Więcej informacji na temat współrzędnych tekstur można znaleźć w kolejnych tematach lub w zarządzanym sdk Direct3D.  
  
 W poniższym przykładzie pokazano, jak utworzyć jedną ścianę modelu modułu w kodzie proceduralnym. Można narysować cały moduł jako pojedynczy GeometryModel3D; w tym przykładzie rysuje twarz modułu jako odrębny model w celu zastosowania oddzielnych tekstur do każdej ściany później.  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>'
## <a name="applying-materials-to-the-model"></a>Stosowanie materiałów do modelu  
  
 Aby siatka wyglądała jak obiekt trójwymiarowy, musi mieć zastosowaną teksturę, aby pokryć powierzchnię zdefiniowaną przez jej wierzchołki i trójkąty, aby mogła być oświetlona i rzutowana przez aparat. W 2D <xref:System.Windows.Media.Brush> klasy służy do stosowania kolorów, wzorów, gradientów lub innej zawartości wizualnej do obszarów ekranu.  Wygląd obiektów 3D jest jednak funkcją modelu oświetlenia, a nie tylko koloru lub wzoru zastosowanego do nich. Rzeczywiste obiekty odbijają światło w różny sposób w zależności od jakości ich powierzchni: błyszczące i błyszczące powierzchnie nie wyglądają tak samo jak szorstkie lub matowe powierzchnie, a niektóre obiekty wydają się absorbować światło, podczas gdy inne świecą. Do obiektów 3D, które można zastosować do obiektów 2D, można zastosować wszystkie te same pędzle, ale nie można ich zastosować bezpośrednio.  
  
 Aby zdefiniować właściwości powierzchni modelu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa <xref:System.Windows.Media.Media3D.Material> klasy abstrakcyjnej. Podklasy betonowe Material określają niektóre cechy wyglądu powierzchni modelu, a każda z nich zapewnia również Brush właściwości, do którego można przekazać SolidColorBrush, TileBrush lub VisualBrush.  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial>określa, że pędzel zostanie zastosowany do modelu tak, jakby ten model był podświetlony rozproszono. Korzystanie DiffuseMaterial najbardziej przypomina przy użyciu pędzli bezpośrednio w modelach 2D; powierzchni modelu nie odbija światła tak, jakby błyszczące.  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial>określa, że szczotka zostanie zastosowana do modelu tak, jakby powierzchnia modelu była twarda lub błyszcząca, zdolna do odbijania podświetleń. Można ustawić stopień, w jakim tekstura zasugeruje tę odblaskową <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> jakość lub "połysk", określając wartość właściwości.  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial>pozwala określić, że tekstura zostanie zastosowana tak, jakby model emitował światło równe kolorowi pędzla. To nie sprawia, że model światło; jednak będzie uczestniczyć inaczej w cieniowaniu niż gdyby teksturowane z DiffuseMaterial lub SpecularMaterial.  
  
 Aby uzyskać lepszą wydajność, backfaces of (te <xref:System.Windows.Media.Media3D.GeometryModel3D> twarze, które są poza widoku, ponieważ są one po przeciwnej stronie modelu z kamery) są wybite ze sceny.  Aby określić a, <xref:System.Windows.Media.Media3D.Material> aby zastosować do tylnej powierzchni modelu <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> jak płaszczyzny, należy ustawić właściwość modelu.  
  
 Aby uzyskać pewne właściwości powierzchni, takie jak efekty świecące lub odblaskowe, można zastosować kilka różnych pędzli do modelu z rzędu. Za pomocą <xref:System.Windows.Media.Media3D.MaterialGroup> klasy można zastosować i ponownie użyć wielu materiałów. Dziewki Grupy materiałów są stosowane jako pierwsze do ostatniego w wielu przebiegach renderowania.  
  
 Poniższe przykłady kodu pokazują, jak zastosować jednolity kolor i rysunek jako pędzle do modeli 3D.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  ' [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
 ' [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
  [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>Oświetlanie sceny  
 Światła w grafice 3D robią to, co światła robią w świecie rzeczywistym: sprawiają, że powierzchnie są widoczne. Bardziej do punktu, światła określają, jaka część sceny zostanie uwzględniona w projekcji. Obiekty świetlne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tworzeniu różnych efektów światła i cienia i są wzorowane na zachowaniu różnych rzeczywistych świateł. Uwzględnij co najmniej jedno światło w scenie lub żadne modele nie będą widoczne.  
  
 Następujące światła pochodzą z klasy <xref:System.Windows.Media.Media3D.Light>podstawowej:  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>: Zapewnia oświetlenie otoczenia, które równomiernie oświetla wszystkie obiekty, niezależnie od ich położenia lub orientacji.  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>: Świeci jak odległe źródło światła.  Światła kierunkowe <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> mają określony jako Vector3D, ale nie ma określonej lokalizacji.  
  
- <xref:System.Windows.Media.Media3D.PointLight>: Świeci jak pobliskie źródło światła. PointLights mają pozycję i rzucają światło z tej pozycji. Obiekty w scenie są oświetlone w zależności od ich położenia i odległości w stosunku do światła. <xref:System.Windows.Media.Media3D.PointLightBase>udostępnia <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> właściwość, która określa odległość, po przekroszeniu której modele nie będą oświetlone przez światło. PointLight ujawnia również właściwości tłumienia, które określają, w jaki sposób intensywność światła zmniejsza się z odległości. Można określić interpolacje stałe, liniowe lub kwadratowe dla tłumienia światła.  
  
- <xref:System.Windows.Media.Media3D.SpotLight>: Dziedziczy <xref:System.Windows.Media.Media3D.PointLight>po . Reflektory świecą się jak PointLight i mają zarówno położenie, jak i kierunek. Rzutują światło w obszarze w kształcie <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> stożka ustawionym przez i właściwości, określonymi w stopniach.  
  
 Światła <xref:System.Windows.Media.Media3D.Model3D> są obiektami, dzięki czemu można przekształcać i animować właściwości światła, w tym położenie, kolor, kierunek i zakres.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>
## <a name="transforming-models"></a>Przekształcanie modeli  
 Podczas tworzenia modeli mają one określoną lokalizację w scenie. Aby przenieść te modele w scenie, aby je obrócić lub zmienić ich rozmiar, nie jest praktyczne, aby zmienić wierzchołki, które definiują same modele.  Zamiast tego, podobnie jak w 2D, stosuje się przekształcenia do modeli.  
  
 Każdy obiekt modelu <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> ma właściwość, za pomocą której można przenosić, przeorientować lub zmienić rozmiar modelu.  Po zastosowaniu przekształcenia skutecznie przesuniesz wszystkie punkty modelu o dowolny wektor lub wartość określoną przez transformację. Innymi słowy przekształciliśmy przestrzeń współrzędnych, w której zdefiniowano model ("przestrzeń modelu"), ale nie zmieniono wartości, które tworzą geometrię modelu w układzie współrzędnych całej sceny ("przestrzeń świata").  
  
 Aby uzyskać więcej informacji na temat przekształcania modeli, zobacz [Omówienie przekształceń 3D](3-d-transformations-overview.md).  
  
<a name="animations"></a>
## <a name="animating-models"></a>Animowanie modeli  
 Implementacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3D uczestniczy w tym samym systemie chronometrażu i animacji co grafika 2D. Innymi słowy, aby animować scenę 3D, animuj właściwości jej modeli. Istnieje możliwość animowania właściwości umietywnych bezpośrednio, ale zazwyczaj łatwiej jest animować przekształcenia, które zmieniają położenie lub wygląd modeli. Ponieważ przekształcenia mogą <xref:System.Windows.Media.Media3D.Model3DGroup> być stosowane do obiektów, a także poszczególnych modeli, istnieje możliwość zastosowania jednego zestawu animacji do podrzędnego Model3DGroup i innego zestawu animacji do grupy obiektów podrzędnych. Można również uzyskać wiele efektów wizualnych, animując właściwości oświetlenia sceny. Na koniec można animować samą projekcję, animując pozycję kamery lub pole widzenia. Aby uzyskać podstawowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informacje na temat systemu chronometrażu i animacji, zobacz [omówienie animacji,](animation-overview.md) [Omówienie scenochorystyki](storyboards-overview.md)i [Bezpłatne obiekty Omówienie](../advanced/freezable-objects-overview.md) tematów.  
  
 Aby animować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obiekt w programie , należy utworzyć oś czasu, zdefiniować animację (która jest naprawdę zmianą w niektórych wartości właściwości w czasie) i określić właściwość, do której ma być stosowana animacja. Ponieważ wszystkie obiekty w scenie 3D <xref:System.Windows.Controls.Viewport3D>są częściami podrzędnymi , właściwości, do których odnosi się dowolna animacja, którą chcesz zastosować do sceny, są właściwościami viewport3D.  
  
 Załóżmy, że chcesz, aby model wydawał się chwiać się w miejscu. Można zastosować a <xref:System.Windows.Media.Media3D.RotateTransform3D> do modelu i animować oś jego obrotu z jednego wektora do drugiego. Poniższy przykład kodu pokazuje zastosowanie Vector3DAnimation do Axis właściwości rotat3D transformacji, przy założeniu RotateTransform3D jest jednym z kilku przekształceń stosowanych do modelu z TransformGroup.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>
## <a name="add-3d-content-to-the-window"></a>Dodawanie zawartości 3D do okna  
 Aby renderować scenę, dodaj <xref:System.Windows.Media.Media3D.Model3DGroup>modele i <xref:System.Windows.Media.Media3D.Model3DGroup> światła <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> do <xref:System.Windows.Media.Media3D.ModelVisual3D>, a następnie ustaw jako . Dodaj <xref:System.Windows.Media.Media3D.ModelVisual3D> do <xref:System.Windows.Controls.Viewport3D.Children%2A> kolekcji <xref:System.Windows.Controls.Viewport3D>. Dodaj kamery <xref:System.Windows.Controls.Viewport3D> do, <xref:System.Windows.Controls.Viewport3D.Camera%2A> ustawiając jego właściwość.  
  
 Na koniec dodaj <xref:System.Windows.Controls.Viewport3D> do okna. Gdy <xref:System.Windows.Controls.Viewport3D> jest uwzględniony jako zawartość elementu układu, takiego jak Kanwa, określ <xref:System.Windows.FrameworkElement.Height%2A> rozmiar <xref:System.Windows.FrameworkElement.Width%2A> viewport3D, <xref:System.Windows.FrameworkElement>ustawiając jego i właściwości (dziedziczone po ).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [Omówienie przekształceń 3D](3-d-transformations-overview.md)
- [Maksymalizuj wydajność 3D WPF](maximize-wpf-3d-performance.md)
- [Tematy in jakże](3-d-graphics-how-to-topics.md)
- [Przegląd Kształty i podstawowe rysowanie w WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
