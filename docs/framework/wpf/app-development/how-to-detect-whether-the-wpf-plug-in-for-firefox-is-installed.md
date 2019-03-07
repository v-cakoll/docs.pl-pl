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
ms.openlocfilehash: 138c212e79654b8ac875628692b49bb6a38cb695
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469316"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a><span data-ttu-id="0b14b-102">Instrukcje: Wykryj, czy wtyczka WPF dla Firefox jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="0b14b-102">How to: Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>

<span data-ttu-id="0b14b-103">Windows Presentation Foundation (WPF) wtyczka dla programu Firefox umożliwia [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] i luźno pliki XAML w celu uruchomienia w przeglądarce Mozilla Firefox.</span><span class="sxs-lookup"><span data-stu-id="0b14b-103">The Windows Presentation Foundation (WPF) plug-in for Firefox enables [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML files to run in the Mozilla Firefox browser.</span></span> <span data-ttu-id="0b14b-104">Ten temat zawiera skrypt napisany w kodzie HTML i JavaScript, które Administratorzy mogą używać do określenia, czy wtyczka WPF dla Firefox jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="0b14b-104">This topic provides a script written in HTML and JavaScript that administrators can use to determine whether the WPF plug-in for Firefox is installed.</span></span>

> [!NOTE]
> <span data-ttu-id="0b14b-105">Aby uzyskać więcej informacji na temat instalowania i wdrażania oraz wykrywanie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], zobacz [Instalowanie programu .NET Framework dla deweloperów](../../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="0b14b-105">For more information about installing, deploying, and detecting the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>

## <a name="example"></a><span data-ttu-id="0b14b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b14b-106">Example</span></span>

<span data-ttu-id="0b14b-107">Gdy [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] jest zainstalowane, komputer kliencki jest skonfigurowany przy użyciu wtyczka WPF dla Firefox.</span><span class="sxs-lookup"><span data-stu-id="0b14b-107">When the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, the client computer is configured with a WPF plug-in for Firefox.</span></span> <span data-ttu-id="0b14b-108">Poniższy przykładowy skrypt szuka wtyczka WPF dla Firefox, a następnie wyświetla komunikat o stanie odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="0b14b-108">The following example script checks for the WPF plug-in for Firefox and then displays an appropriate status message.</span></span>

```html
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

<span data-ttu-id="0b14b-109">W przypadku pomyślnego dostępności wtyczka WPF dla Firefox jest wyświetlany następujący komunikat o stanie:</span><span class="sxs-lookup"><span data-stu-id="0b14b-109">If the check for the WPF plug-in for Firefox is successful, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is installed.`

<span data-ttu-id="0b14b-110">W przeciwnym razie jest wyświetlany następujący komunikat o stanie:</span><span class="sxs-lookup"><span data-stu-id="0b14b-110">Otherwise, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a><span data-ttu-id="0b14b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b14b-111">See also</span></span>

- [<span data-ttu-id="0b14b-112">Wykrywanie, czy wtyczka .NET Framework 3.0 jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="0b14b-112">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [<span data-ttu-id="0b14b-113">Wykrywanie, czy wtyczka .NET Framework 3.5 jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="0b14b-113">Detect Whether the .NET Framework 3.5 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [<span data-ttu-id="0b14b-114">Aplikacje przeglądarek WPF XAML — omówienie</span><span class="sxs-lookup"><span data-stu-id="0b14b-114">WPF XAML Browser Applications Overview</span></span>](wpf-xaml-browser-applications-overview.md)
