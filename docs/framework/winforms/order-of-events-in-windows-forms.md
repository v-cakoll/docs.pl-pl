---
title: "Kolejność zdarzeń w formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f822133b44f0f32224402463b4332811f8cd52b5
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="order-of-events-in-windows-forms"></a>Kolejność zdarzeń w formularzach systemu Windows
Kolejność, w której zdarzenia są generowane w aplikacjach formularzy systemu Windows ma szczególne znaczenie dla deweloperów związane z obsługi każdego z tych zdarzeń z kolei. Rozwiązania wymaga dokładnych obsługi zdarzenia, na przykład gdy są ponownego narysowania części formularza, konieczne jest świadomości dokładne kolejności, w której zdarzenia są generowane w czasie wykonywania. Ten temat zawiera pewne szczegóły rzędu zdarzenia podczas kilka ważnych etapach cykl życia aplikacji i kontrolek. Aby uzyskać szczegółowe informacje o zamówieniu myszy zdarzenia wejściowe, zobacz [zdarzenia myszy w formularzach systemu Windows](../../../docs/framework/winforms/mouse-events-in-windows-forms.md). Przegląd zdarzeń w formularzach systemu Windows, temacie [Przegląd zdarzeń](../../../docs/framework/winforms/events-overview-windows-forms.md). Aby uzyskać więcej informacji o w skład programów obsługi zdarzeń, zobacz [Przegląd obsługi zdarzeń](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
## <a name="application-startup-and-shutdown-events"></a>Uruchamianie aplikacji i zdarzeń zamknięcia systemu  
 <xref:System.Windows.Forms.Form> i <xref:System.Windows.Forms.Control> klasy ujawnia zestaw zdarzeń związanych z aplikacji uruchamiania i wyłączania. Po uruchomieniu aplikacji formularzy systemu Windows zdarzenia uruchamiania formularza głównego pojawienia się w następującej kolejności:  
  
-   <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 Po zamknięciu aplikacji, zdarzenia zamknięcia formularza głównego pojawienia się w następującej kolejności:  
  
-   <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <xref:System.Windows.Forms.Application.ApplicationExit> Zdarzenie <xref:System.Windows.Forms.Application> klasy jest wywoływane po wykonaniu zdarzeń zamknięcia formularza głównego.  
  
> [!NOTE]
>  Visual Basic 2005 zawiera zdarzenia dodatkowych aplikacji, takich jak <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> i <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.  
  
## <a name="focus-and-validation-events"></a>Fokus i zdarzenia walidacji  
 Po zmianie fokusu przy użyciu klawiatury (TAB, SHIFT + TAB i tak dalej), przez wywołanie metody <xref:System.Windows.Forms.Control.Select%2A> lub <xref:System.Windows.Forms.Control.SelectNextControl%2A> metody, lub przez ustawienie <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> właściwości do bieżącego formularza zdarzenia fokus <xref:System.Windows.Forms.Control> klasy występują w następującej kolejności :  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
 Po zmianie fokusu za pomocą myszy lub poprzez wywołanie <xref:System.Windows.Forms.Control.Focus%2A> metody, zdarzenia fokus <xref:System.Windows.Forms.Control> klasy występują w następującej kolejności:  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
