---
title: Dodatki Firefox wspierające wdrożenie aplikacji .NET
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: f05f5afa0c0a7ef858442bd98233865834b8b89b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547446"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>Dodatki Firefox wspierające wdrożenie aplikacji .NET
Włącz Windows Presentation Foundation (WPF) dodatek plug-in dla przeglądarki Firefox i .NET Framework Assistant dla przeglądarki Firefox [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)], utracić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]i ClickOnce — aplikacje do pracy z przeglądarki Mozilla Firefox.  
  
## <a name="wpf-plug-in-for-firefox"></a>Dodatek Plug-in dla przeglądarki Firefox WPF  
 Dodatek plug-in dla przeglądarki Firefox WPF umożliwia [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i utracić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki do przejście i uruchamia na najwyższym poziomie lub z elementu IFRAME HTML przeglądarki Firefox. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Jest [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, które mogą być publikowane na serwerze sieci Web i uruchamiana w obsługiwanych przeglądarkach. Luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to plik tylko do języka XAML, który może być przejście i wyświetlane w obsługiwanych przeglądarkach, podobnie jak w pliku XML.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Dodatek plug-in dla przeglądarki Firefox jest instalowany z [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. Znajdują się w nim 7 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], ale nie obejmuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dodatek plug-in dla przeglądarki Firefox. Nie można zainstalować [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dodatek plug-in dla przeglądarki Firefox w systemie Windows 7.  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] Nie obejmuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dodatek plug-in dla przeglądarki Firefox. Jednak jeśli oba [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] i [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] są zainstalowane, dodatek plug-in dla przeglądarki Firefox WPF jest instalowany z [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. W związku z tym [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] aplikacje będą nadal działać, ponieważ WPF Host załaduje prawidłową wersję struktury. Aby uzyskać więcej informacji, zobacz [WPF hosta (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 .NET Framework Asystencie dla przeglądarki Firefox pozwala na uruchamianie z przeglądarki Firefox autonomicznej aplikacji ClickOnce. .NET Framework Asystencie Firefox funkcji tak samo w przypadku, gdy jest zainstalowany, przed i po przeglądarki Firefox. Po uruchomieniu przeglądarki Firefox i [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] jest zainstalowany, Firefox wyszukuje i instaluje Asystenta pakietu .NET Framework dla programu Firefox. Użytkownicy mogą konfigurować .NET Framework Asystencie dla przeglądarki Firefox wykonywać następujące czynności:  
  
-   Monituj przed uruchomieniem aplikacji ClickOnce.  
  
-   Raport wszystkich zainstalowanych wersji programu .NET Framework lub tylko najnowszą wersję.  
  
 .NET Framework Asystencie dla przeglądarki Firefox jest dołączana do [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]. Informacji o usuwaniu .NET Framework Assistant dla przeglądarki Firefox, zobacz [jak usunąć Asystenta pakietu .NET Framework dla programu Firefox](http://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie aplikacji WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [Aplikacje przeglądarek WPF XAML — omówienie](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)  
 [Wykrywanie, czy wtyczka WPF dla Firefox jest zainstalowana](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
