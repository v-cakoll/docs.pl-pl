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
ms.openlocfilehash: bee16a388d823f74bc9c88bc34b510d2a5907393
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649219"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="872f8-102">Instrukcje: nawigowanie do adresu URL za pomocą kontrolki WebBrowser</span><span class="sxs-lookup"><span data-stu-id="872f8-102">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="872f8-103">Poniższy przykład kodu pokazuje, jak nawigować po <xref:System.Windows.Forms.WebBrowser> kontroli na określony adres URL.</span><span class="sxs-lookup"><span data-stu-id="872f8-103">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>  
  
 <span data-ttu-id="872f8-104">Aby określić, kiedy nowy dokument jest w pełni załadowane, obsługi <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="872f8-104">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="872f8-105">Demonstracyjne tego zdarzenia, zobacz [jak: Drukowanie za pomocą formantu WebBrowser](how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="872f8-105">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="872f8-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="872f8-106">Example</span></span>  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="872f8-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="872f8-107">Compiling the Code</span></span>  
 <span data-ttu-id="872f8-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="872f8-108">This example requires:</span></span>  
  
- <span data-ttu-id="872f8-109">A <xref:System.Windows.Forms.WebBrowser> formantu o nazwie `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="872f8-109">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
- <span data-ttu-id="872f8-110">Odwołuje się do `System` i `System.Windows.Forms` zestawów.</span><span class="sxs-lookup"><span data-stu-id="872f8-110">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="872f8-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="872f8-111">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="872f8-112">WebBrowser, kontrolka</span><span class="sxs-lookup"><span data-stu-id="872f8-112">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="872f8-113">Instrukcje: Drukowanie za pomocą formantu WebBrowser</span><span class="sxs-lookup"><span data-stu-id="872f8-113">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
