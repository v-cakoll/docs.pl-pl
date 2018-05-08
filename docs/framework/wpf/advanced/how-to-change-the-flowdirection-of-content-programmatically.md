---
title: Jak zmienić FlowDirection zawartości za pomocą programowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
ms.openlocfilehash: 97a64ad54384077a15a643dc528d043b2ef6627a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>Jak zmienić FlowDirection zawartości za pomocą programowania
W tym przykładzie pokazano, jak programowo zmienić <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość <xref:System.Windows.Controls.FlowDocumentReader>.  
  
## <a name="example"></a>Przykład  
 Dwa <xref:System.Windows.Controls.Button> elementy są tworzone, każdy reprezentuje jedną z możliwych wartości <xref:System.Windows.FlowDirection>. Kliknięcie przycisku wartości właściwości skojarzonej, ponieważ jest stosowany do zawartości <xref:System.Windows.Controls.FlowDocumentReader> o nazwie `tf1`.  Wartość właściwości są równocześnie zapisywane w <xref:System.Windows.Controls.TextBlock> o nazwie `txt1`.  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>Przykład  
 Zdarzenia powiązane z kliknięcia przycisków zdefiniowanych powyżej są obsługiwane w pliku związanym z kodem C#.  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
