---
title: Pędzle i wypełnione kształty w GDI+
ms.date: 03/30/2017
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
ms.openlocfilehash: fc6d6857e912ba14fca382eb49373655004534d5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720946"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>Pędzle i wypełnione kształty w GDI+
Kształt zamknięty, takich jak prostokąta lub elipsy, składa się z konturem i wewnętrzne. Konspekt jest rysowany przy użyciu pióra i wewnętrznych jest wypełniany pędzla. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] dostarcza kilka klas, pędzla do wypełniania wnętrza kształty zamknięte: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, i <xref:System.Drawing.Drawing2D.PathGradientBrush>. Wszystkie te klasy dziedziczy <xref:System.Drawing.Brush> klasy. Na poniższej ilustracji pokazuje prostokąt wypełnione pędzla i elipsy wypełnione przy użyciu kreskowania pędzla.  
  
 ![Wypełnione kształty](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>Stałe pędzli  
 Do wypełnienia kształtu zamkniętego, potrzebne jest wystąpienie <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Brush>. Wystąpienie <xref:System.Drawing.Graphics> klasa dostarcza metody, takie jak <xref:System.Drawing.Graphics.FillRectangle%2A> i <xref:System.Drawing.Graphics.FillEllipse%2A>i <xref:System.Drawing.Brush> przechowuje atrybuty wypełnienia, takich jak kolor lub deseń. <xref:System.Drawing.Brush> Jest przekazywany jako argumenty do metody fill. Poniższy przykład kodu pokazuje sposób wypełniania elipsę jednolitym kolorem czerwonym.  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  W powyższym przykładzie Pędzel, jest typu <xref:System.Drawing.SolidBrush>, który dziedziczy z <xref:System.Drawing.Brush>.  
  
## <a name="hatch-brushes"></a>Pędzlami ze stylem kreskowania  
 Po wypełnieniu kształtu przy użyciu kreskowania pędzla, można określić kolor pierwszego planu, kolor tła i Styl kreskowania. Kolor pierwszego planu jest kolor kreskowaniu.  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zawiera więcej niż 50 Styl kreskowania; są trzy style pokazano na poniższej ilustracji <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, i <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.  
  
 ![Wypełnione kształty](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>Pędzle z fakturą  
 Pędzlem tekstury można wypełnianie kształtów wzorem przechowywany w mapie bitowej. Załóżmy na przykład, poniższy obraz jest przechowywany w pliku dysku o nazwie `MyTexture.bmp`.  
  
 ![Wypełniony kształt](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 Poniższy przykład kodu pokazuje, jak wypełnić elipsy, powtarzając zdjęcie na `MyTexture.bmp`.  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 Poniższa ilustracja przedstawia wypełnioną elipsę.  
  
 ![Wypełniony kształt](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>Pędzle gradientów  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zawiera dwa rodzaje pędzle gradientów: liniowej i ścieżkę. Pędzel gradientów liniowych służy do wypełnienia kształtu zmienia stopniowo podczas przenoszenia między kształtu w poziomie, w pionie lub po przekątnej kolorem. Poniższy przykład kodu pokazuje sposób wypełniania elipsę z poziomy pędzla gradientu, który zmienia się pomiędzy niebieski zielony, po przeniesieniu od lewej krawędzi elipsy do prawej krawędzi.  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 Poniższa ilustracja przedstawia wypełnioną elipsę.  
  
 ![Wypełniony kształt](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 Pędzel gradientu ścieżki można skonfigurować tak, aby zmienić kolor w czasie poruszania się w Centrum w kierunku krawędzi kształtu.  
  
 ![Wypełniony kształt](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 Pędzle gradientów ścieżki są bardzo elastyczne. Pędzel gradientów, używany do wypełniania trójkąt następujące zmiany ilustracji stopniowo z red w środku do każdego z trzech różnych kolorów w wierzchołków.  
  
 ![Wypełniony kształt](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [Linie, krzywe i kształty](lines-curves-and-shapes.md)
- [Instrukcje: Rysuj wypełniony prostokąt w formularzu Windows](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [Instrukcje: Rysuj wypełnioną elipsę w formularzu Windows](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
