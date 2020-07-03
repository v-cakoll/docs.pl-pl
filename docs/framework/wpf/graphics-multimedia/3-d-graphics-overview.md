---
title: Omówienie grafiki 3D
description: Zapoznaj się z grafiką 3D w Windows Presentation Foundation (WPF), aby narysować, przekształcić i animować grafikę 3D w kodzie znaczników i procedur.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D graphics [WPF]
- graphics [WPF], 3D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: 51da6a1ed6d5e98b99c64ee23be52f7b2385897f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853879"
---
# <a name="3d-graphics-overview"></a>Omówienie grafiki 3D
<a name="introduction"></a>Funkcje 3W w programie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umożliwiają deweloperom rysowanie, transformację i animowanie grafiki 3D w kodzie znaczników i procedur. Deweloperzy mogą łączyć grafiki 2D i 3D w celu tworzenia rozbudowanych kontrolek, zapewniać złożone ilustracje danych lub ulepszać środowisko użytkownika interfejsu aplikacji. Obsługa 3W w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie jest przeznaczona do dostarczania w pełni funkcjonalnej platformy deweloperskiej. Ten temat zawiera omówienie funkcji 3W w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemie graficznym.  

<a name="threed_in_2d"></a>
## <a name="3d-in-a-2d-container"></a>3W w kontenerze 2D  
 zawartość grafiki 3D w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest hermetyzowana w elemencie, <xref:System.Windows.Controls.Viewport3D> która może uczestniczyć w dwuwymiarowej strukturze elementów. System grafiki traktuje <xref:System.Windows.Controls.Viewport3D> się jako dwuwymiarowy element wizualny, taki jak wiele innych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . <xref:System.Windows.Controls.Viewport3D>działa jako okno — okienko ekranu — w trójwymiarowej scenie. Dokładniej, jest to powierzchnia, na której jest rzutowana scena 3D.  
  
 W konwencjonalnej aplikacji 2D Użyj <xref:System.Windows.Controls.Viewport3D> tak jak innego elementu kontenera, takiego jak siatka lub Kanwa.  Chociaż można używać <xref:System.Windows.Controls.Viewport3D> z innymi obiektami rysowania 2D w tym samym grafie sceny, nie można przeniknąć obiektów 2D i 3W w obrębie <xref:System.Windows.Controls.Viewport3D> .  Ten temat koncentruje się na sposobie rysowania grafiki 3D wewnątrz <xref:System.Windows.Controls.Viewport3D> .  
  
<a name="coord_space"></a>
## <a name="3d-coordinate-space"></a>Przestrzeń współrzędnej 3W  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Układ współrzędnych dla grafiki 2D lokalizuje źródło w lewym górnym rogu obszaru renderowania (zazwyczaj ekranu). W systemie 2D wartości dodatniej osi x przechodzą do prawej i dodatniej wartości osi y przechodzą w dół.  Jednak w układzie współrzędnych 3W, źródło znajduje się w środku obszaru renderowania, a dodatnie wartości osi x są przechodzą w prawo, ale dodatnie wartości osi y przechodzą w górę, a dodatnie wartości osi z przechodzą na zewnątrz od początku do przeglądarki.  
  
 ![Układy współrzędnych](./media/coordsystem-1.png "CoordSystem-1")  
