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
ms.openlocfilehash: 45ef0b5920e43300e047d363149ea10a7833477b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912230"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>Pędzle i wypełnione kształty w GDI+
Kształt zamknięty, taki jak prostokąt lub Elipsa, składa się z konspektu i wnętrza. Konspekt jest rysowany piórem, a wnętrze jest wypełnione pędzlem. Interfejs GDI+ zapewnia kilka klas pędzla do wypełniania wnętrza zamkniętych <xref:System.Drawing.SolidBrush>kształtów <xref:System.Drawing.Drawing2D.HatchBrush>: <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>,, <xref:System.Drawing.Drawing2D.PathGradientBrush>i. Wszystkie te klasy dziedziczą z <xref:System.Drawing.Brush> klasy. Na poniższej ilustracji przedstawiono prostokąt wypełniony pędzlem Solid i elipsą wypełnioną pędzlem.  
  
 ![Wypełnione kształty](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>Pełne pędzle  
 Aby wypełnić zamknięty kształt, potrzebujesz wystąpienia <xref:System.Drawing.Graphics> klasy <xref:System.Drawing.Brush>i. Wystąpienie <xref:System.Drawing.Graphics> klasy zawiera metody, takie jak <xref:System.Drawing.Graphics.FillRectangle%2A> i <xref:System.Drawing.Graphics.FillEllipse%2A>, oraz <xref:System.Drawing.Brush> atrybuty przechowywane wypełnienia, takie jak Color i Pattern. <xref:System.Drawing.Brush> Jest przenoszona jako jeden z argumentów metody Fill. Poniższy przykład kodu pokazuje, jak wypełnić elipsę wypełnionym czerwonym kolorem.  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
> W poprzednim przykładzie Pędzel jest typu <xref:System.Drawing.SolidBrush>, który dziedziczy z. <xref:System.Drawing.Brush>  
  
## <a name="hatch-brushes"></a>Pędzle kreskowania  
 Po wypełnieniu kształtu pędzlem kreskowym należy określić kolor pierwszego planu, kolor tła i styl kreskowania. Kolor pierwszego planu jest kolorem wylęgu.  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 Interfejs GDI+ zapewnia więcej niż 50 stylów kreskowania; trzy style pokazane na poniższej ilustracji <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal> <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>:, i <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.  
  
 ![Wypełnione kształty](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>Pędzle tekstury  
 Pędzel tekstury umożliwia wypełnienie kształtu wzorcem przechowywanym w mapie bitowej. Załóżmy na przykład, że następujący obraz jest przechowywany w pliku dysku o nazwie `MyTexture.bmp`.  
  
 ![Wypełniony kształt](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 Poniższy przykład kodu pokazuje, jak wypełnić wielokropek przez powtórzenie obrazu przechowywanego w `MyTexture.bmp`.  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 Na poniższej ilustracji przedstawiono wypełnioną elipsę.  
  
 ![Wypełniony kształt](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>Pędzle gradientowe  
 Interfejs GDI+ zapewnia dwa rodzaje pędzli gradientu: liniowe i ścieżki. Można użyć gradientowego pędzla, aby wypełnić kształt kolorem, który zmienia się stopniowo w miarę poruszania się w obrębie kształtu w poziomie, w pionie lub ukośnie. Poniższy przykład kodu pokazuje, jak wypełnić elipsę w poziomym pędzlu gradientu, który zmienia się z niebieski na zielony podczas przesuwania od lewej krawędzi elipsy do prawej krawędzi.  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 Na poniższej ilustracji przedstawiono wypełnioną elipsę.  
  
 ![Wypełniony kształt](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 Pędzel gradientu ścieżki można skonfigurować tak, aby zmieniał kolor podczas przenoszenia z środka kształtu do krawędzi.  
  
 ![Wypełniony kształt](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 Pędzle gradientowe ścieżki są dość elastyczne. Pędzel gradientu używany do wypełnienia trójkąta na poniższej ilustracji zmienia się stopniowo z czerwonego w środku do każdego z trzech różnych kolorów na wierzchołkach.  
  
 ![Wypełniony kształt](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [Linie, krzywe i kształty](lines-curves-and-shapes.md)
- [Instrukcje: Rysowanie wypełnionego prostokąta w formularzu systemu Windows](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [Instrukcje: Rysowanie wypełnionej elipsy w formularzu systemu Windows](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
