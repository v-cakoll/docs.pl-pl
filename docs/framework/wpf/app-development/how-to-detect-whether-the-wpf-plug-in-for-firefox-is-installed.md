---
title: "Jak wykryć, czy wtyczka WPF dla Firefox jest zainstalowana"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3012afc118420a83c869785d26c28f1eee969cb3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Jak wykryć, czy wtyczka WPF dla Firefox jest zainstalowana
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Dodatek plug-in dla przeglądarki Firefox umożliwia [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] utrata plików XAML, aby uruchomić w przeglądarce Mozilla Firefox. Ten temat zawiera skrypt zapisywane w kodzie HTML i JavaScript, które Administratorzy mogą używać do określenia, czy jest zainstalowany dodatek plug-in dla przeglądarki Firefox WPF.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat Instalowanie, wdrażanie i wykrywanie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], zobacz [Zainstaluj program .NET Framework dla deweloperów](../../../../docs/framework/install/guide-for-developers.md).  
  
## <a name="example"></a>Przykład  
 Gdy [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] jest zainstalowane, komputer kliencki jest skonfigurowany z użyciem WPF dodatek plug-in dla przeglądarki Firefox. W poniższym przykładzie skryptu wyszukuje WPF dodatek plug-in dla przeglądarki Firefox, a następnie wyświetli komunikat o stanie odpowiednie.  
  
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
  
 Jeśli sprawdzanie WPF dodatek plug-in dla przeglądarki Firefox zakończy się pomyślnie, zostanie wyświetlony następujący komunikat o stanie:  
  
 `The WPF plug-in for Firefox is installed.`  
  
 W przeciwnym razie zostanie wyświetlony następujący komunikat stanu:  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a>Zobacz też  
 [Wykryj, czy jest zainstalowany program .NET Framework 3.0](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)  
 [Wykryj, czy jest zainstalowany program .NET Framework 3.5](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)  
 [Omówienie aplikacje przeglądarki XAML w WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)
