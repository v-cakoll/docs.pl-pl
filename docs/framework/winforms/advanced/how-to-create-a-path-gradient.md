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
ms.openlocfilehash: 8399a56fca87704e10456a4cf8109d7c80d4db45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964402"
---
# <a name="how-to-create-a-path-gradient"></a>Instrukcje: Tworzenie gradientu ścieżki
<xref:System.Drawing.Drawing2D.PathGradientBrush> Klasa pozwala dostosować sposób wypełnienia kształtu przy użyciu stopniowej zmiany kolorów. Na przykład można określić jeden kolor dla środka ścieżki i inny kolor granicy ścieżki. Możesz również określić oddzielne kolory dla każdego z kilku punktów wzdłuż granicy ścieżki.  
  
> [!NOTE]
> W interfejsie GDI+ ścieżka jest sekwencją wierszy i krzywych obsługiwanych przez <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt. Aby uzyskać więcej informacji na temat ścieżek GDI+, zobacz [ścieżki grafiki w GDI+](graphics-paths-in-gdi.md) i [Konstruowanie i rysowanie ścieżek](constructing-and-drawing-paths.md).  

Przykłady w tym artykule to metody, które są wywoływane z programu obsługi <xref:System.Windows.Forms.Control.Paint> zdarzeń kontrolki.  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Aby wypełnić wielokropek z gradientem ścieżki  
  
