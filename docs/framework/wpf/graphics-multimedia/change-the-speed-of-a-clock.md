---
title: 'Instrukcje: Zmień prędkość zegara bez zmiany prędkości jego przedziału czasowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- speed of Clock [WPF], changing
- clocks [WPF], changing speed of
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
ms.openlocfilehash: 19e6874b9b472cb4a5f716677f99af03f2b73b10
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358278"
---
# <a name="how-to-change-the-speed-of-a-clock-without-changing-the-speed-of-its-timeline"></a>Instrukcje: Zmień prędkość zegara bez zmiany prędkości jego przedziału czasowego
A <xref:System.Windows.Media.Animation.ClockController> obiektu <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> Właściwość pozwala zmienić szybkość <xref:System.Windows.Media.Animation.Clock> bez zmiany <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> zegara <xref:System.Windows.Media.Animation.Timeline>. W poniższym przykładzie <xref:System.Windows.Media.Animation.ClockController> jest używane do modyfikowania interaktywnie <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> zegara. <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> Zdarzenia a zegarem <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> właściwości są używane do wyświetlania bieżącej szybkości globalnego zegara każdym jego interaktywne <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> zostanie zmieniony.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]
