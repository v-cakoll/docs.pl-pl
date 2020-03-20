---
title: 'Porady: tworzenie gradientu ścieżki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: cf4dc558c008fb8adfc327a6a894a428e985df03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182631"
---
# <a name="how-to-create-a-path-gradient"></a>Porady: tworzenie gradientu ścieżki
Klasa <xref:System.Drawing.Drawing2D.PathGradientBrush> umożliwia dostosowanie sposobu wypełniania kształtu stopniowo zmieniającymi się kolorami. Można na przykład określić jeden kolor dla środka ścieżki i inny kolor dla granicy ścieżki. Można również określić oddzielne kolory dla każdego z kilku punktów wzdłuż granicy ścieżki.  
  
> [!NOTE]
> W GDI+ ścieżka jest sekwencją linii i krzywych obsługiwanych przez <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt. Aby uzyskać więcej informacji na temat ścieżek GDI+, zobacz [Ścieżki graficzne w GDI+](graphics-paths-in-gdi.md) oraz [Konstruowanie i rysowanie ścieżek](constructing-and-drawing-paths.md).  

Przykłady w tym artykule są metody, które <xref:System.Windows.Forms.Control.Paint> są wywoływane z obsługi zdarzeń formantu.  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Aby wypełnić elipsę gradientem ścieżki  
  
