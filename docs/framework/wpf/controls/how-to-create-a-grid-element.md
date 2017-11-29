---
title: "Jak utworzyć element siatki"
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
helpviewer_keywords: Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd9614aee6e2bf7085b2fbee77993217439320a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-grid-element"></a>Jak utworzyć element siatki
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia i używania wystąpienia <xref:System.Windows.Controls.Grid> za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] lub kodu. W tym przykładzie użyto trzy <xref:System.Windows.Controls.ColumnDefinition> obiektów i trzy <xref:System.Windows.Controls.RowDefinition> obiektów do tworzenia siatki z dziewięciu komórki, taki jak arkusza. Każda komórka zawiera <xref:System.Windows.Controls.TextBlock> zawiera element, który reprezentuje dane i górnym wierszu <xref:System.Windows.Controls.TextBlock> z <xref:System.Windows.Controls.Grid.ColumnSpan%2A> właściwości stosowane. Aby wyświetlić granice każdej komórki <xref:System.Windows.Controls.Grid.ShowGridLines%2A> właściwość jest włączona.  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Grid>  
 [Omówienie paneli](../../../../docs/framework/wpf/controls/panels-overview.md)
