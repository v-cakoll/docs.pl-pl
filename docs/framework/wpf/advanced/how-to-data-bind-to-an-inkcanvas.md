---
title: "Jak powiązać dane z InkCanvas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- InkCanvas [WPF], binding data to
- binding data [WPF], to InkCanvas
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fdcd67f972dafa2de7fb74e01b4a3c22dfd848fb
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-data-bind-to-an-inkcanvas"></a><span data-ttu-id="8ebf9-102">Jak powiązać dane z InkCanvas</span><span class="sxs-lookup"><span data-stu-id="8ebf9-102">How to: Data Bind to an InkCanvas</span></span>
## <a name="example"></a><span data-ttu-id="8ebf9-103">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ebf9-103">Example</span></span>  
 <span data-ttu-id="8ebf9-104">W poniższym przykładzie pokazano, jak można powiązać <xref:System.Windows.Controls.InkCanvas.Strokes%2A> właściwość <xref:System.Windows.Controls.InkCanvas> do innego <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="8ebf9-104">The following example demonstrates how to bind the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property of an <xref:System.Windows.Controls.InkCanvas> to another <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 <span data-ttu-id="8ebf9-105">W poniższym przykładzie pokazano, jak można powiązać <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> właściwości ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="8ebf9-105">The following example demonstrates how to bind the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property to a data source.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 <span data-ttu-id="8ebf9-106">Poniższy przykład deklaruje dwa <xref:System.Windows.Controls.InkCanvas> obiektów w kodzie XAML i ustanawia powiązania danych między nimi i innych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="8ebf9-106">The following example declares two <xref:System.Windows.Controls.InkCanvas> objects in XAML and establishes data binding between them and other data sources.</span></span>  <span data-ttu-id="8ebf9-107">Pierwszy <xref:System.Windows.Controls.InkCanvas>o nazwie `ic`, jest powiązany z dwóch źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="8ebf9-107">The first <xref:System.Windows.Controls.InkCanvas>, called `ic`, is bound to two data sources.</span></span>  <span data-ttu-id="8ebf9-108"><xref:System.Windows.Controls.InkCanvas.EditingMode%2A> i <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> właściwości `ic` są powiązane z <xref:System.Windows.Controls.ListBox> obiektów, które z kolei są powiązane z tablicami zdefiniowane w pliku XAML.</span><span class="sxs-lookup"><span data-stu-id="8ebf9-108">The <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> and <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties on `ic` are bound to <xref:System.Windows.Controls.ListBox> objects, which are in turn bound to arrays defined in the XAML.</span></span>  <span data-ttu-id="8ebf9-109"><xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, I <xref:System.Windows.Controls.InkCanvas.Strokes%2A> właściwości drugiego <xref:System.Windows.Controls.InkCanvas> powiązanych do pierwszej <xref:System.Windows.Controls.InkCanvas>, `ic`.</span><span class="sxs-lookup"><span data-stu-id="8ebf9-109">The <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, and <xref:System.Windows.Controls.InkCanvas.Strokes%2A> properties of the second <xref:System.Windows.Controls.InkCanvas> are bound to the first <xref:System.Windows.Controls.InkCanvas>, `ic`.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
