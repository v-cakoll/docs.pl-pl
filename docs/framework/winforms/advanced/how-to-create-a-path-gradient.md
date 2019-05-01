---
title: 'Instrukcje: Tworzenie gradientu ścieżki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: a04465c31b160f97568ed88c434e7e3a5126ebb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938063"
---
# <a name="how-to-create-a-path-gradient"></a>Instrukcje: Tworzenie gradientu ścieżki
<xref:System.Drawing.Drawing2D.PathGradientBrush> Klasy pozwala dostosować sposób wypełnienia kształtu z stopniowo zmiana kolorów. Na przykład można określić jeden kolor środek ścieżka i innego koloru dla granicy ścieżki. Można również określić różne kolory dla każdego z kilku punktów wzdłuż granic ścieżki.  
  
> [!NOTE]
>  W GDI + ścieżki jest sekwencją linii i krzywych utrzymywane przez <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu. Aby uzyskać więcej informacji na temat ścieżek GDI + zobacz [ścieżki grafiki w GDI +](graphics-paths-in-gdi.md) i [Constructing i rysowanie ścieżek](constructing-and-drawing-paths.md).  

Przykłady w niniejszym artykule są metody, które są wywoływane z poziomu kontroli <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Aby wypełnić elipsę gradientu ścieżki  
  
