---
title: Formularze systemu Windows i niezarządzane aplikacje
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: bc0c848d1c92871dacab93497c674645f3ac83fe
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615066"
---
# <a name="windows-forms-and-unmanaged-applications"></a>Formularze systemu Windows i niezarządzane aplikacje
Aplikacje Windows Forms i formanty może współpracować z niezarządzanych aplikacji za pomocą niektóre zastrzeżenia. Poniżej opisano scenariusze i konfiguracje obsługujące aplikacje i formanty Windows Forms oraz te, które nie obsługują.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd formularzy Windows Forms i niezarządzanych aplikacji](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 Udostępnia ogólne informacje o sposobie używania i zaimplementowania kontrolek Windows Forms, współpracujących z niezarządzanych aplikacji.  
  
 [Instrukcje: obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 Zawiera przykładowy kod, który pokazuje, jak używać <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę, aby uruchomić formularza Windows w niezarządzanej aplikacji.  
  
 [Instrukcje: obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 Zawiera przykładowy kod, który pokazuje, jak uruchomić formularza Windows w jego własnym wątku.  
  
 Zobacz też [wskazówki: Obsługa międzyoperacyjności modelu COM, wyświetlanie każdego formularzu Windows w jego własnej wątku](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 Użyty do utworzenia oddzielnego wątku dla formularza Windows.  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 Uruchamia pętli komunikatów dla wątku.  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 Organizuje wywołania z niezarządzanych aplikacji do formularza.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Udostępnianie składników .NET Framework modelowi COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 Udostępnia ogólne informacje o sposobie używania typów programu .NET Framework w aplikacjach niezarządzanych.
