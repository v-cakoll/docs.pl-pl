---
title: 'Instrukcje: Wykryj, czy wtyczka WPF dla Firefox jest zainstalowana'
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: f017aec8788d9ed38476262bba457f4621217519
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677982"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Instrukcje: Wykryj, czy wtyczka WPF dla Firefox jest zainstalowana
Windows Presentation Foundation (WPF) wtyczka dla programu Firefox umożliwia [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] i luźno pliki XAML w celu uruchomienia w przeglądarce Mozilla Firefox. Ten temat zawiera skrypt napisany w kodzie HTML i JavaScript, które Administratorzy mogą używać do określenia, czy wtyczka WPF dla Firefox jest zainstalowana.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat instalowania i wdrażania oraz wykrywanie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], zobacz [Instalowanie programu .NET Framework dla deweloperów](../../../../docs/framework/install/guide-for-developers.md).  
  
## <a name="example"></a>Przykład  
 Gdy [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] jest zainstalowane, komputer kliencki jest skonfigurowany przy użyciu wtyczka WPF dla Firefox. Poniższy przykładowy skrypt szuka wtyczka WPF dla Firefox, a następnie wyświetla komunikat o stanie odpowiednie.  
  
```  
<HTML>  
  
  <HEAD>  
    <TITLE>Test for the WPF plug-in for Firefox</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT type="text/javascript">  
    <!--  
    function OnLoad()  
    {  
  
       // Check for the WPF plug-in for Firefox and report  
       var msg = "The WPF plug-in for Firefox is ";  
       var wpfPlugin = navigator.plugins["Windows Presentation Foundation"];  
       if( wpfPlugin != null ) {  
          document.writeln(msg + " installed.");  
       }  
       else {  
          document.writeln(msg + " not installed. Please install or reinstall the .NET Framework 3.5.");  
       }  
    }  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY onload="OnLoad()" />  
  
</HTML>  
```  
  
 W przypadku pomyślnego dostępności wtyczka WPF dla Firefox jest wyświetlany następujący komunikat o stanie:  
  
 `The WPF plug-in for Firefox is installed.`  
  
 W przeciwnym razie jest wyświetlany następujący komunikat o stanie:  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a>Zobacz także
- [Wykrywanie, czy wtyczka .NET Framework 3.0 jest zainstalowana](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [Wykrywanie, czy wtyczka .NET Framework 3.5 jest zainstalowana](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [Aplikacje przeglądarek WPF XAML — omówienie](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)
