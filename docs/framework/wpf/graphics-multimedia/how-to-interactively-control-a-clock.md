---
title: 'Instrukcje: Interakcyjne sterowanie zegarem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 05989b6a03e03fb5723a70c9c36d5e32f9117049
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186592"
---
# <a name="how-to-interactively-control-a-clock"></a>Instrukcje: Interakcyjne sterowanie zegarem
A <xref:System.Windows.Media.Animation.Clock> obiektu <xref:System.Windows.Media.Animation.ClockController> Właściwość pozwala interaktywnie Uruchom, wstrzymać, wznowić, wyszukiwanie, przejdź zegar okresu wypełnienia i zatrzymać zegara. Tylko zegara głównego drzewa chronometrażu mogą być kontrolowane interaktywnie.  
  
> [!NOTE]
>  Istnieją inne sposoby, aby interaktywnie animacji kontrolki niewymagających współpracować bezpośrednio z zegary: Możesz również użyć scenorysów. Scenorysy są obsługiwane zarówno w przypadku znaczników, jak i kod. Aby uzyskać przykład, zobacz [animować właściwość przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md) lub [Przegląd animacja](animation-overview.md).  
  
 W poniższym przykładzie kilka przyciski są używane do interaktywnie kontrolować zegar animacji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Animowanie właściwości przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md)
- [Animacja — przegląd](animation-overview.md)
