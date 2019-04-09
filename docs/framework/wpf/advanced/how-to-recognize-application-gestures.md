---
title: 'Instrukcje: Rozpoznawanie gestów w aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application gestures [WPF], recognizing
- gestures [WPF], recognizing
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
ms.openlocfilehash: 647e7c9c1d785cebfdc362dc48511d865f3945dc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191513"
---
# <a name="how-to-recognize-application-gestures"></a>Instrukcje: Rozpoznawanie gestów w aplikacji
Poniższy przykład pokazuje, jak usunąć atrament, gdy użytkownik wykonuje <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gestów na <xref:System.Windows.Controls.InkCanvas>. W tym przykładzie założono <xref:System.Windows.Controls.InkCanvas>, co jest nazywane `inkCanvas1`, jest zadeklarowana w pliku XAML.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[HowToRecognizeGestures#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Ink.ApplicationGesture>
- <xref:System.Windows.Controls.InkCanvas>
- <xref:System.Windows.Controls.InkCanvas.Gesture>
