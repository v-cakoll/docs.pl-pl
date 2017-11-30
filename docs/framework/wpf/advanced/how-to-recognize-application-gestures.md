---
title: "Jak rozpoznać gesty aplikacji"
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
- application gestures [WPF], recognizing
- gestures [WPF], recognizing
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24d9e4435362f5f87185d04f911caf76517a0de9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-recognize-application-gestures"></a><span data-ttu-id="2b246-102">Jak rozpoznać gesty aplikacji</span><span class="sxs-lookup"><span data-stu-id="2b246-102">How To: Recognize Application Gestures</span></span>
<span data-ttu-id="2b246-103">W poniższym przykładzie pokazano sposób wymazywania, kiedy użytkownik tworzy <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gestów na <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="2b246-103">The following example demonstrates how to erase ink when a user makes a <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gesture on an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="2b246-104">W tym przykładzie założono <xref:System.Windows.Controls.InkCanvas>o nazwie `inkCanvas1`, jest zadeklarowany w pliku XAML.</span><span class="sxs-lookup"><span data-stu-id="2b246-104">This example assumes an <xref:System.Windows.Controls.InkCanvas>, called `inkCanvas1`, is declared in the XAML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b246-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b246-105">Example</span></span>  
 [!code-csharp[HowToRecognizeGestures#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2b246-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b246-106">See Also</span></span>  
 <xref:System.Windows.Ink.ApplicationGesture>  
 <xref:System.Windows.Controls.InkCanvas>  
 <xref:System.Windows.Controls.InkCanvas.Gesture>