- Poniższy przykład wypełnia elipsę z pędzla gradientu ścieżki. Kolor jest ustawiona na niebieski i Akwamaryna jest ustawiony kolor granic. Poniższa ilustracja przedstawia wypełnioną elipsę.  
  
     ![Ścieżka gradientu wypełnienia elipsy.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     Domyślnie pędzla gradientu ścieżki nie jest rozszerzana poza granicami ścieżki. Jeśli używasz pędzla gradientu ścieżki do wypełnienia rysunku, który wykracza poza granicę ścieżkę obszaru ekranu poza ścieżka nie zostanie wypełnione.  
  
     Na poniższej ilustracji pokazano, co się stanie, jeśli zmienisz <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> wywołania następujący kod do `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`:  
  
     ![Ścieżka gradientu wykracza poza granicę ścieżki.](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     W poprzednim przykładzie kodu jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> e, który jest parametrem z <xref:System.Windows.Forms.PaintEventHandler>.  
  
### <a name="to-specify-points-on-the-boundary"></a>Aby określić punktów na granicy  
  
- Poniższy przykład tworzy pędzla gradientów ścieżki ze ścieżki kształcie gwiazdy. Zestawy kodów <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> właściwość, która ustawia kolor na środek strefy widocznego gwiazdkę na czerwony. A następnie ustawia kod <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> właściwość, aby określić różne kolory (przechowywane w `colors` tablicy) na poszczególnych etapach `points` tablicy. Instrukcja kodu końcowego wypełnia ścieżki kształcie gwiazdy z pędzla gradientu ścieżki.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- Poniższy przykład pobiera gradientu ścieżki bez <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu w kodzie. Określonych <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> konstruktora w przykładzie odbiera tablicę punkty, ale nie wymaga <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu. Ponadto należy pamiętać, że <xref:System.Drawing.Drawing2D.PathGradientBrush> jest używany do wypełniania prostokąt, nie ścieżkę. Prostokąt jest większy niż ścieżki zamkniętej używane do definiowania pędzla, więc niektóre prostokąta nie jest malowane przez pędzla. Na poniższej ilustracji przedstawiono prostokąt (linia przerywana) i części prostokąt malowane przez pędzla gradientu ścieżki: 
  
     ![Część gradientu malowane przez pędzla gradientu ścieżki.](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Aby dostosować gradientu ścieżki  
  
- Pierwszym sposobem dostosowania pędzla gradientu ścieżki jest ustalenie jego <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> właściwości. Skaluje fokus Określ wewnętrzny ścieżki, który znajduje się w ścieżce głównej. Kolor jest wyświetlany wszędzie, gdzie w tej ścieżce wewnętrzne, a nie tylko w momencie Centrum.  
  
     Poniższy przykład obejmuje tworzenie pędzla gradientu ścieżki na podstawie ścieżki elipsy. Kod ustawia kolor granic na niebieski, ustawia kolor Akwamaryna i następnie używa pędzla gradientu ścieżki do wypełnienia eliptycznego ścieżki.  
  
     Następnie kod ustawia skale fokus pędzla gradientu ścieżki. Skala fokus x jest równa 0,3 i skalowania fokus y jest równa 0,8. Kod wywołuje <xref:System.Drawing.Graphics.TranslateTransform%2A> metody <xref:System.Drawing.Graphics> obiektu, aby kolejne wywołanie <xref:System.Drawing.Graphics.FillPath%2A> wypełnia elipsy, który znajduje się po prawej stronie pierwszej elipsy.  
  
     Aby zobaczyć efekt skale fokus, Wyobraź sobie małych elipsy, która udostępni środek głównego elipsy. Małe wielokropka (wewnętrzny) jest głównym elipsy skalowania (o jej środka) poziomo ośmiokrotnego 0,3 i w pionie przez współczynnik 0,8. Po przeniesieniu od granicę zewnętrzne elipsy do granicy wewnętrzny elipsy zmienia kolor stopniowo od niebieskiego na akwamarynowy. Jak przenieść z granic wewnętrzny elipsy do udostępnionego Centrum Akwamaryna pozostaje kolorów.  
  
     Poniższa ilustracja przedstawia dane wyjściowe następujący kod. Elipsa po lewej stronie jest Akwamaryna tylko na punktu centralnego. Wielokropka po prawej stronie jest Akwamaryna wszędzie, gdzie wewnątrz ścieżki wewnętrznego.  
  
 ![Efekt gradientu skali koncentracji uwagi](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>Aby dostosować przy użyciu interpolacji  
  
- Innym sposobem dostosowania pędzla gradientu ścieżki jest aby określić tablicę interpolacji kolorów i tablicę interpolacji pozycji.  
  
     Poniższy przykład obejmuje tworzenie pędzla gradientu ścieżki oparte na trójkąt. Zestawy kodów <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> właściwość pędzla gradientu ścieżki, aby określić tablicę kolorów interpolacji (Ciemnozielony, Akwamaryna, niebieski) i Tablica pozycji interpolacji (0, 0,25, 1). Jak przenieść z granic trójkąta punktu centralnego zmienia kolor stopniowo z Ciemnozielony na akwamarynowy Akwamaryna na niebieski, a następnie. Zmiana Ciemnozielony Akwamaryna odbywa się w odległości od Ciemnozielony na niebieski 25 procent.  
  
     Poniższa ilustracja przedstawia trójkąt wypełnione pędzla gradientu ścieżki niestandardowej.  
  
     ![Trójkąt wypełniony pędzla gradientu ścieżki niestandardowej.](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Można ustawić punktu centralnego  
  
- Domyślnie punktu centralnego pędzla gradientu ścieżki wynosi centroida — oś ścieżki używany do budowy pędzla. Można zmienić położenie punktu środkowego ustawiając <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> właściwość <xref:System.Drawing.Drawing2D.PathGradientBrush> klasy.  
  
     Poniższy przykład obejmuje tworzenie pędzla gradientu ścieżki oparte na elipsę. Środek elipsy wynosi (70, 35), ale punktu centralnego pędzla gradientu ścieżki jest ustawiona na (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     Na poniższej ilustracji przedstawiono wypełnioną elipsę i punktu centralnego pędzla gradientu ścieżki:  
  
     ![Gradientu ścieżki z wypełnioną elipsę i punkt środkowy.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- Można ustawić punktu centralnego pędzla gradientu ścieżki do lokalizacji poza ścieżki, które zostało użyte do konstruowania pędzla. Poniższy przykład zastępuje wywołanie, aby ustawić <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> właściwość w poprzednim kodzie.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     Na poniższej ilustracji przedstawiono dane wyjściowe z tej zmiany:  
  
     ![Gradientu ścieżki z punktu centralnego poza ścieżki.](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     Na powyższej ilustracji punkty po prawej stronie elipsy nie są czyste niebieski, (mimo że są one bardzo ścisłej). Kolory gradientu są umieszczone tak, jakby wypełnienie osiągnięty punkt (145, 35), gdzie kolor będzie czysty niebieskiego (0, 0, 255). Ale wypełnienie nigdy nie osiągnie (145, 35), ponieważ ścieżka pędzla gradientów do malowania tylko wewnątrz jego ścieżki.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższych przykładach są skonstruowane do użycia za pomocą interfejsu Windows Forms i wymagają one <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie pędzla gradientów do wypełniania kształtów](using-a-gradient-brush-to-fill-shapes.md)
