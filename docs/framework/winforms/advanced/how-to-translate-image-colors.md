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
ms.openlocfilehash: fb9ec30c06740214b8dc6b65d32eba4e2920c89b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592929"
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
  
 Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i przekształcone obraz po prawej stronie:  
  
 ![Zrzut ekranu przedstawiający obrazu oryginalnego i przekształcone.](./media/how-to-translate-image-colors/original-image-translate-colors.png)  
  
 W poniższej tabeli wymieniono wektorów kolor słupków cztery przed i po nim czerwony tłumaczenia. Należy pamiętać, że maksymalna wartość dla składnika koloru jest 1, składnik czerwony, w drugim wierszu nie zmienia się. (Podobnie, wartość minimalna dla składnika koloru wynosi 0).  
  
|Oryginał|Tłumaczenie|  
|--------------|----------------|  
|Czarny (0, 0, 0, 1)|(0.75, 0, 0, 1)|  
|Czerwony (1, 0, 0, 1)|(1, 0, 0, 1)|  
|Kolor zielony (0, 1, 0, 1)|(0.75, 1, 0, 1)|  
|Niebieski (0, 0, 1, 1)|(0.75, 0, 1, 1)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń. Zastąp `ColorBars.bmp` za pomocą nazwy pliku obrazu i ścieżki, które są prawidłowe w tym systemie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Ponowne kolorowanie obrazów](recoloring-images.md)
