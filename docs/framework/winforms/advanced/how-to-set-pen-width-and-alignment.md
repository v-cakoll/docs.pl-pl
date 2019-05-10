---
title: 'Instrukcje: Ustawianie szerokości i wyrównania pióra'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: 1f1ea6e8ef0b94aa46a4bf8177d59e59297d6e3f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605835"
---
# <a name="how-to-set-pen-width-and-alignment"></a>Instrukcje: Ustawianie szerokości i wyrównania pióra
Po utworzeniu <xref:System.Drawing.Pen>, szerokość pióra można podać jako jeden z argumentów do konstruktora. Możesz również zmienić szerokość z <xref:System.Drawing.Pen.Width%2A> właściwość <xref:System.Drawing.Pen> klasy.  
  
 Teoretyczna wiersz ma szerokość 0. Po narysowaniu linii, o szerokości 1 piksela, pikseli jest wyśrodkowywana teoretycznych wiersza. Po narysowaniu linii z więcej niż jeden piksel szeroką, piksele albo jest wyśrodkowywana w wierszu teoretycznych lub pojawiają się obok wiersza teoretycznych. Można ustawić właściwości wyrównania pióra <xref:System.Drawing.Pen> Aby ustalić położenie pikseli narysowany przy tym pióra względem teoretycznych wierszy.  
  
 Wartości <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, i <xref:System.Drawing.Drawing2D.PenAlignment.Inset> są widoczne w następujące przykłady kodu są elementami członkowskimi <xref:System.Drawing.Drawing2D.PenAlignment> wyliczenia.  
  
 Poniższy kod rysuje dwa razy: zielony pióra szerokości 10 raz przy użyciu pióra czarne o szerokości 1 i drugi raz.  
  
### <a name="to-vary-the-width-of-a-pen"></a>Aby zmienić jego szerokość pióra  
  
- Ustaw wartość <xref:System.Drawing.Pen.Alignment%2A> właściwość <xref:System.Drawing.Drawing2D.PenAlignment.Center> (ustawienie domyślne) do określenia, czy pikseli z zielonym pióro zostanie tematyka koncentruje się na teoretycznych wiersza. Poniższa ilustracja przedstawia wynikowego wiersza.  
  
     ![Czarna linia alokowania elastycznego za pomocą Wyróżnij zielony.](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-line.gif)  
  
     Poniższy kod rysuje prostokąt dwa razy: zielony pióra szerokości 10 raz przy użyciu pióra czarne o szerokości 1 i drugi raz.  
  
     [!code-csharp[System.Drawing.UsingAPen#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a>Aby zmienić wyrównania pióra  
  
- Ustaw wartość <xref:System.Drawing.Pen.Alignment%2A> właściwości <xref:System.Drawing.Drawing2D.PenAlignment.Center> do określenia, czy pikseli narysować za pomocą pióra zielony będzie wyśrodkowana na krawędzi prostokąta.  
  
     Na poniższej ilustracji przedstawiono wynikowe prostokąt:
  
     ![Prostokąt z czarnym alokowania elastycznego wiersze z zielone podświetlenie.](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-rectangle.gif)  
  
     [!code-csharp[System.Drawing.UsingAPen#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a>Aby utworzyć wstawki pióra  
  
- Zmienianie wyrównania pióra zielony, modyfikując trzecia instrukcja w powyższym przykładzie kodu w następujący sposób:  
  
     [!code-csharp[System.Drawing.UsingAPen#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     Pikseli szerokości zieloną linią pojawiają się wewnątrz prostokąta jak pokazano na poniższej ilustracji:
  
     ![Prostokąt z czarnym wiersze z szerokiego zieloną linią wewnątrz.](./media/how-to-set-pen-width-and-alignment/green-pixels-inside-rectangle.gif)  
  
## <a name="see-also"></a>Zobacz także

- [Rysowanie linii i kształtów za pomocą pióra](using-a-pen-to-draw-lines-and-shapes.md)
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
