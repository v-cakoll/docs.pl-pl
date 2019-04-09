---
title: Używanie przekształceń do skalowania kolorów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: 9c8f2392137d04f56096120cec64b60c42c47419
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107988"
---
# <a name="using-transformations-to-scale-colors"></a>Używanie przekształceń do skalowania kolorów
Przekształcenie skalowania mnoży co najmniej cztery składowych przez liczbę. Wpisów macierzy kolorów, które reprezentują skalowania są podane w poniższej tabeli.  
  
|Składnik skalowania|Wpis macierzy|  
|----------------------------|------------------|  
|Czerwony|[0][0]|  
|Zielony|[1][1]|  
|Niebieski|[2][2]|  
|alfa|[3][3]|  
  
## <a name="scaling-one-color"></a>Skalowanie z jednego koloru  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku ColorBars2.bmp. Następnie kod jest skalowana składnik niebieski każdego piksela na obrazie ośmiokrotnego 2. Oryginalny obraz jest rysowany wraz z obrazu przekształcone.  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i skalowany obraz po prawej stronie:  
  
 ![Zrzut ekranu porównuje kolory oryginalnego i skalowanych.](./media/using-transformations-to-scale-colors/four-bar-scale-one-color.png)  
  
 W poniższej tabeli wymieniono wektorów kolor słupków cztery przed i po nim niebieski skalowania. Pamiętaj, że składnik niebieski w czwartym pasek koloru próby z 0,8 Update 0.6. To dlatego, że [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zachowuje część ułamkową wyniku. Na przykład (2)(0.8) = 1.6, i Update 0.6 część ułamkową parametru 1.6. Zachowywanie tylko część ułamkową gwarantuje, czy wynik jest zawsze w zakresie [0, 1].  
  
|Oryginał|Skalowanie|  
|--------------|------------|  
|(0.4, 0.4, 0.4, 1)|(0.4, 0.4, 0.8, 1)|  
|(0.4, 0.2, 0.2, 1)|(0.4, 0.2, 0.4, 1)|  
|(0.2, 0.4, 0.2, 1)|(0.2, 0.4, 0.4, 1)|  
|(0.4, 0.4, 0.8, 1)|(0.4, 0.4, 0.6, 1)|  
  
## <a name="scaling-multiple-colors"></a>Skalowanie wielu kolorów  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku ColorBars2.bmp. Następnie kod skaluje składników czerwonego, zielonego i niebieskiego każdego piksela na obrazie. Składniki czerwone są skalowane w dół 25 procent, zielony składniki są skalowane w dół 35 procent i składniki niebieskie są skalowane w dół 50 procent.  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i skalowany obraz po prawej stronie:  
  
 ![Zrzut ekranu porównuje kolory oryginalnego i skalowanych.](./media/using-transformations-to-scale-colors/four-bar-scale-multiple-colors.png)  
  
 W poniższej tabeli wymieniono wektorów kolor słupków cztery przed i po nim czerwonego, zielonego i niebieskiego skalowanie.  
  
|Oryginał|Skalowanie|  
|--------------|------------|  
|(0.6, 0.6, 0.6, 1)|(0.45, 0.39, 0.3, 1)|  
|(0, 1, 1, 1)|(0, 0.65, 0.5, 1)|  
|(1, 1, 0, 1)|(0.75, 0.65, 0, 1)|  
|(1, 0, 1, 1)|(0.75, 0, 0.5, 1)|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika i rysowanie w formularzach systemu Windows](graphics-and-drawing-in-windows-forms.md)
- [Ponowne kolorowanie obrazów](recoloring-images.md)
