---
title: 'Instrukcje: Programowe zmienianie parametru TextWrapping zawartości'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
ms.openlocfilehash: 21ca31d24121492fe6927cd533d5b3c0785b5a28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975003"
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a>Instrukcje: Programowe zmienianie parametru TextWrapping zawartości
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak zmienić wartość <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> właściwość programowo.  
  
 Trzy <xref:System.Windows.Controls.Button> elementy są umieszczane w ramach <xref:System.Windows.Controls.StackPanel> element [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Każdy <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie <xref:System.Windows.Controls.Button> odpowiada za pomocą programu obsługi zdarzeń w kodzie. Programy obsługi zdarzeń Użyj taką samą nazwę jak <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> wartości będą one dotyczyć `txt2` po kliknięciu przycisku. Ponadto tekstu w `txt1` ( <xref:System.Windows.Controls.TextBlock> nie są wyświetlane w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) zostanie zaktualizowany w celu odzwierciedlenia zmiany we właściwości.  
  
 [!code-xaml[TextWrapProperty#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>
- <xref:System.Windows.TextWrapping>
