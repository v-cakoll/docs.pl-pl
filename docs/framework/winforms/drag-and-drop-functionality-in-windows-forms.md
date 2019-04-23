---
title: Funkcjonalność przeciągania i upuszczania w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], Windows Forms
- Windows Forms, drag and drop
ms.assetid: 65cd2c03-8782-474e-b958-cbe43eeb902c
ms.openlocfilehash: 437b632706b27cd487d60c2ad23db3f9a3c96c09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108020"
---
# <a name="drag-and-drop-functionality-in-windows-forms"></a>Funkcjonalność przeciągania i upuszczania w formularzach systemu Windows
Windows Forms zawiera zestaw metod, zdarzeń i klasy, które implementują zachowanie przeciągnij i upuść. Ten temat zawiera omówienie obsługi przeciągania i upuszczania w formularzach Windows Forms.  Zobacz też [operacji przeciągania i upuszczania oraz Obsługa schowka](./advanced/drag-and-drop-operations-and-clipboard-support.md).  
  
## <a name="performing-drag-and-drop-operations"></a>Wykonywanie operacji przeciągania i upuszczania  
 Aby wykonać operację przeciągania i upuszczania, należy użyć <xref:System.Windows.Forms.Control.DoDragDrop%2A> metody <xref:System.Windows.Forms.Control> klasy. Aby uzyskać więcej informacji na temat sposobu wykonywana jest operacja przeciągania i upuszczania, zobacz <xref:System.Windows.Forms.Control.DoDragDrop%2A>. Aby uzyskać prostokąt, w którym muszą zostać przeciągnięte wskaźnik myszy nad, przed rozpoczęciem operacji przeciągania i upuszczania, użyj <xref:System.Windows.Forms.SystemInformation.DragSize%2A> właściwość <xref:System.Windows.Forms.SystemInformation> klasy.  
  
## <a name="events-related-to-drag-and-drop-operations"></a>Zdarzenia związane z operacjami przeciągania i upuszczania  
 Istnieją dwie kategorie zdarzeń podczas operacji przeciągania i upuszczania: wydarzenia, występujących na bieżący obiekt docelowy operacji przeciągania i upuszczania oraz zdarzeń występujących w źródle operacji przeciągania i upuszczania.  
  
### <a name="events-on-the-current-target"></a>Zdarzenia w bieżącym elemencie docelowym  
 W poniższej tabeli przedstawiono zdarzenia, które wystąpiły na bieżący obiekt docelowy operacji przeciągania i upuszczania.  
  
|Zdarzenia myszy|Opis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.DragEnter>|To zdarzenie występuje po przeciągnięciu obiektu w granice formantu. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragOver>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty, gdy wskaźnik myszy znajduje się w granicach formantu. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragDrop>|To zdarzenie występuje po zakończeniu operacji przeciągania i upuszczania. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragLeave>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty poza granice formantu. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.EventArgs>.|  
  
 <xref:System.Windows.Forms.DragEventArgs> Klasy zawiera lokalizację wskaźnika myszy, bieżący stan przycisków myszy i klawisze modyfikujące klawiatury danych przeciąganie, i <xref:System.Windows.Forms.DragDropEffects> wartości, które określają dozwolone przez źródło zdarzenia przeciągania operacje i efekt listy docelowej dla tej operacji.  
  
### <a name="events-on-the-source"></a>Zdarzenia w źródle  
 W poniższej tabeli przedstawiono zdarzeń występujących w źródle operacji przeciągania i upuszczania.  
  
|Zdarzenia myszy|Opis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.GiveFeedback>|To zdarzenie występuje podczas operacji przeciągania. Zapewnia możliwość oferowanie wizualną użytkownika, który występuje operacji przeciągania i upuszczania, takiej jak zmiana wartości wskaźnika myszy. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.GiveFeedbackEventArgs>.|  
|<xref:System.Windows.Forms.Control.QueryContinueDrag>|To zdarzenie jest wywoływane podczas operacji przeciągania i upuszczania oraz umożliwia źródłom przeciągania określenie, czy operacja przeciągania i upuszczania powinna zostać anulowana. Program obsługi dla tego zdarzenia odbiera argumentu typu <xref:System.Windows.Forms.QueryContinueDragEventArgs>.|  
  
 <xref:System.Windows.Forms.QueryContinueDragEventArgs> Klasy zawiera bieżący stan myszą przycisków i klawisze modyfikujące klawiatury wartość określającą, czy został naciśnięty klawisz ESC, a <xref:System.Windows.Forms.DragAction> wartości, które można ustawić, aby określić, czy należy kontynuować operacji przeciągania i upuszczania.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](mouse-input-in-a-windows-forms-application.md)
