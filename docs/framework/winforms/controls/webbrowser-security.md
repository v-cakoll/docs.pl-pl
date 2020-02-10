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
# <a name="webbrowser-security"></a>Zabezpieczenia WebBrowser
Formant <xref:System.Windows.Forms.WebBrowser> jest przeznaczony do pracy tylko w trybie pełnego zaufania. Zawartość HTML wyświetlana w formancie może pochodzić z zewnętrznych serwerów sieci Web i może zawierać kod niezarządzany w postaci skryptów lub kontrolek sieci Web. Jeśli używasz kontrolki <xref:System.Windows.Forms.WebBrowser> w tej sytuacji, formant nie jest mniej bezpieczny niż program Internet Explorer, ale zarządzany formant <xref:System.Windows.Forms.WebBrowser> nie uniemożliwia uruchamiania tego niezarządzanego kodu.  
  
 Aby uzyskać więcej informacji na temat problemów z zabezpieczeniami związanych z podstawową kontrolką `WebBrowser` ActiveX, zobacz [formant WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.WebBrowser>
- [WebBrowser, kontrolka — omówienie](webbrowser-control-overview.md)
- [WebBrowser, kontrolka](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))
