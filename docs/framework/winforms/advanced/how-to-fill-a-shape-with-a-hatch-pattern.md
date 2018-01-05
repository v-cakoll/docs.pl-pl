---
title: "Porady: wypełnianie kształtów wzorem kreskowanym"
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
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f44289b79812f2330639cc333727bd21b6ef4fe6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>Porady: wypełnianie kształtów wzorem kreskowanym
Wzorzec kreskowania staje się z dwóch kolorów: jeden dla tła i jeden dla wierszy, które tworzą wzorca w tle. Aby wypełnić zamkniętego kształtów wzorem kreskowanym, użyj <xref:System.Drawing.Drawing2D.HatchBrush> obiektu. W poniższym przykładzie pokazano sposób wypełniania elipsy wzorem kreskowanym:  
  
## <a name="example"></a>Przykład  
 <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> Konstruktor ma trzy argumenty: Styl kreskowania, kolor kreskowania linii i kolor tła. Argument Styl kreskowania może mieć dowolną wartość z <xref:System.Drawing.Drawing2D.HatchStyle> wyliczenia. Istnieje więcej niż 50 elementów w <xref:System.Drawing.Drawing2D.HatchStyle> wyliczenie; niektóre z tych elementów są wyświetlane na poniższej liście:  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 Na poniższej ilustracji przedstawiono wypełnioną elipsę.  
  
 ![Wzorzec kreskowania](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")  
  
 [!code-csharp[System.Drawing.UsingABrush#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie pędzla do wypełniania kształtów](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
