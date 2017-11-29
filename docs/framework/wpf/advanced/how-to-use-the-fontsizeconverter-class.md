---
title: "Jak użyć klasy FontSizeConverter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bcf2d7348ca5b6b9d3b2edc44f92afbd46d32594
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>Jak użyć klasy FontSizeConverter
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób tworzenia wystąpienia <xref:System.Windows.FontSizeConverter> i użyj go, aby zmienić rozmiar czcionki.  
  
 W przykładzie zdefiniowano niestandardowe metodę o nazwie `changeSize` Konwertuje zawartość <xref:System.Windows.Controls.ListBoxItem>, zgodnie z definicją w oddzielnej [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku, aby wystąpienie <xref:System.Double>lub nowszy w <xref:System.String>. Ta metoda przekazuje <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.FontSizeConverter> obiektu, który konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na wystąpienie <xref:System.Double>. Ta wartość jest następnie przekazywany z powrotem jako wartość <xref:System.Windows.Controls.TextBlock.FontSize%2A> właściwość <xref:System.Windows.Controls.TextBlock> elementu.  
  
 W tym przykładzie zdefiniowano także drugi niestandardowej metody, która jest wywoływana `changeFamily`. Ta metoda konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do <xref:System.String>, a następnie przekazuje tę wartość do <xref:System.Windows.Controls.TextBlock.FontFamily%2A> właściwość <xref:System.Windows.Controls.TextBlock> elementu.  
  
 W tym przykładzie nie działa.  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FontSizeConverter>
