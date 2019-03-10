---
title: 'Instrukcje: Stosowanie macierzy kolorów ustawiania wartości alfa na obrazach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
ms.openlocfilehash: 9e102f51d00953d05ed1d217a345e32178676ffe
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716338"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>Instrukcje: Stosowanie macierzy kolorów ustawiania wartości alfa na obrazach
<xref:System.Drawing.Bitmap> Klasy (który dziedziczy z <xref:System.Drawing.Image> klasy) oraz <xref:System.Drawing.Imaging.ImageAttributes> klasy zapewniają funkcje służące do pobierania i ustawiania wartości pikseli. Możesz użyć <xref:System.Drawing.Imaging.ImageAttributes> klasy, aby zmodyfikować alfa wartości dla całego obrazu lub może wywołać <xref:System.Drawing.Bitmap.SetPixel%2A> metody <xref:System.Drawing.Bitmap> klasy, aby zmodyfikować wartości poszczególnych pikseli.  
  
## <a name="example"></a>Przykład  
 <xref:System.Drawing.Imaging.ImageAttributes> Klasa ma wiele właściwości, które służy do modyfikowania obrazów podczas renderowania. W poniższym przykładzie <xref:System.Drawing.Imaging.ImageAttributes> obiekt jest używany do ustawiania wartości alfa do 80 procent o tym, co było. Odbywa się przez inicjowanie macierzy kolorów i ustawienie alfa, wartość w macierzy, aby 0,8 skalowania. Adres macierzy kolorów jest przekazywany do <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metody <xref:System.Drawing.Imaging.ImageAttributes> obiektu, a <xref:System.Drawing.Imaging.ImageAttributes> obiekt jest przekazywany do <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> obiektu.  
  
 Podczas renderowania, wartości alfa w mapie bitowej są konwertowane do 80 procent o tym, co było. Skutkuje to obrazu, która jest zmieszana w tle. Jak pokazano na poniższej ilustracji, Przezroczysty; wygląd obrazu mapy bitowej Możesz zobaczyć czarna linia ciągła przy jego użyciu.  
  
 ![Przenikanie alfa, za pomocą macierzy](./media/image2.png "obraz2")  
  
 W przypadku obrazu na fragment białe tło, obraz, który ma zostały mieszane z kolor biały znak. Gdzie obraz przecina czarna linia obrazu jest zmieszana przy użyciu kolor czarny.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Przenikanie alfa linii i wypełnień](alpha-blending-lines-and-fills.md)
