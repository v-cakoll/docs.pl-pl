---
title: "Przycinanie i skalowanie obrazów w GDI+"
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
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0bbe7ac4b8c541ea76392f94f538e41816cf5c3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cropping-and-scaling-images-in-gdi"></a>Przycinanie i skalowanie obrazów w GDI+
Można użyć <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> klasy do rysowania i umieść wektor obrazów i obrazów rastrowych. <xref:System.Drawing.Graphics.DrawImage%2A>jest przeciążona metoda, więc może dostarczyć argumenty na kilka sposobów.  
  
## <a name="drawimage-variations"></a>DrawImage zmian  
 Zmiana jednego <xref:System.Drawing.Graphics.DrawImage%2A> metoda <xref:System.Drawing.Bitmap> i <xref:System.Drawing.Rectangle>. Prostokąt określa obiekt docelowy operacji rysowania; oznacza to określa prostokąta do rysowania obrazu. Jeśli rozmiar docelowy prostokąt różni się od rozmiaru oryginalnego obrazu, obraz jest skalowane w celu dopasowania prostokąt docelowy. Poniższy przykład kodu pokazuje sposób rysowania trzy razy ten sam obraz: drugi raz z bez skalowania, drugi raz z rozszerzenia, a drugi raz z kompresji:  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 Na poniższej ilustracji przedstawiono trzy obrazy.  
  
 ![Skalowanie](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")  
  
 Niektóre zmiany <xref:System.Drawing.Graphics.DrawImage%2A> metoda ma parametr prostokąta źródłowego, a także parametr docelowy prostokąt. Parametr prostokąta źródłowego określa część oryginalnego obrazu do rysowania. Docelowy prostokąt określa prostokąta do rysowania część obrazu. Jeśli rozmiar docelowy prostokąt różni się od rozmiaru prostokąta źródłowego, obraz jest skalowane w celu dopasowania prostokąt docelowy.  
  
 Poniższy przykładowy kod przedstawia sposób tworzenia <xref:System.Drawing.Bitmap> z pliku Runner.jpg. Obraz jest rysowany z bez skalowania w (0, 0). Następnie niewielką część obrazu jest rysowany dwa razy: raz z kompresji i drugi raz z rozszerzenia.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 Na poniższej ilustracji przedstawiono nieskalowanego obrazu i części obrazu skompresowanej i rozszerzonej.  
  
 ![Przycinanie i skalowanie](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")  
  
## <a name="see-also"></a>Zobacz też  
 [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