Konwencjonalne reprezentacje układu współrzędnych 2D i 3W  
  
 Przestrzeń zdefiniowana przez te osie jest nieruchomą ramką odwołania dla obiektów 3D w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . W miarę kompilowania modeli w tym miejscu i tworzenia lamp i kamer w celu ich wyświetlania, warto rozróżnić tę nieruchomą ramkę odniesienia lub "przestrzeń świata" z lokalnej ramki odniesienia, którą tworzysz dla każdego modelu, gdy stosowane są przekształcenia. Należy pamiętać, że obiekty w przestrzeni świata mogą wyglądać zupełnie inaczej lub nie być widoczne w ogóle, w zależności od ustawień świateł i aparatu, ale położenie kamery nie zmienia lokalizacji obiektów w przestrzeni świata.  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>Kamery i projekcje  
 Deweloperzy, którzy pracują w 2D, są przyzwyczajoni do pozycjonowania elementów podstawowych na dwuwymiarowym ekranie. Podczas tworzenia sceny 3W należy pamiętać, że naprawdę tworzysz reprezentację 2D obiektów 3W. Ponieważ scena 3D wygląda inaczej, w zależności od punktu widzenia onlooker, należy określić ten punkt widoku. <xref:System.Windows.Media.Media3D.Camera>Klasa umożliwia określenie tego punktu widoku dla sceny 3W.  
  
 Innym sposobem na zrozumienie, jak scena 3D jest reprezentowana na powierzchni 2D, jest opisywanie sceny jako projekcji na powierzchni wyświetlania. <xref:System.Windows.Media.Media3D.ProjectionCamera>Pozwala określić różne projekcje i ich właściwości, aby zmienić sposób, w jaki onlooker widzi modele 3W. A <xref:System.Windows.Media.Media3D.PerspectiveCamera> określa projekcję, która foreshortens scenę.  Innymi słowy, <xref:System.Windows.Media.Media3D.PerspectiveCamera> zapewnia perspektywę punktu znikania.  Możesz określić pozycję aparatu w przestrzeni współrzędnych sceny, kierunek i pola widoku dla aparatu oraz wektor, który definiuje kierunek "w górę" w scenie. Na poniższym diagramie przedstawiono <xref:System.Windows.Media.Media3D.PerspectiveCamera> projekcję.  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>Właściwości i <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> <xref:System.Windows.Media.Media3D.ProjectionCamera> ograniczają zakres projekcji aparatu. Ponieważ aparaty mogą znajdować się w dowolnym miejscu sceny, istnieje możliwość, że aparat znajduje się w rzeczywistości wewnątrz modelu lub w bardzo blisko modelu, dzięki czemu trudno jest prawidłowo odróżnić obiekty.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>pozwala określić minimalną odległość między aparatem, po którym obiekty nie będą rysowane.  Z drugiej strony, <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> pozwala określić odległość od aparatu, poza którym obiekty nie będą rysowane, co gwarantuje, że obiekty zbyt daleko do rozpoznawalnego nie zostaną uwzględnione w scenie.  
  
 ![Konfiguracja aparatu](./media/coordsystem-6.png "CoordSystem-6")  
Położenie kamery  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>Określa rzutowanie modelu 3D na powierzchnię graficzną 2D. Podobnie jak w przypadku innych kamer, określa położenie, kierunek oglądania i kierunek "w górę". W przeciwieństwie do <xref:System.Windows.Media.Media3D.PerspectiveCamera> , jednak <xref:System.Windows.Media.Media3D.OrthographicCamera> opisuje projekcję, która nie zawiera foreshortening perspektywy. Inaczej mówiąc, <xref:System.Windows.Media.Media3D.OrthographicCamera> opisuje pole wyświetlania, którego boki są równoległe, a nie jeden, którego boki są spotykane w punkcie w aparacie. Na poniższej ilustracji przedstawiono ten sam model, który jest wyświetlany przy użyciu <xref:System.Windows.Media.Media3D.PerspectiveCamera> i <xref:System.Windows.Media.Media3D.OrthographicCamera> .  
  
 ![Rzutowanie ortogonalne i perspektywiczne](./media/camera-projections4.png "Camera_projections4")  
