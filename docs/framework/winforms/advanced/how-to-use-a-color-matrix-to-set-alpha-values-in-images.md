---
title: 'Porady: stosowanie macierzy kolorów ustawiania wartości alfa na obrazach'
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
ms.openlocfilehash: 73e820845d040856a0ae367da8b9371ad6afa142
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423738"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>Porady: stosowanie macierzy kolorów ustawiania wartości alfa na obrazach
Klasa <xref:System.Drawing.Bitmap> (która dziedziczy z klasy <xref:System.Drawing.Image>) i Klasa <xref:System.Drawing.Imaging.ImageAttributes> zapewniają funkcje pobierania i ustawiania wartości pikseli. Za pomocą klasy <xref:System.Drawing.Imaging.ImageAttributes> można modyfikować wartości alfa dla całego obrazu lub wywołać metodę <xref:System.Drawing.Bitmap.SetPixel%2A> klasy <xref:System.Drawing.Bitmap>, aby modyfikować poszczególne wartości pikseli.  
  
## <a name="example"></a>Przykład  
 Klasa <xref:System.Drawing.Imaging.ImageAttributes> ma wiele właściwości, których można użyć do modyfikowania obrazów podczas renderowania. W poniższym przykładzie obiekt <xref:System.Drawing.Imaging.ImageAttributes> jest używany do ustawiania wszystkich wartości alfa na 80 procent ich wielkości. Jest to realizowane przez zainicjowanie macierzy kolorów i ustawienie wartości skalowania alfa w macierzy na 0,8. Adres macierzy kolorów jest przesyłany do metody <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> obiektu <xref:System.Drawing.Imaging.ImageAttributes>, a obiekt <xref:System.Drawing.Imaging.ImageAttributes> jest przesyłany do metody <xref:System.Drawing.Graphics.DrawString%2A> obiektu <xref:System.Drawing.Graphics>.  
  
 Podczas renderowania wartości alfa w mapie bitowej są konwertowane na 80 procent ich wielkości. Powoduje to obraz, który jest mieszany z tłem. Jak widać na poniższej ilustracji, obraz mapy bitowej wygląda niewidoczny; za jego pomocą można wyświetlić pełną czarną linię.  
  
 ![Zrzut ekranu przedstawiający mieszanie alfa przy użyciu macierzy.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "Obraz2")  
  
 Gdy obraz znajduje się na białej części tła, obraz został zmieszany z kolorem biały. Gdy obraz przecina czarną linię, obraz zostanie zmieszany z kolorem czarnym.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także

- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Przenikanie alfa linii i wypełnień](alpha-blending-lines-and-fills.md)
