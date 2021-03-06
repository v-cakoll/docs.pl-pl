---
title: 'Instrukcje: Używanie właściwości BetweenShowDelay'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: 9b63675ec21294496117860aa5b58af132c4284a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614530"
---
# <a name="how-to-use-the-betweenshowdelay-property"></a>Instrukcje: Używanie właściwości BetweenShowDelay
W tym przykładzie pokazano, jak używać <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> czasu właściwość tak, aby szybko są wyświetlane etykietki narzędzi — z opóźnieniem niewielkiego lub żadnego — gdy użytkownik przesuwa wskaźnik myszy z jednej etykietki narzędzia bezpośrednio do innego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> właściwość jest ustawiona na sekundę (1000 milisekund) i <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> jest ustawiony na dwóch sekund (2000 MS) dla etykietki narzędzi w obu <xref:System.Windows.Shapes.Ellipse> kontrolki. Wyświetlić etykietkę narzędzia dla jednego z wielokropek, a następnie przenieś wskaźnik myszy do innego elipsę w ramach dwóch sekund i wstrzymania na nim, natychmiast wyświetla etykietkę narzędzia drugi elipsy.  
  
 W jednym z następujących scenariuszy <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> ma zastosowanie, co powoduje, że etykietkę narzędzia dla drugiego ikonę wielokropka, aby czekać przed wygląda na to:  
  
- Jeśli czas wymagany na przeniesienie do drugiego przycisku jest więcej niż dwóch sekund.  
  
- Jeśli etykietka narzędzia nie jest widoczny na początku przedział czasowy na potrzeby pierwszego elipsy.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Tematy z instrukcjami](tooltip-how-to-topics.md)
- [ToolTip — omówienie](tooltip-overview.md)