- Poniższy przykład wypełnia elipsę przy użyciu pędzla gradientu ścieżki. Kolor środka jest ustawiony na niebieską i kolor granicy jest ustawiony na wartość akwamaryna. Na poniższej ilustracji przedstawiono wypełnioną elipsę.  
  
     ![Ścieżka gradientu wypełnia elipsę.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     Domyślnie pędzel gradientu ścieżki nie wykracza poza granicę ścieżki. Jeśli używasz pędzla ze ścieżką do wypełnienia rysunku, który wykracza poza granice ścieżki, obszar ekranu poza ścieżką nie zostanie wypełniony.  
  
     Na poniższej ilustracji pokazano, <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> co się `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`dzieje w przypadku zmiany wywołania w poniższym kodzie:  
  
     ![Ścieżka gradientu rozszerzona poza granicą ścieżki.](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     Poprzedni przykład kodu jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> e, który jest <xref:System.Windows.Forms.PaintEventHandler>parametrem.  
  
### <a name="to-specify-points-on-the-boundary"></a>Aby określić punkty na granicy  
  
- Poniższy przykład tworzy pędzel gradientu ścieżki ze ścieżki w kształcie gwiazdki. Kod ustawia <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> właściwość, która ustawia kolor centroida gwiazdki na czerwony. Następnie kod ustawia <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> właściwość, aby określić różne kolory (przechowywane `colors` w tablicy) w poszczególnych punktach `points` tablicy. Końcowa instrukcja Code wypełnia ścieżkę w kształcie gwiazdy przy użyciu pędzla gradientu ścieżki.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- Poniższy przykład rysuje gradient ścieżki bez <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu w kodzie. Określony <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> Konstruktor w przykładzie otrzymuje tablicę punktów, ale nie <xref:System.Drawing.Drawing2D.GraphicsPath> wymaga obiektu. Należy również pamiętać, że <xref:System.Drawing.Drawing2D.PathGradientBrush> jest używany do wypełnienia prostokąta, a nie ścieżki. Prostokąt jest większy niż ZAMKNIĘTA ścieżka użyta do zdefiniowania pędzla, więc część prostokąta nie jest malowana przez pędzel. Na poniższej ilustracji przedstawiono prostokąt (linia kropkowana) oraz część prostokąta rysowanego przez pędzel gradientu ścieżki: 
  
     ![Fragment gradientu malowany przez pędzel gradientu ścieżki.](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Aby dostosować gradient ścieżki  
  
- Jednym ze sposobów dostosowywania pędzla ścieżki jest ustawienie jego <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> właściwości. Skala fokusu określa wewnętrzną ścieżkę, która leży wewnątrz ścieżki głównej. Kolor środkowy jest wyświetlany wszędzie w tej ścieżce wewnętrznej, a nie tylko w punkcie centralnym.  
  
     Poniższy przykład tworzy pędzel gradientu ścieżki na podstawie ścieżki eliptycznej. Kod ustawia kolor granicy na niebieski, ustawia kolor środka na wartość akwamaryna, a następnie używa pędzla w postaci ścieżki do wypełnienia ścieżki eliptycznej.  
  
     Następnie kod ustawia skale fokusu dla pędzla gradientu ścieżki. Skala fokusu x jest ustawiona na 0,3, a skala fokusu y jest ustawiona na 0,8. Kod wywołuje <xref:System.Drawing.Graphics.TranslateTransform%2A> metodę <xref:System.Drawing.Graphics> obiektu, tak aby kolejne wywołanie <xref:System.Drawing.Graphics.FillPath%2A> wypełniło elipsę znajdującą się po prawej stronie pierwszej elipsy.  
  
     Aby zobaczyć efekt skalowania fokusu, Załóżmy, że mała Elipsa współużytkuje centrum z główną elipsą. Mała (wewnętrzna) Elipsa to główna Elipsa skalowana w poziomie (około jej centrum) pozioma przez współczynnik 0,3 i pionowy przez współczynnik 0,8. Podczas przesuwania od granicy wielokropka zewnętrzna do granicy wielokropka wewnętrznego, kolor zmienia się stopniowo od niebieski do akwamaryna. Gdy przeniesiesz od granicy wielokropka wewnętrznej do centrum udostępnionego, kolor pozostaje akwamaryna.  
  
     Na poniższej ilustracji przedstawiono dane wyjściowe poniższego kodu. Elipsa po lewej stronie ma wartość akwamaryna tylko w punkcie centralnym. Elipsa po prawej stronie jest w dowolnym miejscu w ścieżce wewnętrznej.  
  
 ![Efekt gradientowy skali ostrości](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>Aby dostosować przy użyciu interpolacji  
  
- Innym sposobem dostosowania pędzla ścieżki jest określenie tablicy kolorów interpolacji i tablicę pozycji interpolacji.  
  
     Poniższy przykład tworzy pędzel gradientu ścieżki na podstawie trójkąta. Kod ustawia <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> Właściwość pędzla w ścieżce, aby określić tablicę kolorów interpolacji (ciemnozielone, akwamaryna, Blue) i tablicę pozycji interpolacji (0, 0,25, 1). Gdy przenosisz od granicy trójkąta do punktu centralnego, kolor zmienia się stopniowo od ciemnozielony do akwamaryna, a następnie od akwamaryna do niebieski. Zmiana z ciemnego koloru na zieloną jest wykonywana w 25 procentach odległości od ciemnozielony do niebieski.  
  
     Na poniższej ilustracji przedstawiono Trójkąt wypełniony przy użyciu pędzla gradientu niestandardowej ścieżki.  
  
     ![Trójkąt wypełniony użyciem pędzla gradientu niestandardowej ścieżki.](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Aby ustawić punkt środkowy  
  
- Domyślnie punkt środkowy pędzla gradientu ścieżki jest centroida ścieżki używanej do konstruowania pędzla. Lokalizację punktu centralnego można zmienić, ustawiając <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> Właściwość <xref:System.Drawing.Drawing2D.PathGradientBrush> klasy.  
  
     Poniższy przykład tworzy pędzel gradientu ścieżki na podstawie elipsy. Środek wielokropka ma wartość (70, 35), ale punkt środkowy pędzla gradientu ścieżki jest ustawiony na (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     Na poniższej ilustracji przedstawiono wypełnioną elipsę i punkt środkowy pędzla gradientu ścieżki:  
  
     ![Ścieżka gradientu z wypełnionym elipsą i punktem środkowy.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- Możesz ustawić punkt środkowy pędzla gradientu ścieżki do lokalizacji poza ścieżką, która została użyta do skonstruowania pędzla. Poniższy przykład zastępuje wywołanie, aby ustawić <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> właściwość w poprzednim kodzie.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     Na poniższej ilustracji przedstawiono dane wyjściowe z tą zmianą:  
  
     ![Ścieżka gradientu z punktem środkowym poza ścieżką.](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     Na powyższej ilustracji punkty znajdujące się po prawej stronie wielokropka nie są czyste jako niebieskie (choć są bardzo blisko nich). Kolory w gradiencie są pozycjonowane tak, jakby wypełnienie osiągnęło punkt (145, 35), gdzie kolor będzie czysty (0, 0, 255). Ale wypełnienie nigdy nie osiągnie (145, 35), ponieważ pędzel gradientu ścieżki maluje tylko wewnątrz ścieżki.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższe przykłady są przeznaczone do użycia z Windows Forms i wymagają <xref:System.Windows.Forms.PaintEventArgs> `e`, który <xref:System.Windows.Forms.Control.Paint> jest parametrem programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie pędzla gradientów do wypełniania kształtów](using-a-gradient-brush-to-fill-shapes.md)
