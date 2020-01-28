---
title: Kolejność zdarzeń
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: 618ac5a6a6a32ae1a53fc60ac80700d7648c81a7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734860"
---
# <a name="order-of-events-in-windows-forms"></a>Kolejność zdarzeń w formularzach systemu Windows
Kolejność, w której zdarzenia są zgłaszane w Windows Forms aplikacji, jest szczególnie interesująca dla deweloperów, którzy z kolei obsługują każde z tych zdarzeń. Gdy sytuacja wywołuje dokładnych obsługi zdarzeń, na przykład podczas ponownego rysowania części formularza, należy zapoznać się z dokładną kolejnością, w której zdarzenia są zgłaszane w czasie wykonywania. Ten temat zawiera pewne szczegóły dotyczące kolejności zdarzeń w kilku ważnych etapach w okresie istnienia aplikacji i kontroli. Aby uzyskać szczegółowe informacje na temat kolejności zdarzeń wejściowych myszy, zobacz [zdarzenia myszy w Windows Forms](mouse-events-in-windows-forms.md). Aby zapoznać się z omówieniem zdarzeń w Windows Forms, zobacz [Omówienie zdarzeń](events-overview-windows-forms.md). Aby uzyskać szczegółowe informacje na temat korzeń programów obsługi zdarzeń, zobacz [Omówienie obsługi zdarzeń](event-handlers-overview-windows-forms.md).  
  
## <a name="application-startup-and-shutdown-events"></a>Zdarzenia uruchamiania i zamykania aplikacji  
 Klasy <xref:System.Windows.Forms.Form> i <xref:System.Windows.Forms.Control> uwidaczniają zestaw zdarzeń związanych z uruchamianiem i wyłączaniem aplikacji. Po uruchomieniu aplikacji Windows Forms zdarzenia uruchamiania głównego formularza są zgłaszane w następującej kolejności:  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 Po zamknięciu aplikacji zdarzenia zamknięcia głównego formularza są zgłaszane w następującej kolejności:  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 Zdarzenie <xref:System.Windows.Forms.Application.ApplicationExit> klasy <xref:System.Windows.Forms.Application> jest wywoływane po zdarzeniach zamknięcia głównego formularza.  
  
> [!NOTE]
> Visual Basic 2005 zawiera dodatkowe zdarzenia aplikacji, takie jak <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> i <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.  
  
## <a name="focus-and-validation-events"></a>Zdarzenia fokusu i walidacji  
 Gdy zmienisz fokus przy użyciu klawiatury (TAB, SHIFT + TAB itd.), wywołując metody <xref:System.Windows.Forms.Control.Select%2A> lub <xref:System.Windows.Forms.Control.SelectNextControl%2A> lub ustawiając właściwość <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> na bieżącą formę, zdarzenia fokusu klasy <xref:System.Windows.Forms.Control> są wykonywane w następującej kolejności:  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 Gdy zmienisz fokus przy użyciu myszy lub wywołując metodę <xref:System.Windows.Forms.Control.Focus%2A>, zdarzenia fokusu klasy <xref:System.Windows.Forms.Control> są wykonywane w następującej kolejności:  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](creating-event-handlers-in-windows-forms.md)
