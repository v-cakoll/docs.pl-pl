---
title: Globalne i lokalne transformacje
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
ms.openlocfilehash: e4ed103e781cc2e59d62c11f3233357c77b81cb9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004578"
---
# <a name="global-and-local-transformations"></a>Globalne i lokalne transformacje
Globalne przekształcenie jest przekształcenie, które mają zastosowanie do każdego elementu narysowanymi przez dany <xref:System.Drawing.Graphics> obiektu. Z kolei lokalnego transformacji jest przekształcenie, które mają zastosowanie do określonego elementu do narysowania.  
  
## <a name="global-transformations"></a>Globalne przekształcenia  
 Aby utworzyć przekształcenie globalnego, należy utworzyć <xref:System.Drawing.Graphics> obiektu, a następnie manipulować jego <xref:System.Drawing.Graphics.Transform%2A> właściwości. <xref:System.Drawing.Graphics.Transform%2A> Właściwość <xref:System.Drawing.Drawing2D.Matrix> obiektu, dzięki czemu może on przechowywać dowolnej sekwencji affine — przekształcenia. Transformacja przechowywane w <xref:System.Drawing.Graphics.Transform%2A> właściwość nazywa się transformacji świata. <xref:System.Drawing.Graphics> Klasa udostępnia kilka metod budowania transformacji świata złożonego: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, i <xref:System.Drawing.Graphics.TranslateTransform%2A>. Poniższy przykład Rysuje elipsę dwa razy: raz przed tworzeniem transformacji świata i jeden raz po. Przekształcenie najpierw skaluje o 0,5 w kierunku y, a następnie tłumaczy 50 jednostek w kierunku x, a następnie obraca się 30 stopni.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 Poniższa ilustracja przedstawia macierzy zaangażowanych w transformacji.  
  
 ![Przekształcenia](./media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
>  W powyższym przykładzie elipsy jest obracany o pochodzenie współrzędnych, który znajduje się w lewym górnym rogu obszaru klienta. To daje różne wyniki niż obracanie elipsę o własne Centrum.  
  
## <a name="local-transformations"></a>Lokalne przekształcenia  
 Lokalne przekształcenia mają zastosowanie do określonego elementu do narysowania. Na przykład <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt ma <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> metodę, która umożliwia przekształcenie punktów danych tej ścieżki. Poniższy przykład rysuje prostokąt o nie przekształcania i ścieżki z transformacji obrotu. (Przyjęto założenie, że nie istnieje żadne transformacji świata).  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 Można połączyć transformacji świata przekształceń lokalne, aby uzyskać różne wyniki. Na przykład można użyć transformacji świata korygowanie w układzie współrzędnych i za pomocą lokalnego przekształcania obracać i skalować obiektów na nowy układ współrzędnych.  
  
 Załóżmy, że chcesz, aby system współrzędnych, jego pochodzenie 200 pikseli od lewej krawędzi obszaru klienta i 150 pikseli od górnej krawędzi obszaru klienta. Ponadto Załóżmy, mają jednostka miary jako pikseli, za pomocą osi x, wskazując i prawej osi y skierowana w górę. System współrzędnych domyślne ma osi y skierowany w dół, więc trzeba wykonać odbicie wzdłuż osi poziomej. Poniższa ilustracja przedstawia macierz takich odbicia.  
  
 ![Przekształcenia](./media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 Następnie przyjęto założenie, że trzeba wykonać 200 jednostek tłumaczenia, z prawej strony i 150 jednostki w dół.  
  
 Poniższy przykład określa układ współrzędnych właśnie opisanego przez ustawienie transformacji świata z <xref:System.Drawing.Graphics> obiektu.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 Poniższy kod (umieszczona na końcu poprzedniego przykładu) tworzy ścieżki, która składa się z pojedynczego prostokąt z jego lewego dolnego rogu w źródle nowy układ współrzędnych. Prostokąt jest wypełniana po nie lokalnych transformacji i drugi raz lokalne przekształcenia. Przekształcenie lokalne składa się z skalowanie w poziomie przez współczynnik 2 następuje 30 stopni.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 Na poniższej ilustracji przedstawiono nowy układ współrzędnych i dwoma prostokątami.  
  
 ![Przekształcenia](./media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>Zobacz także

- [Systemy i przekształcenia współrzędnych](coordinate-systems-and-transformations.md)
- [Używanie przekształceń w zarządzanym GDI+](using-transformations-in-managed-gdi.md)
