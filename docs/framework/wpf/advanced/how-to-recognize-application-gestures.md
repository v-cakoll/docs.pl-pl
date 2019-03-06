---
title: 'Instrukcje: Rozpoznaj gesty aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application gestures [WPF], recognizing
- gestures [WPF], recognizing
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
ms.openlocfilehash: 99deaa528a089f2d16268747f2e946873f3420a0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370517"
---
# <a name="how-to-recognize-application-gestures"></a><span data-ttu-id="22671-102">Instrukcje: Rozpoznaj gesty aplikacji</span><span class="sxs-lookup"><span data-stu-id="22671-102">How To: Recognize Application Gestures</span></span>
<span data-ttu-id="22671-103">Poniższy przykład pokazuje, jak usunąć atrament, gdy użytkownik wykonuje <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gestów na <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="22671-103">The following example demonstrates how to erase ink when a user makes a <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gesture on an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="22671-104">W tym przykładzie założono <xref:System.Windows.Controls.InkCanvas>, co jest nazywane `inkCanvas1`, jest zadeklarowana w pliku XAML.</span><span class="sxs-lookup"><span data-stu-id="22671-104">This example assumes an <xref:System.Windows.Controls.InkCanvas>, called `inkCanvas1`, is declared in the XAML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22671-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="22671-105">Example</span></span>  
 [!code-csharp[HowToRecognizeGestures#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="22671-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22671-106">See also</span></span>
- <xref:System.Windows.Ink.ApplicationGesture>
- <xref:System.Windows.Controls.InkCanvas>
- <xref:System.Windows.Controls.InkCanvas.Gesture>
