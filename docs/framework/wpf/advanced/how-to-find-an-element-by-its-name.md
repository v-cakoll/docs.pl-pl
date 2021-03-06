---
title: 'Instrukcje: Znajdowanie elementu po jego nazwie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
ms.openlocfilehash: 7405f9ba8db5d4db0ce35ca250f13e456685f39b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757849"
---
# <a name="how-to-find-an-element-by-its-name"></a>Instrukcje: Znajdowanie elementu po jego nazwie
W tym przykładzie przedstawiono sposób użycia <xref:System.Windows.FrameworkElement.FindName%2A> metodę, aby znaleźć element po jego <xref:System.Windows.FrameworkElement.Name%2A> wartość.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie metody do znalezienia konkretnego elementu według jego nazwy są zapisywane jako program obsługi zdarzeń przycisku. `stackPanel` jest <xref:System.Windows.FrameworkElement.Name%2A> głównego <xref:System.Windows.FrameworkElement> wyszukiwana, a przykładowa metoda następnie wizualnie wskazuje znaleziono element przez rzutowanie go jako <xref:System.Windows.Controls.TextBlock> i jednej <xref:System.Windows.Controls.TextBlock> widoczne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] właściwości.  
  
 [!code-csharp[FEFindName#Find](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
