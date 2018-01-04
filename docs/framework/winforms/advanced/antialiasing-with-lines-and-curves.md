---
title: Stosowanie antyaliasingu do linii i krzywych
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
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8552f185a93b688555dbcfab3da9d28d9bfde6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="antialiasing-with-lines-and-curves"></a>Stosowanie antyaliasingu do linii i krzywych
Jeśli używasz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] do rysowania linii, podaj punkt początkowy i końcowy punkt wiersza, ale nie musisz podać wszystkie informacje o poszczególnych pikseli w wierszu. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]działa w połączeniu z oprogramowaniem sterownik ekranu do określenia, które piksele zostanie włączona do wyświetlenia na urządzeniu określonego wiersza.  
  
## <a name="aliasing"></a>Aliasów  
 Należy wziąć pod uwagę wprost red wiersza, który jest przesyłany z punktu (4, 2) w punkcie (16, 10). Przykładowa współrzędnych ma swoją witryną źródłową w lewym górnym rogu i że jednostka miary piksela. Założono także osi x punktów w dół w prawo i w punktach osi y. Na poniższej ilustracji przedstawiono powiększania widoku czerwona linia rysowana na tle różnych kolorach.  
  
 ![Wiersz, bez antialiasingu](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")  
  
 Czerwony pikseli, używany do renderowania wiersza są nieprzezroczyste. W wierszu nie ma żadnych częściowo przezroczyste pikseli. Tego typu linii renderowania daje wiersza nieregularne wygląd i wiersz wygląda nieco jak klatka schodowa. Ta technika reprezentujących linię o klatka schodowa nosi nazwę aliasów; klatka schodowa jest aliasem teoretycznego wiersza.  
  
## <a name="antialiasing"></a>Antialiasingu  
 Bardziej zaawansowane techniki renderowania linii polega na użyciu częściowo przezroczyste piksele wraz z nieprzezroczyste pikseli. Pikseli są ustawione na czysty czerwony, lub do niektórych blend czerwony i kolor tła, w zależności od sposobu Zamknij znajdują się w wierszu. Ten typ renderowania nosi antialiasingu i powoduje linii ludzkiego oka przewiduje jako bardziej smooth. Na poniższej ilustracji przedstawiono, jak niektórych pikseli są mieszane do wyprodukowania linii antyaliasowany w tle.  
  
 ![Antialiasing linii](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")  
  
 Antialiasing, nazywany również wygładzanie, dotyczą również krzywych. Na poniższej ilustracji przedstawiono powiększania widoku wygładzonymi elipsy.  
  
 ![Krzywe antialiasingu](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")  
  
 Na poniższej ilustracji przedstawiono tego samego elipsy w rozmiarze rzeczywistym bez antialiasingu i drugi raz z antialiasingu.  
  
 ![Przykład antialiasingu](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")  
  
 Rysowanie linii i krzywych, które używają antialiasingu, Utwórz wystąpienie <xref:System.Drawing.Graphics> klasy i ustawić jej <xref:System.Drawing.Graphics.SmoothingMode%2A> właściwości <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> lub <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>. Następnie wywołaj jednej z metod rysowania tego samego <xref:System.Drawing.Graphics> klasy.  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Instrukcje: stosowanie antyaliasingu do tekstu](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)
