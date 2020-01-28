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
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Jak wykryć, czy wtyczka WPF dla Firefox jest zainstalowana

Wtyczka Windows Presentation Foundation (WPF) dla przeglądarki Firefox Włącza aplikacje przeglądarki XAML (XBAP) i luźne pliki XAML do uruchomienia w przeglądarce Mozilla Firefox. Ten temat zawiera skrypt zapisany w formacie HTML i JavaScript, za pomocą którego Administratorzy mogą określić, czy wtyczka WPF dla programu Firefox jest zainstalowana.

> [!NOTE]
> Aby uzyskać więcej informacji na temat instalowania, wdrażania i wykrywania .NET Framework, zobacz [instalowanie .NET Framework dla deweloperów](../../install/guide-for-developers.md).

## <a name="example"></a>Przykład

Po zainstalowaniu .NET Framework 3,5 na komputerze klienckim jest konfigurowana wtyczka WPF dla programu Firefox. Poniższy przykładowy skrypt sprawdza, czy wtyczka WPF dla programu Firefox, a następnie wyświetla odpowiedni komunikat o stanie.

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

Jeśli sprawdzanie wtyczki WPF dla programu Firefox powiedzie się, zostanie wyświetlony następujący komunikat o stanie:

`The WPF plug-in for Firefox is installed.`

W przeciwnym razie zostanie wyświetlony następujący komunikat o stanie:

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a>Zobacz także

- [Wykrywanie, czy wtyczka .NET Framework 3.0 jest zainstalowana](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [Wykrywanie, czy wtyczka .NET Framework 3.5 jest zainstalowana](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [Aplikacje przeglądarek WPF XAML — omówienie](wpf-xaml-browser-applications-overview.md)
