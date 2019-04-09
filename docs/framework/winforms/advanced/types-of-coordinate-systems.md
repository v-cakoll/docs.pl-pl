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
ms.openlocfilehash: 765df4bcd3cef83e624ad8b11676696b95f7d035
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089305"
---
# <a name="types-of-coordinate-systems"></a>Typy systemów współrzędnych
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] używa trzech przestrzeni współrzędnych: świata, strony i urządzeń. Współrzędne świata są współrzędne używane do modelowania określonego świata graficznego i współrzędne, które są przekazywane do metody w programie .NET Framework. Współrzędne strony można znaleźć w układzie współrzędnych używana przez powierzchnię rysunku, na przykład jako formularz lub formant. Współrzędne urządzenia są współrzędne używane przez urządzenie fizyczne rysowania, takie jak ekran, lub arkusz papieru. Podczas wywoływania `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, punkty, które są przekazywane do <xref:System.Drawing.Graphics.DrawLine%2A> metody —`(0, 0)` i `(160, 80)`— znajdują się w przestrzeni współrzędnych świata. Przed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można narysować linię na ekranie, współrzędne przechodzą przez sekwencję transformacji. Jeden przekształcenia, nazywane transformacji świata konwertuje współrzędne świata na współrzędne strony, a inny przekształcenia, o nazwie przekształcenie strony konwertuje współrzędne strony współrzędnych urządzenia.  
  
## <a name="transforms-and-coordinate-systems"></a>Transformacje i systemów współrzędnych  
 Załóżmy, że chcesz pracować z współrzędnych pochodzenia w treści obszaru klienta, a nie w lewym górnym rogu. Powiedz, na przykład, ma punkt początkowy za 100 pikseli od lewej krawędzi obszaru klienta i 50 pikseli od górnej krawędzi obszaru klienta. Poniższa ilustracja przedstawia układ współrzędnych.  
  
 ![System współrzędnych](./media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 Podczas wywoływania `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, Pobierz wiersz pokazano na poniższej ilustracji.  
  
 ![System współrzędnych](./media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 Współrzędne punktów końcowych linii w trzech przestrzeni współrzędnych są następujące:  
  
|||  
|-|-|  
|Świata|(0, 0) do (160, 80)|  
|Strona|(100, 50) na (260, 130)|  
|Urządzenie|(100, 50) na (260, 130)|  
  
 Należy pamiętać, że przestrzeni współrzędnych strony ma pochodzenia w lewym górnym rogu obszaru klienckiego; zawsze będzie to wymagane. Należy również zauważyć, że ponieważ jednostka miary jest piksel, urządzenia współrzędne są takie same jak współrzędnych strony. Jeśli ustawisz jednostka miary na coś innego niż pikseli (na przykład, w calach) współrzędnych urządzenia może się różnić od współrzędne strony.  
  
 Transformacji świata, który mapuje współrzędne świata na współrzędne strony, są przechowywane w <xref:System.Drawing.Graphics.Transform%2A> właściwość <xref:System.Drawing.Graphics> klasy. W powyższym przykładzie transformacji świata jest 100 jednostek tłumaczenia, w kierunku x i 50 jednostek w kierunku y. W poniższym przykładzie ustawiono transformacji świata z <xref:System.Drawing.Graphics> obiektu, a następnie używa, <xref:System.Drawing.Graphics> obiektu, aby narysować linię pokazano na poprzednim rysunku:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 Przekształcenie strony mapuje współrzędne strony współrzędnych urządzenia. <xref:System.Drawing.Graphics> Klasa udostępnia <xref:System.Drawing.Graphics.PageUnit%2A> i <xref:System.Drawing.Graphics.PageScale%2A> właściwości do manipulowania przekształcenie strony. <xref:System.Drawing.Graphics> Klasa udostępnia także dwie właściwości tylko do odczytu, <xref:System.Drawing.Graphics.DpiX%2A> i <xref:System.Drawing.Graphics.DpiY%2A>, badania poziome i pionowe punktów na cal, urządzenia.  
  
 Możesz użyć <xref:System.Drawing.Graphics.PageUnit%2A> właściwość <xref:System.Drawing.Graphics> klasy, aby określić jednostki miar innych niż piksela.  
  
> [!NOTE]
>  Nie można ustawić <xref:System.Drawing.Graphics.PageUnit%2A> właściwości <xref:System.Drawing.GraphicsUnit.World>, ponieważ to nie jest jednostką fizycznych i spowodują wyjątek.  
  
 Poniższy przykład pobiera wiersz z (0, 0) do (2, 1), gdzie punkt, (2, 1) jest cala 2 z prawej strony oraz 1 cal w dół od punktu (0, 0):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  Jeśli nie określisz szerokość pióra podczas konstruowania pióra, poprzedni przykład będzie rysowanie linii, o szerokości 1 cal. W drugim argumencie można określić szerokość pióra <xref:System.Drawing.Pen> Konstruktor:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 Przy założeniu, że urządzenia wyświetlającego ma 96 punktów na cal w kierunku poziomym i 96 punktów na cal w kierunku pionowym, punkty końcowe wiersza w poprzednim przykładzie mają następujące współrzędne w trzech przestrzeni współrzędnych:  
  
|||  
|-|-|  
|Świata|(0, 0) do (2, 1)|  
|Strona|(0, 0) do (2, 1)|  
|Urządzenie|(0, 0, aby (192, 96)|  
  
 Uwaga: ponieważ pochodzenia przestrzeni współrzędnych świata znajduje się w lewym górnym rogu obszaru klienta, współrzędne strony są takie same jak współrzędnych świata.  
  
 Można połączyć przekształcenia world i strony, aby uzyskać różne efekty. Na przykład załóżmy, że chcesz użyć cala jako jednostka miary i chcesz, aby pochodzenia swoje współrzędnych za 2 cala od lewej krawędzi obszaru klienta i 1/2 cala od góry obszaru klienta. W poniższym przykładzie ustawiono Przekształcanie świata i strony <xref:System.Drawing.Graphics> obiektu, a następnie rysuje linię z (0, 0) do (2, 1):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 Na poniższej ilustracji przedstawiono wiersza i układ współrzędnych.  
  
 ![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 Przy założeniu, że urządzenia wyświetlającego ma 96 punktów na cal w kierunku poziomym i 96 punktów na cal w kierunku pionowym, punkty końcowe wiersza w poprzednim przykładzie mają następujące współrzędne w trzech przestrzeni współrzędnych:  
  
|||  
|-|-|  
|Świata|(0, 0) do (2, 1)|  
|Strona|(2, 0,5) do (4, 1.5)|  
|Urządzenie|(192, 48) do (384, 144)|  
  
## <a name="see-also"></a>Zobacz także

- [Systemy i przekształcenia współrzędnych](coordinate-systems-and-transformations.md)
- [Macierzowe przedstawienie transformacji](matrix-representation-of-transformations.md)
