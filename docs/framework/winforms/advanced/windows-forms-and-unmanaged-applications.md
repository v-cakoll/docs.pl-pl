---
title: Aplikacje niezarządzane
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: 17dc20653d1628dfd460a9891e1b0a21c0ebecbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746366"
---
# <a name="windows-forms-and-unmanaged-applications"></a>Formularze systemu Windows i niezarządzane aplikacje
Windows Forms aplikacje i kontrolki mogą współdziałać z niezarządzanymi aplikacjami z pewnymi zastrzeżeniami. W poniższych sekcjach opisano scenariusze i konfiguracje, które Windows Forms aplikacjami i kontrolami, oraz te, które nie są obsługiwane przez klienta.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd formularzy Windows Forms i niezarządzanych aplikacji](windows-forms-and-unmanaged-applications-overview.md)  
 Zawiera ogólne informacje dotyczące sposobu użycia i implementacji formantów Windows Forms, które działają z niezarządzanymi aplikacjami.  
  
 [Instrukcje: obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md)  
 Zawiera przykładowy kod, który pokazuje, jak używać metody <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> do uruchamiania formularza systemu Windows w niezarządzanej aplikacji.  
  
 [Instrukcje: obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 Zawiera przykładowy kod, który pokazuje, jak uruchomić formularz systemu Windows w jego własnym wątku.  
  
 Zobacz również [Przewodnik: obsługa międzyoperacyjności modelu COM przez wyświetlanie każdego formularza systemu Windows w jego własnym wątku](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 Służy do tworzenia oddzielnego wątku dla formularza systemu Windows.  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 Uruchamia pętlę komunikatów dla wątku.  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 Kierowanie wywołań z niezarządzanej aplikacji do formularza.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Udostępnianie składników .NET Framework modelowi COM](../../interop/exposing-dotnet-components-to-com.md)  
 Zawiera ogólne informacje dotyczące używania typów .NET Framework w niezarządzanych aplikacjach.
