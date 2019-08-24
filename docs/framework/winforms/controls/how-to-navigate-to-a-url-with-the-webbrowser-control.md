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
ms.openlocfilehash: b6c1255fa17d91daaa73001fea04f26e73dba0ae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015829"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Instrukcje: nawigowanie do adresu URL za pomocą kontrolki WebBrowser
Poniższy przykład kodu demonstruje sposób nawigowania <xref:System.Windows.Forms.WebBrowser> kontrolki do określonego adresu URL.

 Aby określić, kiedy nowy dokument jest w pełni załadowany, obsłużyć <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzenie. Aby zapoznać się z prezentacją tego zdarzenia [, zobacz How to: Drukuj z kontrolką](how-to-print-with-a-webbrowser-control.md)WebBrowser.

## <a name="example"></a>Przykład

```vb
Me.webBrowser1.Navigate("http://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("http://www.microsoft.com");
```

## <a name="compiling-the-code"></a>Kompilowanie kodu
 Ten przykład wymaga:

- Kontrolka o `webBrowser1`nazwie. <xref:System.Windows.Forms.WebBrowser>

- Odwołania do `System` zestawów i `System.Windows.Forms` .

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [WebBrowser, kontrolka](webbrowser-control-windows-forms.md)
- [Instrukcje: Drukowanie za pomocą kontrolki WebBrowser](how-to-print-with-a-webbrowser-control.md)
