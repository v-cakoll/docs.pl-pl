---
title: Wykryj, czy wtyczka WPF dla programu Firefox jest zainstalowana
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: 91680859c1742e5d5443d626c81273a80504f4a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740397"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a><span data-ttu-id="37bc4-102">Jak wykryć, czy wtyczka WPF dla Firefox jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="37bc4-102">How to: Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>

<span data-ttu-id="37bc4-103">Wtyczka Windows Presentation Foundation (WPF) dla przeglądarki Firefox Włącza aplikacje przeglądarki XAML (XBAP) i luźne pliki XAML do uruchomienia w przeglądarce Mozilla Firefox.</span><span class="sxs-lookup"><span data-stu-id="37bc4-103">The Windows Presentation Foundation (WPF) plug-in for Firefox enables XAML browser applications (XBAPs) and loose XAML files to run in the Mozilla Firefox browser.</span></span> <span data-ttu-id="37bc4-104">Ten temat zawiera skrypt zapisany w formacie HTML i JavaScript, za pomocą którego Administratorzy mogą określić, czy wtyczka WPF dla programu Firefox jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="37bc4-104">This topic provides a script written in HTML and JavaScript that administrators can use to determine whether the WPF plug-in for Firefox is installed.</span></span>

> [!NOTE]
> <span data-ttu-id="37bc4-105">Aby uzyskać więcej informacji na temat instalowania, wdrażania i wykrywania .NET Framework, zobacz [instalowanie .NET Framework dla deweloperów](../../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="37bc4-105">For more information about installing, deploying, and detecting the .NET Framework, see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>

## <a name="example"></a><span data-ttu-id="37bc4-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="37bc4-106">Example</span></span>

<span data-ttu-id="37bc4-107">Po zainstalowaniu .NET Framework 3,5 na komputerze klienckim jest konfigurowana wtyczka WPF dla programu Firefox.</span><span class="sxs-lookup"><span data-stu-id="37bc4-107">When the .NET Framework 3.5 is installed, the client computer is configured with a WPF plug-in for Firefox.</span></span> <span data-ttu-id="37bc4-108">Poniższy przykładowy skrypt sprawdza, czy wtyczka WPF dla programu Firefox, a następnie wyświetla odpowiedni komunikat o stanie.</span><span class="sxs-lookup"><span data-stu-id="37bc4-108">The following example script checks for the WPF plug-in for Firefox and then displays an appropriate status message.</span></span>

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

<span data-ttu-id="37bc4-109">Jeśli sprawdzanie wtyczki WPF dla programu Firefox powiedzie się, zostanie wyświetlony następujący komunikat o stanie:</span><span class="sxs-lookup"><span data-stu-id="37bc4-109">If the check for the WPF plug-in for Firefox is successful, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is installed.`

<span data-ttu-id="37bc4-110">W przeciwnym razie zostanie wyświetlony następujący komunikat o stanie:</span><span class="sxs-lookup"><span data-stu-id="37bc4-110">Otherwise, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a><span data-ttu-id="37bc4-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37bc4-111">See also</span></span>

- [<span data-ttu-id="37bc4-112">Wykrywanie, czy wtyczka .NET Framework 3.0 jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="37bc4-112">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [<span data-ttu-id="37bc4-113">Wykrywanie, czy wtyczka .NET Framework 3.5 jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="37bc4-113">Detect Whether the .NET Framework 3.5 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [<span data-ttu-id="37bc4-114">Aplikacje przeglądarek WPF XAML — omówienie</span><span class="sxs-lookup"><span data-stu-id="37bc4-114">WPF XAML Browser Applications Overview</span></span>](wpf-xaml-browser-applications-overview.md)
