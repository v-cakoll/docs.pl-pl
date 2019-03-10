---
title: 'Instrukcje: Wypełnianie otwartych figur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: e9743d3268a7a2acfb6266872c3346a05269c369
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702736"
---
# <a name="how-to-fill-open-figures"></a>Instrukcje: Wypełnianie otwartych figur
Możesz wpisać ścieżkę, przekazując <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt <xref:System.Drawing.Graphics.FillPath%2A> metody. <xref:System.Drawing.Graphics.FillPath%2A> Metoda wypełni ścieżkę zgodnie z trybu wypełnienia (alternatywne lub zawijania) ustawione dla ścieżki. Jeśli ścieżka zawiera żadnych otwartych figur, ścieżka jest wypełniony, tak jakby te wartości zostały zamknięte. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Zamyka rysunku za pomocą rysowania prostej od punktu końcowego do punktu początkowego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy ścieżkę, która ma co otwartego rysunku (łuk) i jeden figurę zamkniętą (elipsy). <xref:System.Drawing.Graphics.FillPath%2A> Metoda wypełni ścieżkę zgodnie z domyślny tryb wypełnienia, czyli <xref:System.Drawing.Drawing2D.FillMode.Alternate>.  
  
 Poniższa ilustracja przedstawia dane wyjściowe przykładowego kodu. Należy zauważyć, że ścieżka jest wypełniony (zgodnie z opisem w <xref:System.Drawing.Drawing2D.FillMode.Alternate>) tak, jakby figurę otwartą zostało zamkniętych przez linię prostą rysowaną od jej punkt końcowy do punktu początkowego.  
  
 ![Wprowadź ścieżkę otwartą](./media/fillopenpath.png "FillOpenPath")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [Ścieżki grafiki w GDI+](graphics-paths-in-gdi.md)
