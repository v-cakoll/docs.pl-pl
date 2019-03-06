---
title: Dodatki Firefox wspierające wdrożenie aplikacji .NET
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 837ed1cd41869031e8c0b549ffcd26e3285570cd
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368067"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>Dodatki Firefox wspierające wdrożenie aplikacji .NET
Włącz Windows Presentation Foundation () wtyczka WPF dla Firefox i .NET Framework Asystenta ustawień dla przeglądarki Firefox [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)], luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]i aplikacji ClickOnce do pracy z przeglądarki Mozilla Firefox.  
  
## <a name="wpf-plug-in-for-firefox"></a>Wtyczka WPF dla Firefox  
 Wtyczka WPF dla Firefox umożliwia [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] i utracić wprowadzone [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki przejście, i uruchamiać na najwyższym poziomie lub w ramce IFRAME HTML w przeglądarce Firefox. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Jest [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, które mogą być publikowane na serwerze sieci Web uruchamiana w obsługiwanych przeglądarek. Luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest plikiem tylko do XAML, który może być przejście i wyświetlane w obsługiwanych przeglądarek, podobnie jak w pliku XML.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Wtyczki dla Firefox jest zainstalowana za pomocą [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. Znajdują się w nim 7 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], ale nie uwzględnia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wtyczka dla programu Firefox. Nie można zainstalować [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wtyczkę dla przeglądarki Firefox w systemie Windows 7.  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] Nie obejmuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wtyczka dla programu Firefox. Jednakże jeśli obie [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] i [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] są zainstalowane, wtyczka WPF dla Firefox jest zainstalowana za pomocą [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. W związku z tym [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] aplikacje będą nadal działać, ponieważ WPF Host załaduje poprawną wersję platformy. Aby uzyskać więcej informacji, zobacz [Host WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 .NET Framework Asystenta ustawień dla przeglądarki Firefox umożliwia uruchamianie za pomocą przeglądarki Firefox autonomicznej aplikacji ClickOnce. .NET Framework w Asystencie Firefox funkcji tak samo w przypadku, gdy jest zainstalowany, przed i po nim przeglądarki Firefox. Po uruchomieniu przeglądarki Firefox i [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] jest zainstalowany, Firefox wyszukuje i instaluje .NET Framework Assistant dla programu Firefox. Użytkownicy mogą konfigurować .NET Framework Asystenta ustawień dla przeglądarki Firefox, wykonaj następujące czynności:  
  
-   Monituj przed uruchomieniem aplikacji ClickOnce.  
  
-   Raport wszystkich zainstalowanych wersji programu .NET Framework lub tylko najnowszą wersję.  
  
 .NET Framework Assistant dla programu Firefox jest dołączana [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]. Aby uzyskać informacje o usuwaniu Asystenta pakietu .NET Framework dla programu Firefox, zobacz [jak usunąć Asystenta pakietu .NET Framework dla programu Firefox](https://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Zobacz także
- [Wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md)
- [Aplikacje przeglądarek WPF XAML — omówienie](wpf-xaml-browser-applications-overview.md)
- [Wykrywanie, czy wtyczka WPF dla Firefox jest zainstalowana](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
