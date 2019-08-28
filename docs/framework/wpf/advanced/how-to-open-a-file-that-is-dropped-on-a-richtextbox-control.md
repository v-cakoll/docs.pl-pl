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
ms.openlocfilehash: 408d48856362fa8a77a44e2cc97cb2d5ff608dcf
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046353"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>Instrukcje: Otwieranie pliku, który został upuszczony na kontrolkę RichTextBox

W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ,<xref:System.Windows.Controls.RichTextBox>,, i<xref:System.Windows.Documents.FlowDocument> kontrolki All mają wbudowaną funkcję przeciągania i upuszczania. <xref:System.Windows.Controls.TextBox> Wbudowana funkcja umożliwia przeciąganie i upuszczanie tekstu w obrębie formantów i między nimi. Nie umożliwia jednak otwierania pliku przez upuszczenie go na kontrolce. Te kontrolki oznaczają również zdarzenia przeciągania i upuszczania jako obsługiwane. W związku z tym domyślnie nie można dodać własnych programów obsługi zdarzeń w celu zapewnienia funkcjonalności otwierania plików usuniętych.

Aby dodać do tych formantów dodatkową obsługę zdarzeń przeciągania i upuszczania, użyj <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> metody, aby dodać obsługę zdarzeń dla zdarzeń przeciągania i upuszczania. `handledEventsToo` Ustaw`true` parametr na tak, aby był wywoływany przez określony program obsługi dla zdarzenia trasowanego, które zostało już oznaczone jako obsługiwane przez inny element wzdłuż trasy zdarzenia.

> [!TIP]
> Możesz zastąpić wbudowaną funkcję <xref:System.Windows.Controls.TextBox>przeciągania i upuszczania, <xref:System.Windows.Controls.RichTextBox>i <xref:System.Windows.Documents.FlowDocument> przez obsługę wersji zapoznawczej zdarzeń przeciągania i upuszczania oraz oznaczenie zdarzeń w wersji zapoznawczej jako obsłużone. Spowoduje to jednak wyłączenie wbudowanej funkcji przeciągania i upuszczania. nie jest to zalecane.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak dodać procedury obsługi dla <xref:System.Windows.DragDrop.DragOver> zdarzeń i <xref:System.Windows.DragDrop.Drop> w <xref:System.Windows.Controls.RichTextBox>. W tym przykładzie użyto <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> metody i `handledEventsToo` Ustawia parametr na `true` tak, aby programy obsługi zdarzeń zostały wywołane nawet wtedy, <xref:System.Windows.Controls.RichTextBox> gdy Znaczniki te są traktowane jako obsługiwane. Kod w obsłudze zdarzeń dodaje funkcję, aby otworzyć plik tekstowy, który został usunięty <xref:System.Windows.Controls.RichTextBox>z.

Aby przetestować ten przykład, przeciągnij plik tekstowy lub plik Rich Text Format (RTF) z Eksploratora Windows do <xref:System.Windows.Controls.RichTextBox>. Plik zostanie otwarty w <xref:System.Windows.Controls.RichTextBox>. Jeśli naciśniesz klawisz SHIFT przed upuszczeniem pliku, plik zostanie otwarty w postaci zwykłego tekstu.

[!code-xaml[DragDropSnippets#RtbXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]

[!code-csharp[DragDropSnippets#RtbHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
[!code-vb[DragDropSnippets#RtbHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
