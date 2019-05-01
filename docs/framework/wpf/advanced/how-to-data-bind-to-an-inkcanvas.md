---
title: 'Instrukcje: Powiązywanie danych z elementem InkCanvas'
ms.date: 03/30/2017
helpviewer_keywords:
- InkCanvas [WPF], binding data to
- binding data [WPF], to InkCanvas
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
ms.openlocfilehash: 5d3fc0ed7b6176d7bc68bf20af42c311b5563908
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776470"
---
# <a name="how-to-data-bind-to-an-inkcanvas"></a>Instrukcje: Powiązywanie danych z elementem InkCanvas
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje jak powiązać <xref:System.Windows.Controls.InkCanvas.Strokes%2A> właściwość <xref:System.Windows.Controls.InkCanvas> do innego <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-xaml[InkCanvasBindingSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 Poniższy przykład pokazuje jak powiązać <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> właściwość ze źródłem danych.  
  
 [!code-xaml[InkCanvasBindingSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 Poniższy przykład deklaruje dwie <xref:System.Windows.Controls.InkCanvas> obiekty w XAML i ustanawia powiązanie danych między nimi i innymi źródłami danych.  Pierwszy <xref:System.Windows.Controls.InkCanvas>, co jest nazywane `ic`, jest powiązany z dwoma źródłami danych.  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> i <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> właściwości `ic` są powiązane z <xref:System.Windows.Controls.ListBox> obiektów, które z kolei są powiązane z tablic zdefiniowane w XAML.  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, I <xref:System.Windows.Controls.InkCanvas.Strokes%2A> właściwości drugiego <xref:System.Windows.Controls.InkCanvas> są zobowiązane do pierwszego <xref:System.Windows.Controls.InkCanvas>, `ic`.  
  
 [!code-xaml[InkCanvasBindingSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
