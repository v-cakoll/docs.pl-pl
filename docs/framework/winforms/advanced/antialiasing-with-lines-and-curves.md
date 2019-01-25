---
title: Stosowanie antyaliasingu do linii i krzywych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
ms.openlocfilehash: 364dffe3b4b63e3a369f87dd851ab54a975f881a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496247"
---
# <a name="antialiasing-with-lines-and-curves"></a>Stosowanie antyaliasingu do linii i krzywych
Kiedy używasz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Aby narysować linię, podaj punkt początkowy i końcowy punkt wiersza, ale nie należy podać wszystkie informacje dotyczące poszczególnych pikseli w wierszu. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] działa w połączeniu z oprogramowanie sterownik ekranu w celu ustalenia, które piksele zostanie włączona, aby wyświetlić wiersz na urządzeniu określonego.  
  
## <a name="aliasing"></a>Tworzenie aliasów  
 Należy wziąć pod uwagę bezpośrednio czerwoną linię, która przechodzi z punktu (4, 2) w punkcie (16, 10). Założono w układzie współrzędnych pochodzenia w lewym górnym rogu i to jednostka miary piksela. Również założono osi x punktów w dół po prawej stronie i punktach osi y. Na poniższej ilustracji przedstawiono rozszerzonej czerwoną linią rysowana na tle różnych kolorach.  
  
 ![Wiersz, bez antialiasingu](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")  
  
 Czerwony pikseli, używany do renderowania wiersza są nieprzezroczyste. W wierszu nie ma bez częściowo przezroczyste pikseli. Tego typu linii renderowania udostępnia wiersz nieregularne wygląd, a wiersz wygląda nieco takich jak klatka schodowa. Ta technika reprezentować linii z klatka schodowa nazywa się tworzenie aliasów; klatka schodowa jest aliasem dla teoretycznych wiersza.  
  
## <a name="antialiasing"></a>Antyaliasing  
 Bardziej zaawansowanych technik do renderowania linię pociąga za sobą przy użyciu częściowo przezroczyste piksele wraz z nieprzezroczyste pikseli. Pikseli są ustawione na czerwony czysty, lub do niektórych programu blend czerwony i kolor tła zależności od tego, jak blisko są do wiersza. Tego rodzaju renderowania nosi nazwę antialiasingu i wyników w wierszu, który ludzkiego oka uświadamia sobie, jak bardziej bezproblemowe. Poniższa ilustracja przedstawia, jak niektórych pikseli są mieszane w tle do wyprodukowania antialiased linii.  
  
 ![Antyaliasingu do linii](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")  
  
 Antyaliasing, nazywany również wygładzanie, można zastosować również na krzywe. Na poniższej ilustracji przedstawiono rozszerzonej wygładzone elipsy.  
  
 ![Antyaliasing krzywych](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")  
  
 Poniższa ilustracja przedstawia ten sam elipsy w rzeczywisty rozmiar, jeden raz bez antialiasingu i drugi raz antialiasingu.  
  
 ![Przykład antialiasingu](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")  
  
 Rysowanie linii i krzywych, których stosowanie antyaliasingu do, Utwórz wystąpienie obiektu <xref:System.Drawing.Graphics> klasy i ustaw jego <xref:System.Drawing.Graphics.SmoothingMode%2A> właściwości <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> lub <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>. Następnie wywołać jedną z metod rysowania tego samego <xref:System.Drawing.Graphics> klasy.  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>
- [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [Instrukcje: Stosowanie antyaliasingu do tekstu](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)
