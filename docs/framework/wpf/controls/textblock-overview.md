---
title: "TextBlock — Przegląd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], TextBlock
- TextBlock control [WPF]
ms.assetid: 24720bca-341a-4b03-8a6b-7a678023b10a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a6ec20c43a269ded5d5d7a27bf0ad4be11f6a92
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="textblock-overview"></a>TextBlock — Przegląd
<xref:System.Windows.Controls.TextBlock> Kontroli zapewnia elastyczne tekst obsługę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Element jest przeznaczony głównie kierunku basic [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariusze, które nie wymagają więcej niż jednego akapitu tekstu. Obsługuje wiele właściwości, umożliwiające precyzyjną kontrolę prezentacji, takich jak <xref:System.Windows.Controls.TextBlock.FontFamily%2A>, <xref:System.Windows.Controls.TextBlock.FontSize%2A>, <xref:System.Windows.Controls.TextBlock.FontWeight%2A>, <xref:System.Windows.Controls.TextBlock.TextEffects%2A>, i <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>. Zawartość tekstu można dodać za pomocą <xref:System.Windows.Controls.TextBlock.Text%2A> właściwości. W przypadku używania w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zawartości między otwarcia i zamknięcia tagu niejawnie jest dodawana jako tekstu elementu.  
  
 A <xref:System.Windows.Controls.TextBlock> można wdrożyć elementu bardzo prosty przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[TextBlockSnip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 Podobnie, użycie <xref:System.Windows.Controls.TextBlock> elementu w kodzie jest stosunkowo proste.  
  
 [!code-csharp[TextBlockSnip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Label>
