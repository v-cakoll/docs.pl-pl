---
title: 'Porady: nawigowanie do adresu URL za pomocą formantu WebBrowser'
description: Dowiedz się, jak korzystać z Windows Forms WebBrowser. Przejdź do formantu, aby przejść do określonego adresu URL. Dowiedz się również, jak ustalić, kiedy nowy dokument jest ładowany.
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
ms.openlocfilehash: e6ad360cc73a84ca040869832bb59d354cb78bd5
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325572"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="42002-104">Porady: nawigowanie do adresu URL za pomocą formantu WebBrowser</span><span class="sxs-lookup"><span data-stu-id="42002-104">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="42002-105">Poniższy przykład kodu demonstruje sposób nawigowania <xref:System.Windows.Forms.WebBrowser> kontrolki do określonego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="42002-105">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>

 <span data-ttu-id="42002-106">Aby określić, kiedy nowy dokument jest w pełni załadowany, obsłużyć <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="42002-106">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="42002-107">Aby zapoznać się z prezentacją tego zdarzenia, zobacz [How to: Print with WebBrowser control](how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="42002-107">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>

## <a name="example"></a><span data-ttu-id="42002-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="42002-108">Example</span></span>

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
```

## <a name="compiling-the-code"></a><span data-ttu-id="42002-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="42002-109">Compiling the Code</span></span>
 <span data-ttu-id="42002-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="42002-110">This example requires:</span></span>

- <span data-ttu-id="42002-111"><xref:System.Windows.Forms.WebBrowser>Kontrolka o nazwie `webBrowser1` .</span><span class="sxs-lookup"><span data-stu-id="42002-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>

- <span data-ttu-id="42002-112">Odwołania do `System` zestawów i `System.Windows.Forms` .</span><span class="sxs-lookup"><span data-stu-id="42002-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="42002-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42002-113">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="42002-114">WebBrowser, kontrolka</span><span class="sxs-lookup"><span data-stu-id="42002-114">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="42002-115">Instrukcje: drukowanie za pomocą kontrolki WebBrowser</span><span class="sxs-lookup"><span data-stu-id="42002-115">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
