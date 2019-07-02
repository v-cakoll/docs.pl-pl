---
title: 'Instrukcje: Używanie tabeli ponownego mapowania kolorów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
ms.openlocfilehash: 360ec30563ee5001d784dc7c4ccdb50563867c29
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505765"
---
# <a name="how-to-use-a-color-remap-table"></a>Instrukcje: Używanie tabeli ponownego mapowania kolorów
Ponowne mapowanie jest procesem konwertowania kolory na obrazie zgodnie z tabeli ponownego mapowania kolorów. Tabeli ponownego mapowania kolorów jest tablicą <xref:System.Drawing.Imaging.ColorMap> obiektów. Każdy <xref:System.Drawing.Imaging.ColorMap> obiektów w tablicy ma <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> właściwości i <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> właściwości.  
  
 Jeśli GDI + pobiera obraz, każdego piksela obrazu jest porównywana do tablicy stare kolory. Jeśli kolor piksela odpowiada stary kolor, jego kolor jest zmieniany na odpowiedniej nowy kolor. Kolory są zmieniane tylko w przypadku renderowania — wartości kolorów sam obraz (przechowywane w <xref:System.Drawing.Image> lub <xref:System.Drawing.Bitmap> obiektu) nie są zmieniane.  
  
 Aby narysować ponownie zmapowany obrazu, zainicjowania tablicy <xref:System.Drawing.Imaging.ColorMap> obiektów. Ta tablica do przekazania <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> metody <xref:System.Drawing.Imaging.ImageAttributes> obiektu, a następnie przekazać <xref:System.Drawing.Imaging.ImageAttributes> do obiektu <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku RemapInput.bmp. Ten kod tworzy tabeli ponownego mapowania kolorów, która składa się z pojedynczego <xref:System.Drawing.Imaging.ColorMap> obiektu. <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> Właściwość `ColorRemap` obiekt ma kolor czerwony i <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> właściwość ma kolor niebieski. Obraz jest rysowane raz bez ponownego mapowania i drugi raz z ponownego mapowania. Proces ponownego mapowania zmienia wszystkie piksele czerwony na niebieski.  
  
 Poniższa ilustracja pokazuje oryginalny obraz po lewej stronie i ponownie zmapowany obraz po prawej stronie.  
  
 ![Zrzut ekranu przedstawiający oryginalnego obrazu i ponownie zmapowany obrazu.](./media/how-to-use-a-color-remap-table/original-image-remap-colors.png)  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Ponowne kolorowanie obrazów](recoloring-images.md)
- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