- Poniższy przykład wypełnia elipsę pędzlem gradientu ścieżki. Kolor środkowy jest ustawiony na niebieski, a kolor granicy jest ustawiony na aqua. Na poniższej ilustracji przedstawiono wypełnioną elipsę.  
  
     ![Ścieżka gradientu wypełnia elipsę.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     Domyślnie pędzel gradientu ścieżki nie rozciąga się poza granicę ścieżki. Jeśli użyjesz pędzla gradientu ścieżki, aby wypełnić rysunek, który wykracza poza granicę ścieżki, obszar ekranu poza ścieżką nie zostanie wypełniony.  
  
     Na poniższej ilustracji przedstawiono, co się <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`stanie, jeśli połączenie zostanie zmienione w następującym kodzie na:  
  
     ![Ścieżka gradientu jest wydłużona poza granicę ścieżki.](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     Poprzedni przykład kodu jest przeznaczony do użytku z windows <xref:System.Windows.Forms.PaintEventArgs> forms i wymaga <xref:System.Windows.Forms.PaintEventHandler>e, który jest parametrem .  
  
### <a name="to-specify-points-on-the-boundary"></a>Aby określić punkty na granicy  
  
- Poniższy przykład konstruuje pędzel gradientu ścieżki ze ścieżki w kształcie gwiazdy. Kod ustawia <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> właściwość, która ustawia kolor na centroid gwiazdy na czerwony. Następnie kod ustawia <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> właściwość, aby określić `colors` różne kolory (przechowywane `points` w tablicy) w poszczególnych punktach w tablicy. Końcowa instrukcja kodu wypełnia ścieżkę w kształcie gwiazdy pędzlem gradientu ścieżki.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- Poniższy przykład rysuje gradient <xref:System.Drawing.Drawing2D.GraphicsPath> ścieżki bez obiektu w kodzie. Konstruktora określonego <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> w przykładzie odbiera tablicę <xref:System.Drawing.Drawing2D.GraphicsPath> punktów, ale nie wymaga obiektu. Należy również zauważyć, że <xref:System.Drawing.Drawing2D.PathGradientBrush> jest używany do wypełnienia prostokąta, a nie ścieżki. Prostokąt jest większy niż zamknięta ścieżka używana do definiowania pędzla, więc część prostokąta nie jest malowana przez pędzel. Na poniższej ilustracji przedstawiono prostokąt (linia kropkowana) i część prostokąta malowane przez pędzel gradientu ścieżki:
  
     ![Część gradientu malowana przez pędzel gradientu ścieżki.](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Aby dostosować gradient ścieżki  
  
- Jednym ze sposobów dostosowania pędzla gradientu <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> ścieżki jest ustawienie jego właściwości. Skale fokusu określają ścieżkę wewnętrzną, która znajduje się wewnątrz ścieżki głównej. Kolor środkowy jest wyświetlany wszędzie wewnątrz tej wewnętrznej ścieżki, a nie tylko w punkcie środkowym.  
  
     Poniższy przykład tworzy pędzel gradientu ścieżki na podstawie ścieżki eliptycznej. Kod ustawia kolor granicy na niebieski, ustawia kolor środka na aqua, a następnie używa pędzla gradientu ścieżki do wypełnienia ścieżki eliptycznej.  
  
     Następnie kod ustawia skale fokusu pędzla gradientu ścieżki. Skala ostrości x jest ustawiona na 0,3, a skala ostrości y jest ustawiona na 0,8. Kod wywołuje <xref:System.Drawing.Graphics.TranslateTransform%2A> metodę <xref:System.Drawing.Graphics> obiektu, tak aby <xref:System.Drawing.Graphics.FillPath%2A> kolejne wywołanie wypełnia elipsę, która znajduje się po prawej stronie pierwszej elipsy.  
  
     Aby zobaczyć efekt skal fokusu, wyobraź sobie małą elipsę, która dzieli jego środek z główną elipsą. Mała (wewnętrzna) elipsa jest główną elipsą skalowane (o jej środku) poziomo o współczynnik 0,3 i pionowo o współczynnik 0,8. W miarę przesuwania się od granicy zewnętrznej elipsy do granicy wewnętrznej elipsy kolor zmienia się stopniowo z niebieskiego na aqua. W miarę przesuwania się od granicy wewnętrznej elipsy do wspólnego środka kolor pozostaje wodny.  
  
     Na poniższej ilustracji przedstawiono dane wyjściowe następującego kodu. Elipsa po lewej stronie jest aqua tylko w punkcie centralnym. Elipsa po prawej stronie jest aqua wszędzie wewnątrz wewnętrznej ścieżki.  
  
 ![Efekt gradientu skal fokusu](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>Aby dostosować za pomocą interpolacji  
  
- Innym sposobem dostosowania pędzla gradientu ścieżki jest określenie tablicy kolorów interpolacji i tablicy pozycji interpolacji.  
  
     Poniższy przykład tworzy pędzel gradientu ścieżki na podstawie trójkąta. Kod ustawia <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> właściwość pędzla gradientu ścieżki, aby określić tablicę kolorów interpolacji (ciemnozielony, aqua, niebieski) i tablicy pozycji interpolacji (0, 0,25, 1). Gdy przechodzisz od granicy trójkąta do punktu środkowego, kolor zmienia się stopniowo z ciemnozielonego na aqua, a następnie z aqua na niebieski. Zmiana z ciemnozielonego na aqua odbywa się w 25 procentach odległości od ciemnozielonej do niebieskiej.  
  
     Na poniższej ilustracji przedstawiono trójkąt wypełniony pędzlem gradientu ścieżki niestandardowej.  
  
     ![Trójkąt wypełniony niestandardowym pędzlem gradientu ścieżki.](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Aby ustawić punkt środkowy  
  
- Domyślnie punkt środkowy pędzla gradientu ścieżki znajduje się w centrum ścieżki ścieżki używanej do konstruowania pędzla. Lokalizację punktu środkowego można zmienić, <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> ustawiając <xref:System.Drawing.Drawing2D.PathGradientBrush> właściwość klasy.  
  
     Poniższy przykład tworzy pędzel gradientu ścieżki na podstawie elipsy. Środek elipsy znajduje się na (70, 35), ale punkt środkowy pędzla gradientu ścieżki jest ustawiony na (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     Na poniższej ilustracji przedstawiono wypełnioną elipsę i punkt środkowy pędzla gradientu ścieżki:  
  
     ![Ścieżka gradientu z wypełnioną elipsą i punktem środkowym.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- Punkt środkowy pędzla gradientu ścieżki można ustawić na lokalizację poza ścieżką używaną do konstruowania pędzla. Poniższy przykład zastępuje wywołanie, <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> aby ustawić właściwość w poprzednim kodzie.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     Na poniższej ilustracji przedstawiono dane wyjściowe z tą zmianą:  
  
     ![Ścieżka gradientu z punktem środkowym poza ścieżką.](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     Na poprzedniej ilustracji punkty po prawej stronie elipsy nie są czyste niebieskie (chociaż są bardzo blisko). Kolory gradientu są ustawione tak, jakby wypełnienie osiągnęło punkt (145, 35), gdzie kolor byłby czysty niebieski (0, 0, 255). Ale wypełnienie nigdy nie osiąga (145, 35), ponieważ pędzel gradientu ścieżki maluje tylko wewnątrz ścieżki.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższe przykłady są przeznaczone do użytku z <xref:System.Windows.Forms.PaintEventArgs> `e`formularzami systemu Windows <xref:System.Windows.Forms.Control.Paint> i wymagają , który jest parametrem programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też

- [Używanie pędzla gradientów do wypełniania kształtów](using-a-gradient-brush-to-fill-shapes.md)
