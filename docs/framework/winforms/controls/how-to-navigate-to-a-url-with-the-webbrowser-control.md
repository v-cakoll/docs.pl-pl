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
ms.openlocfilehash: f34577d45ddfbd2445fd4558c5694facf3f1aa29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531888"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="044e6-102">Porady: nawigowanie do adresu URL za pomocą formantu WebBrowser</span><span class="sxs-lookup"><span data-stu-id="044e6-102">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="044e6-103">Poniższy przykład kodu pokazuje sposób przejścia <xref:System.Windows.Forms.WebBrowser> kontroli z określonym adresem URL.</span><span class="sxs-lookup"><span data-stu-id="044e6-103">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>  
  
 <span data-ttu-id="044e6-104">Aby określić, kiedy nowy dokument zostanie całkowicie załadowany, obsługi <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="044e6-104">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="044e6-105">Aby demonstracyjne tego zdarzenia, zobacz [porady: drukowanie za pomocą formantu WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="044e6-105">For a demonstration of this event, see [How to: Print with a WebBrowser Control](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="044e6-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="044e6-106">Example</span></span>  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="044e6-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="044e6-107">Compiling the Code</span></span>  
 <span data-ttu-id="044e6-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="044e6-108">This example requires:</span></span>  
  
-   <span data-ttu-id="044e6-109">A <xref:System.Windows.Forms.WebBrowser> formantu o nazwie `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="044e6-109">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="044e6-110">Odwołuje się do `System` i `System.Windows.Forms` zestawów.</span><span class="sxs-lookup"><span data-stu-id="044e6-110">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="044e6-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="044e6-111">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>  
 [<span data-ttu-id="044e6-112">WebBrowser, kontrolka</span><span class="sxs-lookup"><span data-stu-id="044e6-112">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
 [<span data-ttu-id="044e6-113">Instrukcje: drukowanie za pomocą kontrolki WebBrowser</span><span class="sxs-lookup"><span data-stu-id="044e6-113">How to: Print with a WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
