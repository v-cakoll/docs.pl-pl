---
title: "Globalne i lokalne przekształcenia"
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
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 432402fefc6c958fbab0b1450a429d9b130b8239
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="global-and-local-transformations"></a>Globalne i lokalne przekształcenia
Globalne przekształcenie jest transformację, która ma zastosowanie do każdego elementu narysowanymi przez dany <xref:System.Drawing.Graphics> obiektu. Z kolei transformację lokalnego jest transformację, która ma zastosowanie do określonego elementu do narysowania.  
  
## <a name="global-transformations"></a>Globalne przekształcenia  
 Aby utworzyć transformację globalnego, należy utworzyć <xref:System.Drawing.Graphics> obiekt, a następnie wykonywać jego <xref:System.Drawing.Graphics.Transform%2A> właściwości. <xref:System.Drawing.Graphics.Transform%2A> Jest właściwość <xref:System.Drawing.Drawing2D.Matrix> obiektu, więc może zawierać żadnych sekwencji affine — przekształcenia. Transformacja przechowywane w <xref:System.Drawing.Graphics.Transform%2A> właściwości jest wywoływana transformacji świata. <xref:System.Drawing.Graphics> Klasa udostępnia kilka metod budowania przekształcenia złożonego world: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, i <xref:System.Drawing.Graphics.TranslateTransform%2A>. Poniższy przykład Rysuje elipsę dwa razy: raz w przed utworzeniem transformacja świata i jeden raz po. Transformacja skaluje najpierw według współczynnika 0,5 w kierunku y, a następnie wykonuje translację 50 jednostek w kierunku x i obraca się 30 stopni.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 Na poniższej ilustracji przedstawiono objętego przekształcenia macierzy.  
  
 ![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
>  W powyższym przykładzie elipsy obraca się wokół pochodzenia współrzędnych, która jest w lewym górnym rogu obszaru klienckiego. To daje różne wyniki niż obracanie elipsy temat własnego Centrum.  
  
## <a name="local-transformations"></a>Lokalne przekształcenia  
 Transformację lokalnego ma zastosowanie do określonego elementu do narysowania. Na przykład <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt ma <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> — metoda, która pozwala na Przekształcanie punktów danych tej ścieżki. Poniższy przykład rysuje prostokąt z nie transformacji i ścieżki z transformację obrotu. (Przyjmowane jest nie transformacja świata).  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 Transformacja świata przekształceń lokalnego, aby uzyskać różne wyniki można łączyć. Na przykład można transformacji świata korygowanie współrzędnych i lokalne przekształcenia umożliwia obracanie i skalowanie obiektów na nowy układ współrzędnych.  
  
 Załóżmy, że ma układ współrzędnych, jego pochodzenie 200 pikseli od lewej krawędzi obszaru klienckiego i 150 pikseli od góry obszaru klienckiego. Ponadto wariantem jednostki miary być pikseli, o wskazanie osi y skierowany w górę i prawej osi x. Domyślny układ współrzędnych ma osi y skierowany w dół, więc należy przeprowadzić odbicie wzdłuż osi poziomej. Na poniższej ilustracji przedstawiono macierzy takie odbicia.  
  
 ![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 Następnie przyjęto założenie, że należy przeprowadzić translacji 200 w prawo i 150 jednostek w dół.  
  
 Poniższy przykład ustanawia współrzędnych właśnie opisanego przez ustawienie transformacji świata <xref:System.Drawing.Graphics> obiektu.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 Poniższy kod (umieszczona na końcu powyższego przykładu) tworzy ścieżki, która składa się z jednego prostokąt z jego lewym dolnym rogu źródłem nowy układ współrzędnych. Prostokąt jest wypełniana raz nie transformację lokalnych i drugi raz z transformację lokalnego. Transformacja lokalnego składa się z skalowanie w poziomie przez współczynnik 2 następuje 30 stopni.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 Na poniższej ilustracji przedstawiono nowe współrzędnych i prostokąty dwa.  
  
 ![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>Zobacz też  
 [Systemy i transformacje współrzędnych](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Używanie przekształceń w zarządzanym GDI +](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
