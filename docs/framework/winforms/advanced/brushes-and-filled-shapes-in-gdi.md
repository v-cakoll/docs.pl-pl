---
title: "Pędzle i wypełnione kształty w GDI+"
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
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01d7359499c858ad7c4f1da2fa24f18e801bb324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>Pędzle i wypełnione kształty w GDI+
Kształt zamknięty, takich jak prostokąta lub elipsy składa się z konspektu i wewnętrzne. Konspekt jest rysowane przy użyciu pióra i wewnętrznych jest wypełniony pędzla. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]udostępnia kilka klas pędzla do wypełniania wnętrza kształty zamknięte: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, i <xref:System.Drawing.Drawing2D.PathGradientBrush>. Wszystkie te klasy dziedziczy <xref:System.Drawing.Brush> klasy. Na poniższej ilustracji przedstawiono wypełniony prostokąt z pędzla pełnego koloru i elipsy wypełniany pędzla kreskowania.  
  
 ![Wypełnione kształty](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>Pędzle stałych  
 Aby wypełnić kształt zamknięty, należy wystąpienie <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Brush>. Wystąpienie <xref:System.Drawing.Graphics> klasa dostarcza metody, takie jak <xref:System.Drawing.Graphics.FillRectangle%2A> i <xref:System.Drawing.Graphics.FillEllipse%2A>i <xref:System.Drawing.Brush> przechowuje atrybuty wypełnienia, takie jak kolor i wzorzec. <xref:System.Drawing.Brush> Jest przekazywany jako argumenty do metody fill. W poniższym przykładzie przedstawiono sposób wypełnienia elipsy jednolitym kolorem czerwonym.  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  W powyższym przykładzie pędzla jest typu <xref:System.Drawing.SolidBrush>, który dziedziczy z <xref:System.Drawing.Brush>.  
  
## <a name="hatch-brushes"></a>Pędzlami ze stylem kreskowania  
 Po wypełnieniu kształtu przy użyciu pędzla kreskowania Określ kolor pierwszego planu, kolor tła i Styl kreskowania. Kolor pierwszego planu jest kolor kreskowaniu.  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]zawiera więcej niż 50 Styl kreskowania; są trzy style pokazano na poniższej ilustracji <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, i <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.  
  
 ![Wypełnione kształty](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>Pędzle z fakturą  
 Przy użyciu pędzla tekstury można wypełnianie kształtów wzorem przechowywane mapy bitowej. Załóżmy na przykład, następujący obraz jest przechowywany w pliku dysku o nazwie `MyTexture.bmp`.  
  
 ![Wypełniony kształt](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 Poniższy przykładowy kod przedstawia sposób wypełnienia elipsy powtarzając obraz przechowywany w `MyTexture.bmp`.  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 Na poniższej ilustracji przedstawiono wypełnioną elipsę.  
  
 ![Wypełniony kształt](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>Pędzle gradientów  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]zawiera dwa rodzaje pędzle gradientów: liniowej i ścieżkę. Wypełnianie kształtów z kolor, który zmienia się stopniowo przenoszenia między kształtu w poziomie, w pionie albo pod kątem umożliwia pędzla gradientu liniowego. Poniższy przykład kodu pokazuje, jak umożliwia wypełnienie elipsy pędzla gradientów poziomie zmieni się z blue zielony, jak przenieść od lewej krawędzi elipsy do prawej krawędzi.  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 Na poniższej ilustracji przedstawiono wypełnioną elipsę.  
  
 ![Wypełniony kształt](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 Aby zmienić kolor, jak przenieść z Centrum kierunku krawędzi kształtu można skonfigurować pędzla gradientu ścieżki.  
  
 ![Wypełniony kształt](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 Pędzle gradientów ścieżki są bardzo elastyczne. Pędzla gradientu używany do wypełniania trójkąt następujące zmiany ilustracji stopniowo z czerwonego w Centrum do każdego z trzech różnych kolorach na wierzchołków.  
  
 ![Wypełniony kształt](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Porady: Rysowanie wypełnionego prostokąta w formularzu systemu Windows](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)  
 [Porady: Rysowanie wypełnionej elipsy w formularzu systemu Windows](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)
