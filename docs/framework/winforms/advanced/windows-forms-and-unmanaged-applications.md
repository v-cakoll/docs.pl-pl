---
title: "Formularze systemu Windows i niezarządzane aplikacje"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2672e8f87b28e81a9aa233cbf0f1b2c24b2239c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-and-unmanaged-applications"></a>Formularze systemu Windows i niezarządzane aplikacje
Aplikacji formularzy systemu Windows i formantów może współdziałać z niezarządzanych aplikacji, z niektórych ostrzeżenia. W poniższych sekcjach opisano scenariusze i konfiguracje obsługujące aplikacje i formantów formularzy systemu Windows oraz te, które nie obsługują.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd formularzy Windows Forms i niezarządzanych aplikacji](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 Udostępnia ogólne informacje o sposobie używania i implementować formanty formularzy systemu Windows, które współpracują z niezarządzanych aplikacji.  
  
 [Instrukcje: obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 Zawiera przykładowy kod, który przedstawia sposób użycia <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę do uruchomienia w formularzu systemu Windows w niezarządzanej aplikacji.  
  
 [Instrukcje: obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 Zawiera przykładowy kod, który pokazuje sposób uruchamiania formularza systemu Windows w jego własnym wątku.  
  
 Zobacz też [wskazówki: Obsługa międzyoperacyjności z modelem COM. wyświetlania każdego formularza systemu Windows w jego własnym wątku w](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 Pozwala utworzyć oddzielnym wątku dla formularza systemu Windows.  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 Uruchamia Pętla wiadomości dla wątku.  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 Marshals wywołania z niezarządzanych aplikacji z formularzem.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Udostępnianie składników .NET Framework modelowi COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 Udostępnia ogólne informacje o sposobie używania typów .NET Framework w niezarządzanych aplikacji.
