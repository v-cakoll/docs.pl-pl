---
title: Jak użyć właściwości BetweenShowDelay
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: 7d48fb859ec6d37abd2490bc718d58cbdaa67f13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552717"
---
# <a name="how-to-use-the-betweenshowdelay-property"></a>Jak użyć właściwości BetweenShowDelay
Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> czasu właściwości elementy ToolTip będą wyświetlane szybko — z opóźnieniem niewielkiego lub żadnego — po użytkownik przesuwa wskaźnik myszy z jednego tooltip bezpośrednio do innego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> właściwość jest ustawiona na 1 sekundę (1000 milisekund) i <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> jest ustawiony na dwóch sekund (2000 MS) dla etykietek narzędzi obu <xref:System.Windows.Shapes.Ellipse> kontrolki. Wyświetl etykietki narzędzia dla jednego z wielokropek, a następnie przenieś wskaźnik myszy do innego elipsy w dwóch sekund i Wstrzymaj na nim, etykietka narzędzia drugi elipsy Wyświetla natychmiast.  
  
 W jednym z następujących scenariuszy <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> ma zastosowanie, co powoduje, że etykietkę narzędzia dla drugiego elipsy oczekiwania przed wygląda na to:  
  
-   Jeśli czas potrzebny do przenoszenia do drugiego przycisku jest więcej niż dwie sekundy.  
  
-   Jeśli element tooltip nie jest widoczny na początku przedział czasu dla pierwszego elipsy.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [ToolTip — omówienie](../../../../docs/framework/wpf/controls/tooltip-overview.md)
