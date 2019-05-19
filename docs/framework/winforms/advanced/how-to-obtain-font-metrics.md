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
ms.openlocfilehash: 75177b609f14d335aa57aba77d647827f50a8692
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881852"
---
# <a name="how-to-obtain-font-metrics"></a>Instrukcje: Uzyskiwanie miar czcionek
<xref:System.Drawing.FontFamily> Klasa udostępnia następujące metody, które pobierają różne metryki dla kombinacji określonej rodziny/styl:  
  
- <xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)  
  
- <xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)  
  
- <xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)  
  
- <xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)  
  
 Liczby zwrócone przez te metody są w jednostkach projektowania czcionki, dzięki czemu są one niezależne od rozmiaru i jednostki określonego <xref:System.Drawing.Font> obiektu.  
  
 Na poniższej ilustracji przedstawiono różne metryki:
  
 ![Ilustracja miar czcionek: ascent, zejścia i wierszami.](./media/how-to-obtain-font-metrics/various-font-metrics.png)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia metryki dla stylu normalnego rodziny czcionek Arial. Tworzy również kod <xref:System.Drawing.Font> obiektu (oparte na Arial rodziny) o rozmiarze 16 pikseli i wyświetla metryki (w pikselach) dla konkretnego <xref:System.Drawing.Font> obiektu.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe przykładowego kodu:
  
 ![Przykładowe dane wyjściowe kodu czcionka Arial metryk.](./media/how-to-obtain-font-metrics/example-output-code-arial-font.png)  
  
 Należy pamiętać, pierwsze dwa wiersze danych wyjściowych na poprzedniej ilustracji. <xref:System.Drawing.Font> Zwraca rozmiar 16 i <xref:System.Drawing.FontFamily> zwraca wysokość em 2048. Te dwie wartości (16 i 2048) są kluczem do konwersji między jednostkami projektowania czcionki i jednostek (w tym przypadku pikselach) <xref:System.Drawing.Font> obiektu.  
  
 Na przykład możesz przekształcić wzrastająca od projektowania jednostek do pikseli w następujący sposób:  
  
 ![Formuła przedstawiający Konwersja jednostki projektu do pikseli](./media/how-to-obtain-font-metrics/convert-font-units-example.png)  
  
 Poniższy kod ustawia położenie tekstu w pionie, ustawiając <xref:System.Drawing.PointF.Y%2A> element członkowski danych <xref:System.Drawing.PointF> obiektu. Współrzędna y jest zwiększana o `font.Height` dla każdego nowego wiersza tekstu. <xref:System.Drawing.Font.Height%2A> Właściwość <xref:System.Drawing.Font> zwraca wierszami (w pikselach) dotyczące konkretnego <xref:System.Drawing.Font> obiektu. W tym przykładzie numer zwrócone przez <xref:System.Drawing.Font.Height%2A> jest 19. Należy pamiętać, że jest taki sam jak numer (z zaokrągleniem do liczby całkowitej), uzyskanego konwertując metryki odstępów między wierszami pikseli.  
  
 Należy pamiętać, że wysokość em (nazywane również rozmiar rozmiar lub em) nie jest sumą i zejścia. Suma i zejścia nosi nazwę wysokość komórki. Wysokość komórki minus wiodących wewnętrznego jest równa wysokość em. Wysokość komórki, a także wiodących zewnętrznych jest równe odstępy.  
  
 [!code-csharp[System.Drawing.FontsAndText#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także

- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Używanie czcionek i tekstu](using-fonts-and-text.md)
