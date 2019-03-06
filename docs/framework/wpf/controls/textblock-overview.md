---
title: TextBlock — Przegląd
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], TextBlock
- TextBlock control [WPF]
ms.assetid: 24720bca-341a-4b03-8a6b-7a678023b10a
ms.openlocfilehash: a3ea656a902f8a112a700667b6e08cae7463f68d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374469"
---
# <a name="textblock-overview"></a>TextBlock — Przegląd
<xref:System.Windows.Controls.TextBlock> Kontroli zapewnia obsługę tekst elastyczny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Element jest przeznaczona głównie basic [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenariusze, które nie wymagają więcej niż jeden akapit. Obsługuje ona wiele właściwości, umożliwiające precyzyjną kontrolę nad prezentacji, takich jak <xref:System.Windows.Controls.TextBlock.FontFamily%2A>, <xref:System.Windows.Controls.TextBlock.FontSize%2A>, <xref:System.Windows.Controls.TextBlock.FontWeight%2A>, <xref:System.Windows.Controls.TextBlock.TextEffects%2A>, i <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>. Zawartość tekstowa można dodać za pomocą <xref:System.Windows.Controls.TextBlock.Text%2A> właściwości. Gdy są używane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zawartości między otwieranie i zamykanie tag niejawnie jest dodawany jako tekstu elementu.  
  
 A <xref:System.Windows.Controls.TextBlock> elementu mogą być tworzone w bardzo prosty sposób przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[TextBlockSnip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 Podobnie, użycie <xref:System.Windows.Controls.TextBlock> elementu w kodzie jest stosunkowo prosta.  
  
 [!code-csharp[TextBlockSnip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.Label>
