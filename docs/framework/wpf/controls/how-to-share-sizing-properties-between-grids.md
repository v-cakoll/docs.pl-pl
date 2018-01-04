---
title: "Jak udostępniać właściwości ustalania rozmiaru miedzy siatkami"
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
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8f80d93f9625ff962a3e3fab1f6647678ecf32f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-share-sizing-properties-between-grids"></a>Jak udostępniać właściwości ustalania rozmiaru miedzy siatkami
W tym przykładzie pokazano, jak udostępniać dane zmiany rozmiaru kolumn i wierszy między <xref:System.Windows.Controls.Grid> elementy, aby zachować zmiany rozmiaru spójne.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwa <xref:System.Windows.Controls.Grid> jako elementy podrzędne elementu nadrzędnego <xref:System.Windows.Controls.DockPanel>. <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> Dołączona właściwość <xref:System.Windows.Controls.Grid> jest zdefiniowany w nadrzędnej <xref:System.Windows.Controls.DockPanel>.  
  
 Przykład manipuluje wartość właściwości przy użyciu dwóch <xref:System.Windows.Controls.Button> elementy; każdy element reprezentuje jednej wartości właściwości typu Boolean. Gdy <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> ma ustawioną wartość właściwości `true`, każdy członek kolumny lub wiersza z <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> udostępnia informacje dotyczące zmiany rozmiaru, niezależnie od zawartości wierszy lub kolumn.  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 ...  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 W poniższym przykładzie kodu powiązanego obsługuje metody który przycisk <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zgłasza zdarzenie. W przykładzie polecenie zapisuje wyniki tych wywołań metody <xref:System.Windows.Controls.TextBlock> elementów powiązanych Użyj get metody zwracać wartości właściwości jako ciągi.  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)
