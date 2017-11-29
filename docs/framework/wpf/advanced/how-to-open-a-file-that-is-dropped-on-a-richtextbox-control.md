---
title: "Jak otworzyć plik, który został upuszczony na formant RichTextBox"
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
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f65ecaf9c6ef34176967e1ebf9134ceee195036b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>Jak otworzyć plik, który został upuszczony na formant RichTextBox
W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, i <xref:System.Windows.Documents.FlowDocument> wszystkie formanty ma wbudowaną funkcję przeciągania i upuszczania. Wbudowanej funkcji umożliwia przeciągania i upuszczania tekstu w ramach i między formantami. Jednak nie umożliwia otwarcie pliku przez usunięcie pliku w formancie. Formanty również oznaczanie przeciągania i upuszczania, jako obsługi. W związku z tym domyślnie nie można dodać własne programy obsługi zdarzeń umożliwiają korzystanie z funkcji można otworzyć porzucone pliki.  
  
 Aby dodać dodatkowe obsługę przeciągania i upuszczania w tych kontrolek, użyj <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> metody w celu dodania programu obsługi zdarzeń dla zdarzenia przeciągania i upuszczania. Ustaw `handledEventsToo` parametr `true` ma określony program obsługi, można wywołać dla kierowanego zdarzenia, który już został oznaczony jako obsługiwany przez inny element wzdłuż trasy zdarzenia.  
  
> [!TIP]
>  Można zastąpić wbudowanych funkcjonalność przeciągania i upuszczania <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, i <xref:System.Windows.Documents.FlowDocument> Obsługa wersji Podglądu zdarzeń przeciągania i upuszczania i oznaczenie Podgląd zdarzeń, ponieważ obsługiwane. Jednak to spowoduje wyłączenie wbudowanej funkcji przeciągania i upuszczania, a nie jest zalecane.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak dodać obsługę <xref:System.Windows.DragDrop.DragOver> i <xref:System.Windows.DragDrop.Drop> zdarzeń na <xref:System.Windows.Controls.RichTextBox>. W tym przykładzie użyto <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> — metoda i zestawy `handledEventsToo` parametr `true` tak, aby programy obsługi zdarzeń zostanie wywołany, nawet jeśli <xref:System.Windows.Controls.RichTextBox> oznacza te zdarzenia, jako obsłużone. Kod obsługi zdarzeń dodaje funkcje do otwierania plików tekstowych, które są przenoszone na <xref:System.Windows.Controls.RichTextBox>.  
  
 Aby przetestować w tym przykładzie, przeciągnij plik tekstowy lub pliku RTF sformatowany (RTF) z Eksploratora Windows, aby <xref:System.Windows.Controls.RichTextBox>. Plik zostanie otwarty w <xref:System.Windows.Controls.RichTextBox>. Jeśli naciśniesz klawisz SHIFT przed zaniechaniem pliku, plik zostanie otwarty jako zwykły tekst.  
  
 [!code-xaml[DragDropSnippets#RtbXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
