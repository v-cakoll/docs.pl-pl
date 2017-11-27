---
title: "Jak użyć obiektu ThicknessConverter"
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
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ce70dcd749f31d77061b4669d83d2e0b83726c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-thicknessconverter-object"></a>Jak użyć obiektu ThicknessConverter
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób tworzenia wystąpienia <xref:System.Windows.ThicknessConverter> i użyj go, aby zmienić szerokość krawędzi.  
  
 W przykładzie zdefiniowano niestandardowe metodę o nazwie `changeThickness`; ta metoda konwertuje najpierw zawartość <xref:System.Windows.Controls.ListBoxItem>, zgodnie z definicją w oddzielnej [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliku, aby wystąpienie <xref:System.Windows.Thickness>i później Konwertuje zawartość do <xref:System.String>. Ta metoda przekazuje <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.ThicknessConverter> obiektu, który konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na wystąpienie <xref:System.Windows.Thickness>. Ta wartość jest następnie przekazywany z powrotem jako wartość <xref:System.Windows.Controls.Border.BorderThickness%2A> właściwość <xref:System.Windows.Controls.Border>.  
  
 W tym przykładzie nie działa.  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Thickness>  
 <xref:System.Windows.ThicknessConverter>  
 <xref:System.Windows.Controls.Border>  
 [Porady: Zmienianie właściwości margines](http://msdn.microsoft.com/en-us/8a313efd-5f99-4097-b4c1-8fa49d8379a2)  
 [Porady: Konwertowanie elementu ListBoxItem na nowy typ danych](http://msdn.microsoft.com/en-us/7a080b88-184e-4b27-bb61-d42bafba9727)  
 [Omówienie paneli](../../../../docs/framework/wpf/controls/panels-overview.md)
