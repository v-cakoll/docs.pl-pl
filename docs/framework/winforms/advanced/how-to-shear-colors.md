---
title: 'Instrukcje: Zmienianie kolorów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: bf645cf88c4905cd5cf47c2a6c7af088fa428c8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076253"
---
# <a name="how-to-shear-colors"></a>Instrukcje: Zmienianie kolorów
Pochylanie zwiększa lub zmniejsza składnika koloru o kwotę proporcjonalną do innego składnika koloru. Na przykład należy wziąć pod uwagę transformacji, w której składnik czerwony jest zwiększana o połowę wartość składnik niebieski. W obszarze takie przekształcenia kolorów (0,2, 0,5, 1) staną się (0,7, 0,5, 1). Nowy składnik czerwony jest wymagane 0,2 + (1/2)(1) = 0,7.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku ColorBars4.bmp. Następnie kod stosuje transformację nożycy opisane w poprzednim akapicie do każdego piksela na obrazie.  
  
 Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i pochylone obraz po prawej stronie: 
  
 ![Dwa pola z kolorowe paski side-by-side pokazujący oryginalnego obrazu i pochylone obrazu.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 W poniższej tabeli wymieniono wektorów kolor słupków cztery przed i po nim nożycy transformacji.  
  
|Oryginał|Pochylono|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń. Zastąp `ColorBars.bmp` przy użyciu nazwy obrazu i ścieżki prawidłowy w tym systemie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Ponowne kolorowanie obrazów](recoloring-images.md)
