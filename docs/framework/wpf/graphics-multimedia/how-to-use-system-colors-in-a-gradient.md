---
title: 'Instrukcje: Używanie kolorów systemowych w gradiencie'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 55c99640907a0c372f8c7bbc50b9b45c9f15ef3c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229443"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Instrukcje: Używanie kolorów systemowych w gradiencie
Aby użyć kolorów systemowych w gradiencie, należy użyć  *\<SystemColor >* kolorów i  *\<SystemColor >* właściwości statycznej ColorKey <xref:System.Windows.SystemColors> klasy w celu uzyskania Odwołanie do koloru, gdzie  *\<SystemColor >* jest nazwą koloru żądany system. Użyj  *\<SystemColor >* ColorKey właściwości, gdy użytkownik chce utworzyć dynamiczne odwołania, który jest aktualizowany automatycznie, zgodnie ze zmianami motywu systemu. W przeciwnym razie użyj  *\<SystemColor >* koloru właściwości.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto dynamicznego systemu zasoby koloru do Tworzenie gradientu.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 W następnym przykładzie użyto statycznego zasoby koloru do Tworzenie gradientu.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.SystemColors>
- [Malowanie obszaru pędzlem systemowym](how-to-paint-an-area-with-a-system-brush.md)
- [Malowanie jednolitymi kolorami i gradientami — przegląd](painting-with-solid-colors-and-gradients-overview.md)
