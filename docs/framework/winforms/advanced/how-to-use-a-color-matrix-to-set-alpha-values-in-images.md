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
ms.openlocfilehash: ed129cd9487ba1416cd69b2e13f59747856cb598
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522349"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>Porady: stosowanie macierzy kolorów ustawiania wartości alfa na obrazach
<xref:System.Drawing.Bitmap> Klasy (który dziedziczy z <xref:System.Drawing.Image> klasy) oraz <xref:System.Drawing.Imaging.ImageAttributes> klasy zapewniają funkcje służące do pobierania i ustawiania wartości pikseli. Można użyć <xref:System.Drawing.Imaging.ImageAttributes> klasę, aby zmodyfikować alfa wartości dla całego obrazu lub można wywołać <xref:System.Drawing.Bitmap.SetPixel%2A> metody <xref:System.Drawing.Bitmap> klasy, aby zmodyfikować wartości poszczególnych pikseli.  
  
## <a name="example"></a>Przykład  
 <xref:System.Drawing.Imaging.ImageAttributes> Klasa ma wiele właściwości, które służy do modyfikowania obrazów podczas renderowania. W poniższym przykładzie <xref:System.Drawing.Imaging.ImageAttributes> obiekt jest używany do ustawiania wartości alfa do 80 procent jakie były. Jest to realizowane przez inicjowania macierzy kolorów i ustawienie alfa wartość w macierzy 0,8 skalowania. Adres macierzy kolorów są przekazywane do <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metody <xref:System.Drawing.Imaging.ImageAttributes> obiektu i <xref:System.Drawing.Imaging.ImageAttributes> obiekt jest przekazywany do <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> obiektu.  
  
 Podczas renderowania wartości alfa w mapie bitowej są konwertowane na jakie były 80 procent. Powoduje to obraz, który jest mieszane w tle. Jak pokazano na poniższej ilustracji, Przezroczysty; wygląd obrazu mapy bitowej widać stałe czarnej linii przy jego użyciu.  
  
 ![Przenikanie alfa przy użyciu macierzy](../../../../docs/framework/winforms/advanced/media/image2.png "obraz2")  
  
 W przypadku obrazu na fragment białe tło, obraz ma zostały mieszane z kolor biały znak. Gdy obraz przecina czarnej linii obrazu jest mieszane z kolor czarny.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Przenikanie alfa linii i wypełnień](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
