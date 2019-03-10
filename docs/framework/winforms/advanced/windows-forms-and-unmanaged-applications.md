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
ms.openlocfilehash: 65465f22b1806d385523c894cce2103afe33c2f0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702662"
---
# <a name="windows-forms-and-unmanaged-applications"></a>Formularze systemu Windows i niezarządzane aplikacje
Aplikacje Windows Forms i formanty może współpracować z niezarządzanych aplikacji za pomocą niektóre zastrzeżenia. Poniżej opisano scenariusze i konfiguracje obsługujące aplikacje i formanty Windows Forms oraz te, które nie obsługują.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd formularzy Windows Forms i niezarządzanych aplikacji](windows-forms-and-unmanaged-applications-overview.md)  
 Udostępnia ogólne informacje o sposobie używania i zaimplementowania kontrolek Windows Forms, współpracujących z niezarządzanych aplikacji.  
  
 [Instrukcje: Obsługa międzyoperacyjności modelu COM za pomocą wyświetlania formularza Windows, za pomocą ShowDialog — metoda](com-interop-by-displaying-a-windows-form-shadow.md)  
 Zawiera przykładowy kod, który pokazuje, jak używać <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę, aby uruchomić formularza Windows w niezarządzanej aplikacji.  
  
 [Instrukcje: Obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza Windows w jego własnym wątku](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 Zawiera przykładowy kod, który pokazuje, jak uruchomić formularza Windows w jego własnym wątku.  
  
 Zobacz też [instruktażu: Obsługiwanie COM Interop poprzez wyświetlanie każdego formularzu Windows w jego własnym wątku](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 Użyty do utworzenia oddzielnego wątku dla formularza Windows.  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 Uruchamia pętli komunikatów dla wątku.  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 Organizuje wywołania z niezarządzanych aplikacji do formularza.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Udostępnianie składników .NET Framework modelowi COM](../../interop/exposing-dotnet-components-to-com.md)  
 Udostępnia ogólne informacje o sposobie używania typów programu .NET Framework w aplikacjach niezarządzanych.
