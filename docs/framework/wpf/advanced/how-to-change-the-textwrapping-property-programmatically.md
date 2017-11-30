---
title: "Jak zmienić właściwość TextWrapping za pomocą programowania"
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
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 74ddcf55c8918602ecac866913f2007da143f443
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a>Jak zmienić właściwość TextWrapping za pomocą programowania
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób zmień wartość <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> właściwości programowo.  
  
 Trzy <xref:System.Windows.Controls.Button> elementy są umieszczane w <xref:System.Windows.Controls.StackPanel> element [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Każdy <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia dla <xref:System.Windows.Controls.Button> odpowiada program obsługi zdarzeń w kodzie. Programy obsługi zdarzeń, użyj takiej samej nazwie jak <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> wartość będzie dotyczyć `txt2` po kliknięciu przycisku. Ponadto tekst w `txt1` ( <xref:System.Windows.Controls.TextBlock> nie są wyświetlane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) jest aktualizowana w celu odzwierciedlenia zmian we właściwości.  
  
 [!code-xaml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>  
 <xref:System.Windows.TextWrapping>
