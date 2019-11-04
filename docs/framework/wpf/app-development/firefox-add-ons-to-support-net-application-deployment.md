---
title: Dodatki Firefox wspierające wdrożenie aplikacji .NET
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 6e8a333fc84eb85b7a312cb87207ebc235fbfe9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424562"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>Dodatki Firefox wspierające wdrożenie aplikacji .NET
Wtyczka Windows Presentation Foundation (WPF) dla programu Firefox i asystenta .NET Framework dla przeglądarki Firefox umożliwiają korzystanie z aplikacji przeglądarki XAML (XBAP), luźnych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]i aplikacji ClickOnce do pracy z przeglądarką Mozilla Firefox.  
  
## <a name="wpf-plug-in-for-firefox"></a>Wtyczka WPF dla programu Firefox  
 Wtyczka WPF dla programu Firefox umożliwia działanie aplikacji XBAP i luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików do przechodzenia do i uruchamiania na najwyższego poziomu lub w pliku IFRAME HTML w przeglądarce Firefox. Aplikacja XBAP jest aplikacją [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], która może zostać opublikowana na serwerze sieci Web i uruchomiona w obsługiwanych przeglądarkach. Luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to plik tylko w języku XAML, który można przechodzenie do i wyświetlać w obsługiwanych przeglądarkach, podobnie jak plik XML.  
  
 Wtyczka [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dla programu Firefox jest instalowana z .NET Framework 3,5. Okno 7 zawiera .NET Framework 3,5, ale nie zawiera wtyczki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dla programu Firefox. Nie można zainstalować wtyczki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dla programu Firefox w systemie Windows 7.  
  
 .NET Framework 4 nie obejmuje wtyczki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dla programu Firefox. Jeśli jednak zarówno .NET Framework 3,5 i .NET Framework 4 są zainstalowane, wtyczka WPF dla programu Firefox zostanie zainstalowana z .NET Framework 3,5. W związku z tym .NET Framework 4 aplikacje będą nadal działać, ponieważ Host WPF załaduje poprawną wersję platformy. Aby uzyskać więcej informacji, zobacz [host WPF (PresentationHost. exe)](wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 Asystent .NET Framework dla programu Firefox umożliwia uruchamianie autonomicznych aplikacji ClickOnce w przeglądarce Firefox. Asystent .NET Framework dla programu Firefox działa identycznie, gdy jest zainstalowany przed i po przeglądarce Firefox. Po uruchomieniu przeglądarki Firefox i zainstalowaniu .NET Framework 3,5 SP1 program Firefox odnajdzie i instaluje asystenta .NET Framework dla programu Firefox. Użytkownicy mogą skonfigurować asystenta .NET Framework dla programu Firefox, aby wykonali następujące czynności:  
  
- Monituj przed uruchomieniem aplikacji ClickOnce.  
  
- Zgłoś wszystkie zainstalowane wersje .NET Framework lub tylko najnowszą wersję.  
  
 Asystent .NET Framework dla programu Firefox jest dołączony do .NET Framework 3,5 z dodatkiem SP1. Informacje o usuwaniu asystenta .NET Framework dla programu Firefox można znaleźć w temacie [How to remove the .NET Framework Assistant for Firefox](https://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Zobacz także

- [Wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md)
- [Aplikacje przeglądarek WPF XAML — omówienie](wpf-xaml-browser-applications-overview.md)
- [Wykrywanie, czy wtyczka WPF dla Firefox jest zainstalowana](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
