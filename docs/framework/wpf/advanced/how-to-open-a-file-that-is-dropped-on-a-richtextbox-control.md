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
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a><span data-ttu-id="f7234-102">Jak otworzyć plik, który został upuszczony na formant RichTextBox</span><span class="sxs-lookup"><span data-stu-id="f7234-102">How to: Open a File That is Dropped on a RichTextBox Control</span></span>
<span data-ttu-id="f7234-103">W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, i <xref:System.Windows.Documents.FlowDocument> wszystkie formanty ma wbudowaną funkcję przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="f7234-103">In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], the <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Documents.FlowDocument> controls all have built-in drag-and-drop functionality.</span></span> <span data-ttu-id="f7234-104">Wbudowanej funkcji umożliwia przeciągania i upuszczania tekstu w ramach i między formantami.</span><span class="sxs-lookup"><span data-stu-id="f7234-104">The built-in functionality enables drag-and-drop of text within and between the controls.</span></span> <span data-ttu-id="f7234-105">Jednak nie umożliwia otwarcie pliku przez usunięcie pliku w formancie.</span><span class="sxs-lookup"><span data-stu-id="f7234-105">However, it does not enable opening a file by dropping the file on the control.</span></span> <span data-ttu-id="f7234-106">Formanty również oznaczanie przeciągania i upuszczania, jako obsługi.</span><span class="sxs-lookup"><span data-stu-id="f7234-106">These controls also mark the drag-and-drop events as handled.</span></span> <span data-ttu-id="f7234-107">W związku z tym domyślnie nie można dodać własne programy obsługi zdarzeń umożliwiają korzystanie z funkcji można otworzyć porzucone pliki.</span><span class="sxs-lookup"><span data-stu-id="f7234-107">As a result, by default, you cannot add your own event handlers to provide functionality to open dropped files.</span></span>  
  
 <span data-ttu-id="f7234-108">Aby dodać dodatkowe obsługę przeciągania i upuszczania w tych kontrolek, użyj <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> metody w celu dodania programu obsługi zdarzeń dla zdarzenia przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="f7234-108">To add additional handling for drag-and-drop events in these controls, use the <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> method to add your event handlers for the drag-and-drop events.</span></span> <span data-ttu-id="f7234-109">Ustaw `handledEventsToo` parametr `true` ma określony program obsługi, można wywołać dla kierowanego zdarzenia, który już został oznaczony jako obsługiwany przez inny element wzdłuż trasy zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f7234-109">Set the `handledEventsToo` parameter to `true` to have the specified handler be invoked for a routed event that has already been marked as handled by another element along the event route.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="f7234-110">Można zastąpić wbudowanych funkcjonalność przeciągania i upuszczania <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, i <xref:System.Windows.Documents.FlowDocument> Obsługa wersji Podglądu zdarzeń przeciągania i upuszczania i oznaczenie Podgląd zdarzeń, ponieważ obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f7234-110">You can replace the built-in drag-and-drop functionality of <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Documents.FlowDocument> by handling the preview versions of the drag-and-drop events and marking the preview events as handled.</span></span> <span data-ttu-id="f7234-111">Jednak to spowoduje wyłączenie wbudowanej funkcji przeciągania i upuszczania, a nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="f7234-111">However, this will disable the built-in drag-and-drop functionality, and is not recommended.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7234-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7234-112">Example</span></span>  
 <span data-ttu-id="f7234-113">W poniższym przykładzie pokazano, jak dodać obsługę <xref:System.Windows.DragDrop.DragOver> i <xref:System.Windows.DragDrop.Drop> zdarzeń na <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="f7234-113">The following example demonstrates how to add handlers for the <xref:System.Windows.DragDrop.DragOver> and <xref:System.Windows.DragDrop.Drop> events on a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="f7234-114">W tym przykładzie użyto <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> — metoda i zestawy `handledEventsToo` parametr `true` tak, aby programy obsługi zdarzeń zostanie wywołany, nawet jeśli <xref:System.Windows.Controls.RichTextBox> oznacza te zdarzenia, jako obsłużone.</span><span class="sxs-lookup"><span data-stu-id="f7234-114">This example uses the <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> method and sets the `handledEventsToo` parameter to `true` so that the events handlers will be invoked even though the <xref:System.Windows.Controls.RichTextBox> marks these events as handled.</span></span> <span data-ttu-id="f7234-115">Kod obsługi zdarzeń dodaje funkcje do otwierania plików tekstowych, które są przenoszone na <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="f7234-115">The code in the event handlers adds functionality to open a text file that is dropped on the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="f7234-116">Aby przetestować w tym przykładzie, przeciągnij plik tekstowy lub pliku RTF sformatowany (RTF) z Eksploratora Windows, aby <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="f7234-116">To test this example, drag a text file or a rich text format (RTF) file from Windows Explorer to the <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="f7234-117">Plik zostanie otwarty w <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="f7234-117">The file will be opened in the <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="f7234-118">Jeśli naciśniesz klawisz SHIFT przed zaniechaniem pliku, plik zostanie otwarty jako zwykły tekst.</span><span class="sxs-lookup"><span data-stu-id="f7234-118">If you press the SHIFT key before the dropping the file, the file will be opened as plain text.</span></span>  
  
 [!code-xaml[DragDropSnippets#RtbXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
