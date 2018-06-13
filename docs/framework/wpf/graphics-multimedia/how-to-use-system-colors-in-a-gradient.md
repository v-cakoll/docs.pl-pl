---
title: Jak użyć kolorów systemowych w gradiencie
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 4c3fca1db031b0dc397e9db58195b9714ff8aa9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562183"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Jak użyć kolorów systemowych w gradiencie
Użyj kolorów systemu w gradiencie, należy użyć  *\<SystemColor >* kolorów i  *\<SystemColor >* ColorKey właściwości statycznej <xref:System.Windows.SystemColors> klasy w celu uzyskania Odwołanie do kolorów, gdzie  *\<SystemColor >* jest nazwą koloru żądany system. Użyj  *\<SystemColor >* ColorKey właściwości, gdy chcesz utworzyć odwołanie do dynamicznej aktualizacji automatycznie jako zmian kompozycji systemu. W przeciwnym razie użyj  *\<SystemColor >* kolor właściwości.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto dynamicznego systemu kolor zasobów do Tworzenie gradientu.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 W następnym przykładzie użyto zasobów kolorów systemu statycznego do Tworzenie gradientu.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.SystemColors>  
 [Malowanie obszaru pędzlem systemowym](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Malowanie jednolitymi kolorami i gradientami — przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
