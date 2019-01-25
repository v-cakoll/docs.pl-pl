---
title: 'Instrukcje: Użyj kolorów systemowych w gradiencie'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 44dfd30dc8d21e638855a383f1c9360a61ce81f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726419"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Instrukcje: Użyj kolorów systemowych w gradiencie
Aby użyć kolorów systemowych w gradiencie, należy użyć  *\<SystemColor >* kolorów i  *\<SystemColor >* właściwości statycznej ColorKey <xref:System.Windows.SystemColors> klasy w celu uzyskania Odwołanie do koloru, gdzie  *\<SystemColor >* jest nazwą koloru żądany system. Użyj  *\<SystemColor >* ColorKey właściwości, gdy użytkownik chce utworzyć dynamiczne odwołania, który jest aktualizowany automatycznie, zgodnie ze zmianami motywu systemu. W przeciwnym razie użyj  *\<SystemColor >* koloru właściwości.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto dynamicznego systemu zasoby koloru do Tworzenie gradientu.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 W następnym przykładzie użyto statycznego zasoby koloru do Tworzenie gradientu.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.SystemColors>
- [Malowanie obszaru pędzlem systemowym](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Malowanie jednolitymi kolorami i gradientami — przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
