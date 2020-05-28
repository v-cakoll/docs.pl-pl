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
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="33de1-102">Porady: nawigowanie do adresu URL za pomocą formantu WebBrowser</span><span class="sxs-lookup"><span data-stu-id="33de1-102">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="33de1-103">Poniższy przykład kodu demonstruje sposób nawigowania <xref:System.Windows.Forms.WebBrowser> kontrolki do określonego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="33de1-103">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>

 <span data-ttu-id="33de1-104">Aby określić, kiedy nowy dokument jest w pełni załadowany, obsłużyć <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="33de1-104">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="33de1-105">Aby zapoznać się z prezentacją tego zdarzenia, zobacz [How to: Print with WebBrowser control](how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="33de1-105">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>

## <a name="example"></a><span data-ttu-id="33de1-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="33de1-106">Example</span></span>

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
```

## <a name="compiling-the-code"></a><span data-ttu-id="33de1-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="33de1-107">Compiling the Code</span></span>
 <span data-ttu-id="33de1-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="33de1-108">This example requires:</span></span>

- <span data-ttu-id="33de1-109"><xref:System.Windows.Forms.WebBrowser>Kontrolka o nazwie `webBrowser1` .</span><span class="sxs-lookup"><span data-stu-id="33de1-109">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>

- <span data-ttu-id="33de1-110">Odwołania do `System` zestawów i `System.Windows.Forms` .</span><span class="sxs-lookup"><span data-stu-id="33de1-110">References to the `System` and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="33de1-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33de1-111">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="33de1-112">WebBrowser, kontrolka</span><span class="sxs-lookup"><span data-stu-id="33de1-112">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="33de1-113">Instrukcje: drukowanie za pomocą kontrolki WebBrowser</span><span class="sxs-lookup"><span data-stu-id="33de1-113">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
