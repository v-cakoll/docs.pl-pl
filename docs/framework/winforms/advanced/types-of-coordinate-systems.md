---
title: Typy systemów współrzędnych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: bbb0d4908d4a281499336d262c653d7b72f3ccdc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159809"
---
# <a name="types-of-coordinate-systems"></a>Typy systemów współrzędnych
Interfejs GDI+ używa trzech przestrzeni współrzędnych: świecie, strony i urządzenia. Współrzędne świata są współrzędnymi używanymi do modelowania określonego świata grafiki i są współrzędnymi przekazywanymi do metod w .NET Framework. Współrzędne strony odwołują się do układu współrzędnych używanego przez powierzchnię rysowania, taką jak formularz lub kontrolka. Współrzędne urządzenia są współrzędnymi używanymi przez urządzenie fizyczne, na przykład na ekranie lub arkuszu papieru. Po nadaniu wywołania `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`punkty przekazane do metody <xref:System.Drawing.Graphics.DrawLine%2A> —`(0, 0)` i `(160, 80)`— znajdują się na świecie współrzędnych. Zanim GDI+ będzie mógł narysować linię na ekranie, współrzędne przechodzą przez sekwencję transformacji. Jedną transformację, nazywaną transformację światową, konwertuje współrzędne świata na współrzędne strony, a inna transformacja, nazywana przekształceniem strony, konwertuje współrzędne strony na współrzędne urządzenia.  
  
## <a name="transforms-and-coordinate-systems"></a>Transformacje i systemy współrzędnych  
 Załóżmy, że chcesz korzystać z układu współrzędnych, który ma swoją zawartość w treści obszaru klienta, a nie w lewym górnym rogu. Załóżmy na przykład, że źródło ma mieć 100 pikseli od lewej krawędzi obszaru klienta i 50 pikseli od góry obszaru klienckiego. Na poniższej ilustracji przedstawiono układ współrzędnych.  
  
 ![System współrzędnych](./media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 Po nadaniu wywołania `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`uzyskasz wiersz przedstawiony na poniższej ilustracji.  
  
 ![System współrzędnych](./media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 Współrzędne punkty końcowe linii w trzech miejscach współrzędnych są następujące:  
  
|||  
|-|-|  
|Międzynarodowa|(od 0 do 0) do (160, 80)|  
|Stronic|(100, 50) do (260, 130)|  
|Urządzenie|(100, 50) do (260, 130)|  
  
 Należy zauważyć, że obszar współrzędnej strony ma swój początek w lewym górnym rogu obszaru klienckiego. zawsze będzie to miało zastosowanie. Należy również zauważyć, że ponieważ jednostka miary jest pikselem, współrzędne urządzenia są takie same jak współrzędne strony. Jeśli ustawisz jednostkę miary na coś innego niż piksele (na przykład centymetry), współrzędne urządzenia będą różnić się od współrzędnej strony.  
  
 Transformacja świata, która mapuje współrzędne świata na współrzędne strony, jest utrzymywana we właściwości <xref:System.Drawing.Graphics.Transform%2A> klasy <xref:System.Drawing.Graphics>. W poprzednim przykładzie transformacja świata jest jednostką translacji 100 w kierunku x i 50 jednostek w kierunku y. Poniższy przykład ustawia światową transformację obiektu <xref:System.Drawing.Graphics>, a następnie używa tego obiektu <xref:System.Drawing.Graphics> do rysowania linii pokazanej na poprzednim rysunku:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 Transformacja strony mapuje współrzędne strony na współrzędne urządzeń. Klasa <xref:System.Drawing.Graphics> udostępnia właściwości <xref:System.Drawing.Graphics.PageUnit%2A> i <xref:System.Drawing.Graphics.PageScale%2A> na potrzeby manipulowania transformację strony. Klasa <xref:System.Drawing.Graphics> udostępnia również dwie właściwości tylko do odczytu, <xref:System.Drawing.Graphics.DpiX%2A> i <xref:System.Drawing.Graphics.DpiY%2A>do badania w poziomie i w pionie na cal urządzenia wyświetlającego.  
  
 Aby określić jednostkę miary inną niż piksel, można użyć właściwości <xref:System.Drawing.Graphics.PageUnit%2A> klasy <xref:System.Drawing.Graphics>.  
  
> [!NOTE]
> Nie można ustawić właściwości <xref:System.Drawing.Graphics.PageUnit%2A> na <xref:System.Drawing.GraphicsUnit.World>, ponieważ nie jest to jednostka fizyczna i spowoduje wyjątek.  
  
 Poniższy przykład rysuje linię od (0, 0) do (2, 1), gdzie punkt (2, 1) jest 2 cala po prawej i 1 cal w dół od punktu (0, 0):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
> Jeśli nie określisz szerokości pióra podczas tworzenia pióra, w poprzednim przykładzie zostanie narysowana linia o szerokości jednego cala. Możesz określić szerokość pióra w drugim argumencie konstruktora <xref:System.Drawing.Pen>:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 Jeśli założono, że urządzenie wyświetlające ma 96 punktów na cal w kierunku poziomym i 96 punktów na cal w kierunku pionowym, punkty końcowe wiersza w poprzednim przykładzie mają następujące współrzędne w trzech miejscach współrzędnych:  
  
|||  
|-|-|  
|Międzynarodowa|(od 0 do 0) do (2, 1)|  
|Stronic|(od 0 do 0) do (2, 1)|  
|Urządzenie|(od 0 do 0) do (192, 96)|  
  
 Należy zauważyć, że ze względu na to, że początek przestrzeni współrzędnych świata znajduje się w lewym górnym rogu obszaru klienta, współrzędne strony są takie same jak współrzędne świata.  
  
 Możesz połączyć przekształcenia światowe i strony, aby osiągnąć różne efekty. Załóżmy na przykład, że chcesz użyć cali jako jednostki miary, i chcesz, aby początkowa część układu współrzędnych była równa 2 cala od lewej krawędzi obszaru klienckiego i 1/2 cala od góry obszaru klienckiego. Poniższy przykład ustawia przekształcenia na świecie i na stronie obiektu <xref:System.Drawing.Graphics>, a następnie rysuje linię od (0, 0) do (2, 1):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 Poniższa ilustracja przedstawia układ linii i układu współrzędnych.  
  
 ![System współrzędnych](./media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 Jeśli założono, że urządzenie wyświetlające ma 96 punktów na cal w kierunku poziomym i 96 punktów na cal w kierunku pionowym, punkty końcowe wiersza w poprzednim przykładzie mają następujące współrzędne w trzech miejscach współrzędnych:  
  
|||  
|-|-|  
|Międzynarodowa|(od 0 do 0) do (2, 1)|  
|Stronic|(2, 0,5) do (4, 1,5)|  
|Urządzenie|(192, 48) do (384, 144)|  
  
## <a name="see-also"></a>Zobacz też

- [Systemy i przekształcenia współrzędnych](coordinate-systems-and-transformations.md)
- [Macierzowe przedstawienie przekształcenia](matrix-representation-of-transformations.md)
