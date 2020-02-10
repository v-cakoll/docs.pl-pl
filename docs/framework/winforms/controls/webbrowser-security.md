---
title: Zabezpieczenia WebBrowser
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: b25cabca050d06dbfe97c563eb56622d1f21be54
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095258"
---
# <a name="webbrowser-security"></a><span data-ttu-id="b9aa1-102">Zabezpieczenia WebBrowser</span><span class="sxs-lookup"><span data-stu-id="b9aa1-102">WebBrowser Security</span></span>
<span data-ttu-id="b9aa1-103">Formant <xref:System.Windows.Forms.WebBrowser> jest przeznaczony do pracy tylko w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="b9aa1-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="b9aa1-104">Zawartość HTML wyświetlana w formancie może pochodzić z zewnętrznych serwerów sieci Web i może zawierać kod niezarządzany w postaci skryptów lub kontrolek sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b9aa1-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="b9aa1-105">Jeśli używasz kontrolki <xref:System.Windows.Forms.WebBrowser> w tej sytuacji, formant nie jest mniej bezpieczny niż program Internet Explorer, ale zarządzany formant <xref:System.Windows.Forms.WebBrowser> nie uniemożliwia uruchamiania tego niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="b9aa1-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="b9aa1-106">Aby uzyskać więcej informacji na temat problemów z zabezpieczeniami związanych z podstawową kontrolką `WebBrowser` ActiveX, zobacz [formant WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="b9aa1-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9aa1-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9aa1-107">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="b9aa1-108">WebBrowser, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="b9aa1-108">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- <span data-ttu-id="b9aa1-109">[WebBrowser, kontrolka](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b9aa1-109">[WebBrowser Control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))</span></span>
