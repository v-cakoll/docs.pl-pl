---
title: 'Instrukcje: Dostosowywanie znaczników na suwaku'
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: 3b32bbedb5f654ce75e90a827eb0c4dba1d4d345
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164245"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a>Instrukcje: Dostosowywanie znaczników na suwaku
W tym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Controls.Slider> formant, który zawiera znaczniki.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.Primitives.TickBar> Wyświetlana po ustawieniu <xref:System.Windows.Controls.Slider.TickPlacement%2A> właściwości na wartość inną niż <xref:System.Windows.Controls.Primitives.TickPlacement.None>, która jest wartością domyślną.  
  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.Slider> z <xref:System.Windows.Controls.Primitives.TickBar> , wyświetla znaczniki. <xref:System.Windows.Controls.Slider.TickPlacement%2A> i <xref:System.Windows.Controls.Slider.TickFrequency%2A> właściwości definiują lokalizację znaczników oraz interwału między nimi. Przy przenoszeniu <xref:System.Windows.Controls.Primitives.Thumb>, wyświetlania wartości w etykietkach ekranowych <xref:System.Windows.Controls.Slider>. <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> Właściwość określa, gdzie występują etykietki narzędzi. <xref:System.Windows.Controls.Primitives.Thumb> Przeniesień odnoszą się do lokalizacji pliku znaczników ponieważ <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> ustawiono `true`.  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.Slider.Ticks%2A> właściwości do utworzenia znaczniki wzdłuż osi <xref:System.Windows.Controls.Slider> w nieregularnych odstępach czasu.  
  
 [!code-xaml[Slider#4](~/samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Slider>
- <xref:System.Windows.Controls.Primitives.TickBar>
- <xref:System.Windows.Controls.Slider.TickPlacement%2A>
- [Instrukcje: Powiąż suwak na wartość właściwości](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms788716(v=vs.90))
