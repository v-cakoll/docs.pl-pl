---
title: Zabezpieczenia WebBrowser
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: 957c11a085c971a81e5baa81a5b797dd53f2451a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703435"
---
# <a name="webbrowser-security"></a><span data-ttu-id="6dfef-102">Zabezpieczenia WebBrowser</span><span class="sxs-lookup"><span data-stu-id="6dfef-102">WebBrowser Security</span></span>
<span data-ttu-id="6dfef-103"><xref:System.Windows.Forms.WebBrowser> Kontroli jest przeznaczona do pracy w trybie tylko pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="6dfef-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="6dfef-104">Zawartość HTML, wyświetlany w formancie mogą pochodzić z zewnętrznych serwerów sieci Web i może zawierać kodu niezarządzanego w formie skryptów lub formantów sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6dfef-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="6dfef-105">Jeśli używasz <xref:System.Windows.Forms.WebBrowser> kontroli w tej sytuacji formant jest nie mniej bezpieczne niż program Internet Explorer, ale zarządzanych <xref:System.Windows.Forms.WebBrowser> formantu nie uniemożliwia taki niezarządzany kod działa.</span><span class="sxs-lookup"><span data-stu-id="6dfef-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="6dfef-106">Aby uzyskać więcej informacji na temat problemów z zabezpieczeniami dotyczące podstawowych ActiveX `WebBrowser` sterowania, zobacz [formantu WebBrowser](https://go.microsoft.com/fwlink/?LinkId=198812).</span><span class="sxs-lookup"><span data-stu-id="6dfef-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](https://go.microsoft.com/fwlink/?LinkId=198812).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dfef-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6dfef-107">See also</span></span>
- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="6dfef-108">WebBrowser, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="6dfef-108">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- [<span data-ttu-id="6dfef-109">WebBrowser, kontrolka</span><span class="sxs-lookup"><span data-stu-id="6dfef-109">WebBrowser Control</span></span>](https://go.microsoft.com/fwlink/?LinkId=198812)
