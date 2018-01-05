---
title: "TrackBar — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e62fc49a8a08c79138df080246b99b6fe891162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.TrackBar> formantu (nazywanych także "suwaka") jest używany na potrzeby nawigowaniu po dużej ilości informacji lub wizualnie dostosowywania liczbowych ustawienie. <xref:System.Windows.Forms.TrackBar> Formantu ma dwie części: thumb, znanej także jako suwaka i znaczniki osi. Stronie przycisku suwaka wchodzi w skład, którą można dostosować. Odpowiada jego położenie <xref:System.Windows.Forms.TrackBar.Value%2A> właściwości. Znaczniki są wskaźniki wizualne, które są rozmieszczone w regularnych odstępach czasu. Trackbar jest przesuwany w przyrostach, które określają i można wyrównać poziomo czy pionowo. Na przykład można użyć do kontrolowania szybkość lub mysz migania kursora dla systemu pasek śledzenia.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwości klucza obiektu <xref:System.Windows.Forms.TrackBar> sterowania stanowią <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, i <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>jest odstępy to znaczniki osi. <xref:System.Windows.Forms.TrackBar.Minimum%2A>i <xref:System.Windows.Forms.TrackBar.Maximum%2A> to najmniejsza i największa wartości, które mogą być przedstawiane na pasek śledzenia.  
  
 Są dwa inne ważne właściwości <xref:System.Windows.Forms.TrackBar.SmallChange%2A> i <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. Wartość <xref:System.Windows.Forms.TrackBar.SmallChange%2A> właściwość jest liczba pozycji przycisku przewijania przenosi w odpowiedzi na potrzeby naciśnięto klawisz Strzałka w lewo lub w. Wartość <xref:System.Windows.Forms.TrackBar.LargeChange%2A> właściwość jest liczba pozycji stronie przycisku suwaka przejdzie w odpowiedzi na potrzeby naciśnięto klawisz PAGE UP lub PAGE DOWN, lub w odpowiedzi na myszy kliknie pasek śledzenia na każdej stronie przycisku suwaka.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TrackBar>  
 [TrackBar, kontrolka](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
