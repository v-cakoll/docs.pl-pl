---
title: "Jak użyć kolorów systemowych w gradiencie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 105e22588f68d999811f5482342d53851a4d25eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Jak użyć kolorów systemowych w gradiencie
Użyj kolorów systemu w gradiencie, należy użyć  *\<SystemColor >*kolorów i  *\<SystemColor >*ColorKey właściwości statycznej <xref:System.Windows.SystemColors> klasy w celu uzyskania Odwołanie do kolorów, gdzie  *\<SystemColor >* jest nazwą koloru żądany system. Użyj  *\<SystemColor >*ColorKey właściwości, gdy chcesz utworzyć odwołanie do dynamicznej aktualizacji automatycznie jako zmian kompozycji systemu. W przeciwnym razie użyj  *\<SystemColor >*kolor właściwości.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto dynamicznego systemu kolor zasobów do Tworzenie gradientu.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 W następnym przykładzie użyto zasobów kolorów systemu statycznego do Tworzenie gradientu.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.SystemColors>  
 [Malowanie obszar o pędzla systemu](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Malowanie pełnych kolorów i gradientów — omówienie](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