Perspektywy i projekcje ortogonalne  
  
 Poniższy kod przedstawia niektóre typowe ustawienia aparatu.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>Elementy pierwotne modelu i siatki  
  
 <xref:System.Windows.Media.Media3D.Model3D>jest abstrakcyjną klasą bazową, która reprezentuje ogólny obiekt 3W. Aby zbudować scenę 3W, potrzebne są pewne obiekty, a obiekty tworzące wykres sceny pochodzą od <xref:System.Windows.Media.Media3D.Model3D> . Obecnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsługa modelowania geometrie z <xref:System.Windows.Media.Media3D.GeometryModel3D> . <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>Właściwość tego modelu Pobiera element podstawowy siatki.  
  
 Aby skompilować model, Zacznij od skompilowania elementu pierwotnego lub siatki. Element podstawowy 3W to kolekcja wierzchołków tworzących pojedynczą jednostkę 3W. Większość systemów 3W oferuje elementy podstawowe modelowane na najprostszej ilustracji zamkniętej: Trójkąt zdefiniowany przez trzy wierzchołki.  Ponieważ trzy punkty trójkąta są współrzędnymi, możesz kontynuować dodawanie trójkątów, aby modelować bardziej złożone kształty o nazwie siatki.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]System 3W obecnie udostępnia <xref:System.Windows.Media.Media3D.MeshGeometry3D> klasę, co pozwala na określenie dowolnej geometrii; obecnie nie obsługuje wstępnie zdefiniowanych elementów pierwotnych 3W, takich jak sfery i formularze sześcienne. Rozpocznij tworzenie <xref:System.Windows.Media.Media3D.MeshGeometry3D> przez określenie listy wierzchołków trójkąta jako <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> właściwości. Każdy wierzchołek jest określony jako <xref:System.Windows.Media.Media3D.Point3D> .  (W programie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] należy określić tę właściwość jako listę liczb pogrupowanych w trzech, które reprezentują współrzędne każdego wierzchołka). W zależności od geometrii, Siatka może składać się z wielu trójkątów, a niektóre z nich mają te same rogi (wierzchołki). Aby poprawnie narysować siatkę, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] potrzebne są informacje o tym, które wierzchołki są współużytkowane przez te trójkąty. Te informacje można podać, określając listę indeksów trójkątnych z <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> właściwością. Ta lista określa kolejność, w jakiej punkty określone na <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liście będą określać trójkąt.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 W poprzednim przykładzie <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> lista określa osiem wierzchołków służących do definiowania siatki w kształcie sześcianu. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>Właściwość określa listę dwunastu grup trzech indeksów.  Każda liczba na liście odnosi się do przesunięcia na <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listę.  Na przykład pierwsze trzy wierzchołki określone przez <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> listę to (1, 1, 0), (0, 1, 0) i (0, 0, 0). Pierwsze trzy indeksy określone przez <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> listę to 0, 2 i 1, które odpowiadają pierwszym, trzecim i drugim punktom na <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liście. W związku z tym pierwszy Trójkąt, który tworzy model modułu, będzie składać się z (1, 1, 0) do (0, 1, 0) do (0, 0, 0), a pozostałe jedenaście trójkątów zostanie określona w podobny sposób.  
  
 Można kontynuować definiowanie modelu przez określenie wartości <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> właściwości i.  Aby renderować powierzchnię modelu, system graficzny potrzebuje informacji o kierunku, w którym powierzchnia jest umieszczona na dowolnym trójkącie. Te informacje służą do przeprowadzania obliczeń oświetlenia dla modelu: powierzchnie, które bezpośrednio nadają się do źródła światła, są bardziej jaśniejsze niż te, na których się odchylono od światła. Chociaż [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można określić domyślne wektory normalne przy użyciu współrzędnych położenia, można również określić różne normalne wektory do przybliżonego wyglądu zakrzywionych powierzchni.  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>Właściwość określa kolekcję <xref:System.Windows.Point> s, która informuje system graficzny o sposobie mapowania współrzędnych, które określają sposób rysowania tekstury w wierzchołkach siatki. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>są określone jako wartość z przedziału od 0 do 1 włącznie.  Podobnie jak w przypadku <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> właściwości, system grafiki może obliczyć domyślne Współrzędne tekstury, ale można ustawić różne współrzędne tekstury, aby kontrolować mapowanie tekstury, która obejmuje część powtarzalnego wzorca, na przykład. Więcej informacji na temat współrzędnych tekstury można znaleźć w kolejnych tematach lub w zarządzanym zestawie SDK Direct3D.  
  
 Poniższy przykład pokazuje, jak utworzyć jedną z modeli modułu w kodzie proceduralnym. Cały moduł można narysować jako pojedynczy elementu GeometryModel3D; Ten przykład rysuje powierzchnie modułu jako odrębny model, aby zastosować oddzielne tekstury do każdej z nich w przyszłości.  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>'
## <a name="applying-materials-to-the-model"></a>Stosowanie materiałów do modelu  
  
 Aby siatka wyglądała jak obiekt trójwymiarowy, musi mieć zastosowana tekstura, aby pokryć powierzchnię zdefiniowaną przez jej wierzchołki i Trójkąty, aby można było ją świecić i przedstawić w projekcji przez aparat. W 2D należy użyć <xref:System.Windows.Media.Brush> klasy do zastosowania kolorów, wzorców, gradientów lub innej zawartości wizualnej do obszarów ekranu.  Wygląd obiektów 3W jest jednak funkcją modelu oświetlenia, a nie tylko z zastosowanym kolorem lub deseniem. Rzeczywiste obiekty odzwierciedlają nieco inaczej, w zależności od jakości ich powierzchni: powierzchnie błyszczące i Shiny nie wyglądają tak samo jak powierzchnie o stanie surowym lub matowym, a niektóre obiekty pozornie pozostały do zaabsorbowania. Można zastosować wszystkie te same pędzle do obiektów 3D, które można stosować do obiektów 2D, ale nie można ich zastosować bezpośrednio.  
  
 Aby zdefiniować charakterystykę powierzchni modelu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa <xref:System.Windows.Media.Media3D.Material> klasy abstrakcyjnej. Konkretne podklasy materiału decydują o cechach wyglądu powierzchni modelu, a każda z nich zawiera również właściwość pędzla, do której można przekazać SolidColorBrush, obiekt TileBrush lub VisualBrush.  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial>Określa, że pędzel zostanie zastosowany do modelu, tak jakby ten model był oświetlony diffusely. Używanie DiffuseMaterial przypomina używanie pędzli bezpośrednio w modelach 2D; powierzchnie modelu nie odzwierciedlają światła, jakby Shiny.  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial>Określa, że pędzel zostanie zastosowany do modelu, tak jakby powierzchnia modelu była twarda lub Shinya, która może odzwierciedlać najważniejsze elementy. Można ustawić stopień, w jakim tekstura będzie sugerować tę jakość odbicia, lub "komfort", określając wartość <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> właściwości.  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial>umożliwia określenie, że tekstura zostanie zastosowana, ponieważ model emituje światło równe kolorowi pędzla. Nie powoduje to, że model jest lekki; jednak będzie ona uczestniczyć inaczej w obserwowanie niż w przypadku tekstury z DiffuseMaterial lub SpecularMaterial.  
  
 W celu uzyskania lepszej wydajności, tylnych twarzy a <xref:System.Windows.Media.Media3D.GeometryModel3D> (tych, które znajdują się na przeciwległej stronie modelu z aparatu), są wyłączane z sceny.  Aby określić, <xref:System.Windows.Media.Media3D.Material> Aby zastosować do warstwy czołowej modelu, jak płaszczyzna, ustaw <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> Właściwość modelu.  
  
 Aby osiągnąć niektóre cechy powierzchniowe, takie jak blask lub efekty odbicia, warto zastosować kilka różnych pędzli do modelu. Można stosować i ponownie używać wielu materiałów przy użyciu <xref:System.Windows.Media.Media3D.MaterialGroup> klasy. Elementy podrzędne środka są stosowane po raz pierwszy do ostatniego w wielu przebiegach renderowania.  
  
 Poniższy przykład kodu pokazuje, jak zastosować pełny kolor i rysunek jako pędzle do modeli 3W.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  ' [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
 ' [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
  [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>Oświetlenia sceny  
 Sygnalizatory w grafikach 3D umożliwiają działanie świateł w świecie rzeczywistym: sprawiają, że powierzchnie są widoczne. Dokładniej, światła wskazują, która część sceny zostanie uwzględniona w projekcji. Jasne obiekty w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tworzą różne efekty jasne i cieniowe, które są modelowane po zachowaniu różnych rzeczywistych sygnalizatorów. Uwzględnij co najmniej jedno światło w scenie lub nie będą widoczne żadne modele.  
  
 Następujące sygnalizatory pochodzą z klasy bazowej <xref:System.Windows.Media.Media3D.Light> :  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>: Zapewnia oświetlenie otoczenia, które w sposób jednorodny oświetla wszystkie obiekty niezależnie od ich lokalizacji lub orientacji.  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>: Świecy się jak odległe Źródło światła.  Światła kierunkowe mają <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> określone jako Vector3D, ale nie w określonej lokalizacji.  
  
- <xref:System.Windows.Media.Media3D.PointLight>: Świecy jak w pobliżu źródła światła. PointLights mieć położenie i sygnalizator rzutowania od tej pozycji. Obiekty w scenie są oświetlone w zależności od ich położenia i odległości w odniesieniu do światła. <xref:System.Windows.Media.Media3D.PointLightBase>uwidacznia <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> Właściwość, która określa odległość ponad modelami, które nie są oświetlone przez jasne. PointLight udostępnia również właściwości tłumienia, które określają, jak intensywność światła zmniejsza się z odległości. Można określić stałe, liniowe lub interpolacje kwadratowe dla tłumieniea światła.  
  
- <xref:System.Windows.Media.Media3D.SpotLight>: Dziedziczy z <xref:System.Windows.Media.Media3D.PointLight> . Funkcja Spotlights jest oświetlana jak PointLight i ma zarówno pozycję, jak i kierunek. Są one jasne w kształcie prostokątnym ustawione przez <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> i <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> właściwości, określone w stopniach.  
  
 Sygnalizatory są <xref:System.Windows.Media.Media3D.Model3D> obiektami, dzięki czemu można przekształcać i animować właściwości jasne, w tym pozycje, kolory, kierunek i zakres.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>
## <a name="transforming-models"></a>Transformowanie modeli  
 Podczas tworzenia modeli mają one określoną lokalizację w scenie. Aby przenieść te modele wokół sceny, aby je obrócić lub zmienić ich rozmiar, nie można zmienić wierzchołków, które definiują same modele.  Zamiast tego, podobnie jak w przypadku 2D, stosowane są przekształcenia do modeli.  
  
 Każdy obiekt modelu ma <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> Właściwość, za pomocą której można przenosić i zmieniać orientację lub skalować model.  Po zastosowaniu przekształcenia można efektywnie przesunąć wszystkie punkty modelu według dowolnego wektora lub wartości określonej przez transformację. Innymi słowy, została przekształcona przestrzeń współrzędnych, w której zdefiniowany jest model ("przestrzeń modelowa"), ale nie zmieniono wartości, które tworzą geometrię modelu w układzie współrzędnych całej sceny ("przestrzeń świata").  
  
 Aby uzyskać więcej informacji na temat przekształcania modeli, zobacz [Omówienie przekształceń 3W](3-d-transformations-overview.md).  
  
<a name="animations"></a>
## <a name="animating-models"></a>Animowanie modeli  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Implementacja 3W uczestniczy w tym samym systemie chronometrażu i animacji co grafika 2D. Innymi słowy, aby animować scenę 3W, Animuj właściwości jej modeli. Istnieje możliwość bezpośredniej animacji właściwości elementów pierwotnych, ale jest to zwykle prostsze, aby animować przekształcenia, które zmieniają pozycję lub wygląd modeli. Ponieważ przekształcenia można stosować do <xref:System.Windows.Media.Media3D.Model3DGroup> obiektów, a także poszczególnych modeli, istnieje możliwość zastosowania jednego zestawu animacji do elementu podrzędnego Model3DGroup i innego zestawu animacji do grupy obiektów podrzędnych. Możesz również uzyskać różnorodne efekty wizualne, animowanie właściwości oświetlenia sceny. Na koniec można animować projekcję przez animowanie położenia kamery lub pola widoku. Informacje ogólne dotyczące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemu chronometrażu i animacji można znaleźć w tematach Omówienie [animacji](animation-overview.md), [przeglądów scenorysów](storyboards-overview.md)i [Freezable obiektów](../advanced/freezable-objects-overview.md) .  
  
 Aby animować obiekt w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , należy utworzyć oś czasu, zdefiniować animację (co jest naprawdę zmianą wartości właściwości w czasie) i określić właściwość, do której ma zostać zastosowana animacja. Ponieważ wszystkie obiekty w scenie 3D są elementami podrzędnymi <xref:System.Windows.Controls.Viewport3D> , właściwości, które są przeznaczone dla każdej animacji, która ma zostać zastosowana do sceny, są właściwościami Viewport3D.  
  
 Załóżmy, że chcesz utworzyć model, aby Wobble się na miejscu. Możesz zdecydować się na zastosowanie <xref:System.Windows.Media.Media3D.RotateTransform3D> do modelu i animować oś jego obrotu z jednego wektora do innego. Poniższy przykład kodu demonstruje stosowanie Vector3DAnimation do właściwości osi Rotation3D transformacji, przy założeniu, że RotateTransform3D być jednym z kilku transformacji zastosowanych do modelu z transformą.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>
## <a name="add-3d-content-to-the-window"></a>Dodaj zawartość 3D do okna  
 Aby renderować scenę, Dodaj modele i sygnalizatory do <xref:System.Windows.Media.Media3D.Model3DGroup> , a następnie ustaw <xref:System.Windows.Media.Media3D.Model3DGroup> jako <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> <xref:System.Windows.Media.Media3D.ModelVisual3D> . Dodaj <xref:System.Windows.Media.Media3D.ModelVisual3D> do <xref:System.Windows.Controls.Viewport3D.Children%2A> kolekcji <xref:System.Windows.Controls.Viewport3D> . Dodaj kamery do programu <xref:System.Windows.Controls.Viewport3D> przez ustawienie jego <xref:System.Windows.Controls.Viewport3D.Camera%2A> właściwości.  
  
 Na koniec Dodaj <xref:System.Windows.Controls.Viewport3D> do okna. Gdy <xref:System.Windows.Controls.Viewport3D> jest dołączany jako zawartość elementu układu, takiego jak Kanwa, określ rozmiar Viewport3D przez ustawienie jego <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> właściwości i (dziedziczone z <xref:System.Windows.FrameworkElement> ).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [Omówienie przekształceń 3D](3-d-transformations-overview.md)
- [Maksymalizuj wydajność 3D WPF](maximize-wpf-3d-performance.md)
- [— Tematy porad](3-d-graphics-how-to-topics.md)
- [Przegląd Kształty i podstawowe rysowanie w WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md)
