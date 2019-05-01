---
title: 'Instrukcje: Programowe zmienianie parametru FlowDirection zawartości'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
ms.openlocfilehash: ec159ed0efce8b5514788331e8715a55e7a8a638
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776561"
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>Instrukcje: Programowe zmienianie parametru FlowDirection zawartości
W tym przykładzie przedstawiono sposób programowego modyfikowania <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość <xref:System.Windows.Controls.FlowDocumentReader>.  
  
## <a name="example"></a>Przykład  
 Dwa <xref:System.Windows.Controls.Button> elementy są tworzone, każdy reprezentuje jedną z możliwych wartości <xref:System.Windows.FlowDirection>. Po kliknięciu przycisku wartości skojarzonej właściwości są stosowane do zawartości <xref:System.Windows.Controls.FlowDocumentReader> o nazwie `tf1`.  Wartość właściwości są równocześnie zapisywane <xref:System.Windows.Controls.TextBlock> o nazwie `txt1`.  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>Przykład  
 Obsługi zdarzeń powiązanych ze kliknięć przycisków, zdefiniowanych powyżej w C# pliku CodeBehind.  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
