---
title: Funkcja przeciągania i upuszczania
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], Windows Forms
- Windows Forms, drag and drop
ms.assetid: 65cd2c03-8782-474e-b958-cbe43eeb902c
ms.openlocfilehash: 603dc158719c0b11def4386eb24a33f235cf3a42
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732758"
---
# <a name="drag-and-drop-functionality-in-windows-forms"></a>Funkcjonalność przeciągania i upuszczania w formularzach systemu Windows
Windows Forms obejmuje zestaw metod, zdarzeń i klas, które implementują zachowanie metodą przeciągania i upuszczania. Ten temat zawiera omówienie obsługi przeciągania i upuszczania w Windows Forms.  Zobacz również [operacje przeciągania i upuszczania oraz obsługa schowka](./advanced/drag-and-drop-operations-and-clipboard-support.md).  
  
## <a name="performing-drag-and-drop-operations"></a>Wykonywanie operacji przeciągania i upuszczania  
 Aby wykonać operację przeciągania i upuszczania, użyj metody <xref:System.Windows.Forms.Control.DoDragDrop%2A> klasy <xref:System.Windows.Forms.Control>. Aby uzyskać więcej informacji na temat sposobu wykonywania operacji przeciągania i upuszczania, zobacz <xref:System.Windows.Forms.Control.DoDragDrop%2A>. Aby uzyskać prostokąt, który wskaźnik myszy musi być przeciągany przed rozpoczęciem operacji przeciągania i upuszczania, użyj właściwości <xref:System.Windows.Forms.SystemInformation.DragSize%2A> klasy <xref:System.Windows.Forms.SystemInformation>.  
  
## <a name="events-related-to-drag-and-drop-operations"></a>Zdarzenia związane z operacjami przeciągania i upuszczania  
 W operacji przeciągania i upuszczania istnieją dwie kategorie zdarzeń: zdarzenia występujące w bieżącym elemencie docelowym operacji przeciągania i upuszczania oraz zdarzenia występujące w źródle operacji przeciągania i upuszczania.  
  
### <a name="events-on-the-current-target"></a>Zdarzenia w bieżącym miejscu docelowym  
 W poniższej tabeli przedstawiono zdarzenia występujące w bieżącym miejscu docelowym operacji przeciągania i upuszczania.  
  
|Zdarzenie myszy|Opis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.DragEnter>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty do zakresu formantu. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragOver>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty, gdy wskaźnik myszy znajduje się w granicach formantu. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragDrop>|To zdarzenie występuje, gdy zostanie ukończona operacja przeciągania i upuszczania. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragLeave>|To zdarzenie występuje, gdy obiekt zostanie przeciągnięty poza granice formantu. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.EventArgs>.|  
  
 Klasa <xref:System.Windows.Forms.DragEventArgs> zawiera lokalizację wskaźnika myszy, bieżący stan przycisków myszy i klawiszy modyfikujących klawiaturę, przeciągane dane oraz <xref:System.Windows.Forms.DragDropEffects> wartości, które określają operacje dozwolone przez Źródło zdarzenia przeciągania i docelowy efekt upuszczania dla operacji.  
  
### <a name="events-on-the-source"></a>Zdarzenia w źródle  
 W poniższej tabeli przedstawiono zdarzenia występujące w źródle operacji przeciągania i upuszczania.  
  
|Zdarzenie myszy|Opis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.GiveFeedback>|To zdarzenie występuje podczas operacji przeciągania. Zapewnia możliwość udostępnienia wizualnej wizualizacji użytkownikowi, że występuje operacja przeciągania i upuszczania, taka jak zmiana wskaźnika myszy. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.Windows.Forms.GiveFeedbackEventArgs>.|  
|<xref:System.Windows.Forms.Control.QueryContinueDrag>|To zdarzenie jest wywoływane podczas operacji przeciągania i upuszczania oraz umożliwia źródło przeciągania, aby określić, czy operacja przeciągania i upuszczania powinna zostać anulowana. Procedura obsługi dla tego zdarzenia otrzymuje argument typu <xref:System.Windows.Forms.QueryContinueDragEventArgs>.|  
  
 Klasa <xref:System.Windows.Forms.QueryContinueDragEventArgs> zapewnia bieżący stan przycisków myszy i klawiszy modyfikujących klawiaturę, wartość określającą, czy naciśnięto klawisz ESC, oraz wartość <xref:System.Windows.Forms.DragAction>, którą można ustawić, aby określić, czy operacja przeciągania i upuszczania powinna być kontynuowana.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](mouse-input-in-a-windows-forms-application.md)
