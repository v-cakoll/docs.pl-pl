---
title: "Jak interaktywnie kontrolować zegar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: debe65ef1587171dc2f324a19da4b43e7274c438
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-interactively-control-a-clock"></a>Jak interaktywnie kontrolować zegar
A <xref:System.Windows.Media.Animation.Clock> obiektu <xref:System.Windows.Media.Animation.ClockController> właściwość umożliwia interaktywnie uruchamiania, wstrzymać, wznowić, wyszukiwanie, poprawić zegara, aby okresu i zatrzymać zegara. Zegar w katalogu głównego drzewa czasu można sterować interaktywnie.  
  
> [!NOTE]
>  Istnieją inne sposoby interaktywnie animacje kontroli niewymagających pracować bezpośrednio z zegary: umożliwia także Scenorys. Scenorys są obsługiwane zarówno znaczników i kodu. Na przykład zobacz [animować właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) lub [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 W poniższym przykładzie kilka przycisków są używane do sterowania interaktywnego zegara animacji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>Zobacz też  
 [Animować właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [Animacja — omówienie](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
