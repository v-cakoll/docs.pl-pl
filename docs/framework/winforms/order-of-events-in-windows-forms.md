---
title: Kolejność zdarzeń
description: Zapoznaj się ze szczegółami dotyczącymi kolejności zdarzeń w Windows Forms podczas kilku ważnych etapów w okresie istnienia aplikacji i kontrolek.
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: b16d544d11500b2c684e87a915fc4b8eec071faa
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904341"
---
# <a name="order-of-events-in-windows-forms"></a>Kolejność zdarzeń w formularzach systemu Windows
Kolejność, w której zdarzenia są zgłaszane w Windows Forms aplikacji, jest szczególnie interesująca dla deweloperów, którzy z kolei obsługują każde z tych zdarzeń. Gdy sytuacja wywołuje dokładnych obsługi zdarzeń, na przykład podczas ponownego rysowania części formularza, należy zapoznać się z dokładną kolejnością, w której zdarzenia są zgłaszane w czasie wykonywania. Ten temat zawiera pewne szczegóły dotyczące kolejności zdarzeń w kilku ważnych etapach w okresie istnienia aplikacji i kontroli. Aby uzyskać szczegółowe informacje na temat kolejności zdarzeń wejściowych myszy, zobacz [zdarzenia myszy w Windows Forms](mouse-events-in-windows-forms.md). Aby zapoznać się z omówieniem zdarzeń w Windows Forms, zobacz [Omówienie zdarzeń](events-overview-windows-forms.md). Aby uzyskać szczegółowe informacje na temat korzeń programów obsługi zdarzeń, zobacz [Omówienie obsługi zdarzeń](event-handlers-overview-windows-forms.md).  
  
## <a name="application-startup-and-shutdown-events"></a>Zdarzenia uruchamiania i zamykania aplikacji  
 <xref:System.Windows.Forms.Form>Klasy i <xref:System.Windows.Forms.Control> uwidaczniają zestaw zdarzeń związanych z uruchamianiem i zamykaniem aplikacji. Po uruchomieniu aplikacji Windows Forms zdarzenia uruchamiania głównego formularza są zgłaszane w następującej kolejności:  
  
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
  
 <xref:System.Windows.Forms.Application.ApplicationExit>Zdarzenie <xref:System.Windows.Forms.Application> klasy jest wywoływane po zdarzeniach zamknięcia głównego formularza.  
  
> [!NOTE]
> Visual Basic 2005 zawiera dodatkowe zdarzenia aplikacji, takie jak <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> i <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType> .  
  
## <a name="focus-and-validation-events"></a>Zdarzenia fokusu i walidacji  
 Gdy zmienisz fokus przy użyciu klawiatury (TAB, SHIFT + TAB itd.), wywołując <xref:System.Windows.Forms.Control.Select%2A> <xref:System.Windows.Forms.Control.SelectNextControl%2A> metody lub, lub ustawiając <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> Właściwość na bieżącą formę, zdarzenia fokusu <xref:System.Windows.Forms.Control> klasy są wykonywane w następującej kolejności:  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 Gdy zmienisz fokus przy użyciu myszy lub wywołując <xref:System.Windows.Forms.Control.Focus%2A> metodę, zdarzenia fokusu <xref:System.Windows.Forms.Control> klasy są wykonywane w następującej kolejności:  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](creating-event-handlers-in-windows-forms.md)
