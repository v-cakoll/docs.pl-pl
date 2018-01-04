---
title: "Używanie przekształceń do skalowania kolorów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7515f34858ef6f4b0495ac6fc545ae498d45c7f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-transformations-to-scale-colors"></a>Używanie przekształceń do skalowania kolorów
Transformacja skalowania mnoży przynajmniej jednej z czterech składowych liczbą. Wpisów macierzy kolorów, które reprezentują skalowanie są podane w poniższej tabeli.  
  
|Składnik skalowania|Wpis macierzy|  
|----------------------------|------------------|  
|czerwony|[0][0]|  
|zielony|[1][1]|  
|niebieski|[2][2]|  
|Alpha|[3][3]|  
  
## <a name="scaling-one-color"></a>Skalowanie jednego koloru  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiektów z pliku ColorBars2.bmp. Następnie kod skaluje składnika niebieski każdego piksela obrazu o 2. Oryginalnego obrazu jest rysowane obok przekształcone obrazu.  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej stronie i skalowanie obrazów po prawej stronie.  
  
 ![Skali kolorów](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")  
  
 W poniższej tabeli wymieniono wektory kolor słupków cztery przed i po niebieski skalowania. Należy pamiętać, że składnik niebieski w czwartym pasek koloru próby z 0,8 0,6. Jest to spowodowane tym [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zachowuje część ułamkowa wyniku. Na przykład (2)(0.8) = 1.6, i część ułamkowa w wersji 1.6 jest 0,6. Zachowywanie tylko część ułamkowa zapewnia, że wynik zawsze jest w zakresie [0, 1].  
  
|Oryginał|Skalowania|  
|--------------|------------|  
|(0.4, 0.4, 0.4, 1)|(0.4, 0.4, 0.8, 1)|  
|(0.4, 0.2, 0.2, 1)|(0.4, 0.2, 0.4, 1)|  
|(0.2, 0.4, 0.2, 1)|(0.2, 0.4, 0.4, 1)|  
|(0.4, 0.4, 0.8, 1)|(0.4, 0.4, 0.6, 1)|  
  
## <a name="scaling-multiple-colors"></a>Skalowanie wiele kolorów  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiektów z pliku ColorBars2.bmp. Następnie kod skaluje składniki czerwony, zielonemu i niebieskiemu każdego piksela obrazu. Czerwony składniki są skalowane w dół 25 procent zielony składniki są skalowane w dół 35% i niebieski składniki są skalowane w dół 50 procent.  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej stronie i skalowanie obrazów po prawej stronie.  
  
 ![Skali kolorów](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")  
  
 W poniższej tabeli wymieniono wektory kolor słupków cztery przed i po czerwonemu, zielonemu i niebieski skalowanie.  
  
|Oryginał|Skalowania|  
|--------------|------------|  
|(0.6, 0.6, 0.6, 1)|(0.45, 0.39, 0.3, 1)|  
|(0, 1, 1, 1)|(0, 0.65, 0.5, 1)|  
|(1, 1, 0, 1)|(0.75, 0.65, 0, 1)|  
|(1, 0, 1, 1)|(0.75, 0, 0.5, 1)|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Ponowne kolorowanie obrazów](../../../../docs/framework/winforms/advanced/recoloring-images.md)
