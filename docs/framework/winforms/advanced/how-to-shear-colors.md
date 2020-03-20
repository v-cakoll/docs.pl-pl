---
title: 'Porady: zmienianie kolorów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 825e5a90ebb0d9df3b894ce7bd353e917b676939
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142397"
---
# <a name="how-to-shear-colors"></a>Porady: zmienianie kolorów
Ścinanie zwiększa lub zmniejsza komponent koloru o kwotę proporcjonalną do innego komponentu koloru. Rozważmy na przykład transformację, w której czerwony składnik jest zwiększany o połowę wartości niebieskiego składnika. W ramach takiej transformacji kolor (0,2, 0,5, 1) stałby się (0,7, 0,5, 1). Nowy czerwony komponent to 0,2 + (1/2)(1) = 0,7.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiekt z pliku ColorBars4.bmp. Następnie kod stosuje transformację ścinania opisaną w poprzednim akapicie do każdego piksela obrazu.  
  
 Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i ścięty obraz po prawej stronie:
  
 ![Dwa kwadraty z kolorowymi paskami obok siebie ilustrujące oryginalny obraz i ścięty obraz.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 W poniższej tabeli wymieniono wektory kolorów dla czterech pasków przed i po transformacji ścinania.  
  
|Oryginał|Ścięty|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy przykład jest przeznaczony do użytku z <xref:System.Windows.Forms.PaintEventArgs> `e`formularzami systemu Windows <xref:System.Windows.Forms.Control.Paint> i wymaga , który jest parametrem obsługi zdarzeń. Zastąp `ColorBars.bmp` nazwą obrazu i ścieżką prawidłową w systemie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Ponowne kolorowanie obrazów](recoloring-images.md)
