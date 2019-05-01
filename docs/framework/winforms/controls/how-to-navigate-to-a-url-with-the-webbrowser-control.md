---
title: 'Instrukcje: nawigowanie do adresu URL za pomocą kontrolki WebBrowser'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
ms.openlocfilehash: a174b6ae60f87e91e6f97e8fa7f8ad3892ef017a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913474"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Instrukcje: nawigowanie do adresu URL za pomocą kontrolki WebBrowser
Poniższy przykład kodu pokazuje, jak nawigować po <xref:System.Windows.Forms.WebBrowser> kontroli na określony adres URL.  
  
 Aby określić, kiedy nowy dokument jest w pełni załadowane, obsługi <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzeń. Demonstracyjne tego zdarzenia, zobacz [jak: Drukowanie za pomocą formantu WebBrowser](how-to-print-with-a-webbrowser-control.md).  
  
## <a name="example"></a>Przykład  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- A <xref:System.Windows.Forms.WebBrowser> formantu o nazwie `webBrowser1`.  
  
- Odwołuje się do `System` i `System.Windows.Forms` zestawów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [WebBrowser, kontrolka](webbrowser-control-windows-forms.md)
- [Instrukcje: Drukowanie za pomocą formantu WebBrowser](how-to-print-with-a-webbrowser-control.md)
