---
title: 'Instrukcje: Przesuwanie kolorów obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
ms.openlocfilehash: 7a3ed1f3f6b3e89c8df160b7e753839e20acd877
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549762"
---
# <a name="how-to-translate-image-colors"></a>Instrukcje: Przesuwanie kolorów obrazu
Tłumaczenie dodaje wartość do przynajmniej jednej z czterech składowych. Wpisów macierzy kolorów, które reprezentują tłumaczenia są podane w poniższej tabeli.  
  
|Składnik ma zostać poddany translacji|Wpis macierzy|  
|--------------------------------|------------------|  
|Czerwony|[4][0]|  
|Zielony|[4][1]|  
|Niebieski|[4][2]|  
|alfa|[4][3]|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku ColorBars.bmp. Następnie kod dodaje wartość 0,75 do składnika czerwony każdego piksela na obrazie. Oryginalny obraz jest rysowany wraz z obrazu przekształcone.  
  
 Poniższa ilustracja pokazuje oryginalny obraz po lewej stronie i przekształcone obraz po prawej stronie.  
  
 ![Translate Colors](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")  
  
 W poniższej tabeli wymieniono wektorów kolor słupków cztery przed i po nim czerwony tłumaczenia. Należy pamiętać, że maksymalna wartość dla składnika koloru jest 1, składnik czerwony, w drugim wierszu nie zmienia się. (Podobnie, wartość minimalna dla składnika koloru wynosi 0).  
  
|Oryginał|Tłumaczenie|  
|--------------|----------------|  
|Czarny (0, 0, 0, 1)|(0.75, 0, 0, 1)|  
|Czerwony (1, 0, 0, 1)|(1, 0, 0, 1)|  
|Kolor zielony (0, 1, 0, 1)|(0.75, 1, 0, 1)|  
|Niebieski (0, 0, 1, 1)|(0.75, 0, 1, 1)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń. Zastąp `ColorBars.bmp` za pomocą nazwy pliku obrazu i ścieżki, które są prawidłowe w tym systemie.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [Ponowne kolorowanie obrazów](../../../../docs/framework/winforms/advanced/recoloring-images.md)
