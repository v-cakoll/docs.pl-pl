---
title: Struktura interfejsu grafiki
ms.date: 03/30/2017
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
ms.openlocfilehash: d3b16249b6bae4a113661f5a3a47097046ba20f1
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505268"
---
# <a name="structure-of-the-graphics-interface"></a>Struktura interfejsu grafiki
Klasa zarządzana interfejs GDI + zawiera około 60 klas, 50 wyliczenia i struktury 8. <xref:System.Drawing.Graphics> Klasy jest sercem funkcje interfejsu GDI +; jest to klasa, która faktycznie rysuje linie, krzywe, rysunki, obrazów i tekstu.  
  
## <a name="important-classes"></a>Ważne klas  
 Wiele klas pracować razem <xref:System.Drawing.Graphics> klasy. Na przykład <xref:System.Drawing.Graphics.DrawLine%2A> metoda otrzymuje <xref:System.Drawing.Pen> obiektu, który zawiera atrybuty (kolor, szerokość, Styl kreskowania i podobne) wiersz, który ma być rysowany. <xref:System.Drawing.Graphics.FillRectangle%2A> Metoda może odbierać wskaźnik do <xref:System.Drawing.Drawing2D.LinearGradientBrush> obiektu, który współdziała z <xref:System.Drawing.Graphics> obiekt, aby wypełnić prostokąt kolorem stopniowo zmiany. <xref:System.Drawing.Font> i <xref:System.Drawing.StringFormat> obiekty mają wpływ na sposób <xref:System.Drawing.Graphics> obiektu rysuje tekst. A <xref:System.Drawing.Drawing2D.Matrix> obiekt przechowuje i obsługuje transformacji świata z <xref:System.Drawing.Graphics> obiektu, który służy do obracania, skalowanie i przerzucanie obrazów.  
  
 GDI + zapewnia kilka struktur (na przykład <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, i <xref:System.Drawing.Size>) służący do organizowania danych grafiki. Ponadto niektórych klas służyć przede wszystkim jako strukturą typów danych. Na przykład <xref:System.Drawing.Imaging.BitmapData> klasa jest pomocnika dla <xref:System.Drawing.Bitmap> klasy i <xref:System.Drawing.Drawing2D.PathData> klasa jest pomocnika dla <xref:System.Drawing.Drawing2D.GraphicsPath> klasy.  
  
 GDI + definiuje kilka wyliczenia, które są kolekcjami pokrewnych stałych. Na przykład <xref:System.Drawing.Drawing2D.LineJoin> wyliczenia zawiera elementy <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, i <xref:System.Drawing.Drawing2D.LineJoin.Round>, które określą style, które mogą służyć do dołączenia do dwóch wierszy.  
  
## <a name="see-also"></a>Zobacz także

- [Grafika — omówienie](graphics-overview-windows-forms.md)
- [Informacje o kodzie zarządzanym GDI+](about-gdi-managed-code.md)
- [Używanie zarządzanych klas grafiki](using-managed-graphics-classes.md)
