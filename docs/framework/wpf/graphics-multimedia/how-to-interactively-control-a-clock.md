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
ms.openlocfilehash: 2d18f395974750a6b85458f636a27f6101e7978f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951335"
---
# <a name="how-to-interactively-control-a-clock"></a>Instrukcje: Interakcyjne sterowanie zegarem
Właściwość<xref:System.Windows.Media.Animation.ClockController>obiektupozwala interaktywnie uruchamiać, wstrzymywać, wznawiać, poszukiwać, przełączać do jego okresu wypełniania i <xref:System.Windows.Media.Animation.Clock> zatrzymywać zegar. Tylko zegar główny drzewa chronometrażu może być interaktywnie kontrolowany.  
  
> [!NOTE]
> Istnieją inne sposoby interaktywnej kontroli animacji, które nie wymagają bezpośredniej pracy z zegarami: można również użyć scenorysów. Scenorysy są obsługiwane zarówno w znacznikach, jak i w kodzie. Aby zapoznać się z przykładem, zobacz [Animuj Właściwość za pomocą scenorysu](how-to-animate-a-property-by-using-a-storyboard.md) lub [Przegląd animacji](animation-overview.md).  
  
 W poniższym przykładzie kilka przycisków służy do interaktywnego sterowania zegarem animacji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>Zobacz także

- [Animowanie właściwości przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md)
- [Animacja — przegląd](animation-overview.md)
