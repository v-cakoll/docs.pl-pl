---
title: Kolejność zdarzeń w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: a88fd7b912063af5961a2bb366b42b0f67411f5f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720297"
---
# <a name="order-of-events-in-windows-forms"></a>Kolejność zdarzeń w formularzach systemu Windows
Kolejność, w której zdarzenia są wywoływane w aplikacjach Windows Forms ma szczególne znaczenie dla deweloperów zaniepokojona obsługi, każde z tych wydarzeń z kolei. Rozwiązania wymaga dokładnych obsługi zdarzeń, takich jak kiedy są odświeżanie części formularza, niezbędne jest rozpoznawanie dokładne kolejność, w której zdarzenia są wywoływane w czasie wykonywania. Ten temat zawiera kilka szczegółów rzędu kilku zdarzeń kilku etapach ważne w okresie istnienia aplikacji i formantów. Aby uzyskać szczegółowe informacje na temat kolejności zdarzeń wejściowych myszy zobacz [zdarzeń myszy w formularzach Windows Forms](mouse-events-in-windows-forms.md). Aby uzyskać przegląd zdarzeń w formularzach Windows Forms, zobacz [Przegląd zdarzeń](events-overview-windows-forms.md). Aby uzyskać szczegółowe informacje o korzeń procedury obsługi zdarzeń, zobacz [Przegląd obsługi zdarzeń](event-handlers-overview-windows-forms.md).  
  
## <a name="application-startup-and-shutdown-events"></a>Uruchamianie aplikacji i zamykania  
 <xref:System.Windows.Forms.Form> i <xref:System.Windows.Forms.Control> klasy udostępnić zestaw zdarzeń związanych z aplikacji, uruchamiania i zamykania. Po uruchomieniu aplikacji Windows Forms zdarzenia uruchamiania formularza głównego są wywoływane w następującej kolejności:  
  
-   <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 Po zakończeniu działania aplikacji, zdarzeń zamknięcia formularza głównego są wywoływane w następującej kolejności:  
  
-   <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <xref:System.Windows.Forms.Application.ApplicationExit> Zdarzenia <xref:System.Windows.Forms.Application> klasy jest wywoływane po wykonaniu zdarzeń zamknięcia formularza głównego.  
  
> [!NOTE]
>  Visual Basic 2005 zawiera zdarzenia dodatkowych aplikacji, takich jak <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> i <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.  
  
## <a name="focus-and-validation-events"></a>Fokus i zdarzenia walidacji  
 Po zmianie fokusu przy użyciu klawiatury (karty, SHIFT + TAB i tak dalej), przez wywołanie metody <xref:System.Windows.Forms.Control.Select%2A> lub <xref:System.Windows.Forms.Control.SelectNextControl%2A> metod, lub poprzez skonfigurowanie <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> właściwości bieżącego formularza zdarzenia fokusu <xref:System.Windows.Forms.Control> klasy zachodzą w następującej kolejności :  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
 Po zmianie fokusu przy użyciu myszy lub przez wywołanie <xref:System.Windows.Forms.Control.Focus%2A> metody, zdarzenia fokusu <xref:System.Windows.Forms.Control> klasy zachodzą w następującej kolejności:  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>Zobacz także
- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](creating-event-handlers-in-windows-forms.md)
