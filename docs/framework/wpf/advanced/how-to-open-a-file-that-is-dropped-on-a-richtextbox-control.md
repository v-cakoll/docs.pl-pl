---
title: 'Instrukcje: Otwieranie pliku, który został upuszczony na kontrolkę RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
ms.openlocfilehash: 8ffa4c9919788060dc4524e127c181ee8282e6f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768605"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>Instrukcje: Otwieranie pliku, który został upuszczony na kontrolkę RichTextBox
W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, i <xref:System.Windows.Documents.FlowDocument> wszystkich kontrolek posiada wbudowanej funkcji przeciągania i upuszczania. Wbudowane funkcje umożliwia przeciąganie i upuszczanie tekstu wewnątrz i pomiędzy kontrolki. Jednak nie umożliwia otwarcie pliku przez usunięcie plików na formancie. Te kontrolki również oznaczyć zdarzenia przeciągania i upuszczania, jako obsługiwane. Co w efekcie domyślnie nie można dodać własne programy obsługi zdarzeń do zapewnienia funkcji do otwierania plików porzuconych.  
  
 Aby dodać dodatkowe Obsługa przeciągania i upuszczania w tych kontrolek, należy użyć <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> metody w celu dodania usługi obsługi zdarzeń dla zdarzenia przeciągania i upuszczania. Ustaw `handledEventsToo` parametr `true` mieć określony program obsługi, można wywołać dla zdarzenia trasowanego, która już została oznaczona jako obsługiwane w innym elemencie wzdłuż trasy zdarzeń.  
  
> [!TIP]
>  Możesz zastąpić wbudowanych funkcji przeciągania i upuszczania <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, i <xref:System.Windows.Documents.FlowDocument> przez obsługi wersje zapoznawcze zdarzenia przeciągania i upuszczania oraz oznaczanie zdarzenia (wersja zapoznawcza), jako obsługiwane. Jednak to spowoduje wyłączenie funkcji przeciągania i upuszczania wbudowane i nie jest zalecane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak dodać procedury obsługi dla <xref:System.Windows.DragDrop.DragOver> i <xref:System.Windows.DragDrop.Drop> zdarzenia <xref:System.Windows.Controls.RichTextBox>. W tym przykładzie użyto <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> metody i zestawy `handledEventsToo` parametr `true` tak, aby programy obsługi zdarzeń zostanie wywołany, nawet jeśli <xref:System.Windows.Controls.RichTextBox> oznacza te zdarzenia, jako obsługiwane. Kod w procedurze obsługi zdarzeń dodaje funkcjonalność do otwierania pliku tekstowego, który został upuszczony na <xref:System.Windows.Controls.RichTextBox>.  
  
 Aby przetestować w tym przykładzie, przeciągnij plik tekstowy lub plik RTF sformatowany (RTF) z Eksploratora Windows, aby <xref:System.Windows.Controls.RichTextBox>. Plik zostanie otwarty w <xref:System.Windows.Controls.RichTextBox>. Jeśli naciśniesz klawisz SHIFT przed zaniechaniem pliku, plik zostanie otwarty w postaci zwykłego tekstu.  
  
 [!code-xaml[DragDropSnippets#RtbXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
