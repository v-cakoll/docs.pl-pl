---
title: "Jak konfigurować Visual Studio, aby debugować aplikację przeglądarki XAML i wywołać usługę sieci Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 330ee213e147cfef709c919c95cb0e58159bc37b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Jak konfigurować Visual Studio, aby debugować aplikację przeglądarki XAML i wywołać usługę sieci Web
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]Uruchom w piaskownicy zabezpieczenia częściowego zaufania, który jest ograniczony do strefy Internet zestawu uprawnień. Ten zestaw uprawnień ogranicza wywołania usługi sieci Web tylko usługi, które znajdują się w sieci Web [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] aplikacji witryny pochodzenia. Gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] debugowania z [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], ale uznano nie mają tej samej witrynie pochodzenia, zgodnie z sieci Web usługi odwołania. Wyjątki zabezpieczeń powoduje, że wygenerowany, gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] próby wywołania usługi sieci Web. Jednak [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] projektu można skonfigurować w celu symulowania o tej samej lokacji pochodzenia jako usługę sieci Web wywołuje podczas debugowania. Dzięki temu [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bezpiecznie wywołać usługę sieci Web bez powodowania wyjątki zabezpieczeń.  
  
## <a name="configuring-visual-studio"></a>Konfigurowanie programu Visual Studio  
 Aby skonfigurować [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] debugowania [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] wywołującym usługi sieci Web:  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  W **projektanta projektu**, kliknij przycisk **debugowania** kartę.  
  
3.  W **Akcja uruchamiania** zaznacz **uruchomienia programu zewnętrznego** i wprowadź następujące:  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  W **opcje uruchamiania** wprowadź poniższy **argumenty wiersza polecenia** pole tekstowe:  
  
     `-debug`  *Nazwa pliku*  
  
     *Filename* wartość **-debug** parametru jest nazwa pliku .xbap, np.:  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  Jest to konfiguracja domyślna rozwiązań, które zostały utworzone z [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] szablonu projektu.  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  W **projektanta projektu**, kliknij przycisk **debugowania** kartę.  
  
3.  W **opcje uruchamiania** Dodaj następujący parametr wiersza polecenia do **argumenty wiersza polecenia** pole tekstowe:  
  
     `-debugSecurityZoneURL`  *ADRES URL*  
  
     *Adres URL* wartość **- debugSecurityZoneURL** jest parametr [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] dla lokalizacji, w której chcesz symulować jako witryny pochodzenia aplikacji.  
  
 Na przykład należy wziąć pod uwagę [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] używającą usługi sieci Web z następującymi [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 Witryny pochodzenia [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] dla tej witryny sieci Web service jest:  
  
 `http://services.msdn.microsoft.com`  
  
 W rezultacie pełną **- debugSecurityZoneURL** parametru wiersza polecenia, a wartość to:  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## <a name="see-also"></a>Zobacz też  
 [Host WPF (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
