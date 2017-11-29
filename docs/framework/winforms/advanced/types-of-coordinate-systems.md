---
title: "Typy systemów współrzędnych"
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be89584ee8e7a82c405bf8664bfad18ced6d989a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="types-of-coordinate-systems"></a>Typy systemów współrzędnych
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]używa trzech przestrzeni współrzędnych: world, strony i urządzenia. Współrzędnych świata są współrzędne użyta do modelowania określonego world grafiki i współrzędne, które są przekazywane do metody w programie .NET Framework. Układ współrzędnych używany przez powierzchni rysowania, takich jak formularz lub formant można znaleźć współrzędnych strony. Współrzędne urządzenia są współrzędne używany przez urządzenie fizyczne sformułowane, takich jak ekranu lub arkusza. Podczas wywoływania `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, punkty, które są przekazywane do <xref:System.Drawing.Graphics.DrawLine%2A> metoda —`(0, 0)` i `(160, 80)`— znajdują się w przestrzeni współrzędnych świata. Przed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można narysować linię na ekranie, współrzędne przekazuj sekwencję transformacji. Jeden przekształcania, nazywany transformacji świata konwertuje współrzędnych świata współrzędnych strony i innym przekształcania, nazywany transformacja strony konwertuje współrzędne strony współrzędnych urządzenia.  
  
## <a name="transforms-and-coordinate-systems"></a>Transformacje i system współrzędnych  
 Załóżmy, że chcesz używać współrzędnych, który ma swoją witryną źródłową w treści obszaru klienckiego, a nie w lewym górnym rogu. Powiedz, na przykład, że chcesz punkt początkowy za 100 pikseli od lewej krawędzi obszaru klienckiego i 50 pikseli od góry obszaru klienckiego. Na poniższej ilustracji przedstawiono układ współrzędnych.  
  
 ![System współrzędnych](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 Podczas wywoływania `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, pobrać wiersza pokazano na poniższej ilustracji.  
  
 ![System współrzędnych](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 Współrzędne punktów końcowych linii w trzech przestrzeni współrzędnych są następujące:  
  
|||  
|-|-|  
|World|(0, 0) do (160, 80)|  
|Strona|(100, 50) do (260, 130)|  
|Urządzenie|(100, 50) do (260, 130)|  
  
 Pamiętaj, że przestrzeni współrzędnych strony ma swoją witryną źródłową w lewym górnym rogu obszaru klienckiego; zawsze będzie wielkość liter. Należy również zauważyć, że jednostka miary jest piksela, współrzędnych urządzenia są takie same jak współrzędnych strony. Jeśli ustawisz jednostka miary inną niż pikseli (na przykład cala) współrzędnych urządzenia może się różnić od współrzędnych strony.  
  
 Transformacja świata, który mapuje współrzędnych świata na współrzędnych strony, jest przechowywany w <xref:System.Drawing.Graphics.Transform%2A> właściwość <xref:System.Drawing.Graphics> klasy. W powyższym przykładzie transformacja świata jest 100 jednostek tłumaczenia, w kierunku x i 50 jednostek w kierunku y. Poniższy przykład przedstawia transformacji świata z <xref:System.Drawing.Graphics> obiekt, a następnie użyty <xref:System.Drawing.Graphics> obiektu do rysowania linii na powyższej ilustracji:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 Transformacja strony mapuje współrzędnych strony współrzędnych urządzenia. <xref:System.Drawing.Graphics> Klasa udostępnia <xref:System.Drawing.Graphics.PageUnit%2A> i <xref:System.Drawing.Graphics.PageScale%2A> właściwości do manipulowania transformacja strony. <xref:System.Drawing.Graphics> Klasa udostępnia również dwie właściwości tylko do odczytu, <xref:System.Drawing.Graphics.DpiX%2A> i <xref:System.Drawing.Graphics.DpiY%2A>, badania poziome i pionowe punktów na cal urządzenia.  
  
 Można użyć <xref:System.Drawing.Graphics.PageUnit%2A> właściwość <xref:System.Drawing.Graphics> klasy, aby określić jednostkę miary niż piksela.  
  
> [!NOTE]
>  Nie można ustawić <xref:System.Drawing.Graphics.PageUnit%2A> właściwości <xref:System.Drawing.GraphicsUnit.World>, ponieważ to nie jest jednostką fizycznych i spowodują wyjątek.  
  
 Poniższy przykład rysuje z (0, 0) do (2, 1), gdzie punktu (2 i 1) to 2 cala w prawo i 1 cala w dół od punktu (0, 0):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  Jeśli nie określisz szerokość pióra podczas konstruowania pióra, poprzedni przykład narysuje wiersza, który jest jeden cal szerokości. Można określić szerokość pióra w drugim argumentem <xref:System.Drawing.Pen> konstruktora:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 Jeśli przyjęto założenie, że urządzenia wyświetlającego ma 96 punktów na cal w kierunku poziomym oraz 96 punktów na cal w kierunku pionowym, punkty końcowe wiersza w powyższym przykładzie są następujące współrzędne w trzech przestrzeni współrzędnych:  
  
|||  
|-|-|  
|World|(0, 0) do (2, 1)|  
|Strona|(0, 0) do (2, 1)|  
|Urządzenie|(0, 0, aby (192, 96)|  
  
 Należy pamiętać, że pochodzenia przestrzeni współrzędnych świata jest w lewym górnym rogu obszaru klienckiego, dlatego współrzędnych strony są takie same jak współrzędnych świata.  
  
 Przekształcenia world i strony, aby uzyskać różne efekty można łączyć. Załóżmy na przykład, ma być używany jako jednostka miary cali i chcesz pochodzenia systemu współrzędnych być 2 cala od lewej krawędzi obszaru klienckiego i 1/2 cala od góry obszaru klienckiego. Poniższy przykład przedstawia transformacji świata i strony z <xref:System.Drawing.Graphics> obiekt, a następnie rysuje z (0, 0) do (2, 1):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 Na poniższej ilustracji przedstawiono wiersza i układ współrzędnych.  
  
 ![System współrzędnych](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 Jeśli przyjęto założenie, że urządzenia wyświetlającego ma 96 punktów na cal w kierunku poziomym oraz 96 punktów na cal w kierunku pionowym, punkty końcowe wiersza w powyższym przykładzie są następujące współrzędne w trzech przestrzeni współrzędnych:  
  
|||  
|-|-|  
|World|(0, 0) do (2, 1)|  
|Strona|(2, 0,5) do (4, 1.5)|  
|Urządzenie|(192, 48) do (384, 144)|  
  
## <a name="see-also"></a>Zobacz też  
 [Systemy i transformacje współrzędnych](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Macierzowe przedstawienie przekształcenia](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)
