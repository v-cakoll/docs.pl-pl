---
title: 'Instrukcje: Uzyskiwanie miar czcionek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
ms.openlocfilehash: 24cada3962339cae0608bbe01e070a0b8e256e73
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119057"
---
# <a name="how-to-obtain-font-metrics"></a>Instrukcje: Uzyskiwanie miar czcionek
<xref:System.Drawing.FontFamily> Klasa udostępnia następujące metody, które pobierają różne metryki dla kombinacji określonej rodziny/styl:  
  
-   <xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)  
  
 Liczby zwrócone przez te metody są w jednostkach projektowania czcionki, dzięki czemu są one niezależne od rozmiaru i jednostki określonego <xref:System.Drawing.Font> obiektu.  
  
 Poniższa ilustracja przedstawia różne metryki.  
  
 ![Czcionki tekstu](./media/fontstext7a.png "fontstext7A")  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia metryki dla stylu normalnego rodziny czcionek Arial. Tworzy również kod <xref:System.Drawing.Font> obiektu (oparte na Arial rodziny) o rozmiarze 16 pikseli i wyświetla metryki (w pikselach) dla konkretnego <xref:System.Drawing.Font> obiektu.  
  
 Poniższa ilustracja przedstawia dane wyjściowe przykładowego kodu.  
  
 ![Fonts Text](./media/csfontstext8.png "csFontsText8")  
  
 Należy pamiętać, pierwsze dwa wiersze danych wyjściowych na poprzedniej ilustracji. <xref:System.Drawing.Font> Zwraca rozmiar 16 i <xref:System.Drawing.FontFamily> zwraca wysokość em 2048. Te dwie wartości (16 i 2048) są kluczem do konwersji między jednostkami projektowania czcionki i jednostek (w tym przypadku pikselach) <xref:System.Drawing.Font> obiektu.  
  
 Na przykład możesz przekształcić wzrastająca od projektowania jednostek do pikseli w następujący sposób:  
  
 ![Czcionki tekstu](./media/fontstext9.png "FontsText9")  
  
 Poniższy kod ustawia położenie tekstu w pionie, ustawiając <xref:System.Drawing.PointF.Y%2A> element członkowski danych <xref:System.Drawing.PointF> obiektu. Współrzędna y jest zwiększana o `font.Height` dla każdego nowego wiersza tekstu. <xref:System.Drawing.Font.Height%2A> Właściwość <xref:System.Drawing.Font> zwraca wierszami (w pikselach) dotyczące konkretnego <xref:System.Drawing.Font> obiektu. W tym przykładzie numer zwrócone przez <xref:System.Drawing.Font.Height%2A> jest 19. Należy pamiętać, że jest taki sam jak numer (z zaokrągleniem do liczby całkowitej), uzyskanego konwertując metryki odstępów między wierszami pikseli.  
  
 Należy pamiętać, że wysokość em (nazywane również rozmiar rozmiar lub em) nie jest sumą i zejścia. Suma i zejścia nosi nazwę wysokość komórki. Wysokość komórki minus wiodących wewnętrznego jest równa wysokość em. Wysokość komórki, a także wiodących zewnętrznych jest równe odstępy.  
  
 [!code-csharp[System.Drawing.FontsAndText#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także

- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Używanie czcionek i tekstu](using-fonts-and-text.md)
