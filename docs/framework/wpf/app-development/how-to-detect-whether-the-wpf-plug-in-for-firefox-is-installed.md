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
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a><span data-ttu-id="5fbb7-102">Jak wykryć, czy wtyczka WPF dla Firefox jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="5fbb7-102">How to: Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>
<span data-ttu-id="5fbb7-103">[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Dodatek plug-in dla przeglądarki Firefox umożliwia [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] utrata plików XAML, aby uruchomić w przeglądarce Mozilla Firefox.</span><span class="sxs-lookup"><span data-stu-id="5fbb7-103">The [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] plug-in for Firefox enables [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML files to run in the Mozilla Firefox browser.</span></span> <span data-ttu-id="5fbb7-104">Ten temat zawiera skrypt zapisywane w kodzie HTML i JavaScript, które Administratorzy mogą używać do określenia, czy jest zainstalowany dodatek plug-in dla przeglądarki Firefox WPF.</span><span class="sxs-lookup"><span data-stu-id="5fbb7-104">This topic provides a script written in HTML and JavaScript that administrators can use to determine whether the WPF plug-in for Firefox is installed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fbb7-105">Aby uzyskać więcej informacji na temat Instalowanie, wdrażanie i wykrywanie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], zobacz [Zainstaluj program .NET Framework dla deweloperów](../../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="5fbb7-105">For more information about installing, deploying, and detecting the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], see [Install the .NET Framework for developers](../../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fbb7-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fbb7-106">Example</span></span>  
 <span data-ttu-id="5fbb7-107">Gdy [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] jest zainstalowane, komputer kliencki jest skonfigurowany z użyciem WPF dodatek plug-in dla przeglądarki Firefox.</span><span class="sxs-lookup"><span data-stu-id="5fbb7-107">When the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, the client computer is configured with a WPF plug-in for Firefox.</span></span> <span data-ttu-id="5fbb7-108">W poniższym przykładzie skryptu wyszukuje WPF dodatek plug-in dla przeglądarki Firefox, a następnie wyświetli komunikat o stanie odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="5fbb7-108">The following example script checks for the WPF plug-in for Firefox and then displays an appropriate status message.</span></span>  
  
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
  
 <span data-ttu-id="5fbb7-109">Jeśli sprawdzanie WPF dodatek plug-in dla przeglądarki Firefox zakończy się pomyślnie, zostanie wyświetlony następujący komunikat o stanie:</span><span class="sxs-lookup"><span data-stu-id="5fbb7-109">If the check for the WPF plug-in for Firefox is successful, the following status message is displayed:</span></span>  
  
 `The WPF plug-in for Firefox is installed.`  
  
 <span data-ttu-id="5fbb7-110">W przeciwnym razie zostanie wyświetlony następujący komunikat stanu:</span><span class="sxs-lookup"><span data-stu-id="5fbb7-110">Otherwise, the following status message is displayed:</span></span>  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a><span data-ttu-id="5fbb7-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5fbb7-111">See Also</span></span>  
 [<span data-ttu-id="5fbb7-112">Wykryj, czy jest zainstalowany program .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="5fbb7-112">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)  
 [<span data-ttu-id="5fbb7-113">Wykryj, czy jest zainstalowany program .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="5fbb7-113">Detect Whether the .NET Framework 3.5 Is Installed</span></span>](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)  
 [<span data-ttu-id="5fbb7-114">Omówienie aplikacje przeglądarki XAML w WPF</span><span class="sxs-lookup"><span data-stu-id="5fbb7-114">WPF XAML Browser Applications Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)
