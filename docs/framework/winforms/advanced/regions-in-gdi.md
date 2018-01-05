---
title: Regiony w GDI+
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
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d3805c2d67f5241425ef72d3802aba996d33cfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="regions-in-gdi"></a>Regiony w GDI+
Region jest częścią obszaru wyświetlania urządzenia wyjściowego. Regiony może być prosty (pojedynczy prostokąt) lub złożonych (kombinacja wielokątów i krzywych zamknięte). Na poniższej ilustracji przedstawiono dwóch regionach: jeden utworzone na podstawie prostokąt i innych utworzone na podstawie ścieżki.  
  
 ![Regiony](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")  
  
## <a name="using-regions"></a>Używanie regionów  
 Regiony są często używane na wycinka i testowanie trafień. Wycinka obejmuje ograniczanie rysunku do regionu obszaru wyświetlania zwykle fragment, który musi zostać zaktualizowany. Testowanie trafień obejmuje sprawdzanie, czy kursor jest w danym regionie ekranu po naciśnięciu przycisku myszy.  
  
 Można utworzyć obszarem prostokąta lub ścieżki. Można też utworzyć złożonych regionów, łącząc istniejący regionów. <xref:System.Drawing.Region> Klasa udostępnia następujące metody łączenie regionów: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, i <xref:System.Drawing.Region.Complement%2A>.  
  
 Część wspólną dwóch regionach jest zestaw wszystkich punktów należących do obu regionów. Unia jest zestaw wszystkich punktów należących do jednej lub drugiej lub obu regionów. Uzupełnienie regionu jest zestaw wszystkich punktów, które nie znajdują się w regionie. Na poniższej ilustracji przedstawiono przecięcia i złożenie dwóch regionach, pokazane na powyższej ilustracji.  
  
 ![Regiony](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")  
  
 <xref:System.Drawing.Region.Xor%2A> Metody stosowane do pary regionów, tworzy region, który zawiera wszystkie punkty, które należą do jednego regionu lub innych, ale nie oba. <xref:System.Drawing.Region.Exclude%2A> Metody stosowane do pary regionów, tworzy region, który zawiera wszystkie punkty w regionie pierwszy, które nie znajdują się w drugim regionu. Na poniższej ilustracji przedstawiono regionów, w wyniku zastosowania <xref:System.Drawing.Region.Xor%2A> i <xref:System.Drawing.Region.Exclude%2A> metody do dwóch regionach pokazywane na początku tego tematu.  
  
 ![Regiony](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")  
  
 Aby wypełnić region, należy <xref:System.Drawing.Graphics> obiektu, <xref:System.Drawing.Brush> obiektu, a <xref:System.Drawing.Region> obiektu. <xref:System.Drawing.Graphics> Zawiera obiekt <xref:System.Drawing.Graphics.FillRegion%2A> metody i <xref:System.Drawing.Brush> obiekt przechowuje atrybuty wypełnienia, takie jak kolor lub deseń. Poniższy przykład wypełnia region jednolitym kolorem.  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [Linie, krzywe i kształty](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Używanie regionów](../../../../docs/framework/winforms/advanced/using-regions.md)
