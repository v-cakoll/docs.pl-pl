---
title: Dodatki Firefox wspierające wdrożenie aplikacji .NET
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: e018048df70470e349f06ac80e7a597cd742dac5
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690514"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>Dodatki Firefox wspierające wdrożenie aplikacji .NET
Włącz Windows Presentation Foundation () wtyczka WPF dla Firefox i .NET Framework Asystenta ustawień dla przeglądarki Firefox [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)], luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]i aplikacji ClickOnce do pracy z przeglądarki Mozilla Firefox.  
  
## <a name="wpf-plug-in-for-firefox"></a>Wtyczka WPF dla Firefox  
 Wtyczka WPF dla Firefox umożliwia [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i utracić wprowadzone [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki przejście, i uruchamiać na najwyższym poziomie lub w ramce IFRAME HTML w przeglądarce Firefox. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Jest [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, które mogą być publikowane na serwerze sieci Web uruchamiana w obsługiwanych przeglądarek. Luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest plikiem tylko do XAML, który może być przejście i wyświetlane w obsługiwanych przeglądarek, podobnie jak w pliku XML.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Wtyczki dla Firefox jest zainstalowana za pomocą programu .NET Framework 3.5. Okno 7 zawiera programu .NET Framework 3.5, ale nie obejmuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wtyczka dla programu Firefox. Nie można zainstalować [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wtyczkę dla przeglądarki Firefox w systemie Windows 7.  
  
 Nie ma programu .NET Framework 4 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wtyczka dla programu Firefox. Jeśli zainstalowano program .NET Framework 3.5 i .NET Framework 4, wtyczka WPF dla Firefox jest zainstalowana za pomocą programu .NET Framework 3.5. W związku z tym aplikacji .NET Framework 4 nadal będzie działać, ponieważ WPF Host załaduje poprawną wersję platformy. Aby uzyskać więcej informacji, zobacz [Host WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 .NET Framework Asystenta ustawień dla przeglądarki Firefox umożliwia uruchamianie za pomocą przeglądarki Firefox autonomicznej aplikacji ClickOnce. .NET Framework w Asystencie Firefox funkcji tak samo w przypadku, gdy jest zainstalowany, przed i po nim przeglądarki Firefox. Po uruchomieniu przeglądarki Firefox i [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] jest zainstalowany, Firefox wyszukuje i instaluje .NET Framework Assistant dla programu Firefox. Użytkownicy mogą konfigurować .NET Framework Asystenta ustawień dla przeglądarki Firefox, wykonaj następujące czynności:  
  
- Monituj przed uruchomieniem aplikacji ClickOnce.  
  
- Raport wszystkich zainstalowanych wersji programu .NET Framework lub tylko najnowszą wersję.  
  
 .NET Framework Assistant dla programu Firefox jest dołączana [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]. Aby uzyskać informacje o usuwaniu Asystenta pakietu .NET Framework dla programu Firefox, zobacz [jak usunąć Asystenta pakietu .NET Framework dla programu Firefox](https://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Zobacz także

- [Wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md)
- [Aplikacje przeglądarek WPF XAML — omówienie](wpf-xaml-browser-applications-overview.md)
- [Wykrywanie, czy wtyczka WPF dla Firefox jest zainstalowana](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
