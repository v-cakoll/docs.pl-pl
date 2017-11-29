---
title: "Funkcjonalność przeciągania i upuszczania w formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drag and drop [Windows Forms], Windows Forms
- Windows Forms, drag and drop
ms.assetid: 65cd2c03-8782-474e-b958-cbe43eeb902c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f86ff2fbb3944ce2ed381cb29e2b3c6df39b62bf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="drag-and-drop-functionality-in-windows-forms"></a>Funkcjonalność przeciągania i upuszczania w formularzach systemu Windows
Formularze systemu Windows zawiera zestaw metod, zdarzeń i klasy, które implementują zachowanie przeciągania i upuszczania. Ten temat zawiera omówienie obsługi przeciągania i upuszczania w formularzach systemu Windows.  Zobacz też [operacji przeciągania i upuszczania oraz Obsługa schowka](http://msdn.microsoft.com/library/fe5ebfwe\(v=vs.110\)).  
  
## <a name="performing-drag-and-drop-operations"></a>Wykonywanie operacji przeciągania i upuszczania  
 Aby wykonać operację przeciągania i upuszczania, należy użyć <xref:System.Windows.Forms.Control.DoDragDrop%2A> metody <xref:System.Windows.Forms.Control> klasy. Aby uzyskać więcej informacji o sposobie wykonywana jest operacja przeciągania i upuszczania, zobacz <xref:System.Windows.Forms.Control.DoDragDrop%2A>. Aby uzyskać prostokąt wskaźnik myszy musi zostać przeciągnięty nad, zanim rozpocznie się wykonywanie operacji przeciągania i upuszczania, należy użyć <xref:System.Windows.Forms.SystemInformation.DragSize%2A> właściwość <xref:System.Windows.Forms.SystemInformation> klasy.  
  
## <a name="events-related-to-drag-and-drop-operations"></a>Zdarzenia związane z operacjami przeciągania i upuszczania  
 Istnieją dwie kategorie zdarzeń w operacji przeciągania i upuszczania: bieżący element docelowy operacji przeciągania i upuszczania zdarzeń i zdarzenia występujące w źródle operacji przeciągania i upuszczania.  
  
### <a name="events-on-the-current-target"></a>Zdarzenia na bieżącą lokalizację docelową.  
 W poniższej tabeli przedstawiono zdarzeń występujących na bieżący element docelowy operacji przeciągania i upuszczania.  
  
|Zdarzenia myszy|Opis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.DragEnter>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty do granice formantu. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragOver>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty, gdy wskaźnik myszy znajduje się w granicach formantu. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragDrop>|To zdarzenie występuje po zakończeniu operacji przeciągania i upuszczania. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragLeave>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty poza granice formantu. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.EventArgs>.|  
  
 <xref:System.Windows.Forms.DragEventArgs> Klasy zawiera lokalizację wskaźnika myszy, bieżący stan przycisku myszy i klawisze modyfikujące klawiatury, dane przeciągane, i <xref:System.Windows.Forms.DragDropEffects> wartości, które określają operacje dozwolone przez źródło zdarzenia przeciągania i efekt listy docelowej dla tej operacji.  
  
### <a name="events-on-the-source"></a>Zdarzenia w źródle  
 W poniższej tabeli przedstawiono zdarzenia, które występują w źródle operacji przeciągania i upuszczania.  
  
|Zdarzenia myszy|Opis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.GiveFeedback>|To zdarzenie występuje podczas operacji przeciągania. Zapewnia możliwość zapewniają wizualnie do użytkownika, który występuje operacji przeciągania i upuszczania, takie jak zmiana wskaźnik myszy. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.GiveFeedbackEventArgs>.|  
|<xref:System.Windows.Forms.Control.QueryContinueDrag>|To zdarzenie jest wywoływane podczas operacji przeciągania i upuszczania i umożliwia źródła przeciągania określić, czy można anulować operację przeciągania i upuszczania. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.QueryContinueDragEventArgs>.|  
  
 <xref:System.Windows.Forms.QueryContinueDragEventArgs> Klasy podaje bieżący stan myszy przycisków i klawisze modyfikujące klawiatury, wartość określającą, czy został naciśnięty klawisz ESC, a <xref:System.Windows.Forms.DragAction> wartości, który można ustawić, aby określić, czy należy kontynuować operację przeciągania i upuszczania.  
  
## <a name="see-also"></a>Zobacz też  
 [Wejście myszy w systemie Windows formularzy aplikacji](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
