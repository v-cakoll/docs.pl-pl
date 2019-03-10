---
title: 'Instrukcje: Stosowanie korekcji Gamma do gradientu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
ms.openlocfilehash: e7205058bc2b93ac453b8c37bfc8d5236433158d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708092"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>Instrukcje: Stosowanie korekcji Gamma do gradientu
Możesz włączyć korekcji gamma pędzel gradientów liniowych, ustawiając pędzla <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> właściwość `true`. Korekcja gamma można wyłączyć, ustawiając <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> właściwość `false`. Korekcja gamma jest domyślnie wyłączona.  
  
## <a name="example"></a>Przykład  
 W przykładzie utworzono pędzel gradientów liniowych i używa tego pędzla do wypełniania dwoma prostokątami. Pierwszy prostokąt zostanie wypełnione bez korekcji gamma, a drugi prostokąta jest wypełniany korekcji gamma.  
  
 Poniższa ilustracja przedstawia dwoma prostokątami wypełniony. Najważniejsze prostokąt, którego nie ma korekcji gamma, pojawi się ciemny w środku. Prostokąt dolnej, mającej korekcja gamma wydaje się mieć więcej intensywność jednolite.  
  
 ![Gradient](./media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Drawing2D.LinearGradientBrush>
- [Używanie pędzla gradientów do wypełniania kształtów](using-a-gradient-brush-to-fill-shapes.md)
