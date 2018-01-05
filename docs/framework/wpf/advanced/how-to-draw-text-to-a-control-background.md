---
title: "Porady: Rysowanie tekstu do formantu &#39; s tła"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 091be80e055279685c9dba33dd6b6635e64eaff0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-text-to-a-control39s-background"></a>Porady: Rysowanie tekstu do formantu &#39; s tła
Tekst można narysować bezpośrednio do tła formantu, konwertując ciąg tekstowy do <xref:System.Windows.Media.FormattedText> obiekt, a następnie rysowania obiektu do formantu <xref:System.Windows.Media.DrawingContext>. Umożliwia także ta technika dla rysunku do tła obiekty pochodne <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.StackPanel>.  
  
 ![Wyświetlanie tekstu jako tła formantów](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
Przykład formantów z tła tekstu niestandardowego  
  
## <a name="example"></a>Przykład  
 Aby narysować do tła formantu, Utwórz nową <xref:System.Windows.Media.DrawingBrush> obiektu i Rysuj tekst skonwertowany do obiektu <xref:System.Windows.Media.DrawingContext>. Następnie przypisz nowe <xref:System.Windows.Media.DrawingBrush> do właściwości tła formantu.  
  
 W poniższym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Media.FormattedText> obiektu i rysowanie do tła <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Button> obiektu.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.FormattedText>  
 [Rysowanie formatowanego tekstu](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
