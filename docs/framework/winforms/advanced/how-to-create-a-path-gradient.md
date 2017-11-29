---
title: "Porady: tworzenie gradientu ścieżki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6222b22ea0bb38ea95304d43a6dab0deee0d2d05
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-path-gradient"></a>Porady: tworzenie gradientu ścieżki
<xref:System.Drawing.Drawing2D.PathGradientBrush> Klasa umożliwia dostosowanie sposób wypełnienia kształtu z stopniowo zmiana kolorów. Na przykład można określić jeden kolor Centrum ścieżki i innym kolorze dla granicy ścieżki. Można również określić różne kolory dla każdego z kilku punktów wzdłuż granicy ścieżki.  
  
> [!NOTE]
>  W [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], ścieżki jest sekwencją linii i krzywych obsługiwanego przez <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu. Aby uzyskać więcej informacji na temat [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ścieżki, zobacz [ścieżki grafiki w GDI +](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md) i [Constructing i rysowanie ścieżek](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md).  
  
### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Aby wypełnić elipsy gradientu ścieżki  
  
-   Poniższy przykład wypełnia elipsę z pędzla gradientu ścieżki. Kolor jest ustawiona na niebieski i kolor granic ustawiono Akwamaryna. Na poniższej ilustracji przedstawiono wypełnioną elipsę.  
  
     ![Ścieżka gradientu](../../../../docs/framework/winforms/advanced/media/pathgradient1.png "pathgradient1")  
  
     Domyślnie pędzla gradientu ścieżki nie rozciąga się poza granicami ścieżki. Jeśli używasz pędzla gradientu ścieżki do wypełnienia rysunku, która wykracza poza granice ścieżki obszaru ekranu poza ścieżka nie zostanie wypełnione.  
  
     Na poniższej ilustracji pokazano, co się stanie w przypadku zmiany <xref:System.Drawing.Graphics.FillEllipse%2A> wywołania w następujący kod do `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`.  
  
     ![Ścieżka gradientu](../../../../docs/framework/winforms/advanced/media/pathgradient2.png "pathgradient2")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     W poprzednim przykładzie kodu jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> e, który jest parametrem elementu <xref:System.Windows.Forms.PaintEventHandler>.  
  
### <a name="to-specify-points-on-the-boundary"></a>Określ punkty na granicy  
  
-   Poniższy przykład tworzy pędzla gradientu ścieżki ze ścieżki w kształcie gwiazdy. Ustawia kod <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> właściwość, która ustawia kolor na centroidę wzdłuż gwiazdy na czerwony. A następnie ustawia kod <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> właściwość, aby określić różne kolory (przechowywane w `colors` tablicy) w poszczególnych punktach `points` tablicy. Instrukcja kodu końcowego wypełnia ścieżka kształcie gwiazdy z pędzla gradientu ścieżki.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
-   Poniższy przykład rysuje gradientu ścieżki bez <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu w kodzie. Szczególne <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> konstruktora w przykładzie odbiera tablicę punkty, ale nie jest wymagane <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu. Ponadto należy pamiętać, że <xref:System.Drawing.Drawing2D.PathGradientBrush> jest używany do wypełniania prostokąta, nie ścieżką. Prostokąt jest większy niż ścieżki zamkniętej używane do definiowania pędzla, więc niektóre prostokąta nie jest rysowane przez pędzla. Na poniższej ilustracji przedstawiono prostokąt (linia przerywana) i część prostokąt malowane przez pędzla gradientu ścieżki.  
  
     ![Gradient](../../../../docs/framework/winforms/advanced/media/gradient4.png "gradient4")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Aby dostosować gradientu ścieżki  
  
-   Pierwszym sposobem dostosowania pędzla gradientu ścieżki jest skonfigurowanie jej <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> właściwości. Skaluje fokus Określ wewnętrzny znajdująca się wewnątrz ścieżki głównego. Kolor jest wyświetlany wszędzie wewnątrz tej ścieżki wewnętrznego, a nie tylko na punktu centralnego.  
  
     Poniższy przykład tworzy pędzla gradientu ścieżki na podstawie ścieżki eliptycznej. Kod ustawia kolor granic na niebieski, ustawia kolor Akwamaryna, a następnie używa pędzla gradientu ścieżki do wypełnienia eliptycznej ścieżki.  
  
     Następnie kod ustawia skale fokus pędzla gradientu ścieżki. Skala fokus x ma ustawioną wartość 0,3 i skali fokus y ma ustawioną wartość 0,8. Kod wywołuje <xref:System.Drawing.Graphics.TranslateTransform%2A> metody <xref:System.Drawing.Graphics> obiekt, aby kolejne wywołanie <xref:System.Drawing.Graphics.FillPath%2A> wypełnia elipsy, która znajduje się na prawo od pierwszego elipsy.  
  
     Aby zobaczyć efekt skali fokus, załóżmy małych elipsy, który współużytkuje środka z głównym elipsy. Mały (wewnętrzny) elipsy jest głównym elipsy skalowania (o jego center) w poziomie przez współczynnik 0,3 i w pionie przez współczynnik 0,8. Podczas przenoszenia z granic zewnętrzne elipsy do granicy wewnętrzny elipsy zmienia kolor stopniowo z niebieski do Akwamaryna. Jak przenieść z granic wewnętrzny elipsy do udostępnionego Centrum Akwamaryna pozostaje kolorów.  
  
     Na poniższej ilustracji przedstawiono dane wyjściowe poniższy kod. Elipsy po lewej stronie jest Akwamaryna tylko na punktu centralnego. Wielokropka po prawej stronie jest Akwamaryna wszędzie wewnątrz ścieżki wewnętrzny.  
  
 ![Gradient](../../../../docs/framework/winforms/advanced/media/focusscales1nogamma.png "focusscales1NoGamma")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>Aby dostosować z interpolacji  
  
-   Innym sposobem dostosowania pędzla gradientu ścieżki jest określenie tablicę interpolacji kolorów i pozycji interpolacji tablicy.  
  
     Poniższy przykład tworzy pędzla gradientu ścieżki oparte na trójkąt. Ustawia kod <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> właściwość pędzla gradientu ścieżki, aby określić tablicę interpolacji kolorów (zielony ciemny, Akwamaryna, niebieski) i tablicę pozycji interpolacji (0, 0,25, 1). Jak przenieść z granic trójkąta punktu centralnego zmienia kolor stopniowo od ciemnym zielony Akwamaryna, a następnie z Akwamaryna na niebieski. Zmiana od ciemnym zielony Akwamaryna odbywa się w 25 procent odległość od ciemnym zielonego na niebieski.  
  
     Na poniższej ilustracji przedstawiono trójkąt wypełnione pędzla gradientu ścieżki niestandardowej.  
  
     ![Ścieżka gradientu](../../../../docs/framework/winforms/advanced/media/pathgradient4.png "pathgradient4")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Aby ustawić punktu centralnego.  
  
-   Domyślnie punktu centralnego pędzla gradientu ścieżki jest centroidę wzdłuż ścieżki używany do budowy pędzla. Możesz zmienić lokalizację punktu centralnego przez ustawienie <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> właściwość <xref:System.Drawing.Drawing2D.PathGradientBrush> klasy.  
  
     Poniższy przykład tworzy pędzla gradientu ścieżki oparte na elipsy. Centrum elipsy wynosi (70, 35), ale ustawiono punktu centralnego pędzla gradientu ścieżki (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     Na poniższej ilustracji przedstawiono wypełnioną elipsę i punktu centralnego pędzla gradientu ścieżki.  
  
     ![Ścieżka gradientu](../../../../docs/framework/winforms/advanced/media/pathgradient5.png "pathgradient5")  
  
-   Można ustawić punktu centralnego pędzla gradientu ścieżki do lokalizacji poza ścieżką, która została użyta do skonstruowania pędzla. Poniższy przykład zastępuje wywołanie ustawiania <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> właściwości w powyższym kodzie.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     Na poniższej ilustracji przedstawiono dane wyjściowe z tą zmianą.  
  
     ![Ścieżka gradientu](../../../../docs/framework/winforms/advanced/media/pathgradient6.png "pathgradient6")  
  
     Na powyższej ilustracji punkty na prawym końcu elipsy nie są czysty blue, (chociaż są one bardzo Zamknij). Kolory gradientu są pozycjonowane tak, jakby wypełnienia osiągnięty punkt (145, 35), gdy jest kolor niebieski czysty (0, 0, 255). Ale nigdy nie osiągnie wypełnienia (145, 35), ponieważ ścieżka pędzla gradientu rysują tylko wewnątrz ścieżki.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższych przykładach są przeznaczone do użytku z formularzy systemu Windows, a potrzebują <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie pędzla gradientów do wypełniania kształtów](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
