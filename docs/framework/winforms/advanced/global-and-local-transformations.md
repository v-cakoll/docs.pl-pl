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
ms.openlocfilehash: f62efb31e95b0797272997fadbc28459579a0de0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955193"
---
# <a name="global-and-local-transformations"></a>Globalne i lokalne transformacje
Globalne przekształcenia to transformacja, która ma zastosowanie do wszystkich elementów rysowanych przez dany <xref:System.Drawing.Graphics> obiekt. W przeciwieństwie do lokalnej transformacji jest transformacja, która ma zastosowanie do określonego elementu do narysowania.  
  
## <a name="global-transformations"></a>Przekształcenia globalne  
 Aby utworzyć globalne przekształcenia, konstruowanie <xref:System.Drawing.Graphics> obiektu, a następnie manipulowanie jego <xref:System.Drawing.Graphics.Transform%2A> właściwością. <xref:System.Drawing.Graphics.Transform%2A> Właściwość<xref:System.Drawing.Drawing2D.Matrix> jest obiektem, dlatego może zawierać dowolną sekwencję transformacji afinicznym. Transformacja przechowywana we <xref:System.Drawing.Graphics.Transform%2A> właściwości jest nazywana transformację światową. <xref:System.Drawing.Graphics.RotateTransform%2A> <xref:System.Drawing.Graphics.MultiplyTransform%2A> <xref:System.Drawing.Graphics.TranslateTransform%2A> <xref:System.Drawing.Graphics.ScaleTransform%2A>Klasa zawiera kilka metod tworzenia złożonej transformacji światowej:,,, i. <xref:System.Drawing.Graphics> Poniższy przykład Rysuje elipsę dwa razy: raz przed utworzeniem transformacji światowej i po nim. Transformacja najpierw skaluje się według współczynnika 0,5 w kierunku y, a następnie tłumaczy jednostki 50 w kierunku x, a następnie obraca 30 stopni.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 Na poniższej ilustracji przedstawiono macierze wykorzystywane podczas transformacji.  
  
 ![Przekształcenia](./media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
> W poprzednim przykładzie elipsa jest obracana o początek układu współrzędnych, który znajduje się w lewym górnym rogu obszaru klienckiego. Daje to inny wynik niż Obracanie elipsy o jej własnym środku.  
  
## <a name="local-transformations"></a>Przekształcenia lokalne  
 Przekształcenie lokalne dotyczy określonego elementu do narysowania. Na przykład <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> ma metodę, która pozwala na Przekształcanie punktów danych tej ścieżki. Poniższy przykład rysuje prostokąt bez transformacji i ścieżkę z przekształceniem obrotu. (Założono, że nie ma żadnych transformacji światowej).  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 Możesz połączyć światową transformację z przekształceniami lokalnymi, aby osiągnąć różne wyniki. Na przykład można użyć transformacji światowej do zmiany układu współrzędnych i użyć lokalnych przekształceń do obrotu i skalowania obiektów rysowanych w nowym systemie współrzędnych.  
  
 Załóżmy, że chcesz, aby system współrzędnych miał swoją rechodzenie 200 pikseli od lewej krawędzi obszaru klienta i 150 pikseli w górnej części obszaru klienckiego. Ponadto Załóżmy, że chcesz, aby jednostka miary była pikselem, a oś x skierowana do prawej i oś y. Domyślny system współrzędnych ma oś y wskazującą w dół, dlatego należy wykonać odbicie na osi poziomej. Na poniższej ilustracji przedstawiono macierz takich odbicia.  
  
 ![Przekształcenia](./media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 Następnie założono, że konieczne jest przeprowadzenie translacji 200 jednostek z prawej strony i 150 jednostek w dół.  
  
 Poniższy przykład ustanawia system współrzędnych opisany przez ustawienie światowej transformacji <xref:System.Drawing.Graphics> obiektu.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 Poniższy kod (umieszczony na końcu poprzedniego przykładu) tworzy ścieżkę, która składa się z pojedynczego prostokąta w lewym dolnym rogu w miejscu pochodzenia nowego układu współrzędnych. Prostokąt jest wypełniany raz bez lokalnego przekształcenia i jednokrotnie z lokalną transformację. Lokalna transformacja składa się z skalowania w poziomie za pomocą współczynnika 2, po którym następują 30 stopniowe obracanie.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 Na poniższej ilustracji przedstawiono nowy system współrzędnych i dwa prostokąty.  
  
 ![Przekształcenia](./media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>Zobacz także

- [Systemy i przekształcenia współrzędnych](coordinate-systems-and-transformations.md)
- [Używanie przekształceń w zarządzanym GDI+](using-transformations-in-managed-gdi.md)
