---
title: Regiony w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
ms.openlocfilehash: ae4931a464421639112c8f369bd27a45550fe7f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708275"
---
# <a name="regions-in-gdi"></a>Regiony w GDI+
Region jest częścią obszaru wyświetlania na urządzeniach. Regiony może być prosty (prostokąt pojedynczego) lub złożona (połączenia wielokąty i krzywych zamknięte). Na poniższej ilustracji przedstawiono dwa regiony: jeden wykonany z prostokąt i innych skonstruowany na podstawie ścieżki.  
  
 ![Regiony](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")  
  
## <a name="using-regions"></a>Używanie regionów  
 Regiony są często używane do wycinka i testowania trafień. Wycinka polega na ograniczenie rysunku do region wyświetlacz, zwykle fragment, który musi zostać zaktualizowany. Testowanie trafień sprawdza się, aby ustalić, czy kursor znajduje się w danym regionie ekranu po naciśnięciu przycisku myszy.  
  
 Można skonstruować obszarem prostokąta lub ścieżki. Można również utworzyć złożone regionów, łącząc istniejących regionach. <xref:System.Drawing.Region> Klasa udostępnia następujące metody łączenia regionów: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, i <xref:System.Drawing.Region.Complement%2A>.  
  
 Część wspólną dwóch regionach to zestaw wszystkich punktów należących do obu regionach. Unia to zestaw wszystkich punktów należących do jednej lub drugiej lub obu regionach. Uzupełnienie region to zestaw wszystkich punktów, które nie znajdują się w regionie. Na poniższej ilustracji przedstawiono część wspólną i sumę dwóch regionach pokazano na poprzedniej ilustracji.  
  
 ![Regiony](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")  
  
 <xref:System.Drawing.Region.Xor%2A> Metody stosowane do pary regionów, tworzy obszar, który zawiera wszystkie punkty, które należą do jednego regionu lub innych, ale nie oba. <xref:System.Drawing.Region.Exclude%2A> Metody stosowane do pary regionów, tworzy obszar, który zawiera wszystkie punkty w pierwszym regionie, które nie znajdują się w drugim regionie. Na poniższej ilustracji przedstawiono regionów, w wyniku zastosowania <xref:System.Drawing.Region.Xor%2A> i <xref:System.Drawing.Region.Exclude%2A> metod w dwóch regionach przedstawionych na początku tego tematu.  
  
 ![Regiony](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")  
  
 Aby wypełnić regionu, należy <xref:System.Drawing.Graphics> obiektu, <xref:System.Drawing.Brush> obiektu, a <xref:System.Drawing.Region> obiektu. <xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.FillRegion%2A> metody i <xref:System.Drawing.Brush> obiekt przechowuje atrybuty wypełnienia, takich jak kolor lub deseń. Poniższy przykład wypełnia obszar jednolitym kolorem.  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [Używanie regionów](../../../../docs/framework/winforms/advanced/using-regions.md)
