---
title: 'Porady: nawigowanie do adresu URL za pomocą formantu WebBrowser'
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
ms.openlocfilehash: f6cb26ff247bba75cc351d453314bade2d38d9f5
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144841"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Porady: nawigowanie do adresu URL za pomocą formantu WebBrowser
Poniższy przykład kodu demonstruje sposób nawigowania <xref:System.Windows.Forms.WebBrowser> kontrolki do określonego adresu URL.

 Aby określić, kiedy nowy dokument jest w pełni załadowany, obsłużyć <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzenie. Aby zapoznać się z prezentacją tego zdarzenia, zobacz [How to: Print with WebBrowser control](how-to-print-with-a-webbrowser-control.md).

## <a name="example"></a>Przykład

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
```

## <a name="compiling-the-code"></a>Kompilowanie kodu
 Ten przykład wymaga:

- <xref:System.Windows.Forms.WebBrowser>Kontrolka o nazwie `webBrowser1` .

- Odwołania do `System` zestawów i `System.Windows.Forms` .

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [WebBrowser, kontrolka](webbrowser-control-windows-forms.md)
- [Instrukcje: drukowanie za pomocą kontrolki WebBrowser](how-to-print-with-a-webbrowser-control.md)
