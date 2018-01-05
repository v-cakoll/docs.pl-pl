---
title: "Jak znaleźć element po jego nazwie"
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
helpviewer_keywords: elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c51f22cb663b77ddcbbc280ab9d93c5e0eb7405
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-an-element-by-its-name"></a>Jak znaleźć element po jego nazwie
W tym przykładzie przedstawiono sposób użycia <xref:System.Windows.FrameworkElement.FindName%2A> metody do znalezienia elementu przez jego <xref:System.Windows.FrameworkElement.Name%2A> wartość.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie metody do znalezienia dany element na podstawie nazwy są zapisywane jako program obsługi zdarzeń przycisku. `stackPanel`jest <xref:System.Windows.FrameworkElement.Name%2A> głównego <xref:System.Windows.FrameworkElement> przeszukiwany, i przykładowa metoda następnie wizualnie wskazuje znaleziono element przez rzutowanie go jako <xref:System.Windows.Controls.TextBlock> i zmiana jednego z <xref:System.Windows.Controls.TextBlock> widoczne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] właściwości.  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
